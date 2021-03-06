NodeJS + express + socket.io Example for CS193C
==================

This is a quick example set up for Stanford's CS193C during Summer 2011 to demo how to use NodeJS, with supplemental files for getting this running on Heroku. It's intended to get people up to speed very quickly, so it sacrifices breadth for brevity.

These directions are primarily directed at Unix-based users (i.e. on OS X). If that's not you, see the resources section at the bottom for more information on how to get this all going.

Layout
------

- `simple` contains a very simple example that doesn't depend on any other files. It uses just express, without any templates.
    - `simple/app.js` runs the express server.

- `complex` is a more complicated example that includes rendering templates and accepting POST requests, as well as serving static files. Depends on:
    - `complex/app.js` runs an express server with more features.
    - `complex/public` contains a `css` directory that contains the static CSS files that are served to style the pages found in...
    - `complex/views` contains [EJS](http://embeddedjs.com/ "EmbeddedJS") templates. `layout.ejs` is rendered for every page, and subpages replace the `<%- body %>` element. Each other *.ejs file contains a template that can be rendered. 

- `socket-simple` is a simple [socket.io](http://socket.io/) example, adapted from http://socket.io/#how-to-use
    - `socket-simple/app.js` runs the server side of the socket.
    - `socket-simple/public/index.html` contains the client-side code.

- `socket-game` is maybe the most complicated example: it uses RaphaelJS and socket.io to play simple networked game. Its client code is in `/public/index.html`, and is included as a tech demo without much futher explanation. You can try it out on your machine, or on http://node.heyanderson.com/. Get some friends to go to that URL with you.

- Other files:
    - `package.json` defines the packages that we want to use with node to serve the website. That's Express and EmbeddedJS.
    - `Procfile` is used on Heroku to define what we want to run. It's set right now to run the complex example.

Directions
----------

1. Get node and npm working. Open a terminal, then run these commands:

        curl http://nodejs.org/dist/node-v0.4.7.tar.gz | tar xvz
        cd node-v0.4.7
        ./configure
        make
        sudo make install       # you'll have to enter your password
        curl http://npmjs.org/install.sh | sudo sh

2. Download this tutorial (you have to modify the last line):

        curl -L https://github.com/chanderson0/cs193c-nodejs-example/tarball/master | tar xvz
        cd chanderson0-cs193c-nodejs-example-<RANDOM_NUMBERS>

3. Try the `simple` example:

        cd simple        # go to the app directory
        npm install      # installs needed packages
        node app.js      # runs webserver

4. Try these urls:

    - http://localhost:3000/
    - http://localhost:3000/hello?name=Sally
    - http://localhost:3000/greetings/John

5. Now, quit that process and load up the `complex` example.

        cd ../complex    # go to next app directory 
        npm install      # install packages for second app
        node app.js      # runs webserver

6. Try these urls:

    - http://localhost:3000/

Using Heroku
------------

1. First, sign up for [Heroku](http://heroku.com/ "Heroku").

2. Get the heroku gem running on your machine (you'll have to enter your password)

        sudo gem install heroku

3. Now, we have to get everything setup with Git. 

    - On OS X, install git via this link: http://git-osx-installer.googlecode.com/files/git-1.7.6-x86_64-snow-leopard.dmg
    - Now, set up your SSH keys. Follow this guide until step 3: http://help.github.com/mac-set-up-git/

4. Get heroku working with the keys you just generated:

        heroku keys:add

5. Create a git repo for all this stuff (inside the `complex` directory):

        cd complex
        git init
        git add .
        git commit -m "initial commit"

6. Create a heroku app, and push our stuff to it

        heroku create --stack cedar
        git push herkou master

7. If everything went well, you should be able to run `heroku open` and see your app!

More Resources
--------------

### Guides
- [Getting Started on Heroku](http://devcenter.heroku.com/articles/quickstart)
- [The Node Beginner Book](http://www.nodebeginner.org/)

### References
- [ExpressJS](http://expressjs.com/)
- [NodeJS](http://nodejs.org/)
- [EJS](http://embeddedjs.com/)
- [socket.io](http://socket.io/)

### Windows
- Getting Node set up: https://github.com/joyent/node/wiki/Building-node.js-on-Cygwin-(Windows)
- Installing heroku: http://flux88.com/2009/06/getting-started-with-heroku-on-windows/