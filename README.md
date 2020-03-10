# oer-md-publish

Template repo for autobuilding OpenLearn sites via nbsphinx using Github Actions and publishing them via Github Pages. 

*Which means what exactly?*

It means you have access to OpenLearn content as simple text files that you can easily edit (i.e. repurpose) and publish via your own website using a free hosting service...

With the magic of Jupytext, it also means you can play with the content via a Jupyter notebook on MyBinder or your own local notebook server.

[![Binder](https://mybinder.org/badge_logo.svg)](https://gke.mybinder.org/v2/gh/psychemedia/openlearn-publish-test/master)


## Contents

- [So how do I start?](#so-how-do-i-start)
- [Reviewing Units on the OpenLearn Site](reviewing-units-on-the-openlearn-site)
- [What Happens When You Submit a "Fetch" Issue?](#what-happens-when-you-submit-a-fetch-issue)
- [So What Exactly Is "MyBinder"?](#so-what-exactly-is-mybinder)
- [Editing the Content on MyBinder](#editing-the-content-on-mybnder)
- [Editing the content on Github](#editing-the-content-on-github)
- [Editing the content on your own computer](#editing-the-content-on-your-own-computer)
- [So how does it work?](#so-how-does-it-work)


## So how do I start?

This template repository can be used as a basis for creating websites derived from OpenLearn content that is available in the OU-XML format (which is most OpenLearn units / courses).

To create your own OpenLearn content site, you need to get a Github account. You can [sign up here](https://github.com/join?source=header-home). Github is owned by Microsoft, so you will be giving your personal data to them...

When you are logged in to Github, generate a copy of this template repository by clicking the green *Use this template* button or [clicking here](https://github.com/psychemedia/openlearn-publish-test/generate).

When you clone the repo, it will also update it's own README to ensure that the links it contains work for your repository. This may take a moment or two, so grab a cup of tea, then refresh the repo homepage. (You can chek progress via the [`Actions`](../../actions) tab of your repo; if an action is running, it's not finished yet!)

In *your* copy of the repo, view the [`SET_UP.md`](./SET_UP.md) page to review a recent-ish list of OpenLearn units; click on the `Grab Unit into this repo` associated with a course to automatically open an issue that can be used to import the course material into your repository.


### Reviewing Units on the OpenLearn Site

If you would rather inspect a unit before importing it into your repository, browse for units using the [OpenLearn course unit](https://www.open.edu/openlearn/free-courses/full-catalogue). When you've found one you'd like to "appropriate", you need to grab its web address / URL: you're looking for a URL that __ends__ in something like `/content-section-0` or `/content-section-0?active-tab=description-tab` (the section number doesn't matter...).

For example, something like:

`https://www.open.edu/openlearn/science-maths-technology/learn-code-data-analysis/content-section-overview-0?active-tab=description-tab learn_to_code`

Copy the URL.

In your repository, go to the [`Issues` tab](.../../issues) and create a new issue by clicking on the green *New issue* button. (Alternativley, [this link](../../issues/new) may do it?)

In the title box, enter:

`Fetch https://www.open.edu/openlearn`

In the main body of the comment, on the first line, paste the URL you copied.

Click the green *Submit new issue* button and go and grab a cup of tea (the first build make take five to ten minutes).


## What Happens When You Submit a "Fetch" Issue?

When you submit the issue, a little helper elf will go and grab the unit,  convert it to a text format, and commit it to your repository in the `content` folder.

__If I have set things up properly, only issues created by you or a collaborator on the repo should trigger any data grabbing and website building activity. If you submit another issue, it will essentially reset the repo, so any changes you have made to content will be lost.__

The import and conversion proceess may take a few minutes, so be patient. You can keep track of activity from your repository's [`Actions`](../../Actions) tab. When the `Fetch https://www.open.edu/openlearn` headed action has completed,  refresh your repository homepage. Click on the `content` directory link in your repository file list (or [click here](./content) and you should see some file directories that contain simple markdown text files that have been generated from the source file for the OpenLearn content.

These files should also have been rendered elsewhere in the repository as HTML web pages (you don't need to know where, but if you're interested, they're in the `gh-pages` branch of the repository... If you don't know what that means, *it doesn't matter*.). You should be able to see the website rendered from them on a URL with the pattern:

`https://YOUR_GITHUB_USERNAME.github.io/YOUR_REPO`

So for example, this repo is:

`https://github.com/psychemedia/openlearn-publish-test/`

and the associated website is at:

`https://psychemedia.github.io/openlearn-publish-test/`

If the website *isn't* there, you may need to give the Github Pages website builder a prod. Go to your repository settings page from the *Settings* tab on the repo toolbar (or [click here](../../settings)) and scroll down until you see the __Github Pages__ heading. Their *should* be a green highlighted link to your pages there. If there *isn't*, in the *Source* dropdown list select `master branch` and then select `gh-pages branch`. This should kick things back into action. After a minute or two, refresh the page and a green backgounded link to you website should be there.

If you click on the link and the OpenLearn materials *aren't* there, force a reload of the webpage in your browser to clear any cached versions of the page.


## So What Exactly Is "MyBinder"?

MyBinder is part of a the Jupyter ecosytem. Clicking the button will cause MyBinder to launch a Jupyter notebook server that looks onto an environment created from this repository.

*When you clone the repo, the button will still point to my repo. I havenlt got round to creating a Github Action to fix that yet... Feel free to edit the `README.md` file on your repository to fix it yourself, or copy your repo URL and paste it into the box at [mybinder.org](https://mybinder.org) to launch your repo via the MyBinder homepage.*

When the Binderised environment is built, the notebook server launched into the `content` directory (you shuld be redirected to it automatically). Click through to the `content` directory and then to one of section folders; click on one of the markdown file links. The document will open up in the interactive, read/write Jupyter notebook user interface. Which means you can edit it, execute any code in it, add and execute code of your own.

*Unfortunately*, there's no safe and direct way of saving your content back to the repository. Instead, you'll have to click on the `Download` button in a notebook toolbar and then open your browser onto the appropriate directory in your repo, and drag the file you just downloaded onto that directory listing. You should see an upload view to upload the files. Commit them (with an explanatory note about them) and the build and republish should be kicked into action again.


## Editing the content on Github

From the Github repository homepage, you can navigate to any or the source markdown webpages and click on the pencil icon (`Edit this file`) button at the bottom of the page. When you are happy with your changes, click the green *Commit changes* button at the bottom of the page. You may also want to edit a *commit message* to describe the change(s) your made.

When you commit the change, a new HTML version of the page will be generated and published to your Github Pages website.

There's a lot more things possible, but I need to write some more docs to explain exactly what...


## Editing the content on MyBinder / Binderhub

If you launch your repo into MyBinder, you can edit the content via a Jupyter notebook user interface: navigate to the `content/` folder and then click on a file to open it, and edit it, via a Jupyter notebook UI.

If you go back the notebook file listing page, you can right-click on a file and download it. On your Github repo page, go to the `content` directory and then to the same directory name that your edited file was in; drag your downloaded file onto the Github page and an an *upload* view should appear.

Wait for the file to upload (the blue background upload status bar turns white when the upload is complete) and then commit it by pressing the big green *Commit* button. Once it is committed, your Github pages site should rebuild to reflect the change.

Alternatively, if you have changed several files in the MyBinder environment, go to the notebook page that lists the contents of the `content/` folder and click the *Download as zip* button in the top right hand corner of the page.

This will download a file called `content.zip` to your desktop. Drag the downloaded `content.zip` file onto your Github repo homepage to upload it. Wait for the file to upload (the blue background upload status bar turns white when the upload is complete) and then commit it by pressing the big green *Commit* button. Once it is committed, *__the contents of the original `content` directory will be deleted__* and the contents of the `content.zip` file unzipped into a newly created `content` directory. The Github pages site should rebuild to reflect the change.


## Editing the content on your own computer

There are several ways you can work with the content locally.

Firstly, you can download a zip file containing the contents of your repo, make changs to the files, and then upload them as per the MyBinder route.

Secondly, if you are a git user, you can clone the repository to a local git repository on your computer, make changes to the  files, commit them and push them back to the `master` branch on the Github repository; the commit to master will force any pages that need rebuilding to be rebuilt.

Thirdly, you can run a notebook container derived from your repo locally, allowing you to edit files within a notebook environment (as per the MyBinder route), but on your own computer, then downloading and uploading the files as per the MyBinder route, or via your own git environment. The easiest way of running the container (which is the same as the one that runs on MyBinder), is by using [ContainDS](https://containds.com/). [Download and install Docker Desktop](https://www.docker.com/products/docker-desktop) and then [download and install ContainDS](https://containds.com/download/). Launch *ContainDS*, click on the *Binder* tab, paste in the URL of your repository on Github, and click *Launch*. A Docker image will be built for you from the repo using `repo2docker`. Once the image has been built, which may take some time on the first run, you will be presented with a container configuration page. Give your container meaningful name (no spaces...) and for the *workspace path* select the directory you want the repo files to be stored in. Click *Create* and the container will be launched. Click on the *Web* icon in the toolbar to open the container's notebook server homepage in your browser. You can then edit the files as you would in MyBinder. Start and stop the container as required from the *ContainDS* application. Your files will always be available in the directory you specified, whether or not the container is running.


## So how does it work?

Short answer: *string'n'glue*.

Longer answer: when you submit this issue, it triggers a Github Action, (a bit like a helpful brownie of folklore fame) that grabs a "source code" version of the OpenLearn unit (an XML document in the OU-XML format). A Python package ([open-ouxml-tools](https://github.com/innovationOUtside/open-ouxml-tools)) is then used to convert this XML to markdown document and places them in the `content` directory, along with an index generating page (`index.rst`) in the top level of the directory. These files are then automatically *committed* and *pushed* the top level of the repository.

The action then uses the Sphinx documentation generation tool to render the markdown pages as HTML. In fact, a lot of magic is done using the `nbsphinx` package with a bit of help from the Jupytext package as part of the conversion. The actual conversion process is `md -> Jupyter notebook (ipynb) -> HTML`. The reason for doing this is that we can edit the markdown in a rich Jupyter notebook style environment to preview various interactive things that we can also render to HTML. It also means that we can execute Python code included in the markdown documents and render the outputs from that code execution (which might include charts, for example, or data tables) in the final HTML. But that needs another set of docs to explain properly...

Once the HTML has been generated, some more Github Action magic copies the HTML pages to where they need to be so that they're viewable as the final, published Github Pages website.
