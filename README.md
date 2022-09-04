# Docker publisher
Tool for invoking 'docker buildx' on linux with configures arguments.

[![commit activity](https://img.shields.io/github/commit-activity/m/rundqvist/tools-docker-publisher)](https://github.com/rundqvist/tools-docker-publisher)
[![last commit](https://img.shields.io/github/last-commit/rundqvist/tools-docker-publisher.svg)](https://github.com/rundqvist/tools-docker-publisher)

## Features
* Building and publishing multiple architectures
* Configuration file support for pre-configured docker images
* Git integration reading branch and tag names
* Preventing accidental releases from wrong branch

## Documentation
### Configuration file 
The 'docker-publisher' tool supports pre configuration by creating the file ```.docker-publisher.conf``` file in the same folder as your Dockerfile.

| Config | Comment |
| - | - |
| ```user``` | The username part in docker ```username/repository:tag``` uri |
| ```name``` | The repository part in docker ```username/repository:tag``` uri |
| ```tagrelease``` | The default tag to use when releasing (default: 'latest') |
| ```tagdev``` | The default tag to use when publishing a development image (default: 'dev') |
| ```arch``` | Architecture(s) to build and publish |
| ```gitenabled``` | Enable get values from GIT (default: true) |
| ```gitmaster``` |  Name of the master/main branch (default: master) |
| ```gitallowtag``` | Allow release from git tag (default: true) |
| ```gitallowmaster``` | Allow release from gitmaster branch (default: false) |
| ```gitallowbranch``` | Allow release from branch other than gitmaster (default: false) |

### Arguments
The configuration can be overridden by passing arguments.
| Argument | Comment |
| - | - |
| ```-u``` | The username part in docker ```username/repository:tag``` uri |
| ```-n``` | The repository part in docker ```username/repository:tag``` uri |
| ```-a``` | Architecture(s) to build and publish |
| ```-r``` | Make release. Adds the configured 'tagrelease' |
| ```-d``` | Make dev release. Adds the configured 'tagdev' |
| ```-t``` | The tag part in docker ```username/repository:tag``` uri.<br/>Can be used multiple times, or in combination with ```-r``` and ```-d``` to add multiple tags |
| ```-p``` | Path to Dockerfile to build and publish |
| ```-f``` | Force release/publish and override 'gitallow*'-settings from config file |

### Git and file system integration
If config 'gitenabled' is true, the tool validates current branch and gets current tag name to tag release (switch local repository to a tag and just execute with ```docker-publisher -r```).

If 'user' and/or 'name' isn't configured by other means, the tool reads current path and sets imagename (docker repository) to current folder and username to one level above.

Example:<br/>
A Dockerfile in path ```/home/myuser/myfolder/``` will publish image as ```myuser/myfolder:[tag]```.

## Issues and feature requests
Please report issues at https://github.com/rundqvist/tools-docker-publisher/issues

## Donations
Please support the development by making a small donation.

[![Revolut](https://img.shields.io/badge/support-Revolut-0665eb)](https://revolut.me/qvist)
[![Flattr](https://img.shields.io/badge/support-Flattr-brightgreen)](https://flattr.com/@rundqvist)
[![By me a coffee](https://img.shields.io/badge/support-Buy%20me%20a%20coffee-orange)](https://www.buymeacoffee.com/rundqvist)
[![PayPal](https://img.shields.io/badge/support-PayPal-blue)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=SZ7J9JL9P5DGE&source=url)