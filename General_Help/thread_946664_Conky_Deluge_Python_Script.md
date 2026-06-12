---
title: "Conky Deluge Python Script"
date: 2008-10-13
forum: General Help
---

### Post by kaivalagi on 2008-10-13
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa"). To use this ppa first delete the old ppa files using this: "**sudo rm /etc/apt/sources.list.d/m-buck***". Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]


**_[SIZE="3"][COLOR="Blue"]Intro[/COLOR][/SIZE]_**

This is a simple script to display what is current downloading in Deluge. The script talks to Deluge using either xmlrpc or twisted and allows templates...

This script (old or new versions) requires Deluge ~v0.9 upwards. The hardy repo's do not provide this version. The deb package for this is available at: [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

There is a README with the install and attached here, I suggest you give it atleast a quick once over!

**_[SIZE="3"][COLOR="Blue"]Basic Install[/COLOR][/SIZE]_**

**[COLOR="Blue"]Method 1: Using apt[/COLOR]**

1) Create the necessary list file for access to the repository by running one of these.

Lucid Lynx:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-lucid.list -O /etc/apt/sources.list.d/conkyhardcore-lucid.list
```

Karmic Koala:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-karmic.list -O /etc/apt/sources.list.d/conkyhardcore-karmic.list
```

Jaunty Jackalope:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-jaunty.list -O /etc/apt/sources.list.d/conkyhardcore-jaunty.list
```

Intrepid Ibex:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-intrepid.list -O /etc/apt/sources.list.d/conkyhardcore-intrepid.list
```

Hardy Heron:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-hardy.list -O /etc/apt/sources.list.d/conkyhardcore-hardy.list
```

2) Add the repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-key.gpg -O- | sudo apt-key add -
```

3) Now that is done simply install a package from the ppa, however there are 2 alternative packages to choice from:
[LIST]
[*]**conkydeluge** (script version 2.13+) - the latest version of the script, to be used with Deluge v.1.2.0 onwards.
[*]**conkydeluge-pre120** (script version 2.12) - the old version of the script, to be used with Deluge 1.9 or lower.
[/LIST]
The 2 packages can't be installed together as they ultimately result in the same file names being installed

To actually install run the following in the terminal, remember the text in blue below can be either "conkydeluge" or "conkydeluge-pre120":
```
sudo apt-get update && sudo apt-get install [COLOR="Blue"]**conkydeluge**[/COLOR]

```

**[COLOR="Blue"]Method 2: Using deb file[/COLOR]**

Download and run the attached .deb file

Warning, this will not ensure you are kept up-to-date. Only method 1 will do that ;)

**[COLOR="Blue"]Method 3: Using tar.gz file[/COLOR]**

Extract all the contents of the attached tar.gz file to an appropriate folder, and edit the conkyDeluge script to point to the correct location where conkyDeluge.py is.

Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use method 1.

Again will will not receive updates using this method. ONLY method 1 can do this for you ;) ;)

All further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE="3"][COLOR="Blue"]Usage Help[/COLOR][/SIZE]_**

To use the script in conky in it's simplist form, you'll need an exec statement like this:

```
${exec conkyDeluge}
```

To use a template for custom output, I suggest you read the README attached, and take a look at the example conkyrc and template files that are installed to "/usr/share/conkydeluge/example".

You can get the current help options at any time by running:

```

conkyDeluge -h

```

or

```

conkyDeluge --help

```

```
Usage: conkyDeluge [options]
Options:
  -h, --help            show this help message and exit
  -s SERVER, --server=SERVER
                        [default: 127.0.0.1] The server to connect to where
                        the deluge core is running
  -p PORT, --port=PORT  [default: 58846] The port to connect to where the
                        deluge core is running
  -S, --showsummary     Display summary output. This is affected by the
                        --activeonly option.
  -H, --hidetorrentdetail
                        Hide torrent detail output, if used no torrent details
                        are output.
  -t FILE, --torrenttemplate=FILE
                        Template file determining the format for each torrent.
                        Use the following placeholders: [name], [state],
                        [totaldone], [totalsize], [progress], [nofiles],
                        [downloadrate], [uploadrate], [eta], [currentpeers],
                        [currentseeds], [totalpeers], [totalseeds], [ratio].
  -T FILE, --summarytemplate=FILE
                        Template file determining the format for summary
                        output. Use the following placeholders: [notorrents],
                        [totalprogress], [totaldone], [totalsize],
                        [totaldownloadrate], [totaluploadrate], [totaleta],
                        [currentpeers], [currentseeds], [totalpeers],
                        [totalseeds], [totalratio].
  -a, --activeonly      If set only info for torrents in an active state will
                        be displayed.
  -l NUMBER, --limit=NUMBER
                        [default: 0] Define the maximum number of torrents to
                        display, zero means no limit.
  -b SORTTYPE, --sortby=SORTTYPE
                        Define the sort method for output, can be "progress",
                        "queue", "eta", "download", "upload" and "ratio". Also
                        note that a torrent's state supersedes anything else
                        for sorting, in the order, from top to bottom:
                        downloading, seeding, queued, paused, unknown)
  -v, --verbose         Request verbose output, no a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

**_[SIZE="3"][COLOR="Blue"]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [https://code.launchpad.net/~m-buck/+junk/conkydeluge](https://code.launchpad.net/~m-buck/+junk/conkydeluge)

All packages available from me can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa](https://launchpad.net/~conkyhardcore/+archive/ppa)

I have also created a new website, for now it is relatively sparse, but it does details my conky scripts to a certain degree. You can find it here: [http://www.kaivalagi.com](http://www.kaivalagi.com)

---

### Post by rjmdomingo2003 on 2008-10-14
Could you also make one for Transmission? That'll be great!:KS

---

### Post by tromort on 2008-10-14
Works great here, you might want to put here you need ${exec conkyDeluge} in your conky. oh and any possibility that you'll add a "time left" to the output? 
Funny thing: it seems to know the dl speed even before that is being displayed in deluge.

:KS

---

### Post by kaivalagi on 2008-10-14
> **tromort said:**
> Works great here, you might want to put here you need ${exec conkyDeluge} in your conky. oh and any possibility that you'll add a "time left" to the output? 
Funny thing: it seems to know the dl speed even before that is being displayed in deluge.

:KS

Yeah, I realised the ETA was missing, there is no direct info for this from the api, I'll need to calculate it in the script based on the amount left to download and the current download speed...if I get bored tonight at some point I'll take a look...

Added the "how to" for conky execution too...

Glad you like it :)

---

### Post by kaivalagi on 2008-10-14
[COLOR="Green"]**[SIZE="5"]UPDATE[/SIZE]**[/COLOR]

Added eta output ;)

It will be in the default output to the right of "state", it can also be used in a template with <eta>

I formatted the eta output in the same way as Deluge does it, e.g. "1d 12h" or "1w 2d" or "12h 44m" or "2m 32s" etc, you get the picture :)

The first post has been updated with new deb, tarball and readme, and my personal repo has the new package for apt/synaptic too, so should update the script automatically for those who added it to their sources.

Chimo

---

### Post by markp1989 on 2008-10-16
any chance of making one for torrentflux?

---

### Post by kaivalagi on 2008-10-16
> **markp1989 said:**
> any chance of making one for torrentflux?

It doesn't look straight forward

TorrentFLux uses BitTornado python source I think, which doesn't have any API connectivity...

Deluge now has a built in web server, maybe you could look into using that? Any particular reason you're using TorrentFlux?

---

### Post by markp1989 on 2008-10-16
> **kaivalagi said:**
> It doesn't look straight forward

TorrentFLux uses BitTornado python source I think, which doesn't have any API connectivity...

Deluge now has a built in web server, maybe you could look into using that? Any particular reason you're using TorrentFlux?

i use torrentflux on my headless torrentslave, i check it using the web interface from my desktop, or any other computer. was hoping that it would be possible to view status on my desktop pc conky

im not sure if deluge can be ran with out X installed? il llok in to it

---

### Post by kaivalagi on 2008-10-17
> **markp1989 said:**
> i use torrentflux on my headless torrentslave, i check it using the web interface from my desktop, or any other computer. was hoping that it would be possible to view status on my desktop pc conky

im not sure if deluge can be ran with out X installed? il llok in to it

I think to do it for TorrentFlux it could be done with a combination of wget, grep and sed in a bash script. How are your bash script skills?

I would have to be running TorrentFlux to do this myself, and really don't want to install it...

If you want to try to do it for yourself I can assist with any questions etc...

---

### Post by markp1989 on 2008-10-17
> **kaivalagi said:**
> I think to do it for TorrentFlux it could be done with a combination of wget, grep and sed in a bash script. How are your bash script skills?

I would have to be running TorrentFlux to do this myself, and really don't want to install it...

If you want to try to do it for yourself I can assist with any questions etc...

i have been looking on torrentflux forums, and they have a few scripts using curl to login and upload new torrents. 

```
!/bin/bash
# TorrentFluxHandler - *nix edition
# Coded by IhatemyISP @ http://www.torrentflux.com/forums/
host=10.0.0.99/torrentflux
user=mark
pass=*************8
torrent=$1
curl -c tf_cookie -d username=$user -d iamhim=$pass $host/login.php >> /dev/null
curl -H "Expect:" -b tf_cookie -F "upload_file=@$torrent" $host/index.php >> /dev/null

```

im not sure on how curl works, is it possible to use curl to pull down stats?

---

### Post by mvoncken on 2008-10-17
Hi, i'm a deluge developer.
Great work.

I noticed you copied and pasted lots of the ui.client source.
Instead of that you could  use:
```
from deluge.ui.client import sclient
```
It is documented here : [http://dev.deluge-torrent.org/wiki/Development/UiClient#sclient](http://dev.deluge-torrent.org/wiki/Development/UiClient#sclient)

For eta formatting you could also use deluge.common:
There are other goodies in deluge.common for formatting speed and size.
```
from deluge.common import ftime, fsize, fspeed
```

---

### Post by kaivalagi on 2008-10-17
> **markp1989 said:**
> i have been looking on torrentflux forums, and they have a few scripts using curl to login and upload new torrents. 

```
!/bin/bash
# TorrentFluxHandler - *nix edition
# Coded by IhatemyISP @ http://www.torrentflux.com/forums/
host=10.0.0.99/torrentflux
user=mark
pass=payj86
torrent=$1
curl -c tf_cookie -d username=$user -d iamhim=$pass $host/login.php >> /dev/null
curl -H "Expect:" -b tf_cookie -F "upload_file=@$torrent" $host/index.php >> /dev/null

```

im not sure on how curl works, is it possible to use curl to pull down stats?

PM'ed you a suggestion so we don't clutter the deluge thread...

---

### Post by kaivalagi on 2008-10-17
> **mvoncken said:**
> Hi, i'm a deluge developer.
Great work.

I noticed you copied and pasted lots of the ui.client source.
Instead of that you could  use:
```
from deluge.ui.client import sclient
```
It is documented here : [http://dev.deluge-torrent.org/wiki/Development/UiClient#sclient](http://dev.deluge-torrent.org/wiki/Development/UiClient#sclient)

For eta formatting you could also use deluge.common:
There are other goodies in deluge.common for formatting speed and size.
```
from deluge.common import ftime, fsize, fspeed
```

Thanks for the heads up, I'll make the changes over the weekend hopefully

Yes, I did source all but the DelugeInfo class from the ui.client code, it's nice when I have python code available to work with :)

I assume there is no risk of this stuff changing to the point of not working for me in the future (atleast whilst Deluge is at version 1.*)?

[COLOR="Blue"]Edit: that was easy, made the switch to use the sclient, fsize, ftime, fpcnt imported functions...working locally, update coming :) I'll take a look at what else I can make use of later on[/COLOR]

---

### Post by mvoncken on 2008-10-17
> **kaivalagi said:**
> 
I assume there is no risk of this stuff changing to the point of not working for me in the future (atleast whilst Deluge is at version 1.*)?


Some small planned changes in 1.1 (but that's probably 1.2)
[http://dev.deluge-torrent.org/wiki/Development/UiClient#Deluge1.0to1.1](http://dev.deluge-torrent.org/wiki/Development/UiClient#Deluge1.0to1.1)

---

### Post by kaivalagi on 2008-10-17
> **mvoncken said:**
> Some small planned changes in 1.1 (but that's probably 1.2)
[http://dev.deluge-torrent.org/wiki/Development/UiClient#Deluge1.0to1.1](http://dev.deluge-torrent.org/wiki/Development/UiClient#Deluge1.0to1.1)

Okay thanks, had a look and it's very likely that nothing will affect the script and if it does it won't be much of a problem

---

### Post by kaivalagi on 2008-10-17
[COLOR="DarkOrange"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've updated the script to import and use deluge sclient and common formatting functions. I also disabled deluge logging functions so the console doesn't get flooded with info when conky is started from it.

The first post is updated and the apt package is available

Chimo

---

### Post by kaivalagi on 2008-10-17
**[COLOR="Red"][SIZE="5"]UPDATE[/SIZE] AGAIN[/COLOR]**

Small problem with the progress output, so fixed it along with other possible issues too, changes below:

[LIST]
[*]Updated to use "progress", "eta", "download_payload_rate", "upload_payload_rate" dictionary data to avoid invalid calculations
[*]--version now only returns version and doesn't try to display normal output too
[/LIST]

The first post has been updated and the apt package is available....now at v1.04

Chimo

---

### Post by wladyx on 2008-10-31
Hi,
Great plugin, is there a way to show only de downloading torrents?
I have 100+ and it kills my conky :)
thanks for any info.

---

### Post by kaivalagi on 2008-10-31
> **wladyx said:**
> Hi,
Great plugin, is there a way to show only de downloading torrents?
I have 100+ and it kills my conky :)
thanks for any info.

Good suggestion, once I have sorted out intrepid I'll add an option for that

---

### Post by kaivalagi on 2008-11-02
[COLOR="Red"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've updated the script with the following changes:

[LIST]
[*]Updated error handling for when no torrent status data available, issues usually happen when half way through torrents output and a torrent is no longer there
[*]Added --errorlogfile and infologfile options, when set with a filepath, errors and info are appended to the filepath given
[*]Added --downloadsonly option to limit output to only currently active torrents in a downloading state
[/LIST]

I neglected to update the README in the package, the new help options are listed below:

```

  -e FILE, --errorlogfile=FILE
                        If a filepath is set, the script appends errors to the
                        filepath.
  -i FILE, --infologfile=FILE
                        If a filepath is set, the script appends info to the
                        filepath.
  -d, --downloadsonly   If set only torrents in a downloading state will be
                        displayed.
```

The changes are available in the first post and via apt.

Chimo

---

### Post by kaivalagi on 2008-11-02
[COLOR="Green"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've published a new package labelled for Intrepid, starting at version 2.0.

The first post has been updated, and the package is available via apt.

To use the new intrepid "labelled" packages via apt, changes to your sources.list are needed. This:

```
deb http://ppa.launchpad.net/m-buck/ubuntu hardy main
deb-src http://ppa.launchpad.net/m-buck/ubuntu hardy main
```

Needs to become this:

```
deb http://ppa.launchpad.net/m-buck/ubuntu intrepid main
deb-src http://ppa.launchpad.net/m-buck/ubuntu intrepid main
```

Currently either hardy or intrepid packages will work with either version of ubuntu.

However going forwards there are no guarantees that packages will continue to work with hardy, development may introduce intrepid specific dependencies. All future revisions will only be available for intrepid.

---

### Post by HippyRandall on 2008-11-02
Just thought of another option to add: "[COLOR=Red]**Share Ratio**[/COLOR]"

---

### Post by kaivalagi on 2008-11-03
> **HippyRandall said:**
> Just thought of another option to add: "[COLOR=Red]**Share Ratio**[/COLOR]"

Yep, this could be added...there is a "ratio" key to use

The following are all the data keys that are available, what other keys would be useful? I can get more setup in one go if you tell me what:

```
'active_time', 'compact', 'distributed_copies', 'download_payload_rate', 'eta', 'file_priorities',
'file_progress', 'files', 'hash', 'is_auto_managed', 'is_seed', 'label', 'max_connections',
'max_download_speed', 'max_upload_slots', 'max_upload_speed', 'message', 'move_on_completed',
'move_on_completed_path', 'name', 'next_announce', 'num_files', 'num_peers', 'num_pieces',
'num_seeds', 'paused', 'peers', 'piece_length', 'prioritize_first_last', 'private', 'progress',
'queue', 'ratio', 'remove_at_ratio', 'save_path', 'seed_rank', 'seeding_time', 'state',
'stop_at_ratio', 'stop_ratio', 'total_done', 'total_payload_download', 'total_payload_upload',
'total_peers', 'total_seeds', 'total_size', 'total_uploaded', 'total_wanted', 'tracker',
'tracker_host', 'tracker_status', 'trackers', 'upload_payload_rate'
```

Some of the above are probably deluge specific most of the time so probably aren't applicable...

---

### Post by cl0ckwork on 2008-11-03
would it be possible for a template setup like your other scripts?

---

### Post by kaivalagi on 2008-11-03
> **cl0ckwork said:**
> would it be possible for a template setup like your other scripts?

There is already a template option, one which defines each piece of data's position for any given torrent's output. It is similar to the way my google calendar template works.

I use this:

```
${color1}${font Liberation Sans:size=9:style=Bold}<name>${font}
${color1}<state> - ${color3}${font Liberation Sans:size=8:style=Bold}ETA:${font}${color1} <eta>
<totaldone>/<totalsize> - <progress>
${color3}${font Liberation Sans:size=8:style=Bold}DL:${font}${color1} <downloadrate> ${font Liberation Sans:size=8:style=Bold}${color3}UL:${font}${color1} <uploadrate>

```

There are place holders for the output within "<" and ">", these are replaced with actual data for each torrent

Is that what you mean?

---

### Post by cl0ckwork on 2008-11-03
yes!  :D

shouldve looked a little harder before asking  :lolflag:

---

### Post by jjgomera on 2008-11-05
thanks, great works again :KS

Is there any possibility too add more options:

-Display only global rates, download and upload without any individual torrent information

-Display only active torrents, important in private tracker, where there are very much torrent seeded, and only someone have leechers and upload anything

---

### Post by kaivalagi on 2008-11-05
> **jjgomera said:**
> thanks, great works again :KS

Is there any possibility too add more options:

-Display only global rates, download and upload without any individual torrent information

-Display only active torrents, important in private tracker, where there are very much torrent seeded, and only someone have leechers and upload anything

Glad you find it useful :)

Isn't the --downloadsonly option what you want for active torrents? If not can you explain as I think I am misunderstanding what you want...

It might be a little while before I can do this development, I am working long hours getting a software release out in time, I don't really want to face more development when I get home :) (most of the time)

Worst case I'll take a look at the end of the month when things have calmed down...I've added the global option to my TODO's in the script. I may get bored at the weekend though....

---

### Post by jjgomera on 2008-11-06
No, im thinking about upload, per example, i have now none download, 386 upload, but only 2-3 uploading really, with some leechers connects.
So, the normal conkydeluge show all, too much information
The downloadonly option dont show nothing.
Im thinking a option to say only global upload and download rate and other to say only active torrents, with peers connected, with appreciable download or/and upload rate, like a activeonly or so
Dont worry about that anyway, really it isnt necessary

---

### Post by kaivalagi on 2008-11-06
> **jjgomera said:**
> No, im thinking about upload, per example, i have now none download, 386 upload, but only 2-3 uploading really, with some leechers connects.
So, the normal conkydeluge show all, too much information
The downloadonly option dont show nothing.
Im thinking a option to say only global upload and download rate and other to say only active torrents, with peers connected, with appreciable download or/and upload rate, like a activeonly or so
Dont worry about that anyway, really it isnt necessary

For the per torrent uploads/downloads, would these 2 options do the trick?

```
--activeonly (both directions only if there are peers/seeds connected)
--uploadonly
```

Also, on the global front, I think we need 2 template options. The current one could be renamed to --torrenttemplate, and a new one added called --summarytemplate

The summary template would output global info as the layout dictates, with a different set of options available such as <notorrents>, <totalprogress>, <totaldone>, <totalsize>, <totaldownloadrate>, <totaluploadrate>, <currentpeers>, <currentseeds>, <totalpeers>, <totalseeds>, <totalratio>

This would print at the top of the conky output to allow for per torrent template output underneath.

Would that work? What summary template options would be useful to you? Anything other than I mentioned above

[COLOR="Blue"]Edit: I have sent a test script to you. I have replaced the --downloadonly option with --activeonly, there is now a --showsummary, with --summarytemplate option to go with. I've attached an example screenshot...[/COLOR]

---

### Post by jjgomera on 2008-11-06
Perfect, i look for that exactly, summary and individual active torrents

> **kaivalagi said:**
> For the per torrent uploads/downloads, would these 2 options do the trick?

```
--activeonly (both directions only if there are peers/seeds connected)
--uploadonly
```

uploadonly its not necesary, with active is enough, so when i donwload something conky shows it too

THANKS AGAIN SIR KAIVALAGI:lolflag:

---

### Post by kaivalagi on 2008-11-06
[COLOR="Red"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've updated the script, any --template options will have to be changed to use --torrenttemplate

Changes as follows:

[LIST]
[*]Updated to output text in utf-8 format, in case of strange characters used in torrent names etc
[*]Replaced the --downloadonly option with --activeonly, when used torrent output is only printed if there are active peers or seeds
[*]Renamed --template option to be called --torrenttemplate as it relates to individual torrent information
[*]Added --showsummary and --summarytemplate options to facilitate the displaying of summary information for all torrents. If --showsummary is used no torrent details are output. This is affected by the --activeonly option.
[*]Added currentpeers, currentseeds, totalpeers, totalseeds and ratio to the data available for torrenttemplate
[/LIST]

The first post has been updated and the apt package will be available shortly

New usage help as follows:

```
Usage: conkyDeluge [options]
Options:
  -h, --help            show this help message and exit
  -s SERVER, --server=SERVER
                        [default: 127.0.0.1] The server to connect to where
                        the deluge core is running
  -p PORT, --port=PORT  [default: 58846] The port to connect to where the
                        deluge core is running
  -S, --showsummary     Display summary output, if used no torrent details are
                        output. This is affected by the --activeonly option.
  -t FILE, --torrenttemplate=FILE
                        Template file determining the format for each torrent.
                        Use the following placeholders: <name>, <state>,
                        <totaldone>, <totalsize>, <progress>, <nofiles>,
                        <downloadrate>, <uploadrate>, <eta>, <currentpeers>,
                        <currentseeds>, <totalpeers>, <totalseeds>, <ratio>.
  -T FILE, --summarytemplate=FILE
                        Template file determining the format for summary
                        output. Use the following placeholders: <notorrents>,
                        <totalprogress>, <totaldone>, <totalsize>,
                        <totaldownloadrate>, <totaluploadrate>,
                        <currentpeers>, <currentseeds>, <totalpeers>,
                        <totalseeds>, <totalratio>.
  -a, --activeonly      If set only info for torrents in an active state will
                        be displayed.
  -e FILE, --errorlogfile=FILE
                        If a filepath is set, the script appends errors to the
                        filepath.
  -i FILE, --infologfile=FILE
                        If a filepath is set, the script appends info to the
                        filepath.
  -v, --verbose         Request verbose output, no a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
```


Have fun :)

---

### Post by kaivalagi on 2008-11-06
> **jjgomera said:**
> 
THANKS AGAIN SIR KAIVALAGI:lolflag:

Enjoy

I need to get a second monitor, so I have enough desktop width for all this stuff :)

---

### Post by slinkey1981 on 2008-11-07
Ummmm, it seems like I ask questions in all of your threads.

I seem to keep getting this error, and I am not knowledgeable enough to figure it out. I installed through aptitude after adding your source, so... Is there something else I need to install?

Any help would be appreciated, but you've already done enough to make my conky the MOST prized item on my desktop.

Keep up the awesome work!

```
shifty@MediaBox:~$ conky
--02:50:25--  http://ip.tupeux.com/
           => `-'
Resolving ip.tupeux.com... 88.191.12.240
Connecting to ip.tupeux.com|88.191.12.240|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13 [text/html]

100%[====================================>] 13            --.--K/s             

02:50:26 (535.52 B/s) - `-' saved [13/13]

Conky: forked to background, pid is 16471
shifty@MediaBox:~$ 
Conky: desktop window (1a6) is root window
Conky: window type - normal
Conky: drawing to created window (1000001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/usr/share/conkydeluge/conkyDeluge.py", line 31, in <module>
    from deluge.ui.client import sclient
ImportError: No module named ui.client

```

My Conky- ```
#Conky Configuration File
maximum_width 300
background yes
border_width 1
cpu_avg_samples 3
default_color light grey
default_outline_color light grey
default_shade_color light grey
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
use_xft yes
xftfont 
xftalpha 0.5
gap_x 3
gap_y 40
minimum_size 5 5
net_avg_samples 1
no_buffers yes
out_to_console no
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 3
update_interval 2
uppercase yes
use_spacer left
alignment top_right
double_buffer yes
text_buffer_size 2048 # use 1024 for the forecast

TEXT

${color db7835}${font Capture it:size=17}System Info${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}OS: ${color light grey}${alignr}Ubuntu 8.04 Hardy Heron
${color dark grey}Kernal: ${color light grey}${alignr}$sysname $kernel 
${color dark grey}User: ${color light grey}${alignr}Shifty@$nodename

${color dark grey}Uptime:$alignr ${offset 10}${color dark red}${font Capture it:25} $uptime
${alignr}${color db7835}${time %H:%M}/23:59

${color db7835}${font Capture it:size=17}Hardware Info${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}CPU Make:$alignr ${color light grey}Intel Celeron
${color dark grey}CPU Frequency:$alignr ${color light grey}$freq MhZ
${color dark grey}CPU Temp:$alignr ${color light grey} ${acpitemp}${color light grey}.C
${color dark grey}GPU Temp:$alignr ${color light grey} ${exec nvidia-settings -q GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2}.C
${color dark grey}Video RAM:$alignr ${color light grey} ${exec nvidia-settings -q VideoRam | grep Attribute | cut -d ' ' -f 6 | cut -c 1-6} KiB

${color db7835}${font Capture it:size=17}CPU/RAM Info${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}CPU: ${color light grey}$alignr ${cpu}%
${color light grey}${cpubar 7,300}
${color dark grey}RAM: ${color light grey}$alignr $memperc% ${color light grey}
${color light grey}${membar 7,300}

${color db7835}${font Capture it:size=17}Storage Info${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}Home $alignr ${color light grey}${fs_free /}/${fs_size /} 
${color light grey}${fs_bar 7,300 /}
${color dark grey}MediaShare $alignr ${color light grey}${fs_free /mnt/MediaShare}/${fs_size /mnt/MediaShare}
${color light grey}${fs_bar 7,300 /mnt/MediaShare}

${color db7835}${font Capture it:size=17}Network Info${voffset -4}${stippled_hr 4}${color dark grey}
${color gray}${font Hardkaze:size=10}Local IP:${color light grey}${alignr}${addr eth0}
${color dark grey}Internet IP:${color light grey}${alignr}${pre_exec wget -O - http://ip.tupeux.com | tail}
${downspeedgraph eth0 38,145 969400 1c5c00} ${alignr}${upspeedgraph eth0 38,145 969400 830000} 
${voffset -45}${color dark grey}Down:${color light grey}${downspeedf eth0}Kbps${color dark grey}${alignr}Up:${color light grey}${upspeedf eth0}Kbps${color dark grey}
${color dark grey}Down: ${color light grey}${totaldown eth0} ${color dark grey}${alignr}Up: ${color light grey}${totalup eth0}

${color db7835}${font Capture it:size=17}Online Friends${voffset -4}${stippled_hr 4}
${color dark grey}${font Hardkaze:size=10}${execpi 60 conkyPidgin -o --template=/usr/share/conkypidgin/example/conkyPidgin.template}

${font Terminus:style=Bold:size=11}Deluge${font}
${color dark grey}${execpi 60 conkyDeluge --template=/usr/share/conkydeluge/example/conkyDeluge.template}

```

My conkyDeluge.template-
 ```
${color1}${font Liberation Sans:size=9:style=Bold}<name>${font}
${color1}<state> - ${color3}${font Liberation Sans:size=8:style=Bold}ETA:${font}${color1} <eta>
<totaldone>/<totalsize> - <progress>
${color3}${font Liberation Sans:size=8:style=Bold}DL:${font}${color1} <downloadrate> ${font Liberation Sans:size=8:style=Bold}${color3}UL:${font}${color1} <uploadrate>
```

---

### Post by kaivalagi on 2008-11-07
> **slinkey1981 said:**
> 
Traceback (most recent call last):
  File "/usr/share/conkydeluge/conkyDeluge.py", line 31, in <module>
    from deluge.ui.client import sclient
ImportError: No module named ui.client
[/CODE]


What version of Deluge are you running?

Version 1.* is required as stated in the first post, this isn't in the ubuntu repo's...0.5 something is in there (very very old)

You need to install the deb file from here instead: [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

The current version is 1.04, which I am using without issue

Hope that helps

---

### Post by jjgomera on 2008-11-07
Here's my configuration:

conkyrc:
```
# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
#xftfont Terminus:size=8
xftfont Sans-Serif:size=9:pixelsize=11

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 10.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 250 5
maximum_width 250

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color ffd700
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 200

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

text_buffer_size 2550

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer none
#Note: doesn't work in conky 1.2 =(


TEXT
${voffset 5}${color blue}${font lprabbits1:size=18}H${voffset -7}${font Anklepants:regular:size=11}${color #5da5d3} deluge$font$alignr${color #888888}What.cd ratio: ${color}${execi 600 sh ~/configuracion/what.cd ratio}
${voffset -7}${color #ffd700}${hr 1}$color
${voffset 3}${color #888888}${execpi 10 /home/jjgomera/Escritorio/conkydelug/conkyDeluge.py -S -T /home/jjgomera/Escritorio/conkydelug/conkyDelugeSummary.template}
${voffset -13}${color #888888}${stippled_hr 2}
${color #888888}${execpi 10 /home/jjgomera/Escritorio/conkydelug/conkyDeluge.py -a -t /home/jjgomera/Escritorio/conkydelug/conkyDeluge.template}
${voffset -18}${color #ffd700}${hr 1}

```

general template:
```
      ${color gold}${font Arrows:size=10}S$font${color white} <totaluploadrate> ${alignr 50}${color gold}${font Arrows:size=10}N$font${color white} <totaldownloadrate>
```

torrent template:
```
${voffset 7}${color white}${font Liberation Sans:size=9:style=Bold}<name>${font}
${color #888888} Progreso:${color}<progress>${alignr}${color #888888}Ratio:${color} <ratio>
${color #888888} Subida:${color} <uploadrate> ${alignr}${color #888888}Descarga:${color} <downloadrate>
${color #888888} Subiendo a <currentpeers> de <totalpeers> pares
```
and here the result, really good, it shows only the active torrents, download or upload, but it doesnt show torrents without activity:

[CENTER][IMG]http://img443.imageshack.us/img443/9924/pantallazowi7.png[/IMG][/CENTER]

---

### Post by cl0ckwork on 2008-11-08
there seems to be an issue...
just thought i would try out your new script, but everytime my conky refreshes, it compounds itself and the display is all jumbled up
[IMG]http://i278.photobucket.com/albums/kk101/clockwork_kills/Screenshot-1.png[/IMG]

should look more like this
[IMG]http://i278.photobucket.com/albums/kk101/clockwork_kills/Screenshot-2.png[/IMG]

any idea?

running conky 1.5.1 and newest version of your deluge script

---

### Post by kaivalagi on 2008-11-08
> **cl0ckwork said:**
> there seems to be an issue...
just thought i would try out your new script, but everytime my conky refreshes, it compounds itself and the display is all jumbled up
any idea?

running conky 1.5.1 and newest version of your deluge script

The script itself will not cause issues like this, it just outputs a string. I am assuming you are using a template and the execp/execpi commands in your conkyrc?

This issue will have something to do with your conky version/conky configuration and the use of offsets and what happens in a refresh  I would imagine.

To maybe resolve the issue when using the execp/execpi I would either, 1) upgrade to intrepid and use a newer version of conky, 2) compile conky 1.6.1 or upwards and use that instead.

To confirm whether the execp/execpi commands are causing this, try running the script as before but using exec/execi instead. The formatting options such as ${font} and ${color} wont work but at least you'll know whether the root cause is what I have suggested...

Sorry I can't help any more, but the script itself wont be at fault.

---

### Post by cl0ckwork on 2008-11-08
not a problem, i was just trying to avoid compiling more code :???:

**Edit**: fresh code, now it works.
didnt mean to bash on your script, just looking for a solution :)

---

### Post by jjgomera on 2008-11-08
i had that problem too other times, always my conkyrc TEXT section starts with a if clause, that happens, i think is a bug, adding a space or a first empty line is enought to fix it

---

### Post by kaivalagi on 2008-11-08
> **cl0ckwork said:**
> not a problem, i was just trying to avoid compiling more code :???:

**Edit**: fresh code, now it works.
didnt mean to bash on your script, just looking for a solution :)

"bash" your "script", nice geek joke there :)

It's okay, I didn't take it that way. Just gave you my 2 pence on the problem.

---

### Post by kaivalagi on 2008-11-09
[COLOR="Blue"]**[SIZE="5"]UPDATE[/SIZE]**[/COLOR]

I've added a --limit option to the script to control the amount of torrent specific info displayed, it doesn't affect the summary at all. I have also ordered the list so highest progress comes first.

So changes for the new build are:

[LIST]
[*]Updated to collect torrent data into a class list to allow sorting (highest to lowest progress)
[*]Added --limit option to restrict the number of torrents displayed, default value of zero means no limit
[*]Updated README
[/LIST]

The first post has been updated and the apt package is available

Chimo

---

### Post by kaivalagi on 2008-11-10
[SIZE="4"]**[COLOR="Green"]UPDATE[/COLOR]**[/SIZE]

Quick update, no functional changes. The script has just been tidied up

The first post is updated and the apt package will be available shortly

---

### Post by slinkey1981 on 2008-11-12
is there any change of getting a bar to fill up as the download percentage increases that resembles the "cpubar" or "membar" or "fs_bar"?

Not that it really needs it, just that it would let my conky be a bit more cohesive.

Thanks for all the awesome conky scripts!

---

### Post by kaivalagi on 2008-11-12
> **slinkey1981 said:**
> is there any change of getting a bar to fill up as the download percentage increases that resembles the "cpubar" or "membar" or "fs_bar"?

Not that it really needs it, just that it would let my conky be a bit more cohesive.

Thanks for all the awesome conky scripts!

As the templates are used for multiple torrent output and are called only once from the script, it is impossible to have conky execbar/execibar functionality. That would require the script being called for each torrent separately so the exec could be done through execbar/execibar (where we don't know the total number everytime).

Unless conky changes so that creating a bar is as simple as ${color} and ${font} this won't be possible.

In theory the summary could be setup to have this as there is only one output, but unless the summary and each torrents output can look the same it's a no go

Sorry

---

### Post by shadesofevil on 2008-11-18
Sorry if this has been already asked,

is there any chance for a "totalETA" option for summary output?

---

### Post by kaivalagi on 2008-11-18
> **shadesofevil said:**
> Sorry if this has been already asked,

is there any chance for a "totalETA" option for summary output?

No, not asked for before :)

Would that be the highest ETA amount of all your torrents?

---

### Post by shadesofevil on 2008-11-19
I was aiming for the eta for all my currently actively downloading torrents, but you're right I think the highest ETA amount would also give me the same thing.

---

### Post by kaivalagi on 2008-11-19
[SIZE="4"]**[COLOR="Green"]UPDATE[/COLOR]**[/SIZE]

Updated the script as follows:

[LIST]
[*]Now handles when Deluge is not running, and skips doing template prep that isn't required
[*]Added --hidetorrentdetail option, so both all combinations of output can be output in one exec call
[*]Added <totaleta> to the summary, basically displaying the highest eta for all torrents
[*]**[COLOR="Red"]Changed option tags from <...> to [...][/COLOR]**, so <eta> now needs to be [eta] in the template to work
[*]Updated example template and README
[/LIST]

The first post is updated and the apt package will be available shortly

---

### Post by HippyRandall on 2008-11-19
> **kaivalagi said:**
> [SIZE=4]**[COLOR=Green]UPDATE[/COLOR]**[/SIZE]

Updated the script as follows:

[LIST]
[*]Now handles when Deluge is not running, and skips doing template prep that isn't required
[*]Added --hidetorrentdetail option, so both all combinations of output can be output in one exec call
[*]Added <totaleta> to the summary, basically displaying the highest eta for all torrents
[*][SIZE=6][B][COLOR=Red]Changed option tags from <...> to [...][/COLOR], so <eta> now needs to be [eta] in the template to work [COLOR=Blue](a simple find + replace in gedit)[/COLOR]
[/B][/SIZE]
[*]Updated example template and README
[/LIST]

The first post is updated and the apt package will be available shortly

PPA deb is now available. YAY!!! and I figured I would make the most significant change stand out some since this tends to get missed...by me most of the time anyway :lolflag:

---

### Post by shadesofevil on 2008-11-19
that was fast! thanks dude you're the man.

I haven't tested the update yet, but will do first thing in the morning. It's a holiday around here so. The first change is a winner!

---

### Post by shadesofevil on 2008-11-23
Alright it seems to be working like I wanted. Thank you so much again

---

### Post by duanedesign on 2008-11-23
this thread has almost 500 pages of .conkyrc files with screenshots. A good resource for customizing your Conky installation.

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by xxploit on 2008-11-29
Question: I have installed conkyDeluge from the repo and when running thru the terminal I get this error:

$ conkyDeluge -S
Traceback (most recent call last):
  File "/usr/share/conkydeluge/conkyDeluge.py", line 37, in <module>
    from deluge.ui.client import sclient
ImportError: No module named ui.client

If someone could throw me some help on this issue it would be appreciated since I'd like to get it working.

System:8.10 Xubuntu 64bit
Deluge: Default from Ubuntu repos

---

### Post by xxploit on 2008-11-29
Nvm, seems all is good when upgrading to the newer versions of deluge since the one in the repo is too old.

---

### Post by kaivalagi on 2008-11-30
> **xxploit said:**
> Nvm, seems all is good when upgrading to the newer versions of deluge since the one in the repo is too old.

That's exactly the problem, from version 0.9...something there api required for this script were introduced. Anything older just won't work, as mentioned in the first post...

Glad you got it working anyway :)

---

### Post by kaivalagi on 2008-12-14
New app added to my PPA, new thread on this can be found through the apps link in my sig below...

---

### Post by Psyfurius on 2009-01-02
kaivalagi, Thank You for this script. :-) Now I can see my downloading torrents in conky thanks to you :)

---

### Post by kaivalagi on 2009-01-02
> **Psyfurius said:**
> kaivalagi, Thank You for this script. :-) Now I can see my downloading torrents in conky thanks to you :)

No worries

If you get bored with conky you can always have a play with my new app (link in my sig) :)

---

### Post by markp1989 on 2009-01-15
> **kaivalagi said:**
> It doesn't look straight forward

TorrentFLux uses BitTornado python source I think, which doesn't have any API connectivity...

Deluge now has a built in web server, maybe you could look into using that? Any particular reason you're using TorrentFlux?


Im just updating you, i got my torrentflux script working, see the link in my sig for details.

---

### Post by kaivalagi on 2009-01-15
> **markp1989 said:**
> Im just updating you, i got my torrentflux script working, see the link in my sig for details.

You have been busy!

All that shell scripting makes me cringe though :)

Have you done any python dev before? You COULD try and retro fit the curl and file scraping into the deluge script...retaining the formatting options that are there. It would be quite a big task but would be worth it...I would do it but I'll never use torrentflux so I can't justify all that time on it.

If you know some python, and want to give it a crack, I can help you out here and there. I wont do things for you but I can point you in the right direction if you would find that useful...I have subscribed to your thread so if you do decide to try the python thing ask for help there and I'll try and assist.

Go on....go for it!!!

---

### Post by kaivalagi on 2009-02-02
**[COLOR="Red"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

New instructions on setting up the repository in your system have been added to the first post, as follows

[COLOR="Red"]**Remove any existing /etc/apt/sources.list entry before or after doing this!**[/COLOR]

1) Create the necessary list file for access to the repository by running this:

```
sudo wget -q http://www.kaivalagi.com/m-buck-ppa.list -O /etc/apt/sources.list.d/m-buck-ppa.list
```

2) Add the repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/m-buck-ppa-key.gpg -O- | sudo apt-key add -
```

---

### Post by kthakore on 2009-02-05
I am using intrepid and I recently install conkydeluge. I installed the following line in my ./conkyrc.

```
${execi 60 conkyDeluge -a}
```

Nothing showed up so I ran the command in my cli, and got the following error.
```

Traceback (most recent call last):
  File "/usr/share/conkydeluge/conkyDeluge.py", line 37, in <module>
    from deluge.ui.client import sclient
ImportError: No module named ui.client

```
My deluge version is Deluge 0.5.9.3

---

### Post by jjgomera on 2009-02-05
> **kthakore said:**
> 
My deluge version is Deluge 0.5.9.3

> **kaivalagi said:**
> 
As this script uses xmlrpc to talk to Deluge, it requires Deluge ~v0.9 upwards. The hardy repo's do not provide this version. At the time of writing I am running v1.02. The deb package for this is available at: [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)


.

---

### Post by kaivalagi on 2009-02-05
Thanks jjgomera

@kthakore - I highly recommend installing the latest package from the deluge website, it is far better than the outdated version in the Ubuntu repo's. It now has a daemon (service) and client...nice bit of development imho

---

### Post by Fivizzz on 2009-02-07
Hello everyone & kaivalagi,
I started using conky only a few days ago tweaking a conkyrc that used most of your scripts. Well thanks for the great work :)

They all work fine, but I'm experiencing problems with both limit and downloadsonly options in the deluge script.

If I try it without any of them, the script works and displays perfectly in my conky.
The line in my .conkyrc file is:
```
${execpi 5 conkyDeluge --torrenttemplate=/home/fivizzz/.conky/conkyDelugeTorrent.template}
```

And my template file is:
```
${voffset -11}[progress]${goto 55}[name]
[eta]${goto 65}[downloadrate]
```

If I add *--limit=3* in the .conkyrc line, the info displays well, until I have 4 or more torrents active in Deluge. Then the Deluge info simply disappears from the conky display.

If I add the *--downloadsonly* option, nothing is displayed. (Though I have torrents in a downloading state)


I use Deluge 1.0.5 (You mentioned it as working in a post above, so I decided I'd try your script with it before upgrading to the latest version) and I installed the script from your repo.

Maybe I am not using the options well, how shall I put it so it works with both options?

---

### Post by kaivalagi on 2009-02-07
> **Fivizzz said:**
> Hello everyone & kaivalagi,
I started using conky only a few days ago tweaking a conkyrc that used most of your scripts. Well thanks for the great work :)

They all work fine, but I'm experiencing problems with both limit and downloadsonly options in the deluge script.

If I try it without any of them, the script works and displays perfectly in my conky.
The line in my .conkyrc file is:
```
${execpi 5 conkyDeluge --torrenttemplate=/home/fivizzz/.conky/conkyDelugeTorrent.template}
```

And my template file is:
```
${voffset -11}[progress]${goto 55}[name]
[eta]${goto 65}[downloadrate]
```

If I add *--limit=3* in the .conkyrc line, the info displays well, until I have 4 or more torrents active in Deluge. Then the Deluge info simply disappears from the conky display.

If I add the *--downloadsonly* option, nothing is displayed. (Though I have torrents in a downloading state)


I use Deluge 1.0.5 (You mentioned it as working in a post above, so I decided I'd try your script with it before upgrading to the latest version) and I installed the script from your repo.

Maybe I am not using the options well, how shall I put it so it works with both options?

--downloadsonly is not an option, --activeonly is, that might be the issue?

run **conkyDeluge -h** at the command line for details.

I am sure the --limit option has worked for me in the past, so maybe it is just the use of --downloadsonly is the problem.

I am about to watch 6 Nations Rugby and get really drunk for the whole weekend so wont be able to look further at this until the start of next week...I like my rugby ;)

---

### Post by Fivizzz on 2009-02-07
> **kaivalagi said:**
> [COLOR="Red"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

I've updated the script with the following changes:

[LIST]
[*]Updated error handling for when no torrent status data available, issues usually happen when half way through torrents output and a torrent is no longer there
[*]Added --errorlogfile and infologfile options, when set with a filepath, errors and info are appended to the filepath given
[*]Added --downloadsonly option to limit output to only currently active torrents in a downloading state
[/LIST]

I neglected to update the README in the package, the new help options are listed below:

```

  -e FILE, --errorlogfile=FILE
                        If a filepath is set, the script appends errors to the
                        filepath.
  -i FILE, --infologfile=FILE
                        If a filepath is set, the script appends info to the
                        filepath.
  -d, --downloadsonly   If set only torrents in a downloading state will be
                        displayed.
```

The changes are available in the first post and via apt.

Chimo

Seeing that post I assumed the option was implemented.
And I tried both options separately.

Anyway, I'm to watch rugby too, and I have to say Go France! :p

---

### Post by kaivalagi on 2009-02-07
> **Fivizzz said:**
> Seeing that post I assumed the option was implemented.
And I tried both options separately.

Anyway, I'm to watch rugby too, and I have to say Go France! :p

Sorry for the confusion, looking at the dev history comments in the script I found this:

```

#    06/11/2008    Replaced the --downloadonly option with --activeonly, when used torrent output is only printed if there are active peers or seeds
```

Too many scripts to keep a track of, good job I put detailed notes in them :)

I assume if you ran the script from the terminal with the --verbose option it would complain of an invalid option...I suggest you take this route if you have issues going forwards, it will better explain what's up.

The --limit option is still causing issues on it's own then? I don't use conky anymore so I'll need to have a tinker for a bit to reproduce the problem. I use my own app, see sig

Enjoy the rugby! Hopefully the Ireland v France match will be more interesting than the Italy v England one...Italy's No.9 shouldn't be there! Very one sided at half time

---

### Post by kaivalagi on 2009-02-08
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Script updated to use "total_wanted" stats (only selected parts of torrent) instead of "total_size", fixes summary progress where partial downloads of torrents are in place

Changes can be seen here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkydeluge_2.05_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkydeluge_2.05_source.changes)

The first post has been updated and the new apt package should be available soon

Chimo

---

### Post by kaivalagi on 2009-03-14
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Script updated, vhanges can be seen here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkydeluge_2.06_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/conkydeluge_2.06_source.changes)

The first post has been updated and the new apt package should be available soon

Chimo

---

### Post by WiseGuy1020 on 2009-04-15
Hey k

I have been getting this error from the deluge script when I run conky.

ERROR: writeOutput:Unexpected error:<Fault 1: "<type 'exceptions.IndexError'>:address_v4 from unsigned long">

Any thoughts?

---

### Post by kaivalagi on 2009-04-15
> **WiseGuy1020 said:**
> Hey k

I have been getting this error from the deluge script when I run conky.

ERROR: writeOutput:Unexpected error:<Fault 1: "<type 'exceptions.IndexError'>:address_v4 from unsigned long">

Any thoughts?

It looks like an issue with Deluge D-Bus rather than the script. I did a little search and came across the same error with the Deluge webui: [http://dev.deluge-torrent.org/ticket/798](http://dev.deluge-torrent.org/ticket/798)

Does it come and go, depending on the torrents you have active?

---

### Post by WiseGuy1020 on 2009-04-15
It will display the torrents for a couple seconds and then they are gone.
I have three different torrents and I don't notice that it matters which torrent I am downloading.

If I pause them though then they display fine.

---

### Post by kaivalagi on 2009-04-15
> **WiseGuy1020 said:**
> It will display the torrents for a couple seconds and then they are gone.
I have three different torrents and I don't notice that it matters which torrent I am downloading.

If I pause them though then they display fine.

I am running v 1.16 with full allocation of torrent files and have no issues.

What are you running and what setting do you have?

If you are not doing so already you can install Deluge through their PPA so you keep up-to-date automatically. More detail here: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)
Make sure you add the key for the repository after adding the urls for the PPA to source.list!

---

### Post by WiseGuy1020 on 2009-04-15
I am also running 1.1.6 on Ubuntu 9.04

and I also have their repo added to my sources.

And I am using the default deluge template.

---

### Post by kaivalagi on 2009-04-15
> **WiseGuy1020 said:**
> I am also running 1.1.6 on Ubuntu 9.04

and I also have their repo added to my sources.

And I am using the default deluge template.

I really don't think I can resolve this issue as it does seem that it is a bug with the Deluge source that you are having for some reason. I am still running Intrepid so am unsure whether it is specific to Jaunty (it is still in Beta...)

It may be worth logging a bug with the Deluge team or approaching them on IRC in #deluge on irc.freenode.net?

---

### Post by WiseGuy1020 on 2009-04-15
Thanks for pointing me in the right direction.

Keep up the good work.

---

### Post by kaivalagi on 2009-04-16
> **WiseGuy1020 said:**
> Thanks for pointing me in the right direction.

Keep up the good work.

Let me know how you get on, there may be others with the same issue...If I know what and why I can tell them too :)

---

### Post by kaivalagi on 2009-04-18
**[COLOR="Green"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

**PPA Location Changes**

I have created new PPA's on launchpad to sub-divide all my scripts into their own categories. As such the installation steps for conky scripts have changed, which have been updated on the first post.

You should all change the repository details using the first post steps to get new updates, no new updates will be applied to the old archive location going forwards.

By all means leave the old settings in place too, but these will not help you much.

**Jaunty Package Support**

I have created equivalent packages for Jaunty Jackalope in my PPA's now. They are identical to the intrepid packages but sit under a jaunty location. In my limited testing they all seem to work fine. Again the first post has been updated to describe the setup steps.

Chimo!

---

### Post by kaivalagi on 2009-04-18
> **WiseGuy1020 said:**
> I am also running 1.1.6 on Ubuntu 9.04

and I also have their repo added to my sources.

And I am using the default deluge template.

Well I have upgraded to Jaunty (a little bit ahead of my usual time) and I am now having the same issues as yourself with the script when trying to get deluge info from the client api...

The good news is I think I have a fix. Currently I try to retrieve all data available for a torrent and this crashes. There is a way to retrieve based on a list of required items, and in testing when I retrieve only that the bits I need the crash doesn't happen :)

I should have a fix in before the end of the weekend...

---

### Post by kaivalagi on 2009-04-18
**[COLOR="Red"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Updated to retrieve data items for each torrent based on a finite list rather than all of them, this stops an error occurring with python 2.6 and xmlrpc in Jaunty, see here for changes: [https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.07_source.changes](https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.07_source.changes)

The first post has been updated and the apt packages should be available shortly

[COLOR="Red"]**REMEMBER:** To get this update you will need to change your repository settings for my new PPA locations available for Intrepid and Jaunty versions of Ubuntu. See the first post install instructions for details...[/COLOR]

Chimo

---

### Post by WiseGuy1020 on 2009-04-19
Awesome from what I can tell that fixed it.

Thanks alot.

---

### Post by snkiz on 2009-05-13
Good morning K, thought I'd give your deluge template a try, but its no working for me. The details, I'm running deluge 1.1.6 on a remote server both my machines are jaunty, I enter this in the terminal
```
--server=192.168.0.101 --port=55961  --showsummary -v
```
and it tells me
```
*** INITIAL OPTIONS:
    server: 192.168.0.101
    port: 55961
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    errorlogfile: None
    infologfile: None
INFO: No session state data is available, nothing to output...

```
so.. what did I miss?

---

### Post by kaivalagi on 2009-05-13
> **snkiz said:**
> Good morning K, thought I'd give your deluge template a try, but its no working for me. The details, I'm running deluge 1.1.6 on a remote server both my machines are jaunty, I enter this in the terminal
```
--server=192.168.0.101 --port=55961  --showsummary -v
```
and it tells me
```
*** INITIAL OPTIONS:
    server: 192.168.0.101
    port: 55961
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    errorlogfile: None
    infologfile: None
INFO: No session state data is available, nothing to output...

```
so.. what did I miss?

The command options look good

I get the same state of things when deluge isn't up and running...

I have never tried using the script against a remote deluge daemon before so I can only assume there is a problem with the remote nature of things.

I've attached a test script with the same connection options as you posted, can you run it where the conky script would normally be run. To run it enter this into the terminal:

```
python test_deluge.py
```

I get the following output (followed by the actual list of torrent names):
```

* setting sclient up
* getting session state of torrents
* going through each torrent item in state and outputting the name
```

How about you?

---

### Post by snkiz on 2009-05-13
I ran i three times, once while seeding a torrent, once while seeding/starting a torrent and once while seeding/ downloading a torrent
this is what I got:
```
snkiz@ckubuntu:~/Desktop$ python test_deluge.py
* setting sclient up
* getting session state of torrents
timed out
snkiz@ckubuntu:~/Desktop$ python test_deluge.py
* setting sclient up
* getting session state of torrents
not well-formed (invalid token): line 1, column 1
snkiz@ckubuntu:~/Desktop$ python test_deluge.py
* setting sclient up
* getting session state of torrents
<ProtocolError for 192.168.0.101:55961/RPC2: -1 >

```
I do seem to be good at messing up your well laid scripts O:) sorry
this wouldn't route anything out past my router would it? because all my public ports are closed

---

### Post by kaivalagi on 2009-05-13
> **snkiz said:**
> I ran i three times, once while seeding a torrent, once while seeding/starting a torrent and once while seeding/ downloading a torrent
this is what I got:
```
snkiz@ckubuntu:~/Desktop$ python test_deluge.py
* setting sclient up
* getting session state of torrents
timed out
snkiz@ckubuntu:~/Desktop$ python test_deluge.py
* setting sclient up
* getting session state of torrents
not well-formed (invalid token): line 1, column 1
snkiz@ckubuntu:~/Desktop$ python test_deluge.py
* setting sclient up
* getting session state of torrents
<ProtocolError for 192.168.0.101:55961/RPC2: -1 >

```
I do seem to be good at messing up your well laid scripts O:) sorry
this wouldn't route anything out past my router would it? because all my public ports are closed

It does look suspiciously like network permissions...

To rule out the server could you try running the same script on the server doing your torrents? 

You'll need to edit the script though changing the uri setting to suit the localhost address of the server (I think: "http://127.0.0.1:55961").

---

### Post by snkiz on 2009-05-13
tried that same result, tried changing to the default you have in the script that gave an unauthorized error
Tried another download now it says error 32 broken pipe
and trying to go to that port with firefox asks me to download a bin file so it is open

---

### Post by kaivalagi on 2009-05-14
> **snkiz said:**
> tried that same result, tried changing to the default you have in the script that gave an unauthorized error
Tried another download now it says error 32 broken pipe
and trying to go to that port with firefox asks me to download a bin file so it is open

Did you try [http://127.0.0.1:55961](http://127.0.0.1:55961) - the port number is different to what was commented out in the script

If the script doesn't work locally on the server then the server has an issue we need to track down - it might have something to do with RPC call permissions...?

I think I'll have to try and setup a second pc with deluge too and try all of this with that, not likely until the weekend though

---

### Post by snkiz on 2009-05-14
strange thing I tried it localy on my desktop with the port you set and it worked. but if I use the port reported by deluge I get broken pipe. so I tried the default port on my server and got connection refused. network tools says that port is closed. Even stranger, I jusst installed conkyDeluge package on my server and it gives same errors. I wonder if we are hitting the right port?

**[COLOR="Red"]UPDATE[/COLOR]**
I think I figured it out. in an effort to simplify my life I setup deluge to run as a daemon on my server, _under its own system user_ I can't use the gtk interface on my server or connect to it with the gtk on my desktop. and I believe that the port conky connects to is the gtk port. I was hopping my setup would be like the way the transmission daemon is setup, but not quite.

---

### Post by snkiz on 2009-05-14
Here is the init script I got from the deluge site as you can see it needs to start as a spefic user [COLOR="Red"]grrr[/COLOR].

```
snkiz@ckbuntu-serv:~$ cat /etc/init.d/deluge-daemon
#!/bin/sh
### BEGIN INIT INFO
# Provides:          deluge-daemon
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      $network
# Should-Stop:       $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Daemonized version of deluge and webui.
# Description:       Starts the deluge daemon with the user specified in
#                    /etc/default/deluge-daemon.
### END INIT INFO

# Author: Adolfo R. Brandes 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Deluge Daemon"
NAME1="deluged"
NAME2="deluge"
DAEMON1=/usr/bin/deluged
DAEMON1_ARGS="-d"
DAEMON2=/usr/bin/deluge
DAEMON2_ARGS="-u web"
PIDFILE1=/var/run/$NAME1.pid
PIDFILE2=/var/run/$NAME2.pid
PKGNAME=deluge-daemon
SCRIPTNAME=/etc/init.d/$PKGNAME

# Exit if the package is not installed
[ -x "$DAEMON1" -a -x "$DAEMON2" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$PKGNAME ] && . /etc/default/$PKGNAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

if [ -z "$RUN_AT_STARTUP" -o "$RUN_AT_STARTUP" != "YES" ]
then
   log_warning_msg "Not starting $PKGNAME, edit /etc/default/$PKGNAME to start it."
   exit 0
fi

if [ -z "$DELUGED_USER" ]
then
    log_warning_msg "Not starting $PKGNAME, DELUGED_USER not set in /etc/default/$PKGNAME."
    exit 0
fi

#
# Function that starts the daemon/service
#
do_start()
{
   # Return
   #   0 if daemon has been started
   #   1 if daemon was already running
   #   2 if daemon could not be started
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER --test > /dev/null
   RETVAL1="$?"
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER --test > /dev/null
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 1

   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --make-pidfile --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER -- $DAEMON1_ARGS
   RETVAL1="$?"
        sleep 2
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --make-pidfile --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER -- $DAEMON2_ARGS
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 2
}

#
# Function that stops the daemon/service
#
do_stop()
{
   # Return
   #   0 if daemon has been stopped
   #   1 if daemon was already stopped
   #   2 if daemon could not be stopped
   #   other if a failure occurred

   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE2
   RETVAL2="$?"
   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE1
   RETVAL1="$?"
   [ "$RETVAL1" = "2" -o "$RETVAL2" = "2" ] && return 2

   rm -f $PIDFILE1 $PIDFILE2

   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] && return 0 || return 1
}

case "$1" in
  start)
   [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME1"
   do_start
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  stop)
   [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME1"
   do_stop
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  restart|force-reload)
   log_daemon_msg "Restarting $DESC" "$NAME1"
   do_stop
   case "$?" in
     0|1)
      do_start
      case "$?" in
         0) log_end_msg 0 ;;
         1) log_end_msg 1 ;; # Old process is still running
         *) log_end_msg 1 ;; # Failed to start
      esac
      ;;
     *)
        # Failed to stop
      log_end_msg 1
      ;;
   esac
   ;;
  *)
   echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
   exit 3
   ;;
esac

:
```
and the /etc/default file
```
# Configuration for /etc/init.d/deluge-daemon

# The init.d script will only run if this variable non-empty.
DELUGED_USER="deluge"             # !!!CHANGE THIS!!!!

# Should we run at startup?
RUN_AT_STARTUP="YES"
```

---

### Post by snkiz on 2009-05-14
I found this at the deluge site, [http://dev.deluge-torrent.org/wiki/UserGuide/Authentication]("http://dev.deluge-torrent.org/wiki/UserGuide/Authentication")
and this[http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient]("http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient") going to try to wrap my head around it

---

### Post by kaivalagi on 2009-05-14
> **snkiz said:**
> I found this at the deluge site, [http://dev.deluge-torrent.org/wiki/UserGuide/Authentication]("http://dev.deluge-torrent.org/wiki/UserGuide/Authentication")
and this[http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient]("http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient") going to try to wrap my head around it

Let's hope you get there...looks promising

Worst come to the worst you could try using rtorrent on the server (I have the daemon init scripts), and host rtgui on apache for a remote gui (requires rtgui download and settings in the apache conf files for RPC). I also have a python script which with a little work could provide rtorrent details remotely in conky using RPC remotely...if we go this route we'll need to take it offline...via PM's or better still email/IM...this is very experimental ;)

In theory none of this should be needed though, for now I would keep plugging away at Deluge. If you get really stuck try talking to the devs on IRC, #deluge at irc.freenode.net. They are normally quite helpful for techy stuff.

Keep me posted

---

### Post by snkiz on 2009-05-14
lol **_GOT IT!_** I need a smoke then I will explain

Ok first off the rpc port is _NOT_ the one reported in the web ui its the one you use, I have no idea what thats for and it doesn't show on a port scan anyway.

since I set things up all wacky I'll explain that first:
I set up a system user on my server with the command:
```
sudo adduser --system deluge
```
then installed the init script I posted in post [#91]("http://ubuntuforums.org/showpost.php?p=7277144&postcount=91") following these instructions I got [here]("http://dev.deluge-torrent.org/wiki/UserGuide/InitScript#DebianUbuntuInitScript")
The small file goes in /etc/default/deluge-daemon and the large one goes in /etc/init.d/deluge-daemon 
> Make the script executable by root

```
sudo chmod 755 /etc/init.d/deluge-daemon
```

Run this script on start up

```
sudo update-rc.d deluge-daemon defaults
```

Start the daemon

```
sudo /etc/init.d/deluge-daemon start
```

That worked and all is right with the world. I can access the web ui from any browser on the network. still working on integration. 

Now to get conkyDeluge to talk to it took some effort. I needed to access the deluge console as the deluge user (you'll see why) so I did this:
```
sudo usermod --shell=/bin/bash deluge ; sudo passwd deluge
```
then entered a password.
now I use this to get to the console
```
su -c "deluge -u console" deluge
```
then follow [these]("http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient#GTKUI") instructions:
> 
   4. Enable remote connections:

      ```
config -s allow_remote True
```

      This allows other machines besides the localhost to be able to connect to the daemon using the GTK UI.
   5. Double check it was set properly:

      ```
config allow_remote
```

   6. Exit the Console UI:

      ```
exit
```

   7. Shutdown the daemon:

      *EDIT*```
su -c "killall deluged" deluge
```

   8. Add yourself to the authentication file:

      *EDIT*```
sudo echo "<username>:<password>" >> home/deluge/.config/deluge/auth
```

      where <username> and <password> are the username and password you intend to use. 

    Note: the username and password can be anything - they do not necessarily have to be your server's username and password.

   1. Restart the daemon:

      *EDIT*```
su -c deluged deluge
```
   
Congratulations! The server is now setup for GTK UI access. 
Check the rpc port (58846 is the default I think) is open by using network tools on your desktop to do a port scan of your server. If thats all good you can reset you deluge user like this:
```
sudo usermod --shell=/bin/false deluge ; sudo passwd -d deluge
```
Now replace the uri in the test script in post [#85]("http://ubuntuforums.org/showpost.php?p=7272059&postcount=85") with <username>:<password>@<server>:58846  and run it should connect. just use that uri as the --server option in in conkyDeluge. this is mine :D
```
conkyDeluge --server=deluge:deluge@192.168.0.101 --showsummary -v

```

---

### Post by snkiz on 2009-05-14
Got it working, showing just a tidy summary without the torrent details. It seems to use a lot cpu time though (10-20 % of my p3@900Mhz) is that normal?

---

### Post by kaivalagi on 2009-05-15
> **snkiz said:**
> Got it working, showing just a tidy summary without the torrent details. It seems to use a lot cpu time though (10-20 % of my p3@900Mhz) is that normal?

Congratulations on the success!

I am guessing because there is a round trip via the network, cpu usage is up, I don't notice any cpu usage at all but I do have 4 cores...Normally the app will spike for a brief moment, I am guess it is spiking close together and looking like constant cpu use.

Try reducing the refresh interval for the command by a few seconds...it might be the frequency of the refresh is on a tripping point for constant cpu use.

It might also make sense to monitor cpu and run the script directly in the terminal a few times...might help explain some things

---

### Post by snkiz on 2009-05-15
> **kaivalagi said:**
> Congratulations on the success!
Thank you.
> **kaivalagi said:**
> I am guessing because there is a round trip via the network, cpu usage is up
During my search of the deluge forums I ran across a post by a dev saying that the gtk interface wasn't optimized for remote access and could cause heavy network traffic. I didn't think about at the time seeing as I'm dealing with a lan, so of course I can't find it now. But is it possible that the web ui rpc calls are somehow more efficient?
> **kaivalagi said:**
> Normally the app will spike for a brief moment
I noticed that, I get a BIG python spike (like everything available) when I enable torrent details
> **kaivalagi said:**
> Try reducing the refresh interval for the command by a few seconds
Um.. how would I do that? The deluge part is in the same window as my clock, don't wanna mess that up.
> **kaivalagi said:**
> It might also make sense to monitor cpu and run the script directly in the terminal a few times...might help explain some things
I tried various conky setups, changing the deluge variables between none, summary, and torrent details. So far as I can tell usage is around 5-10%(baseline conkyWeather and conkyEmail active), 10-20%, 15-70%(maxed out on spikes) respectively.

I can't believe I'm the first to try this on a remote setup. Are you still planing to try it out? I'm sure you'll find things I missed.

---

### Post by kaivalagi on 2009-05-15
> **snkiz said:**
> Um.. how would I do that? The deluge part is in the same window as my clock, don't wanna mess that up.

If you're calling the deluge script from conky with an execi/execpi command the number directly after is the refresh interval. Set it to be 10 for every 10 seconds. If you are using exec change it.

> **snkiz said:**
> I can't believe I'm the first to try this on a remote setup. Are you still planing to try it out? I'm sure you'll find things I missed.

I used to use rtorrent and had a script displaying summary info from it (using XML RPC as with Deluge). I never really got back to a separate client/server setup after that...

---

### Post by stepper on 2009-05-17
> **kaivalagi said:**
> As the templates are used for multiple torrent output and are called only once from the script, it is impossible to have conky execbar/execibar functionality. That would require the script being called for each torrent separately so the exec could be done through execbar/execibar (where we don't know the total number everytime).

Unless conky changes so that creating a bar is as simple as ${color} and ${font} this won't be possible.

In theory the summary could be setup to have this as there is only one output, but unless the summary and each torrents output can look the same it's a no go

Sorry
I found a script on the forums for transmission and I applied it for Deluge with the help of your script. Thanks for another script.

Here is my modified script to show progress bar of each seperate torrent.

```
#/bin/bash
#delugeinfo.sh
#Based on alacrityit's transmission script (http://ubuntuforums.org/showthread.php?t=892148)
#Requires conkyDeluge: 'sudo apt-get install conkydeluge' & ssed

for number in `conkyDeluge -l0 | awk '$0 != "" {printf "%s, ",$0} $0 == "" {printf "\n"}' > current_torrents && cat -n current_torrents | sed '$d' | awk '{print $1}'`
do
        torrentinfo=`conkyDeluge -l0 | awk '$0 != "" {printf "%s, ",$0} $0 == "" {printf "\n"}' | head -$number | tail -1`
        name=`echo "$torrentinfo" | cut -d"," -f1`
        percent=`echo "$torrentinfo"  | cut -d"," -f3 | cut -d"%" -f1- | cut -d"-" -f2`
        percentbar=`echo $percent | ssed -R 's/(\d+).\d+%/\1/'`
        if [ "$percentbar" -lt "10" ];then
                percentbar=`echo $percentbar | ssed -R 's/(\d)/0\1/'`
        fi
        total=`echo "$torrentinfo" | cut -d"," -f3 | cut -d"%" -f1 | cut -d"/" -f2 | cut -d"-" -f1`
        download=`echo "$torrentinfo" | cut -d":" -f2 | cut -d"U" -f1`
        eta=`echo "$torrentinfo" | cut -d":" -f4 | cut -d"," -f1`
        echo "$name"
        echo "$percent of $total  " 'at '"$download"'${goto 275}''ETA:'"$eta "
        echo '${execbar echo .'"$percentbar"'}'   	 
	
done

```The above script is all torrents. For active torrents change -l0 option to -a. Check attached screenshot.

---

### Post by kaivalagi on 2009-05-17
> **stepper said:**
> I found a script on the forums for transmission and I applied it for Deluge with the help of your script. Thanks for another script.

Here is my modified script to show progress bar of each seperate torrent.

...

The above script is all torrents. For active torrents change -l0 option to -a. Check attached screenshot.

Very nicely done, the script and screenshot deserves posting on the conkyrc thread! I am not sure but you might be able to get the same output using just a template too, $percentbar etc can be placed into a template and brought through using execpi

You may also want to check out my gtk-desktop-info app (see my sig) for Deluge output, see the attached. It has the benefit of using html so you can set html templates up for how the output needs to look per summary/torrent etc. What you see is the default output

---

### Post by WiseGuy1020 on 2009-05-18
Hey K

I was trying to limit the number of deluge torrents that are displayed. I tried using the -l option but I remember reading that you cannot use options in the conkyrc file when using a template file. 

I am pretty sure that I cannot use that option in the template file itself. There has to be a way I know, but I cannot figure it out and I really do not want to chose between options or using a template.

Any help would be appreciated.

---

### Post by kaivalagi on 2009-05-19
> **WiseGuy1020 said:**
> Hey K

I was trying to limit the number of deluge torrents that are displayed. I tried using the -l option but I remember reading that you cannot use options in the conkyrc file when using a template file. 

I am pretty sure that I cannot use that option in the template file itself. There has to be a way I know, but I cannot figure it out and I really do not want to chose between options or using a template.

Any help would be appreciated.

You should be okay to use -l / --limit= from the main exec call in your conkyrc....

Normally if something isn't usable when a template option is used I'll make mention in the help (conkyDeluge -h)

Cheers

---

### Post by WiseGuy1020 on 2009-05-19
Thanks for clearing that up.

---

### Post by WiseGuy1020 on 2009-06-01
Hey K the limit option is not working. When I run conkyDeluge in a terminal I can see it picks up the limit option by adding the verbose option but it does not display any torrent info. When I remove the limit option it works fine. I have tried both -l and --limit= and neither works. Please help.


Thanks, 

D

---

### Post by kaivalagi on 2009-06-02
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Updated to work with limit option and handle ~ based template paths, see here for changes: [https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.09_source.changes](https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.09_source.changes)

The first post has been updated and the apt packages should be available shortly

**REMEMBER:** To get this update you will need to change your repository settings for my new PPA locations available for Hardy, Intrepid and Jaunty versions of Ubuntu. See the first post install instructions for details...

Chimo

---

### Post by WiseGuy1020 on 2009-06-02
Hey K,

Your update has got the limit option working but now the template call is broken. I know the syntax is correct because conkyDeluge was calling the template file fine before the update.

Thanks,

D

---

### Post by kaivalagi on 2009-06-03
> **WiseGuy1020 said:**
> Hey K,

Your update has got the limit option working but now the template call is broken. I know the syntax is correct because conkyDeluge was calling the template file fine before the update.

Thanks,

D

Can you post your conkyrc and template so I can reproduce the error, I had a quick look and all _should_ be fine

---

### Post by WiseGuy1020 on 2009-06-03
this is my conkyrc. 

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
background true
default_shade_color grey
default_outline_color black
default_color FFFFFF
use_spacer none
no_buffers yes
uppercase no
color1 D2D2D2
color2 1289D6
minimum_size 250
maximum_width 250
gap_y 30
update_interval 2
text_buffer_size 800

TEXT
${color2}SYSTEM ${hr 2}
${color1}${font}CPU0:${color} ${cpu cpu0}% ${cpubar cpu0}
${font}${color1}CPU1:${color} ${cpu cpu1}% ${cpubar cpu1}
${font}${color1}CPU2:${color} ${cpu cpu2}% ${cpubar cpu2}
${color1}${font}Memory: ${color}$memperc %  $membar
${color1}CPU Temp: ${color}${acpitemp}°C${alignr}${color1}HDD Temp: ${color}${execi 60 ~/.scripts/hddmonit.sh}°C

${color2}NETWORK ${hr 2}${if_existing /sys/class/net/eth0/operstate up}${color1}
Type:${color}Wired ${alignr}${color1}Local IP: ${color}${addr eth0}
${color1}Down: $color${downspeedf eth0} k/s ${alignr}${color1}Up: ${color}${upspeedf eth0} k/s

${endif}${if_existing /sys/class/net/ra0/operstate up}${color1}
Type: ${color}Wireless ${alignr}${color1}Local IP:${color}${addr ra0}
${color1}Mode: ${color}${wireless_mode ra0} ${alignr}${color1}LinkQuality: ${color}${wireless_link_qual_perc ra0}%
${color1}AP: ${color}${wireless_essid ra0} ${alignr}${color1}Bitrate: ${color}${wireless_bitrate ra0}${color1} 
Down: $color${downspeedf ra0} k/s ${alignr}${color1}Up:${color} ${upspeedf ra0} k/s

${endif}${if_existing /sys/class/net/wlan0/operstate up}$color
Type: Wireless ${alignr}Local IP:${addr wlan0}
Mode: ${wireless_mode wlan0} ${alignr}LinkQuality: ${wireless_link_qual_perc wlan0}%
AP: ${wireless_essid wlan0} ${alignr}Bitrate: ${wireless_bitrate wlan0} 
Down: $color${downspeedf wlan0} k/s ${alignr}Up: ${upspeedf wlan0} k/s

${endif}${color2}WEATHER ${hr 2}${color1}
${execpi 300 conkyForecast --imperial --location=USFL0316 --template=/home/dman/.conkyForecast.template}

${color2}MAIL ${hr 2}${color1}
Google: ${color}${execi 300 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=xxxxxxxxxx --password=xxxxxxxx --ssl -i 5 -w 41 -l 2 --port=993}${color}

${color2}TORRENTS ${hr 2}
${color1}${execpi 2 conkyDeluge --torrenttemplate=/home/dman/.conkydeluge.template}
```


and this is my template file 

```
${color}[name]
${color1}[state] - ${color}[progress] ${color1}${alignr}[totaldone]/[totalsize]
${color1}ETA: ${color}[eta]${alignr}${color1}DL: ${color}[downloadrate] ${color1}UL: ${color}[uploadrate]

```

---

### Post by snkiz on 2009-06-03
k mine's broke too. not using the limit option and I haven't changed anything, just did apt-get upgrade.

---

### Post by kaivalagi on 2009-06-03
**[COLOR="Orange"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Fixed the problem with template loading, my bad! :oops: I had missed the os import needed for the ~ based template path support.

See here for changes: [https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.10_source.changes](https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.10_source.changes)

The first post has been updated and the apt packages should be available shortly

**REMEMBER:** To get this update you will need to change your repository settings for my new PPA locations available for Hardy, Intrepid and Jaunty versions of Ubuntu. See the first post install instructions for details...

Chimo

---

### Post by snkiz on 2009-06-04
My gawd K your quick, Thank you again for your efforts.

---

### Post by WiseGuy1020 on 2009-06-18
Hey K, 

 I am getting a new error message when running conkyDeluge. Seems like it is always me. I just did a clean install with the latest jaunty and I am not sure if there was a python upgrade or something that might be messing things up.

Thanks for your help,

D

---

### Post by kaivalagi on 2009-06-19
> **WiseGuy1020 said:**
> Hey K, 

 I am getting a new error message when running conkyDeluge. Seems like it is always me. I just did a clean install with the latest jaunty and I am not sure if there was a python upgrade or something that might be messing things up.

Thanks for your help,

D

I just updated, seeing a deluge upgrade in the mix, but conkyDeluge is still working fine for me (I did restart the deluge daemon too)

Are you running the latest Deluge via the ppa the deluge team setup?

This is what I have setup in sources.list:

```
# deluge
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main
```

I am running Deluge 1.1.9 now

---

### Post by WiseGuy1020 on 2009-06-19
I am also running deluge 1.1.9

---

### Post by kaivalagi on 2009-06-20
> **WiseGuy1020 said:**
> I am also running deluge 1.1.9

All I can suggest is uninstalling deluge fully, then installing again. Never seen this before

---

### Post by WiseGuy1020 on 2009-06-21
Yeah that was the trick. I purged deluge and did an autoremove, reinstalled and everything is working smooth now.

Thanks for your help,

D

---

### Post by merlin_ie on 2009-06-22
Hi kaivalagi. I don't know what I've done, but the title of the torrent seems to push the window wider. Is there a way make the title " spill " onto the next line or some other alternative?

[IMG]http://i198.photobucket.com/albums/aa307/simply-delta/ConkyDeluge.png[/IMG]

```
# set to yes if you want Conky to be forked in the background
background no
# Use Xft?
use_xft yes
xftfont Trebuchet MS:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
    own_window yes
    own_window_transparent yes
    own_window_type override
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 150 0

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
own_window_colour white

# Text alignment, other possible values are commented
alignment top_left

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 0

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer left

# colours
color1 white
# light blue
color2 6892C6
# orange
color3 E77320
# green
color4 78BF39
# red
color5 CC0000
#yellow
color6 FFFF00

TEXT
${font Trebuchet:size=20}${time %H}${font Trebuchet:size=20}${time :%M}${voffset -10}${font Trebuchet:size=10}${time %S}   ${goto 125}${font Trebuchet:size=10}${time %A}      
${goto 110}${voffset 2}${time %d %B %Y}${font}

${hr 2}
${goto 150}${voffset 15}${font Trebuchet:size=10}${alignc}${color1}Amarok${color}${font}
${color6}${voffset -13}${cpubar cpu3 1,100}${alignr 2}${cpubar cpu4 1,100}${color}
${color5}${voffset -13}${cpubar cpu5 4,100}${alignr 2}${cpubar cpu6 4,100}${color}
${if_running amarokapp}${color}${alignc}Now Playing${color white}
${alignc}${execi 1 /etc/conky/amarok artist}
${alignc}${execi 1 /etc/conky/amarok title}
${execibar 1 /etc/conky/amarok progress}
${alignc} ${execi 1 /etc/conky/amarok album} 
${alignc}${execi 1 /etc/conky/amarok year} - ${color white}${alignc}${execi 1 /etc/conky/amarok genre}
${hr 2}
${font Trebuchet:size=10}${goto 110}${alignc}${color1}Torrents${color}${font}
${color6}${voffset -13}${cpubar cpu3 1,100}${alignr 2}${cpubar cpu4 1,85}${color}
${color5}${voffset -13.5}${cpubar cpu5 4,100}${alignr 2}${cpubar cpu6 4,85}${color}

${color1}${execpi 5 conkyDeluge --showsummary --summarytemplate=/etc/conkyDeluge.template}
${color1}${execpi 5 conkyDeluge --torrenttemplate=/etc/conky/conkyDeluge.template}
```

Edit : I just tried using your example of the script and it returned the window to normal but the title of the torrent was cut off. So, I would still like to pursue the option of making the title continue on a new line (if possible)

---

### Post by WiseGuy1020 on 2009-06-22
try adding a maximum_width option in your .conkyrc. 


edit: Actually that would only stop the window getting wider. I don't think you can get the title to wrap. I remember seeing something about not being able to wrap lines on his conkyEmail thread.

Like mine:

```
use_xft 
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color D2D2D2
use_spacer none
no_buffers yes
uppercase no
color1 FFFFFF
minimum_size 250
**maximum_width 250**
gap_y 30
update_interval 2
text_buffer_size 768

```

---

### Post by merlin_ie on 2009-06-22
hhmmm ok. I think I'll just have to make do with it. I don't get many torrents so it's not too much hassle. Now, if only I could get a script to show download status of Rapidshare with "DownThemAll" plugin :D:D

---

### Post by snkiz on 2009-06-23
I bet k is working on it, he fixed the word wrap thing with conky email.

---

### Post by WiseGuy1020 on 2009-06-26
Hey K,

I have noticed that the order in which the torrents are displayed is based off the date the torrent is added to deluge. Would there be a way to make each torrent display in the order that it is queued in deluge?  

Thanks,

D

---

### Post by kaivalagi on 2009-06-26
> **WiseGuy1020 said:**
> Hey K,

I have noticed that the order in which the torrents are displayed is based off the date the torrent is added to deluge. Would there be a way to make each torrent display in the order that it is queued in deluge?  

Thanks,

D

The order is actually more complicated. The list is ordered by state (downloading, seeding and then inactive) then by % complete, isn't that the most appropriate?

---

### Post by WiseGuy1020 on 2009-06-26
If I have multiple torrents that are in the downloading state what dictates the order they are displayed?


Edit:Never mind I re-read your post. It's really late here.

Could you make it possible to change the order?


Thanks,

D

---

### Post by kaivalagi on 2009-06-26
> **WiseGuy1020 said:**
> Could you make it possible to change the order?


I could add an new option for sorting method, but that will go down as a "low priority change request" on my TODO list :)

Edit: I am not even sure whether it will be possible to duplicate the order as in the deluge client...only possible if deluge provides a key in the dbus api data which relates to it's client frontend (doubtful).
What other options for sorting would be useful, i.e. how are you sorting in your deluge client?

---

### Post by WiseGuy1020 on 2009-06-26
There is no real category that I sort my torrents by. I arbitrarily choose the order that are they queued in by using the "queue up" and "queue down" buttons. I just wanted my conky to reflect that order. I had 5 or 6 torrents downloading but my conky is set to display only 3 and thats when I thought of this option. No big deal, I understand the low priority. Just thinking of ways to improve your scripts and thought this would be useful.

Keep up the good work,

D


edit: Thats the way I would want it sorted, but I could think of other options. You could sort by date added, ETA ,or download speed. Ideally it would be nice to have an option to sort in conky for every column that you can sort by in deluge.

---

### Post by kaivalagi on 2009-06-26
> **WiseGuy1020 said:**
> There is no real category that I sort my torrents by. I arbitrarily choose the order that are they queued in by using the "queue up" and "queue down" buttons. I just wanted my conky to reflect that order. I had 5 or 6 torrents downloading but my conky is set to display only 3 and thats when I thought of this option. No big deal, I understand the low priority. Just thinking of ways to improve your scripts and thought this would be useful.

Keep up the good work,

D


edit: Thats the way I would want it sorted, but I could think of other options. You could sort by date added, ETA ,or download speed. Ideally it would be nice to have an option to sort in conky for every column that you can sort by in deluge.

I have found a way to get the queue position as defined in the client for "downloading" state torrents, this means it's do-able

I think I'll add a sortby option to allow a choice between "progress","queue" and "eta", I can then add more options later.

Give me a couple of days :)

---

### Post by WiseGuy1020 on 2009-06-26
You, my man, are awesome. That sounds perfect. Take your time, that is going to be sweet.

Thanks alot,

D

---

### Post by kaivalagi on 2009-06-27
@WiseGuy1020

Can you give the attached deb package a try before I release via synaptic?

It includes a new sortby option as follows:

```
  -b SORTTYPE, --sortby=SORTTYPE
                        Define the sort method for output, can be "progress",
                        "queue" or "eta". Also note that a torrent's state
                        supersedes anything else for sorting, in the order,
                        from top to bottom: downloading, seeding, queued,
                        paused, unknown)

```

Let me know if it works for you...

---

### Post by WiseGuy1020 on 2009-06-29
Just downloaded your .deb. I will give it a try tomorrow morning, it is real late here. 

Thanks,

D

---

### Post by rbcrssn36 on 2009-06-29
I have Ubuntu 8.10 which has until now been working fine. Today, I had changed the login screen theme and had installed the TimeVault application.

Thanks

Jimmy Martin

---

### Post by kaivalagi on 2009-06-29
> **rbcrssn36 said:**
> I have Ubuntu 8.10 which has until now been working fine. Today, I had changed the login screen theme and had installed the TimeVault application.

Thanks

Jimmy Martin

Can you run the script in the terminal with the --verbose option set and post what you see?

---

### Post by WiseGuy1020 on 2009-06-29
Hey K, 

That test deb worked perfectly. Can you add a "downspeed" and "upspeed" and "ratio" options before you update for everyone?

Thanks for your help,

D

---

### Post by kaivalagi on 2009-06-30
> **WiseGuy1020 said:**
> Hey K, 

That test deb worked perfectly. Can you add a "downspeed" and "upspeed" and "ratio" options before you update for everyone?

Thanks for your help,

D

No worries, I'll add the other options in the next day or so and setup the package

Cheers

---

### Post by kaivalagi on 2009-06-30
**[COLOR="Purple"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Added --sortby option, takes either takes either 'progress', 'queue', 'eta', 'download', 'upload' or 'ratio'.

**Also note** that a torrent's state supersedes anything else for sorting, in the order, from top to bottom: downloading, seeding, queued, paused, unknown.

See here for changes: [https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.11_source.changes](https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.11_source.changes)
[COLOR="Navy"]Edit: See here for bug fix for above: [https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.12_source.changes](https://launchpad.net/%7Em-buck/+archive/conky/+files/conkydeluge_2.12_source.changes)[/COLOR]

The first post has been updated and the apt packages should be available shortly

**REMEMBER:** To get this update you will need to change your repository settings for my new PPA locations available for Hardy, Intrepid and Jaunty versions of Ubuntu. See the first post install instructions for details...

Chimo

---

### Post by WiseGuy1020 on 2009-06-30
Hey K,

Something in that update changed things. In my conky the download speed is not displaying KiB/s. Instead it is displaying bytes per second with several decimal places. This also happens when conkyDelgue is ran in a terminal. Can you take a look?

Thanks,

D

---

### Post by kaivalagi on 2009-06-30
> **WiseGuy1020 said:**
> Hey K,

Something in that update changed things. In my conky the download speed is not displaying KiB/s. Instead it is displaying bytes per second with several decimal places. This also happens when conkyDelgue is ran in a terminal. Can you take a look?

Thanks,

D

Whoops, update with fix on it's way...should be in apt soon

---

### Post by WiseGuy1020 on 2009-06-30
Hey K,

Yeah it's working great now. Thanks for the update.

Thanks,

D

---

### Post by archeryguru2000 on 2009-07-05
I have a quick question.  I am currently using ubuntu's repo version (v0.5.8.9) and have decided to try and have conky display some deluge info.  I see know that I must upgrade to v1.xx to utilize the deluge.ui.client commands.

My question is this, am I able to "*pause*" my current downloads (~20) while I remove the old version and install the new version?  Will the downloads take-off from their current state in the new version, or will I have to sacrifice something?

Thanks for any assistance,
~~archery~~

---

### Post by kaivalagi on 2009-07-05
> **archeryguru2000 said:**
> I have a quick question.  I am currently using ubuntu's repo version (v0.5.8.9) and have decided to try and have conky display some deluge info.  I see know that I must upgrade to v1.xx to utilize the deluge.ui.client commands.

My question is this, am I able to "*pause*" my current downloads (~20) while I remove the old version and install the new version?  Will the downloads take-off from their current state in the new version, or will I have to sacrifice something?

Thanks for any assistance,
~~archery~~

Shouldn't be a problem, if I were you I would do this:

[LIST=1]
[*]Pause the torrents
[*]Right click on the deluge icon in the system try and choose "Quit & Shutdown Daemon"
[*]Remove Deluge package via Synaptic then close it *
[*]Setup the deluge repo in your sources list ([https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa))
[*]Load synaptic and click Reload then pick the relevant deluge package for install (check version)
[*]Start deluge again and resume your torrents
[/LIST]

* I can't be sure if the package in the deluge ppa is of the same name as the ubuntu repo, hence the removal and install steps rather than just update - your preferences should persist as they are stored in your home directory

---

### Post by archeryguru2000 on 2009-07-05
> **kaivalagi said:**
> Shouldn't be a problem, if I were you I would do this:

[LIST=1]
[*]Pause the torrents
[*]Right click on the deluge icon in the system try and choose "Quit & Shutdown Daemon"
[*]Remove Deluge package via Synaptic then close it *
[*]Setup the deluge repo in your sources list ([https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa))
[*]Load synaptic and click Reload then pick the relevant deluge package for install (check version)
[*]Start deluge again and resume your torrents
[/LIST]

* I can't be sure if the package in the deluge ppa is of the same name as the ubuntu repo, hence the removal and install steps rather than just update - your preferences should persist as they are stored in your home directory

Completed... success (I think)!  So far, each torrent is in the "Checking" phase.  I'll keep you posted of my progress.  Thanks again for the prompt response.

~~archery~~

---

### Post by archeryguru2000 on 2009-07-05
Alright!  Everything is going great.  It's just taking FOREVER to check each torrent (each one is several gigs :lol: )!  Anyway, thanks for the assistance.  I'll get cracking on setting up conky to accommodate the updated deluge.

~~archery~~

---

### Post by kaivalagi on 2009-07-05
Yeah, it does take some time to check downloads, especially those big ones ;)

I should be about later on in the forums, so will pick up any questions then, have fun!

---

### Post by archeryguru2000 on 2009-07-06
Here's a question for you.  How on Earth can I speed up this new version of Deluge?  I noticed a dramatic decrease in download speed with this new version.  I checked all preference settings, but couldn't determine a mistake in my settings.  I did find [**_this post_**]("http://forum.deluge-torrent.org/viewtopic.php?f=7&t=11165") on the intrawebs, but it doesn't really explain anything (at least not clearly).

Have you (or anybody else) noticed a decrease in speed from 0.5 to 1.0?

~~archery~~

---

### Post by kaivalagi on 2009-07-06
> **archeryguru2000 said:**
> Here's a question for you.  How on Earth can I speed up this new version of Deluge?  I noticed a dramatic decrease in download speed with this new version.  I checked all preference settings, but couldn't determine a mistake in my settings.  I did find [**_this post_**]("http://forum.deluge-torrent.org/viewtopic.php?f=7&t=11165") on the intrawebs, but it doesn't really explain anything (at least not clearly).

Have you (or anybody else) noticed a decrease in speed from 0.5 to 1.0?

~~archery~~

I haven't noticed a speed difference at all, I force encryption though...?

Check the encryption settings to make sure they haven't defaulted to something different from what you have set before. There may be some subtle changes to the configuration options...maybe something is now editable with a different default to before etc etc.

If I were you I would go through all the settings and set them to what you think is best for you (if you haven't already)

I think the same backend libraries are still used as before, so in theory the torrent activity should remain the same as before...unless a setting is making it behave differently

Sorry I can't be of more help

---

### Post by WiseGuy1020 on 2009-07-06
I think it might go without saying but, make sure your ports are completely forwarded through your firewall and router. Also check your modem too. Some modems also need to be configured.


Edit: Or maybe your ISP started shaping your traffic. Nothing you can really do if you already force encryption.I think my ISP monitors specific port traffic so I regularly change my ports, it seems to help.

---

### Post by dballiro1 on 2009-07-08
Maybe I'm overlooking something, but is there an easy way to get the whole output to align to the right?
If I put ${alignr} before the exec command it only does the first line of a torrents name and if I put it in the template file it actually displays the ${alignr} in the output.
Help, please?

---

### Post by WiseGuy1020 on 2009-07-08
Post your conkyrc and template so we can take a look.

---

### Post by dballiro1 on 2009-07-08
Sure. Here's the rc,
```
background        no
update_interval        1.0
double_buffer        yes

use_xft            no
xftfont            Monospace:size=10
xftalpha        0.8

own_window        yes
own_window_transparent    yes
own_window_type        override
own_window_hints    undecorated,below,sticky,skip_taskbar,skip_pager
#on_bottom        yes

minimum_size        300 50
draw_shades        no
draw_outline        yes
draw_borders        yes
draw_graph_borders    no
stippled_borders    0
border_margin        3
border_width        0

default_color        white
default_shade_color    black
default_outline_color    black

alignment        top_right
gap_x            20
gap_y            34
#gap_y            10

no_buffers        yes

TEXT
Networking${alignr}${color #707070}(${color white}speed down${color #707070}/${color white}up${color #707070})${color white} ${color #707070}[${color white}total down${color #707070}/${color white}up${color #707070}]
${hr}
${color #F09000}eth0${color #707070}:${color white} ${addr eth0}${alignr}${color #707070}(${color white}${downspeed eth0}k${color #707070}/${color white}${upspeed eth0}k${color #707070})${color white} ${color #707070}[${color white}${totaldown eth0}${color #707070}/${color white}${totalup eth0}${color #707070}]
${color #F09000}wlan0${color #707070}:${color white} ${wireless_essid wlan0}${alignr}${color #707070}(${color white}${downspeed wlan0}k${color #707070}/${color white}${upspeed wlan0}k${color #707070})${color white} ${color #707070}[${color white}${totaldown wlan0}${color #707070}/${color white}${totalup wlan0}${color #707070}]
${color #F09000}${downspeedgraph wlan0 12, 250 F09000 000000 200} ${color white} ${wireless_link_qual_perc wlan0}%
${color #707070}${hr}
${color #F09000}${exec conkyDeluge --sortby="download" --activeonly --torrenttemplate=~/Conky/conkydeluge}
```and the template
```
${alignr}[name]
${alignr}[state] - ETA: [eta]
${alignr}[totaldone]/[totalsize] - [progress]
${alignr}[downloadrate]/[uploadrate]
```

---

### Post by WiseGuy1020 on 2009-07-08
Your template is working fine, everything is aligned right. The problem must be in your conky config.


Got it. 

Change: ```
${color #F09000}${**exec** conkyDeluge --sortby="download" --activeonly -
```

To this:```
${color #F09000}${**execpi 1** conkyDeluge --sortby="download" --activeonly -
```



sidenote: Anyone know why there is red smiley face in front of the title of my post?

---

### Post by kaivalagi on 2009-07-08
> **WiseGuy1020 said:**
> sidenote: Anyone know why there is red smiley face in front of the title of my post?

Because you are eeeeevil :lolflag:

You must have the post icons option pre-set to that smiley, next time you prepare a post look at the section below where you type

---

### Post by NautilusP on 2009-07-21
Hi!
Can someone help me. I get error message if i run run conky in terminal "sh: conkyDeluge not found". I follow instruction and edit the conkyDeluge script to point to the correct location where conkyDeluge.py is.Here is modified script 
```
#! /bin/sh
cd /home/dimka/scripts/chrunchbang/conkydeluge/
$PYTHONPATH /usr/bin/python /home/dimka/scripts/chrunchbang/conkydeluge/conkyDeluge.py "$@"
```

conkyrc
```
#######################################################################
# variables ###########################################################

# fork to background ? ################################################
background no

# font settings ######################################################
use_xft yes
#font monospace-8
#xftfont Acknowledge TT BRK:size=12
#xftfont Edit Undo BRK:size=8
#xftfont Visitor TT2 (BRK):size=13
#xftfont FloydianCyr:size=12
#xftfont Matricha:size=10
#xftfont Neuropol:size=8
#xftfont DS Moster:size=8
xftfont Epson1:size=12
uppercase no
override_utf8_local yes

# update every 1 secs #################################################
update_interval 1

# stay running forever ################################################
total_run_times 0

# draw to root window #################################################
own_window no

# avoid flickering ####################################################
double_buffer yes

# size ################################################################
minimum_size 1270 800
maximum_width 1270

# position ############################################################
alignment top_left
#alignment top_middle
#alignment top_right
#alignment bottom_left
#alignment bottom_middle
#alignment bottom_right
#alignment middle_left
#alignment middle_right
gap_x 0
gap_y 0

# colors ##############################################################
default_color white
default_shade_color white
default_outline_color black
# custom colors #######################################################
color0 FFFFFF
color1 F5F5F5
color2 A2AEC6
color3 696969
color4 D3D3D3
color5 6495ED
color6 87CEFA
color7 5F9EA0
color8 BBBBBB
color9 262729


# borders #############################################################
draw_borders no
draw_graph_borders no
stippled_borders 8
border_margin 4
border_width 1

# shades ##############################################################
draw_shades no

# outline #############################################################
draw_outline no

# spacer ##############################################################
use_spacer no

# buffers (Substract (file system) buffers from used memory?)##########
no_buffers yes

# sampling ############################################################
cpu_avg_samples 2
net_avg_samples 2

# configuration #######################################################
TEXT

${voffset 20}${offset 15}$color8 /$color3 System$color8 /
${offset 05}$color2 $sysname$color9 -$color2 $machine
${offset 05}$color2 $kernel
${offset 05}$color2 DiMkA$color9 on$color2 $nodename
${offset 05}$color6 ${time %A %d/%m/%y %kh%M}
${offset 05}$color2 Uptime :$color6 $uptime
${offset 1015}$color2 Deluge: ${execpi 1 conkyDeluge --sortby="download" --activeonly --torrenttemplate=/home/dimka/scripts/chrunchbang/conkydeluge/example/conkyDeluge.template}
```

---

### Post by kaivalagi on 2009-07-22
> **NautilusP said:**
> Hi!
Can someone help me. I get error message if i run run conky in terminal "sh: conkyDeluge not found". I follow instruction and edit the conkyDeluge script to point to the correct location where conkyDeluge.py is.Here is modified script 
```
#! /bin/sh
cd /home/dimka/scripts/chrunchbang/conkydeluge/
$PYTHONPATH /usr/bin/python /home/dimka/scripts/chrunchbang/conkydeluge/conkyDeluge.py "$@"
```

Is conkyDeluge in the /usr/bin folder?

Is it executable, if it isn't then run the following in a terminal:

```
sudo chmod +x /usr/bin/conkyForecast 
```
Hope that helps

---

### Post by Jeff Carr on 2009-07-22
Thank you so much for the scripts Kaivalagi.  I'm running the calendar, email, rhythmbox, and weather ones flawlessly.

The only problem I had was with deluge, and not with the script itself.  I wanted to do a ${if_running deluge}...  However, it never sees deluge that way on my machine as Deluge is running as [/usr/bin/python /usr/bin/deluge].

${if_running -x deluge} works just fine though, so I thought I'd pass that info on to anyone else looking for a solution.

---

### Post by kaivalagi on 2009-07-23
> **Jeff Carr said:**
> Thank you so much for the scripts Kaivalagi.  I'm running the calendar, email, rhythmbox, and weather ones flawlessly.

The only problem I had was with deluge, and not with the script itself.  I wanted to do a ${if_running deluge}...  However, it never sees deluge that way on my machine as Deluge is running as [/usr/bin/python /usr/bin/deluge].

${if_running -x deluge} works just fine though, so I thought I'd pass that info on to anyone else looking for a solution.

That is good to know, maybe it's worth you posted that solution onto the conkyrc thread, it should work for checking all python based apps...

---

### Post by dopple on 2009-07-25
Quick question. When I use conkyDeluge it's outputting a square character before it prints anything. You can see it at the end of the last horizontal line. It mist be conkyDeluge that's outputting this because I've tried removing everything before conkyDeluge and it's still there. I've checked the python script but couldn't tell how to fix it.

---

### Post by kaivalagi on 2009-07-25
> **dopple said:**
> Quick question. When I use conkyDeluge it's outputting a square character before it prints anything. You can see it at the end of the last horizontal line. It mist be conkyDeluge that's outputting this because I've tried removing everything before conkyDeluge and it's still there. I've checked the python script but couldn't tell how to fix it.

You're gonna need to post your conkyrc and template (if used). The script doesn't do this, it must be a setting or configuration...

---

### Post by dopple on 2009-07-27
Ok this is conky_dark (I downloaded and installed a version called conkolors. Might be best to scrap this and start fresh?)
```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color 1E1C1A
#default_shade_color white
#default_outline_color black
own_window_colour 1E1C1A

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}

HD ${hr 2}
${voffset 6}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
DELUGE ${hr 2}

${exec conkyDeluge}
```

---

### Post by markp1989 on 2009-10-08
thanks for the scripts, im using the deluge, weather and email scripts on my digital photo frame , its way cool :D 

i moved for torrentflux to deluge as i could get better speed with deluge, and the webui looks sexy

---

### Post by kaivalagi on 2009-10-09
> **markp1989 said:**
> thanks for the scripts, im using the deluge, weather and email scripts on my digital photo frame , its way cool :D 

i moved for torrentflux to deluge as i could get better speed with deluge, and the webui looks sexy

Yeah, Deluge download rates always seemed better than the other options to me too. I use the web ui to administer my remote box - It's nice to have a view of the remote box in conky too though :)

---

### Post by deh69 on 2009-10-11
Hello dudes,im in need of some help.

this is whats happening:
[IMG]http://img.photobucket.com/albums/v313/luixrox/deluge.jpg[/IMG]

basically, only one torrent shows correctly, the rest dont come into display.

conky:
> background yes
use_xft yes 
xftfont Verdana:size=8
xftalpha 0.5
update_interval 2.0
total_run_times 0 
own_window yes
own_window_type normal 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager 
double_buffer yes
minimum_size 250
maximum_width 250
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes 
default_color white
default_shade_color grey
default_outline_color grey
alignment bottom_right
gap_x 695
gap_y 45
no_buffers yes 
uppercase no
cpu_avg_samples 2 
override_utf8_locale yes
border_inner_margin 0
border_outer_margin 0
color1 white
color2 orange 
 
TEXT
${execpi 5 conkyDeluge --sortby=progress --activeonly --torrenttemplate=/deh/Conky/deluge.template}
${font Verdana:bold:size=10}${color orange}torrents$color$font ${hr 2}

deluge.template:
> ${color2}[name]
${color1}[state] - ETA: [eta]
[totaldone]/[totalsize]${alignr}${font Verdana:bold:size=8}[progress] ${font}
Up: [uploadrate]${alignr}${color2}${font Verdana:bold:size=8}Down:${color1} [downloadrate]${color}${font}


---

### Post by VCoolio on 2009-10-11
> **deh69 said:**
> Hello dudes,im in need of some help.

basically, only one torrent shows correctly, the rest dont come into display.


Add a line like this:

```
text_buffer_size 1024
```

If that is not enough, increase the number. It will also increase conky's memory load, so don't overdo it. Hope that solves it.

---

### Post by deh69 on 2009-10-12
It worked!! Thank you!

Its showing up to 4 torrents now. But what if im megalomaniac and i want all my 15+ torrents showing? does that increase in text buffer size handle them? If not, is there a max size i should try out that doesnt screw up memory load and other stuff along with it?

---

### Post by trahtung on 2009-10-14
Due to:
**Deluge 1.2.0_rc1 (07 October 2009)[ ¶]("http://dev.deluge-torrent.org/wiki/ChangeLog#Deluge1.2.0_rc107October2009")**

 **Core[ ¶]("http://dev.deluge-torrent.org/wiki/ChangeLog#Core1")**

 
[LIST]
[*]Implement new RPC protocol DelugeRPC replacing XMLRPC
[/LIST]
conky doesn't work :(

---

### Post by kaivalagi on 2009-10-14
> **trahtung said:**
> Due to:
**Deluge 1.2.0_rc1 (07 October 2009)[ ¶]("http://dev.deluge-torrent.org/wiki/ChangeLog#Deluge1.2.0_rc107October2009")**

 **Core[ ¶]("http://dev.deluge-torrent.org/wiki/ChangeLog#Core1")**

 
[LIST]
[*]Implement new RPC protocol DelugeRPC replacing XMLRPC
[/LIST]
conky doesn't work :(

Thanks for the heads up, although the package hasn't come through to the deluge ppa yet so I wont be updating until it's available for all...

I'll have a look at the changes required now though :)

---

### Post by snkiz on 2009-10-24
Package has come through the ppa now. I upgraded my server (Without reading the change log duh.) before my desktop and couldn't even connect with the gtk-ui. conky no worky now :(

Side note, its a shame the deluge team is probably going to miss the karmic deadline with this release

---

### Post by kaivalagi on 2009-10-24
> **snkiz said:**
> Package has come through the ppa now. I upgraded my server (Without reading the change log duh.) before my desktop and couldn't even connect with the gtk-ui. conky no worky now :(

Side note, its a shame the deluge team is probably going to miss the karmic deadline with this release

I have been playing with the new deluge api, it doesn't really suit this synchronous script at all but I am working on a solution...*fingers crossed*

---

### Post by markp1989 on 2009-10-25
> **snkiz said:**
> Package has come through the ppa now. I upgraded my server (Without reading the change log duh.) before my desktop and couldn't even connect with the gtk-ui. conky no worky now :(

Side note, its a shame the deluge team is probably going to miss the karmic deadline with this release

i acidently updated to the new deluge aswell, i hate it compared to the old 1, i know its still in testing , but it gave me no end of problems.

i rolled back, and will be sticking to the older one untill this script starts working with the newest one .

---

### Post by snkiz on 2009-10-25
> **kaivalagi said:**
> I have been playing with the new deluge api, it doesn't really suit this synchronous script at all but I am working on a solution...*fingers crossed*

Could you hook into the same signals that go out to the web-ui? Its all ajaxy and realtime.

---

### Post by kaivalagi on 2009-10-25
> **snkiz said:**
> Could you hook into the same signals that go out to the web-ui? Its all ajaxy and realtime.

No can do, webui will be driven off the same protocol I am referencing, DelugeRPC. It handles dynamically updating via asynchronous callbacks which suits ajax but not this script, this script is called by conky over and over so cannot perform in the same way.

Maybe all my scripts should write to a file and have conky read that...that way whatever the applicable mechanism is it can be used by the script with conky reading in a file whenever it wants...

---

### Post by snkiz on 2009-10-26
> **kaivalagi said:**
> 
Maybe all my scripts should write to a file and have conky read that...that way whatever the applicable mechanism is it can be used by the script with conky reading in a file whenever it wants...
Isn't that how your weather script works? When it fails to update it still shows the old info, so thats a plus for writing to file. What ever you decide, I'm sure it'll be new and improved. And 25% less packaging. Cheers! :)

---

### Post by lmcadory on 2009-10-28
Hi I wanted to know if your script can be modified to monitor Vuze torrents? I am not familiar with Python and figured I'd ask here.

---

### Post by kaivalagi on 2009-10-28
> **lmcadory said:**
> Hi I wanted to know if your script can be modified to monitor Vuze torrents? I am not familiar with Python and figured I'd ask here.

I have no idea what Vuze torrents are......so I am unlikely to handle them in a script. The script as it stands is made solely to talk to Deluge I am afraid.

---

### Post by lmcadory on 2009-10-29
Oh ok Vuze is Azures. It is a bit torrent application like deluge. I'll do some more research and come up with something

---

### Post by ner0tic on 2009-11-01
how much work is involved in upgrading this to work for deluge 1.2.x?  they no longer use xmlrpc so I was curious and dont have teh time to code it myself..

---

### Post by kaivalagi on 2009-11-01
> **trahtung said:**
> Due to:
**Deluge 1.2.0_rc1 (07 October 2009)[ ¶]("http://dev.deluge-torrent.org/wiki/ChangeLog#Deluge1.2.0_rc107October2009")**

 **Core[ ¶]("http://dev.deluge-torrent.org/wiki/ChangeLog#Core1")**

 
[LIST]
[*]Implement new RPC protocol DelugeRPC replacing XMLRPC
[/LIST]
conky doesn't work :(

> **snkiz said:**
> Package has come through the ppa now. I upgraded my server (Without reading the change log duh.) before my desktop and couldn't even connect with the gtk-ui. conky no worky now :(

Side note, its a shame the deluge team is probably going to miss the karmic deadline with this release

> **ner0tic said:**
> how much work is involved in upgrading this to work for deluge 1.2.x?  they no longer use xmlrpc so I was curious and dont have teh time to code it myself..

Got a new .py for you to test out...it hopefully works with 1.2 onwards....tarball attached.

Just extract it and replace the existing file from your previous install with it, after backing it up, i.e.

```
sudo cp /usr/share/conkydeluge/conkyDeluge.py /usr/share/conkydeluge/conkyDeluge.py.backup 
sudo cp path/to/new/conkyDeluge.py /usr/share/conkydeluge/
```

Let me know how it goes...I've switched OS and torrent client for a while (or more) so have done limited testing on this 8-[

I will be getting into the swing of things again soon, I have switched OS and now use ArchLinux rather than any debian based distro. It looks like the continuing support of my scripts will be without ppa updates, and instead my time will support AUR based installs. I will provide the usual tarball downloads of the source for non Arch users.

---

### Post by kaivalagi on 2009-11-01
formal, but as above...[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

---

### Post by snkiz on 2009-11-02
> **kaivalagi said:**
> formal, but as above...[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

Good luck on your new system K. I was looking at Arch not long ago. (DistroWatch says its Canadian.) Looks promising, don't have the time though just now. Id like to offer my launchpad account to continue the ppa, could you pm me with the details. I'm on limited interweb service for the next day or two, so please be patient with me.  :)

---

### Post by kaivalagi on 2009-11-02
> **snkiz said:**
> Good luck on your new system K. I was looking at Arch not long ago. (DistroWatch says its Canadian.) Looks promising, don't have the time though just now. Id like to offer my launchpad account to continue the ppa, could you pm me with the details. I'm on limited interweb service for the next day or two, so please be patient with me.  :)

There are already packages in the AUR created off the back of the packages I created in Launchpad, so having the launchpad.net side of things running still makes some sense. I haven't looked at whether I can actually build the source debian packages for supplying launchpad with...

If all that fails and it doesn't look like I'll continue supporting launchpad  directly I'll be in touch :) There must be some way of allowing others to build in my ppa, I could still dump sourcecode there as I like bazaar...

---

### Post by snkiz on 2009-11-03
I'm up and running again. Tried your revisions k, it didn't work unfortunately, held conky from even displaying. (But that could be my config.)

heres the output:
```

/usr/lib/pymodules/python2.6/deluge/common.py:65: UserWarning: Module deluge was already imported from /usr/lib/pymodules/python2.6/deluge/__init__.py, but /usr/lib/pymodules/python2.6 is being added to sys.path
  import pkg_resources

```
Is there still a debug flag I could use? I don't remember how we did that before.

---

### Post by kaivalagi on 2009-11-03
> **snkiz said:**
> I'm up and running again. Tried your revisions k, it didn't work unfortunately, held conky from even displaying. (But that could be my config.)

heres the output:
```

/usr/lib/pymodules/python2.6/deluge/common.py:65: UserWarning: Module deluge was already imported from /usr/lib/pymodules/python2.6/deluge/__init__.py, but /usr/lib/pymodules/python2.6 is being added to sys.path
  import pkg_resources

```
Is there still a debug flag I could use? I don't remember how we did that before.

Could try the --verbose option, it might provide more details

---

### Post by snkiz on 2009-11-03
Didn't really add much k sorry
```

snkiz@ckubuntu:~$ conkyDeluge -s 192.168.0.101 -S -v
/usr/lib/pymodules/python2.6/deluge/common.py:65: UserWarning: Module deluge was already imported from /usr/lib/pymodules/python2.6/deluge/__init__.py, but /usr/lib/pymodules/python2.6 is being added to sys.path
  import pkg_resources
*** INITIAL OPTIONS:
    server: 192.168.0.101
    port: 58846
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None
^CINFO: Proceeding with torrent data interpretation...
INFO: Preparing templates...
ERROR: writeOutput:Unexpected error:DelugeInfo instance has no attribute 'torrents_status'

```

---

### Post by jhoms on 2009-11-14
I don't know if this could be of any help but I just tried the .py file in the tar file last posted and it solved my problem with conkyDeluge in Ubuntu 9.10.
 
```
:~$ conkyDeluge -S -v
*** INITIAL OPTIONS:
    server: 127.0.0.1
    port: 58846
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None
INFO: Connection successful
INFO: Proceeding with torrent data interpretation...
INFO: Preparing templates...
INFO: Processing 2 torrent(s)...
INFO: Sorting torrent list using: eta
Total Torrents Queued:2 
107.2 MiB/525.1 MiB - 20.42%
DL: 63.2 KiB/s UL: 12.3 KiB/s
```

This is the piece of code I have embedded in my .conkyrc file

```
{exec conkyDeluge -SH}
```

And this is my deluge version installed

```
:~$ deluge --version
1.2.0-rc3

```

---

### Post by kaivalagi on 2009-11-14
> **jhoms said:**
> I don't know if this could be of any help but I just tried the .py file in the tar file last posted and it solved my problem with conkyDeluge in Ubuntu 9.10.
 
```
:~$ conkyDeluge -S -v
*** INITIAL OPTIONS:
    server: 127.0.0.1
    port: 58846
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None
INFO: Connection successful
INFO: Proceeding with torrent data interpretation...
INFO: Preparing templates...
INFO: Processing 2 torrent(s)...
INFO: Sorting torrent list using: eta
Total Torrents Queued:2 
107.2 MiB/525.1 MiB - 20.42%
DL: 63.2 KiB/s UL: 12.3 KiB/s
```

This is the piece of code I have embedded in my .conkyrc file

```
{exec conkyDeluge -SH}
```

And this is my deluge version installed

```
:~$ deluge --version
1.2.0-rc3

```

That's good to know its working for someone else too, the only issue is if I update the package all pre 1.2.0 users will lose the ability to connect to Deluge :)

---

### Post by ner0tic on 2009-12-02
has anyone had anyluck with deamons running on a different machine?

when i run it on the deamon box:
```
> ./conkyDeluge.py -SHv
/usr/lib/python2.6/site-packages/twisted/internet/_sslverify.py:5: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import itertools, md5
*** INITIAL OPTIONS:
    server: 127.0.0.1
    port: 58846
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None
INFO: Connection successful
INFO: Proceeding with torrent data interpretation...
INFO: Preparing templates...
INFO: Processing 4 torrent(s)...
Total Torrents Queued:4 
778.3 MiB/12.0 GiB - 6.34%
DL: 119.8 KiB/s UL: 125.8 KiB/s

```

but when i run it on my client machine:
```
$ ~/.conky/conkyDeluge.py -SH -s 192.168.1.101 -v
*** INITIAL OPTIONS:
    server: 192.168.1.101
    port: 58846
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None

``` and it just sits, which causes conky not to load because the script doesn't finish.

---

### Post by kaivalagi on 2009-12-03
> **ner0tic said:**
> has anyone had anyluck with deamons running on a different machine?

when i run it on the deamon box:
```
> ./conkyDeluge.py -SHv
/usr/lib/python2.6/site-packages/twisted/internet/_sslverify.py:5: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import itertools, md5
*** INITIAL OPTIONS:
    server: 127.0.0.1
    port: 58846
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None
INFO: Connection successful
INFO: Proceeding with torrent data interpretation...
INFO: Preparing templates...
INFO: Processing 4 torrent(s)...
Total Torrents Queued:4 
778.3 MiB/12.0 GiB - 6.34%
DL: 119.8 KiB/s UL: 125.8 KiB/s

```

but when i run it on my client machine:
```
$ ~/.conky/conkyDeluge.py -SH -s 192.168.1.101 -v
*** INITIAL OPTIONS:
    server: 192.168.1.101
    port: 58846
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None

``` and it just sits, which causes conky not to load because the script doesn't finish.

I did have this working in an old setup, you may need to provide and username and password maybe? You use a user/password by setting the server option like so:

```
-s user:password@address
```

Also ensure you are not running v.1.2 on the remote machine, this version has issues with this script as the whole communications method has changed under the hood of deluge.

---

### Post by ner0tic on 2009-12-03
> **kaivalagi said:**
> I did have this working in an old setup, you may need to provide and username and password maybe? You use a user/password by setting the server option like so:

```
-s user:password@address
```

Also ensure you are not running v.1.2 on the remote machine, this version has issues with this script as the whole communications method has changed under the hood of deluge.

I'll try it with teh user/pass, i have been running 1.2.0rc4 for a while now.  I had to make my own ebuilds since portage and the overlays are behind the times with deluge (portage still offers 1.1.9)
oh and yea, the server box is gentoo.


edit: no change adding the user/pass to the server flag

---

### Post by kaivalagi on 2009-12-03
> **ner0tic said:**
> I'll try it with teh user/pass, i have been running 1.2.0rc4 for a while now.  I had to make my own ebuilds since portage and the overlays are behind the times with deluge (portage still offers 1.1.9)
oh and yea, the server box is gentoo.


edit: no change adding the user/pass to the server flag

So, you are running version 1.1.9 on the server you are trying to get details from?

If so you should use the script currently available in my ppa and not the newer one for v1.2 I attached in recent posts. v1.2 of deluge introduced the twisted framework for the comms, before that it was XML-RPC based, that's the reason for the different between the 2 conky scripts available.

If you've tried both already (with the user/passwd thing) then I am not sure what is up...

---

### Post by ner0tic on 2009-12-03
> **kaivalagi said:**
> So, you are running version 1.1.9 on the server you are trying to get details from?

If so you should use the script currently available in my ppa and not the newer one for v1.2 I attached in recent posts. v1.2 of deluge introduced the twisted framework for the comms, before that it was XML-RPC based, that's the reason for the different between the 2 conky scripts available.

If you've tried both already (with the user/passwd thing) then I am not sure what is up...

no, im running 1.2.0rc4

the script runs when connecting to locahost, but not when i specify an ip

---

### Post by AlanBryant on 2010-01-05
> **ner0tic said:**
> no, im running 1.2.0rc4

the script runs when connecting to locahost, but not when i specify an ip

Anyone got this working on a remote machine yet? I'm having the same problem posted above.

deluge v1.2.0-rc5 on both machines and the py script from the latest tarball.

---

### Post by markp1989 on 2010-01-08
im having problems with conkyDeluge and deluge 1.2.0-rc4

try running from terminal:

```
mark@torrentslave:~$ conkyDeluge 
Traceback (most recent call last):
  File "/usr/share/conkydeluge/conkyDeluge.py", line 43, in <module>
    from deluge.ui.client import sclient
ImportError: cannot import name sclient
mark@torrentslave:~$ 
```

not sure if i am missing a package, or if i have an old version of conkyDeluge that doesnt work with this version?

thanks Markp1989

---

### Post by jhoms on 2010-01-08
My conkyDeluge.py file has a different import file (from deluge.ui.client import client) instead the *sclient* that appears in your case.

Maybe is the conkyDeluge version you are using.

You can check it this way:

```
jaume@jaume-desktop:~$ conkyDeluge --version
conkyDeluge v.2.13
```

---

### Post by kaivalagi on 2010-01-08
> **jhoms said:**
> My conkyDeluge.py file has a different import file (from deluge.ui.client import client) instead the *sclient* that appears in your case.

Maybe is the conkyDeluge version you are using.

You can check it this way:

```
jaume@jaume-desktop:~$ conkyDeluge --version
conkyDeluge v.2.13
```

I really ought to create 2 deluge packages, one for before and one for after the change...I'll get on to it for the new conkyhardcore ppa that's been setup

---

### Post by kaivalagi on 2010-01-09
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)[/COLOR][/SIZE]

**[COLOR="Blue"][SIZE="3"]IMPORTANT NEWS[/SIZE]**

All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa.

The ppa can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa")

To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck*
```
Then follow the modified first post instructions for the scripts
[/COLOR]

---

### Post by tomski on 2010-01-24
> **jhoms said:**
> My conkyDeluge.py file has a different import file (from deluge.ui.client import client) instead the *sclient* that appears in your case.

Maybe is the conkyDeluge version you are using.

You can check it this way:

```
jaume@jaume-desktop:~$ conkyDeluge --version
conkyDeluge v.2.13
```

> **kaivalagi said:**
> I really ought to create 2 deluge packages, one for before and one for after the change...I'll get on to it for the new conkyhardcore ppa that's been setup

any ideas how to fix this because i'm having the same problems :(

---

### Post by kaivalagi on 2010-01-24
> **tomski said:**
> any ideas how to fix this because i'm having the same problems :(

Currently there is a script attached a few posts back which SHOULD work for v1.2.?+, the script in the repo is for v1.1.9

If you are running v.1.2 of deluge then I suggest installing from the repo and overwriting the previously attached .py file over the top...I think I explained it in the post with the attachment...

I don't run Deluge anymore so I am not sure how long it might be before I get around to fixing any issues, Deluge keep changing the way their app works :(

Edit: The post I was referring to is here: [http://ubuntuforums.org/showpost.php?p=8218486&postcount=175](http://ubuntuforums.org/showpost.php?p=8218486&postcount=175)

---

### Post by tomski on 2010-01-24
thanks man i'll check it out :)

---

### Post by tomski on 2010-01-24
nope that one dont work :(

for debug i get this ouput:
```

$conkyDeluge -SH -s 192.168.1.1 -v
*** INITIAL OPTIONS:
    server: 192.168.1.1
    port: 58846
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None
^CINFO: Proceeding with torrent data interpretation...
INFO: Preparing templates...
ERROR: writeOutput:Unexpected error:DelugeInfo instance has no attribute 'torrents_status'

```

i also tried:
conkyDeluge -server=192.168.1.1 -v
conkyDeluge -SH -s user:pass@192.168.1.1 -v
conkyDeluge -s user:pass@192.168.1.1 -v

all give the same output as above

---

### Post by kaivalagi on 2010-01-25
> **tomski said:**
> nope that one dont work :(

for debug i get this ouput:
```

$conkyDeluge -SH -s 192.168.1.1 -v
*** INITIAL OPTIONS:
    server: 192.168.1.1
    port: 58846
    showsummary: True
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None
^CINFO: Proceeding with torrent data interpretation...
INFO: Preparing templates...
ERROR: writeOutput:Unexpected error:DelugeInfo instance has no attribute 'torrents_status'

```

i also tried:
conkyDeluge -server=192.168.1.1 -v
conkyDeluge -SH -s user:pass@192.168.1.1 -v
conkyDeluge -s user:pass@192.168.1.1 -v

all give the same output as above

What happens if you run it locally on the server? Just want to know whether is works locally, if it does then remote access is the problem...

This newer script worked for me locally when I wrote it, maybe things have changed with the deluge code though?

---

### Post by andrewabc on 2010-02-04
> **kaivalagi said:**
> Currently there is a script attached a few posts back which SHOULD work for v1.2.?+, the script in the repo is for v1.1.9

If you are running v.1.2 of deluge then I suggest installing from the repo and overwriting the previously attached .py file over the top...I think I explained it in the post with the attachment...

I don't run Deluge anymore so I am not sure how long it might be before I get around to fixing any issues, Deluge keep changing the way their app works :(

Edit: The post I was referring to is here: [http://ubuntuforums.org/showpost.php?p=8218486&postcount=175](http://ubuntuforums.org/showpost.php?p=8218486&postcount=175)

That file in post got output to conky for me. Thanks. Now to tweak the settings so I only see currently uploading files.

Deluge 1.2.0

---

### Post by kaivalagi on 2010-02-04
> **andrewabc said:**
> That file in post got output to conky for me. Thanks. Now to tweak the settings so I only see currently uploading files.

Deluge 1.2.0

That's great, thanks for letting me and others know

Once you have it working how you want, could you post the conkyrc and template files (without username/password info) for it?

---

### Post by andrewabc on 2010-02-04
I never input user/password into anything.

Although currently I am running deluged daemon (along with the gtkui to see what stuff is doing while testing). New to the daemon today, and havn't messed with conky scripts in a year so I'm still trying to figure out how it all works.

I just want a summary (got that with default conkydelugesummary.template) and only show torrents that are currently uploading data (not all seeding torrents as they can't all fit into screen, only got room for 2 or 3).

Reason for me doing all this with conky/daemon is that when normal deluge gtkui is open xorg starts using 50% cpu and slows stuff down.
The delugeconsole is not very friendly for me, and webui uses lots of cpu as well. I'll open delugegtk when adding torrent or changing state/options, but for casual stuff I only want to see what torrents are currently uploading data and summary with conky.

---

### Post by kaivalagi on 2010-02-04
> **andrewabc said:**
> I just want a summary (got that with default conkydelugesummary.template) and only show torrents that are currently uploading data (not all seeding torrents as they can't all fit into screen, only got room for 2 or 3).

I suggest one template for a summary, called by one execpi, and another template for a detailed list, called by another execpi. You can use the -l/--limit option to restrict the detailed list to 2/3, and I guess if you sort by "upload" you should see your seeds first.

I used Deluge in the past as a daemon but now use transmission as a daemon, it provides a web ui for all my needs which I'm happy with right now. I don't even have a transmission conky script either. I have also run rtorrent before now too, you can get a web frontend for it called "rtgui" which runs out of a web server rather than runs it's own, so you can integrate it into an existing website...but it's a bit fiddly with all the xmlrpc setup.

Any more questions just post :)

---

### Post by andrewabc on 2010-02-04
I'm getting the hang of it, although I have to figure out why my conky file (which includes all my computer info) is only allowing a certain height. I don't have any restrictions in place that I know of. It seems more like the template being inserted into my conky file is limiting itself and cutting off. I think I had this problem before and had to create another .conkyrc file since it can only hold so much info (run two instances of conky)?

At bottom of what is showing on conky desktop where the word Seeding should be it is cut off at 'S' below file name

Oddly I removed my computer info from conkyrc and it is still cutting off info (at similar place) even though it should have lots of room.

How do I sort by upload? Is that a command to input into conkyrc, or in template, or I have to sort in deluge program? In deluge program I sort by date added.

Example:
in my conkyrc file, I just have related to deluge:
> ${color4}Template Output:
${color1}${execpi 5 conkyDeluge --showsummary}
Here is screenshot:
[http://img193.imageshack.us/img193/5968/delugeconky.png](http://img193.imageshack.us/img193/5968/delugeconky.png)
Not sure why it says I have 32 queued, as I don't have any, I just have some paused that have finished downloading. Blacked out stuff is filenames
Shouldn't summary only show deluge summary and not 2 individual filenames? I'm guessing cut off after second filename?

Here is my conky file with above example. Only bottom two lines relate to deluge, rest is computer info.
```
background yes
use_xft yes
xftfont DejaVu Sans:size=10
xftalpha 1.0
update_interval 1.0
total_run_times 0
double_buffer yes
minimum_size 300 0
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
stippled_borders 8
border_margin 4
border_width 1

default_color white
default_shade_color black
default_outline_color white

own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

alignment top_right
gap_x 10
gap_y 28

no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer right

TEXT
Fan: ${color #FFA812}$acpifan    ${color #000000}Temp: ${color #FFA812}$acpitemp °C
${color #000000}$sysname $kernel $alignr Uptime:${color #FFA812} ${color #000000}$uptime_short 
CPU1: ${cpu cpu1}% ${cpubar 5}
${cpugraph cpu1 25 3D59AB FFA812}
CPU2: ${cpu cpu2}% ${cpubar 5}
${cpugraph cpu2 25 3D59AB FFA812}
MEM $alignc $mem / $memmax $alignr $memperc%
$membar
SWP: $alignc $swap / $swapmax $alignr $swapperc% 
$swapbar
${downspeedgraph eth0 35,145 FF9933 33FF99} ${alignr}${upspeedgraph eth0 35,145 FF9933 CC3300} 
 ${voffset -45}Down: ${downspeedf eth0}Kbps${alignr}Up: ${upspeedf eth0}Kbps
 Down: ${totaldown eth0} ${alignr}Up: ${totalup eth0}
${hr 1}
/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}
/data $alignc ${fs_used /media/data} / ${fs_size /media/data} $alignr ${fs_free_perc /media/data}%
${fs_bar /media/data}
${color #FFFFFF}Top Processes${hr 2}
       $alignr CPU%  MEM%
${top name 1} $alignr${top cpu 1}    ${top mem 1}
${color #FFFFFF}${top name 2} $alignr${top cpu 2}    ${top mem 2}
${top name 3} $alignr${top cpu 3}    ${top mem 3}
${top name 4} $alignr${top cpu 4}    ${top mem 4}
${hr 2}

${color4}Template Output:
${color1}${execpi 5 conkyDeluge --showsummary}
```

If I put in
> ${color4}Template Output:
${color1}${execpi 5 conkyDeluge --showsummary --summarytemplate=/usr/share/conkydeluge/example/conkyDelugeSummary.template}
${color1}${execpi 5 conkyDeluge --torrenttemplate=/usr/share/conkydeluge/example/conkyDeluge.template}

${color4}Standard Output:
${voffset 5}${color1}${font}${execi 5 conkyDeluge --showsummary}
${voffset 5}${color1}${font}${execi 5 conkyDeluge}
in my conkyrc file I end up with (I cropped out top part of conky)
[http://img13.imageshack.us/img13/9935/conkydeluge1.png](http://img13.imageshack.us/img13/9935/conkydeluge1.png)
Hm, conky updated and there was also an 'S' at bottom below last filename. So something is getting cut off. If I remove my computer info it is still cut off at same point.
I'm also getting an error with conky:
> Original exception was:
close failed in file object destructor:
Error in sys.excepthook:
keeps repeating itself every time conky refreshes.
I'm not sure how it can be an overloaded conky when because if I remove my computer info/variables, it is cut off at exact same spot, and I would think others would have same problem (making your default templates not work if it auto cuts off after 15 lines or so)

---

### Post by kaivalagi on 2010-02-04
> **andrewabc said:**
> Hm, conky updated and there was also an 'S' at bottom below last filename. So something is getting cut off. If I remove my computer info it is still cut off at same point.


Looks like you're making good progress

The truncation of output is normally because the conky text buffer is too small, it can be modified using an entry above "TEXT" in your conkyrc like this:

```
text_buffer_size 1024
```

Keep upping the value until you see everything, 1024 might well be enough. The default without a setting is 128 bytes I think (i.e. 128 chars per exec)

Hope that helps

---

### Post by andrewabc on 2010-02-04
> **kaivalagi said:**
> Looks like you're making good progress

The truncation of output is normally because the conky text buffer is too small, it can be modified using an entry above "TEXT" in your conkyrc like this:

```
text_buffer_size 1024
```

Keep upping the value until you see everything, 1024 might well be enough. The default without a setting is 128 bytes I think (i.e. 128 chars per exec)

Hope that helps

Thanks that worked.

And I've now figured out how to input the --commands properly into my conkyrc. Got it sorted by upload and limited to 4 torrents showing and it works!
Everything appears to be working now. :)

```
${color4}Standard Output:
${voffset 5}${color1}${font}${execi 5 conkyDeluge --showsummary --activeonly --limit=4 --sortby=upload}
```
Do I need --activeonly command if I am limiting it to only show 4, and have sorted by upload? I presume redundant?

---

### Post by kaivalagi on 2010-02-04
> **andrewabc said:**
> Thanks that worked.

And I've now figured out how to input the --commands properly into my conkyrc. Got it sorted by upload and limited to 4 torrents showing and it works!
Everything appears to be working now. :)

```
${color4}Standard Output:
${voffset 5}${color1}${font}${execi 5 conkyDeluge --showsummary --activeonly --limit=4 --sortby=upload}
```
Do I need --activeonly command if I am limiting it to only show 4, and have sorted by upload? I presume redundant?

Congrats :popcorn:

The --activeonly option hides inactive torrents, seeds or otherwise. Using it would mean if all there was were say 2 seeds and 2 paused inactive torrents, you would see only the 2 seeds, without the option you would see all 4 in the list. As you are also sorting by "upload" you would see the 2 seeds above the 2 inactive torrents.

Your call to use it or not...

Give us a screenshot when you're done too!

---

### Post by andrewabc on 2010-02-04
Currently using
```
${color1}${execpi 5 conkyDeluge --showsummary --limit=4 --sortby=upload --activeonly --summarytemplate=/usr/share/conkydeluge/example/conkyDelugeSummary.template --torrenttemplate=/usr/share/conkydeluge/example/conkyDeluge.template}
```
I havn't edited the templates yet, and disabled colors to white for now (changing background).

Question:
How do I put a space between summary and where it starts listing the torrents? There is no space even when I only use --summary command

[http://img692.imageshack.us/img692/1605/conkydeluge2.png](http://img692.imageshack.us/img692/1605/conkydeluge2.png)

---

### Post by kaivalagi on 2010-02-04
> **andrewabc said:**
> Currently using
```
${color1}${execpi 5 conkyDeluge --showsummary --limit=4 --sortby=upload --activeonly --summarytemplate=/usr/share/conkydeluge/example/conkyDelugeSummary.template --torrenttemplate=/usr/share/conkydeluge/example/conkyDeluge.template}
```
I havn't edited the templates yet, and disabled colors to white for now (changing background).

Question:
How do I put a space between summary and where it starts listing the torrents? There is no space even when I only use --summary command

[http://img692.imageshack.us/img692/1605/conkydeluge2.png](http://img692.imageshack.us/img692/1605/conkydeluge2.png)

Looks like you need to get rid of a final carriage return in the template, delete back to have the cursor on the end of the last line of text and save it...this applies to the detail template as it repeats for each torrent.

Hope that helps

---

### Post by andrewabc on 2010-02-04
> **kaivalagi said:**
> Looks like you need to get rid of a final carriage return in the template, delete back to have the cursor on the end of the last line of text and save it...this applies to the detail template as it repeats for each torrent.

Hope that helps
```
Hmm. It was conkyDeluge.template that had empty last line. I deleted it no difference (I would think it is the reason for spaces between each torrent listed? yet after deleting it still spaces between each torrent).

conkyDelugeSummary.template had no empty last line so I added one and it didn't do anything.

Hmm, ok adding lots of empty lines to bottom of both made no difference so I don't see how that works.

Do I need to edit something in conkyDeluge.py ?
```

Old message before figuring out answer somewhat. If I enter blank line at top of conkyDeluge.template it gives me the space, but it also adds another space between each torrent (two spaces between torrents which I don't want).

Adding spaces to top of conkydelugesummary only adds spaces between my computer info and torrent stuff.
I have entered a '.' on blank line at end of conkydelugesummary and it gives me desired space although there is a . there, but that's fine for me.

I had to get rid of --activeonly because the summary stats would constantly be changing every second as peers tried connecting to different torrents (it would affect total torrents and total space used).

---

### Post by kaivalagi on 2010-02-05
> **andrewabc said:**
> ```
Hmm. It was conkyDeluge.template that had empty last line. I deleted it no difference (I would think it is the reason for spaces between each torrent listed? yet after deleting it still spaces between each torrent).

conkyDelugeSummary.template had no empty last line so I added one and it didn't do anything.

Hmm, ok adding lots of empty lines to bottom of both made no difference so I don't see how that works.

Do I need to edit something in conkyDeluge.py ?
```

Old message before figuring out answer somewhat. If I enter blank line at top of conkyDeluge.template it gives me the space, but it also adds another space between each torrent (two spaces between torrents which I don't want).

Adding spaces to top of conkydelugesummary only adds spaces between my computer info and torrent stuff.
I have entered a '.' on blank line at end of conkydelugesummary and it gives me desired space although there is a . there, but that's fine for me.

I had to get rid of --activeonly because the summary stats would constantly be changing every second as peers tried connecting to different torrents (it would affect total torrents and total space used).

Adding spaces at the top will just push things down, spaces at the bottom are removed (I had thought all of them) so if no space top and bottom the output would be "tight".

Maybe I am getting in a muddle with another script but I thought that I had come across this issue and fixed it in conkyDeluge so that no CRs are in the template mean no spaces between output detail.

I'll take a quick look...but I can't test anything here...

edit: A CR is added for output for each torrent within the getTorrentTemplateOutput function:

```
            # get rid of any excess crlf's and add just one
            output = output.rstrip(" \n")
            output = output + "\n"
```

If these 2 lines are removed in theory you will get no gaps. If you comment out these lines with preceding "#" in /usr/share/conkydeluge/conkyDeluge.py and let me know how it goes?

---

### Post by andrewabc on 2010-02-05
I want the gaps between each torrent. That's fine.

I wanted a gap between summary and torrent list.
I fixed it by just putting a "." at end of summary template which is easy enough to do. What you're suggesting sounds a bit more complicated.

I edited torrent template to put in ratio and seeds/peers :)

[http://img191.imageshack.us/img191/7786/conkydeluge3.png](http://img191.imageshack.us/img191/7786/conkydeluge3.png)

---

### Post by andrewabc on 2010-02-07
Is it normal that when I stop deluge/deluge daemon it freezes/crashes conky?

I at first noticed this when I restarted computer and conky didn't show up It was running with very small maybe 5x5 pixel at top left corner of where it normally is.

I "fixed" it by making sure deluge daemon was running before starting conky again.

---

### Post by kaivalagi on 2010-02-07
> **andrewabc said:**
> Is it normal that when I stop deluge/deluge daemon it freezes/crashes conky?

I at first noticed this when I restarted computer and conky didn't show up It was running with very small maybe 5x5 pixel at top left corner of where it normally is.

I "fixed" it by making sure deluge daemon was running before starting conky again.

I can't say I've noticed, but this script uses the API for 1.2.0 onwards which is very different from the old one and not tested too much. I have not used Deluge since fairly soon after version 1.2.0 was released so don't use this script now myself.

Can you setup logging and post the output? It may be an obvious fix...

---

### Post by andrewabc on 2010-02-10
How do I set up logging?
I started conky in console but when I shutdown deluge nothing new shows up in console for conky.

In gnome system monitor it says under "waiting channel" column *pipe_wait*

---

### Post by kaivalagi on 2010-02-10
> **andrewabc said:**
> How do I set up logging?
I started conky in console but when I shutdown deluge nothing new shows up in console for conky.

In gnome system monitor it says under "waiting channel" column *pipe_wait*

If running the script from within conky you cannot have verbose output from the script as it messes conky up, but there is a file logging option in the script which allows detailed output to a log when running within conky.

The option I am referring to is:

```
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.

```

It might not turn up anything but it's worth a crack

---

### Post by andrewabc on 2010-02-10
```
${color1}${execpi 5 conkyDeluge --errorlogfile=/home/andrew/conky/conky.txt --showsummary --limit=4 --sortby=upload --summarytemplate=/usr/share/conkydeluge/example/conkyDelugeSummary.template --torrenttemplate=/usr/share/conkydeluge/example/conkyDeluge.template}
```

I also tried just --errorlogfile=/home/andrew/conky/

I don't see anything.

---

### Post by kaivalagi on 2010-02-11
> **andrewabc said:**
> ```
${color1}${execpi 5 conkyDeluge --errorlogfile=/home/andrew/conky/conky.txt --showsummary --limit=4 --sortby=upload --summarytemplate=/usr/share/conkydeluge/example/conkyDelugeSummary.template --torrenttemplate=/usr/share/conkydeluge/example/conkyDeluge.template}
```

I also tried just --errorlogfile=/home/andrew/conky/

I don't see anything.

mmmm, the info log option would show something but that's no good if we want to see errors

Conky should never crash regardless of what a script does...

So neither the script or conky details anything...I'm at a loss

---

### Post by oppih on 2010-03-03
conkyDeluge
Traceback (most recent call last):
  File "/usr/share/conkydeluge/conkyDeluge.py", line 42, in <module>
    from deluge.common import ftime, fsize, fspeed
ImportError: No module named deluge.common


——————How to&#65311;

---

### Post by kaivalagi on 2010-03-03
> **oppih said:**
> conkyDeluge
Traceback (most recent call last):
  File "/usr/share/conkydeluge/conkyDeluge.py", line 42, in <module>
    from deluge.common import ftime, fsize, fspeed
ImportError: No module named deluge.common


&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;How to&#65311;

What version of Deluge, if new then you'll need the alternative script some way back in the posts. Deluge had it's API core totally replaced...I'll see if I can find links for the old relevant posts...

Edit: Relevant post with attachment here: [http://ubuntuforums.org/showpost.php?p=8218486&postcount=175](http://ubuntuforums.org/showpost.php?p=8218486&postcount=175)

---

### Post by oppih on 2010-03-03
I&#8216;ve just installed the DEB package in the post.Isn't the proper package?

---

### Post by kaivalagi on 2010-03-04
> **oppih said:**
> I‘ve just installed the DEB package in the post.Isn't the proper package?

I mean what version of Deluge not the script, the script in the deb or via the ppa is okay with Deluge < 1.2. If 1.2+ then you need to look at that linked post I provided.

---

### Post by oppih on 2010-03-04
I'm sorry...
I didn't understand you properly.

I have not installed Deluge.
Sorry again.

---

### Post by kaivalagi on 2010-03-04
> **oppih said:**
> I'm sorry...
I didn't understand you properly.

I have not installed Deluge.
Sorry again.

:lolflag::confused: You need deluge to use this script, this script displays deluge information as per the description in the first post of this thread. Deluge has to be installed separately.

---

### Post by kaivalagi on 2010-03-05
I will shortly be creating a new branch of this script to maintain compatibility with Deluge versions < 1.2. The new code branch and package name will be "conkydeluge-pre120"

Once conkydeluge-pre120 is in place I'll update the current branch and package to work with Deluge 1.2+ as is default in Lucid and available via the Deluge PPA and site.

I'll post an update once this has taken place. When this takes place if you use < 1.2 of Deluge then this update will break your conky initially. I will be fixable easily however by installing the conkydeluge-pre120 package instead.

---

### Post by kaivalagi on 2010-03-06
[COLOR="Green"]**[SIZE="4"]UPDATE[/SIZE]**[/COLOR]

We now have 2 alternative packages to choice from. **Special thanks to mobilediesel **who prepared, uploaded and published the new packages off the back of my code changes in record time :)

The new packages are as follows:
[LIST]
[*]**conkydeluge** (script version 2.13) - the latest version of the script, to be used with Deluge v.1.2.0 onwards. Changes are here: [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkydeluge_2.13_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkydeluge_2.13_source.changes)
[*]**conkydeluge-pre120** (script version 2.12) - the old version of the script, to be used with Deluge 1.9 or lower. Changes are here: [https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkydeluge-pre120_2.12_source.changes](https://launchpad.net/~conkyhardcore/+archive/ppa/+files/conkydeluge-pre120_2.12_source.changes)
[/LIST]

Please update your package install appropriately to suit your version of Deluge. The 2 packages can't be installed together as they ultimately result in the same file names being installed.

I've updated the first post instructions also.

---

### Post by snkiz on 2010-03-18
hey K, any luck with remote server options? I still getting this:
```

ERROR: writeOutput:Unexpected error:DelugeInfo instance has no attribute 'torrents_status'

```

---

### Post by kaivalagi on 2010-03-18
> **snkiz said:**
> hey K, any luck with remote server options? I still getting this:
```

ERROR: writeOutput:Unexpected error:DelugeInfo instance has no attribute 'torrents_status'

```

Not using the script at all as I don't use deluge

The error above really does look like the use of the incompatible script and deluge version. Are you sure you are using the right version of the script for the remote servers deluge version?

---

### Post by snkiz on 2010-03-19
pretty sure
```

ckadmin@ckubuntu-serv:~$ deluge --version
1.2.1

```
and script is
```

snkiz@ckubuntu:~$ conkyDeluge --version
/usr/lib/pymodules/python2.6/deluge/common.py:65: UserWarning: Module deluge was already imported from /usr/lib/pymodules/python2.6/deluge/__init__.py, but /usr/lib/pymodules/python2.6 is being added to sys.path
  import pkg_resources
conkyDeluge v.2.13

```
port scan says its open on the right port and I can connect with gtk. Sorry to hear your not using deluge anymore, your script is the only reason I started using it :)
EDIT:
Its' not working localy either same error. Plus deluge is no longer obeying my ratio settings. I'm going to purge deluge and reinstall, see if that helps.

---

### Post by kaivalagi on 2010-03-20
> **snkiz said:**
> pretty sure
```

ckadmin@ckubuntu-serv:~$ deluge --version
1.2.1

```
and script is
```

snkiz@ckubuntu:~$ conkyDeluge --version
/usr/lib/pymodules/python2.6/deluge/common.py:65: UserWarning: Module deluge was already imported from /usr/lib/pymodules/python2.6/deluge/__init__.py, but /usr/lib/pymodules/python2.6 is being added to sys.path
  import pkg_resources
conkyDeluge v.2.13

```
port scan says its open on the right port and I can connect with gtk. Sorry to hear your not using deluge anymore, your script is the only reason I started using it :)
EDIT:
Its' not working localy either same error. Plus deluge is no longer obeying my ratio settings. I'm going to purge deluge and reinstall, see if that helps.

I have installed Deluge 1.2.1 just to see, bear with me

edit: I give up with Deluge to be honest, they keep changing the way to talk to it and I have no time or energy to keep it working right now...I just tested it and it just sits there waiting for something, last time I ran it for v.1.2.0 it worked fine...](*,)

---

### Post by snkiz on 2010-03-21
thanks K I'm getting that same fustration. I purged all the deluge files and reinstalled, got rid of the python error, but did not fix conky. Although I think I found the problem. I don't think the login credintials are being passed properly to deluge. When I run remote to deluge the script sits, when I run local but as a diffrent user it sits. As of right now it seems to be only working if you connect localy with the user who owns the daemon. That being said, the new version of deluge (1.2.1) is a huge let down in performance and features. Got any recomendations?

---

### Post by kaivalagi on 2010-03-21
> **snkiz said:**
> thanks K I'm getting that same fustration. I purged all the deluge files and reinstalled, got rid of the python error, but did not fix conky. Although I think I found the problem. I don't think the login credintials are being passed properly to deluge. When I run remote to deluge the script sits, when I run local but as a diffrent user it sits. As of right now it seems to be only working if you connect localy with the user who owns the daemon. That being said, the new version of deluge (1.2.1) is a huge let down in performance and features. Got any recomendations?

They just released 1.2.2

Code with this much turn around much have lots of issues.....I will not use Deluge again I don't think. I use transmission daemon now, if I do change I think I'll go back to good old rtorrent with a web ui and xml rpc (the way deluge used to bloody work for my script)

---

### Post by Cas07 on 2010-03-27
> **kaivalagi said:**
> They just released 1.2.2
Code with this much turn around much have lots of issues.....I will not use Deluge again I don't think.

I regularly use the deluge forums and have not seen any mention of this script, which seems very useful, and i find it odd that you have not posted a topic thus meaning the developers will have no knowledge of your issues.

The fact they have released updated versions once a month is not exactly huge code turnaround plus they are keeping up with newer version releases of libtorrent-rastabar.

[http://forum.deluge-torrent.org/index.php](http://forum.deluge-torrent.org/index.php)

---

### Post by kaivalagi on 2010-03-28
> **Caos said:**
> I regularly use the deluge forums and have not seen any mention of this script, which seems very useful, and i find it odd that you have not posted a topic thus meaning the developers will have no knowledge of your issues.

The fact they have released updated versions once a month is not exactly huge code turnaround plus they are keeping up with newer version releases of libtorrent-rastabar.

[http://forum.deluge-torrent.org/index.php](http://forum.deluge-torrent.org/index.php)

The issue for me is that the core of the comms code keeping changing, I will wait a month before doing any more as every time I adjust for it, it changes again... not for any other reason than time required on my part to keep up. I expect changes to the Deluge code to take place regulrly, I just wish the code that affects this script was stable after so much time...

I have posted questions before now in the #deluge irc chat room and atleast one of the developers knows of this script as he has posted on this thread before now highlighting some useful changes I could make.

I look after a fair few scripts for various apps in Linux so posting on the Deluge forums for this one alone doesn't enter the picture....now if someone wants to assist development and get involved with the community feel free, but I don't have the time for it.

Everyone seems finds my scripts useful, but no-one has yet to get involved in the script code itself, bar the forecast script a long time ago...it's all take take take it seems, as is the expectation for a lot in the open source community IMHO.

This script for example has issues, but no one is willing to try and figure out the issues and post patches etc, python is not hard :)

I have even setup a community ppa (the one now used for all the packages) with the option to move all the source code over to it IF others where to get involved more heavily...maybe I need to announce stopping support and see what happens then?

Bottom line is I don't have the time I once had for all of this so it would be nice if others were to help fix problems rather than just highlight problems...

I am generalizing here and I know you are only trying to support the success of this script going forwards so please don't take this as an attack on you personally, you've just triggered something I have had a problem with for a long time...

---

### Post by snkiz on 2010-03-28
> **kaivalagi said:**
> The issue for me is that the core of the comms code keeping changing, I will wait a month before doing any more as every time I adjust for it, it changes again... not for any other reason than time required on my part to keep up. I expect changes to the Deluge code to take place regulrly, I just wish the code that affects this script was stable after so much time...

I have posted questions before now in the #deluge irc chat room and atleast one of the developers knows of this script as he has posted on this thread before now highlighting some useful changes I could make.

I look after a fair few scripts for various apps in Linux so posting on the Deluge forums for this one alone doesn't enter the picture....now if someone wants to assist development and get involved with the community feel free, but I don't have the time for it.

Everyone seems finds my scripts useful, but no-one has yet to get involved in the script code itself, bar the forecast script a long time ago...it's all take take take it seems, as is the expectation for a lot in the open source community IMHO.

This script for example has issues, but no one is willing to try and figure out the issues and post patches etc, python is not hard :)

I have even setup a community ppa (the one now used for all the packages) with the option to move all the source code over to it IF others where to get involved more heavily...maybe I need to announce stopping support and see what happens then?

Bottom line is I don't have the time I once had for all of this so it would be nice if others were to help fix problems rather than just highlight problems...

I am generalizing here and I know you are only trying to support the success of this script going forwards so please don't take this as an attack on you personally, you've just triggered something I have had a problem with for a long time...

I see your frustration K, and I get it. But What may not be hard for you is daunting to others. I've tried K, really. Read every python script I have and a bunch of other docs. and I can't wrap my head around it. Couldn't even find decent docs deluge's new rpc. I hope you get the help you need and you have my sincerest gratitude.

---

### Post by kaivalagi on 2010-03-28
> **snkiz said:**
> I see your frustration K, and I get it. But What may not be hard for you is daunting to others. I've tried K, really. Read every python script I have and a bunch of other docs. and I can't wrap my head around it. Couldn't even find decent docs deluge's new rpc. I hope you get the help you need and you have my sincerest gratitude.

Sorry, I was ranting back there...

I do take my years of experience with different languages for granted :)

As for documentation of the new Deluge RPC stuff it is awful...from memory I think a search for "python twisted reactor" gives some "alright" documentation. The best way to figure out what to search for is first looking at the core code of Deluge to see what it is using, then look at it from the outside...

As with a lot of OSS out there, there is limited documentation, and reading code is the only real way to get a better understanding...not great for a newbie or experienced developer either...

---

### Post by snkiz on 2010-04-01
I don't know if your maintaining the scripts anymore k since they were moved to conky hardcore's ppa. But over in the CH forums someone patched our little problem [http://linux-hardcore.com/index.php?topic=2719.0]("http://linux-hardcore.com/index.php?topic=2719.0") Either way its good to know your not alone yes??

---

### Post by kaivalagi on 2010-04-01
> **snkiz said:**
> I don't know if your maintaining the scripts anymore k since they were moved to conky hardcore's ppa. But over in the CH forums someone patched our little problem [http://linux-hardcore.com/index.php?topic=2719.0]("http://linux-hardcore.com/index.php?topic=2719.0") Either way its good to know your not alone yes??

They should post the fix here...but I am grateful none the less.

I'll post a changed .py file here soon so you can test it before I arrange for a package to be released :) I'll try and get a fix out proper before the end of the looooong weekend :)

Cheers

---

### Post by kaivalagi on 2010-04-01
> **snkiz said:**
> I don't know if your maintaining the scripts anymore k since they were moved to conky hardcore's ppa. But over in the CH forums someone patched our little problem [http://linux-hardcore.com/index.php?topic=2719.0]("http://linux-hardcore.com/index.php?topic=2719.0") Either way its good to know your not alone yes??

They should post the fix here...but I am grateful none the less.

I'll post a changed .py file here soon so you can test it before I arrange for a package to be released :) I'll try and get a fix out proper before the end of the looooong weekend :)

Cheers

edit: previously username and password could be set with the server name from what I remember, I could be wrong...i.e. --servername="username:password@serveraddress"

---

### Post by snkiz on 2010-04-01
working on it now I knew about the old way to log in guess I'm glad the other guy didn't :)

EDIT:
I got it working on the command line but still no love through conky
EDIT2:
Bingo! forgot to remove my old credentials ](*,)

---

### Post by kaivalagi on 2010-04-01
> **snkiz said:**
> working on it now I knew about the old way to log in guess I'm glad the other guy didn't :)

Here's the new py file, although it still doesn't seem to work for me...I have installed from extra (Arch) the version is 1.2.3...

edit: I'm just doing a big upgrade on Arch so I might be some time before I can debug...

---

### Post by snkiz on 2010-04-01
> **kaivalagi said:**
> Here's the new py file, although it still doesn't seem to work for me...I have installed from extra (Arch) the version is 1.2.3...

edit: I'm just doing a big upgrade on Arch so I might be some time before I can debug...

yours works too but I'm on 1.2.2. God I hope the deluge guys didn't mess with login again

---

### Post by kaivalagi on 2010-04-01
.

---

### Post by kaivalagi on 2010-04-01
> **snkiz said:**
> yours works too but I'm on 1.2.2. God I hope the deluge guys didn't mess with login again

What's the betting...

It might be something else related to "twister" though...I really don't like the implementation of this and the fact deluge is using it...but not my call...

---

### Post by snkiz on 2010-04-01
> **kaivalagi said:**
> What's the betting...

It might be something else related to "twister" though...I really don't like the implementation of this and the fact deluge is using it...but not my call...

lol maybe there is something to be said for poking your nose in the deluge forums now and again, at least they'd know the chaos it causes when they do this stuff. could be worse, could be like facebook. they don't tell anyone when they change the api

Edit:
from the [wiki]("http://dev.deluge-torrent.org/wiki/UserGuide/Authentication"):
> Note: Currently, authentication levels aren't used for much but will be in the future.
if they haven't changed it yet they will be.

---

### Post by kaivalagi on 2010-04-02
You seem to forget, I don't use Deluge...why I even put this much time into these problems is beyond me...

I think I'll be leaving it to the nice members at linux hardcore from now on.

---

### Post by merlin_ie on 2010-06-21
> **kaivalagi said:**
> You seem to forget, I don't use Deluge...why I even put this much time into these problems is beyond me...

I think I'll be leaving it to the nice members at linux hardcore from now on.

Kaivalagi, i hate to ask this as i'm not sure if you're giving support for this anymore, but i followed the install process to the letter, i'm sure i have the proper script installed, but at the end of it all, when i go to use conky, it just wont work. it's like it hangs. even if use the default conkyrc. do you think this is a common fault due to the way Deluge was changed or has anyone else had this problem. any help is GREATLY appreciated

---

### Post by kaivalagi on 2010-06-21
I've basically given up on this script until deluge seems more stable and is not changing forever more...they keep messing with the means to retrieve data from an external process which I don't have the time to follow.

This is open source though so if any one else wishes to contribute any fixes I'll happily get them released...

I am out of motivation basically for this script, I may look at it again when I can be bothered

---

### Post by merlin_ie on 2010-06-21
okies. thats fair, i totally understand what you mean. thanks for time anyways and keep up the good work :)

---

### Post by shahin on 2010-07-02
What does Conky do and how please?

---

### Post by dopple on 2010-07-03
Conky is a system monitor that you can configure to show pretty much anything going on on your laptop. [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by kerml on 2010-07-16
I receive always the same error about the 

deluge.ui.client import sclient

I use slackware 13.1 64 bits. Any tips?

I have to make some thing on install of deluge to use that?

My deluge version is the 1.2.3

---

### Post by kaivalagi on 2010-07-16
> **kerml said:**
> I receive always the same error about the 

deluge.ui.client import sclient

I use slackware 13.1 64 bits. Any tips?

I have to make some thing on install of deluge to use that?

My deluge version is the 1.2.3

It will be because the dbus api provided by deluge has changed yet again, read a few posts back to understand my frustration...
I might release a working version of this script by the end of the year...honestlyy, I've pretty much given up on this script because of the number of changes happening and not enough time to work on it every 5 minutes when it is needed.

I am not using Deluge either which makes it even more difficult to keep up with things, I am not testing everyday I torrent...I'm using the Transmission daemon and webpage these days...

---

### Post by goadale on 2010-08-02
I'm having a bit of a problem. 
I added 

```
${execi 5 conkyDeluge --showsummary}
${execi 5 conkyDeluge}
```

to my .conkyrc file and then ran conky from terminal. There are no error messages (nor any other output) in terminal, however conky is not displayed anywhere on my screen. This is the only thing I have changed since it last worked. 
I have installed conkyDeluge according to method #1 in the first post.

I am running Ubuntu 10.04 and I've made sure that everything is up to date.
Deluge is ver. 1.2.3
Libtorrent is ver. 0.14.10.0

Here is my .conkyrc file:

```
# Tipo de letra por defecto.
use_xft yes
xftfont Aller:size=8
override_utf8_locale yes

# Configuración de rendimiento.
update_interval 1
total_run_times 0
double_buffer yes
no_buffers yes
net_avg_samples 2


# Ejecutarlo en su propia ventana en lugar de usar el escritorio.
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Borde.
draw_borders no
border_margin 1

# Color por defecto del fondo de la ventana
own_window_colour 000000

# Color por defecto.
default_color FCFCFC
#default_color EFEEED

# Dibuja marco.
draw_shades no


# Dimensiones mínimas.
minimum_size 768 0

# Posición de Conky.
alignment bottom_left
gap_x 0
gap_y 50

# Texto
TEXT
${goto 15}Gmail  ${execi 30 ~/conky/./gmail_conky.script}
${voffset 20}${font Aller:style=Bold:size=9}${goto 15}Network:${font}${color}${goto 100}D:${downspeed eth0}${goto 160}U:${upspeed eth0}
${voffset 6}${goto 15}Up: ${goto 100}${upspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Aller:style=Bold:size=8}  ${upspeed eth}${font}
${goto 15}Total Up: ${goto 100}${totalup eth0}
${goto 15}Down: ${goto 100}${downspeedgraph eth0 10,100 B7B2AD B7B2AD}${font Aller:style=Bold:size=8}  ${downspeed eth0}${font}
${goto 15}Total Down: ${goto 100}${totaldown eth0}
${goto 15}Local Ip: ${goto 100}${addr eth0}
${goto 15}Public Ip: ${goto 100}${execi 10800 wget http://www.whatismyip.com/automation/n09230945.asp -O - -o /dev/null}


${goto 15}Disk (/):${goto 100}${fs_used /} / ${fs_size /}
${goto 100}${fs_bar 10,100 /}
${voffset 20}${font Aller:style=Bold:size=9}${goto 15}System:${font}${color}${goto 100}${uptime}
${voffset 6}${goto 15}CPU-1: ${goto 100}${cpubar cpu0 10,100}${font Aller:style=Bold:size=8}  ${cpu cpu0}%${font}
${goto 15}CPU-2: ${goto 100}${cpubar cpu1 10,100}${font Aller:style=Bold:size=8}  ${cpu cpu1}%${font}
${goto 15}CPU-3: ${goto 100}${cpubar cpu2 10,100}${font Aller:style=Bold:size=8}  ${cpu cpu2}%${font}
${goto 15}CPU-4: ${goto 100}${cpubar cpu3 10,100}${font Aller:style=Bold:size=8}  ${cpu cpu3}%${font}

${goto 15}RAM: ${goto 100}${membar 10,100}${font Aller:style=Bold:size=8}  $memperc%${font}
${goto 15}SWAP:${goto 100}${swapbar 10,100}${font Aller:style=Bold:size=8}  $swapperc%${font}

${execi 5 conkyDeluge --showsummary}
${execi 5 conkyDeluge}
```

---

### Post by theLegend on 2010-08-07
It appears that because Deluge is constantly changing this script is no longer working and as Mr K pointed out, its too time consuming to keep changing this script to match....hopefully deluge developers will stop changing their API and Mr K can release a stable version.......

****************************************************************************

---

### Post by kaivalagi on 2010-08-17
Just so you all know unless Deluge comes through with decent client code examples and documentation other than source code this is going no where!

I have tried and failed with version 1.2.x connections (twisted reactor doesn't want to accept connections no matter what I try) and just tried 1.3.x too as the api has changed with that (the old one obviously wasn't up to it, now using RPC) but this new api is far from friendly and the docs suck (it is RC after all)

So.....don't bother asking anymore unless you can provide code for a working connection into deluge for retrieving torrent info. If you can then I can plug it in and away we go, but I am not going to hold my breath...

---

### Post by lilone972 on 2010-09-14
hi everybody !
I've a problem with conkyDeluge...
When I put this command on the terminal and I have no reply
```
marvin@DeathstarUbuntu:~$ conkyDeluge -l 0


```I've try different other command of conkyDeluge and the result is the same. No reply and the terminal locked...
Any solution?

---

### Post by lilone972 on 2010-09-14
excuse for this reply, I just wanted to edit my older post

---

### Post by kaivalagi on 2010-09-14
Read my above posts, not supported anymore...not worth the hassle I'm afraid...

---

### Post by lilone972 on 2010-09-14
Sorry I didn't read your post... I'm French and I've little problems with English lol
Do you know an other solution to put deluge's infos in my conky?
Or there is an other bittorent client with we can to do that? I had try with Transmission but there is a problem of authentification and I don't know how to fix it...

---

### Post by kaivalagi on 2010-09-14
> **lilone972 said:**
> Sorry I didn't read your post... I'm French and I've little problems with English lol
Do you know an other solution to put deluge's infos in my conky?
Or there is an other bittorent client with we can to do that? I had try with Transmission but there is a problem of authentification and I don't know how to fix it...

No problems, I am sure I have more problems with french :)

I did use rtorrent for a while and have attached the python script I used for that (no idea if it still works though). Also rtorrent was a little awkward to setup, needing a web server and RPC configuring to allow a web ui for it...without that it is ncurses based (terminal stuff)

I use transmission but don't output anything through conky...I want a fairly minimal desktop these days

---

### Post by WiseGuy1020 on 2010-09-19
The worst part is that Deluge's very own website still links to this thread.

[http://dev.deluge-torrent.org/wiki/Plugins]("http://dev.deluge-torrent.org/wiki/Plugins")

---

### Post by kaivalagi on 2010-09-23
> **WiseGuy1020 said:**
> The worst part is that Deluge's very own website still links to this thread.

[http://dev.deluge-torrent.org/wiki/Plugins]("http://dev.deluge-torrent.org/wiki/Plugins")

Made me chuckle...

---

### Post by maniaq on 2010-10-05
this has probably already been said (haven't checked) but step 2 can be simplified to:

> sudo add-apt-repository ppa:conkyhardcore/ppa

(your version didn't actually work for me)

---

### Post by kaivalagi on 2010-10-07
> **maniaq said:**
> (your version didn't actually work for me)

Read above................

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by Icche Ghuri on 2011-04-29
I've installed conkydeluge via conkyhardcore ppa. I cannot make it work. I've also tried with the example conkyrc, and also failed. Here is the "conkyDeluge -v" output,

```
icche_ghuri@lucid-lynx:~$ conkyDeluge -v
*** INITIAL OPTIONS:
    server: 127.0.0.1
    port: 58846
    username: None
    password: None
    showsummary: False
    torrenttemplate: None
    summarytemplate: None
    activeonly: False
    limit: 0
    sortby: eta
    errorlogfile: None
    infologfile: None

```
At this line it just kept hung. And pressing Ctrl+C gives this
```
INFO: Proceeding with torrent data interpretation...
INFO: Preparing templates...
ERROR: writeOutput:Unexpected error:DelugeInfo instance has no attribute 'torrents_status'

icche_ghuri@lucid-lynx:~$
```

What should I do?

I'm using Deluge 1.2.2

---

### Post by kaivalagi on 2011-04-29
no longer supported.....read back through the posts of the last couple of pages if you want to know why...

---

### Post by Cas07 on 2011-07-07
> **Icche Ghuri said:**
> 
```
ERROR: writeOutput:Unexpected error:DelugeInfo instance has no attribute 'torrents_status'
```
What should I do?

I'm using Deluge 1.2.2

Basically this means you do not have **deluged** running for it to connect to, make sure that Classic Mode is disabled in Prefs.

The app hanging is a bug that I mentioned in this deluge [forum post]("http://forum.deluge-torrent.org/viewtopic.php?f=9&t=30825#p145625"). 

Also you should really be using the latest version, 1.3.2, that is in the [Deluge PPA]("https://launchpad.net/~deluge-team/+archive/ppa").

Edit:

I fixed the code for when the connection fails: [https://github.com/cas--/conkyDeluge](https://github.com/cas--/conkyDeluge)

---

