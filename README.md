# Ingo's Masonry Theme for Shopware 6 

## sw-IngoSMasonryTheme

A Shopware 6 theme used for my demo shop(s) to experiment and showcase frontend customization possibilities while maintaining performance, sustainability, and accessibility.

Content and style are partially inspired by potential customers' requirements.

 - masonry layout for product grid view
 - apricot color palette
 - web fonts
 - ...

The development enviroment is the same as the one used for [Ingo's Cost Transparency](https://github.com/openmindculture/sw-IngoSCostTransparency) extension, based on my [Shopware 6 Theme/Plugin Development Template](https://github.com/openmindculture/IngoSDev6CertPrep), using the Dockware docker-compose setup.

Contribution: you can open issues and pull requests on GitHub.

## Development

### Dockware Development Environment

Thanks to [dasistweb](https://www.dasistweb.de/), the Docker-based [dockware](https://docs.dockware.io/) containers provide a useful alternative to Shopware's nixOS/flex/[devenv-based approach](https://developer.shopware.com/docs/guides/installation/devenv.html). The setup is based on the lastest dev image. We don't need no parent project container repository anymore! `custom/plugins` is now mounted to the project `src` directory as recommended in the [dockware example files on GitHub](https://github.com/dockware/examples).

### Start the Shopware Development Container

- `docker compose up -d`

### Open the Storefront or Administration in a Browser

- http://localhost/
- http://localhost/admin (default credentials: admin:shopware)

### Enter the Container Shell

- `docker exec -it masonry bash`

You will start in the Shopware project root `/var/www/html` where you can type console commands like
`bin/console plugin:create foobar`
to create a new plugin structure.

- use IngoSMasonryTheme in the storefront and for development
  - `bin/console plugin:refresh`
  - `bin/console plugin:install --activate IngoSMasonryTheme`
  - `bin/console theme:refresh`
  - `bin/console theme:change`

#### Useful Console Commands

- `bin/build-storefront.sh`
- `bin/console cache:clear`
- `bin/console theme:refresh`

#### Optional Verbose vs. Silent Switches

There is no verbose switch.
Scripts seem to output verbose warnings by default. Add `--no-debug` to suppress  noncritical warnings and deprecation messages, e.g.:

- `bin/console theme:compile --no-debug`

### Stop the Container

- `docker-compose stop`

### Remove the Container

- `docker-compose down -v` (-v will remove created volumes)

## Logfile Locations

### Shopware Logs in Dockware

- `/var/www/html/var/log`

#### System Logs in Dockware

- `/var/log`

### Shopware Platform Source Code in Dockware

- `/var/www/html/vendor/shopware`

- TODO: mounting this as a secondary volume broke the installation.

- Workaround to see the shop source in the IDE: check it out into another, git-ignored, directory:

- `git clone https://github.com/shopware/shopware.git sw_platform_src`

- then "mark directory as" -> "sources root"

### Extension Export and Verification

Last but not least, you can build an exportable zip archive file to upload into a shop backend or Shopware's plugin marketplace.

There is an optional Shopware CLI that is not included in Dockware. You can get it from
[sw-cli.fos.gg](https://sw-cli.fos.gg) and use the `extension` command to build a theme file:

- `shopware-cli extension zip MyTheme`
