# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2021-04-26

### Added

- All docker builds are now automated and shipped to the `ddtraining` account.
- All services now have a `./build.sh` script which will help with future
  build automation efforts.
- There are now AKS deployment scripts! [#56](https://github.com/DataDog/ecommerce-workshop/pull/56)
- Speaking of deployments, all deployment methods and instructions live under
  `deployments/` complete with READMEs. Pull requests always welcome to improve
  these if you run into issues.
- There is now a traffic replay container [#38](https://github.com/DataDog/ecommerce-workshop/pull/38)

### Fixed

- All docker images are smaller which means faster startup times with less data
  to transfer.
- Fixed a typo with the RUM implementation [#98](https://github.com/DataDog/ecommerce-workshop/pull/98).
- We now use the gem versions of spree commerce which resolves the log spam of
  `Not a .git folder...` at startup.
- Most of the log noise from the storefront app has been silenced. Most of it.
  There is a more long-term fix planned for the next release.
- All of the services have had multiple security fixed applied. Thanks
  Dependabot! :heart:
- Fixed a dangling symlink that caused "No such file or directory" errors when
  building the storefront apps [#51](https://github.com/DataDog/ecommerce-workshop/pull/51)

### Changed

- The default branch has been renamed to `main` over `master`. If you have a
  local clone, you need to update your default branch like so:
  ```bash
  git branch -m master main
  git fetch origin
  git branch -u origin/main main
  ```
- The base app folder for all docker containers is now `/app` to be more
  idiomatic with docker packaging practices. All of the docker-compose configs
  have been updated to match this properly.
- The folder path for the frontend app is now just the base folder instead of
  being under `store-frontend`. So the storefront apps are now just under
  `store-frontend-instrumented-fixed` and `store-frontend-broken-instrumented`.
  This was done to simplify instructions for students so they aren't clicking
  through an extra layer of folders.
- The published docker image names for each service has changed:
  - `advertisements-service` is now `advertisements`
  - `discounts-service` is now `discounts`
  - `discounts-service-fixed` is now `discounts-fixed`
  - `ecommerce-frontend` is now `storefront`
  - `ecommerce-frontend-fixed` is now `storefront-fixed`
- Ruby and Python versions have been updated to their latest or closest to
  latest versions.
- The storefront service now uses [Semantic Logger](https://github.com/rocketjob/semantic_logger)
  for logging instead of Lograge. This drastically reduces the multi-line log
  noise. [#80](https://github.com/DataDog/ecommerce-workshop/pull/80)
