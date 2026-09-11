# Brawl Voice for GitHub Pages

Prepared migration of the existing minimal Brawl Voice website. This package has not yet been uploaded to GitHub or published there.

The website uses GitHub Pages. The Windows installer uses a GitHub Release, so visitors download the original file directly without JavaScript or binary chunks. Relative asset paths support both a project URL and a custom domain.

## Publish

1. Create a public GitHub repository, for example `brawl-voice`, with default branch `main`. Add this package's source files, including `.github/workflows/pages.yml`. Do not add `release-assets` to Git: it is already excluded by `.gitignore`.
2. In the repository's **Settings → Pages**, set the source to **GitHub Actions**.
3. Create a release with tag **v0.2.0**, targeting `main`. Attach `release-assets/Brawl-Voice-Setup-0.2.0-x64.exe` and `release-assets/SHA256SUMS.txt`. Publish the release.
4. The **Publish Brawl Voice website** workflow runs automatically. Its successful deployment provides the live Pages URL. Future pushes to `main` also update the site.

The repository and installer release must be public for anyone to download the app. The deployment account needs repository administration/Pages permissions. No paid hosting, domain, or application server is configured by this package.

## Verification and behavior

The included installer is 136,433,391 bytes. Its SHA-256 is `170f10b8856190d53b6d2102a85584df23b3ce722ba95df7337e236854b679f9`.

The build checks the published release tag, asset name, upload state, size, download URL and checksum when GitHub supplies it. It stops before deployment if the installer is missing or invalid. Run the workflow again after correcting the release if necessary.

The checked-in `site/index.html` is a template. The workflow replaces its download placeholder with the real release URL and publishes only `dist`. No account name or repository URL has been guessed.

The app's shared-host requirement remains explained in the guide. Hosting the download website does not host multiplayer voice rooms.

## Official setup references

- [GitHub Pages workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)
- [Configuring the publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [Distributing binaries with releases](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github)

The original private website remains available while this migration is pending.
