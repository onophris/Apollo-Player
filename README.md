# Apollo Player

Opensource community driven playlist using Spotify, Mopidy, Node.js and Backbone.js


![alt text](https://s3.amazonaws.com/uploads.hipchat.com/24388/138929/xVFWu0fql1hJEkz/output_EfMMwh.gif "Apollo Demo")


![alt text](https://s3.amazonaws.com/uploads.hipchat.com/24388/138929/6pSihkoZfc3MthL/apollo_mobile.png "Apollo Demo Mobile")

## Features

- Simple and elegant group playlist
- Song Bombs =  3 unique votes skips the track and "boos" the player
- Search keywords or Spotify URI's
- Play / Pause toggle 
- Default Playlist (plays when Apollo runs out of songs to play)

## Get Started

### Prerequisites
1. Don't talk about Fight Club.
2. You'll need to have a basic understanding of Node and Node's package manager. I'll add that I didn't have a basic understanding of Node at all before this project and used Apollo to help me learn it... So there's hope for you too!

### Install and configure Mopidy

First we'll need to install Mopidy. Mopidy is a opensource music server that you can connect to many "frontends" or roll your own, which what Apollo is. To read more about Mopidy go [here](http://www.mopidy.com/).

1. Install [Mopidy](http://docs.mopidy.com/en/latest/installation/). Mopidy is an opensource music server that installable on OSX, Debian/Ubuntu, Rasberry Pi. *note: so far we've only tested on Debian and OSX.
    1. You'll need to do the [Spotify installation](https://github.com/mopidy/mopidy-spotify)
    2. Next you'll need to [enable http on Mopidy](http://docs.mopidy.com/en/latest/ext/http/)
2. Start Mopidy on the commandline (if this doesn't work check the mopidy docs, probably a python path issue.)
    ```
    $ mopidy
    ```
3. Optional: You'll want to have Mopidy running in the background at all times for Apollo to work. You'll want to look into [making Mopidy a Daemon](http://www.benjaminguillet.com/blog/2013/08/16/launch-mopidy-at-login-on-os-x/) so that if it crashes it will auto-restart.

### Install Apollo

Now that you have Mopidy up and running, let's setup up Apollo as our Frontend for it.

1. Clone Apollo to a local folder
    ```
    $ git clone https://github.com/samcreate/Apollo-Player.git

    $ cd Apollo-Player
    ```
2. Install Node dependencies 
    ```
    $ npm install
    ```
3. Configure Apollo 
    1. Create a file called config.js in root directory of Apollo
    ```javascript
    $ touch config.js (or just create it with an editor)
    ```
    2. add this structure into config.js file:
        ```javascript
        
            var config = {
                server: {
                    port: 3000,
                },
                "default_playlist_uri": "spotify:user:samcreate:playlist:30M46OlqukAmOgXgaJ0ohU",
                "htmlPretty": "true"
            };

            module.exports = config;
            
    3. Add your Spotify default playlist uri (this has to be a public playlist to work). This is what plays when all the songs in the queue have finished playing (required)

3. Start Apollo
    ```javascript
    $ node apollo.js
    ```

Once Apollo is started, navigate to your localhost: http://localhost:3000

Optionally on Debian/Ubuntu, you might want to start Apollo as a system [service](https://gist.github.com/peterhost/715255).

Finished!

-
### Notes

- If you change a value in config.js, you'll need to restart node (ctrl+c)
- Apollo works best in Chrome.

### Tech used

- Frontend: Backbone, RequireJS, Bootstrap, Handelbars, Jade templating and stylus 
- Backend: Node.js, ExpressJS

### Help? Bugs?

- [Ask questions here](https://groups.google.com/forum/#!forum/apolloplayer)
- [Report Bugs here](https://github.com/samcreate/Apollo-Player/issues)
