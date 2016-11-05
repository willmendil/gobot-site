## Gobot Website

This is the code for the website for Gobot (http://gobot.io) a framework for robotics, physical computing, and the Internet of Things (IoT) written using the Go programming language (http://golang.org/)

If you are looking for the actual Gobot code itself, it is at https://github.com/hybridgroup/gobot

This site is built using [Middleman](http://middlemanapp.com/basics/getting-started/)

To run locally:

      bundle install
      bundle exec middleman

### Documentation

This project uses HAML.

If you want to help us with the documentation of the site, you can follow this steps :

- 1) Download the zip of the branch "master" or clone the project with git.

		  git clone git@github.com:hybridgroup/gobot-site.git "name"

- 2) Create a new branch for the project and switch to that new branch.

		  git branch "new_name"
		  git checkout "new_name"

  or

      git checkout -b "new_name"

- 3) Open the project with your favourite text editor.

- 4) Go to the file `source/documentation` , which has all the documentation of the site.

#### Platforms

All of the page content is generated from the platform's github repo. To add new documentation to any platform, edit the readme in the respective [Gobot module's repository](https://github.com/hybridgroup/gobot/tree/master/platforms).

In order for the readme to be properly extracted, the content being pushed to the site must:

- include a `## How to Install` section following the platform introduction
- have a new line after each code block

To import platforms from the main Gobot repository, run the `bin/import_platforms` script. You'll need to have Git installed.

This script will:

- clone down the Gobot repos
- extract all platform readmes
- convert github markdown syntax to be haml compatible
- save the platform documentation to `source/documentation/platforms/partials`

#### Drivers

To add new information to any driver, do this :

- 1) Go to the file `source/documentation/drivers` , and select the driver you want to edit.

#### Examples

To import examples from the main Gobot repository, run the `bin/import_examples`
script. You'll need to have Git installed.

This script will:

- clone down the Gobot repo
- extract all examples
- create missing example pages and remove those that have also been removed from the main repo
- create/update examples index page

#### Repo Docs

To import docs partials from Gobot adaptor repositories, run the
`bin/import_repo_docs` script.

This script will:

- clone down Gobot adaptor repositories
- extract all `docs/*.md` documents
- add them as partials to `source/documentation/drivers/partials`

If you want to only import docs from a single repo:

```
bin/import_repo_docs hybridgroup/gobot-gpio
```

or

```
bin/import_repo_docs https://github.com/hybridgroup/gobot-gpio.git
```

### Images

To add images for platforms or devices:

- remove entire background
- the image should be 800 width x 600 height
- layer effect: White color overlay with blend mode HUE

Background color is #F3F1EB

### Send your Pull Request

When you have your code ready, create a new PR : `base: master` and `compare:"your_branch"`

### Deploy

[middleman-gh-pages](https://github.com/neo/middleman-gh-pages) gem is being used to build the webpage and deploy to gh-pages branch.

For deploying the webpage, your must be in 'master' branch and run the following command:

      rake publish

You must not have any uncomitted or untracked files in the site dirs, or the publish operation will fail with a message such as `Directory not clean`.

If the publish fails, you might need to remove the `build` dir before trying to run `rake publish` again.
