---
title: "How-to: Getting the funky Compiz Screensaver in Hardy"
date: 2008-08-14
forum: General Help
---

### Post by ZarathustraDK on 2008-08-14
**Disclaimer: This worked for me on Ubuntu 8.04 with Compiz-Fusion 0.7.6, I can't guarantee it'll work for you, and it's tough love if it hoses your system. I am by no means a compiling-expert so do comment if something is fishy (most of this how-to is made up by pressing the up-arrow in the console, backtracking what I did).**

First How-to here.

Yeah, you have probably seen it on youtube, that funky screensaver-function in Compiz-fusion that either spins the cube when idle, or fades the desktop to the skydome while hurling your open windows here and hither. It's pretty, and probably one of the most seamless screensaver-transitions out there. So how do you go about getting it? It's not in the standard Compiz install, so you have to compile it yourself. Fear not, it's not hard, so let's get going, copy-paste awaits :

**Note: Step 1 & 2 might be irrelevant for you, and the plugin might work with your current Compiz-fusion. I haven't tested which versions that work, all I know is that compiz-fusion 0.7.6 does, so feel free to try skipping step 1 & 2 if you'd like.**

1. Add the following launchpad-repositories to Synaptic :
```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb-src http://ppa.launchpad.net/compiz/ubuntu hardy main
```

2. Then you update your repositories and install the latest compiz-fusion (0.7.6 as of this writing). If you already have compiz installed you should receive an update-notifier about a new version of Compiz, making it extra easy.

3. Then you install the things needed to build and use the plugin :
```
sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
```

4. Then you download the source-files for the plugin:
```
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
```
It will land in ~/screensaver/ (a newly created directory in your home-partition)

5. cd to your ~/screensaver/-directory by writing this in a terminal:

```
cd screensaver
```

and once inside that directory write:

```
make && make install
```
...in order to compile and install the source-code for the screensaver (which you downloaded in step 4) using the tools that you installed in step 3.


The plugin is now installed and you can configure it in CCSM (CompizConfig Settings Manager, you installed it earlier in the howto, it's under System->Preferences).

6. Restart Compiz (if it's running, else just start compiz) and you're good to go. The Screensaver-plugin is located in the "Extras"-section of CCSM, you need to configure a key to toggle the screensaver (or just wait the amount of time specified in the settings, it's a screensaver after all)

**I get a strange compiling-error when using the git-repository-sources!**
Well, that stuff happens, I have no control over what they put/add to that repository, and sometimes those additions messes up the the whole thing. So, for your convenience I've tar'ed an older version of the plugin that works (it's the one I use) and attached it to this post (screensaver.tar.gz). Unpack the files and go from step 5 (using the directory you unpacked the files to of course, and also remember to install the stuff in step 3). Yeah, why didn't I write this at the top? Well, the other solution could work, and I presume people want the newest IF it works ;)

---

### Post by Si-Ddevil on 2008-08-14
:~$ git clone git://anongit.compiz-fusion.org/fusion/plugins/screensaver
Initialized empty Git repository in /home/si/screensaver/.git/
fatal: The remote end hung up unexpectedly
fetch-pack from 'git://anongit.compiz-fusion.org/fusion/plugins/screensaver' failed.

:(

---

### Post by ZarathustraDK on 2008-08-14
> **Si-Ddevil said:**
> :~$ git clone git://anongit.compiz-fusion.org/fusion/plugins/screensaver
Initialized empty Git repository in /home/si/screensaver/.git/
fatal: The remote end hung up unexpectedly
fetch-pack from 'git://anongit.compiz-fusion.org/fusion/plugins/screensaver' failed.

:(

Ah sorry it's :

```
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
```

I've corrected it now.

---

### Post by keefy777 on 2008-08-14
5. cd to ~/screensaver/ and run:
Code:

make && make install


Sorry i am a bit new to this can you explain it in more detail ie what does 5 mean and what do i have to type into terminal in order to do this

---

### Post by prshah on 2008-08-14
> **ZarathustraDK said:**
> So how do you go about getting it? It's not in the standard Compiz install,
2. Then you update your repositories and install the latest compiz-fusion (0.7.6 as of this writing). 

Wow, thanks, works great; small point though; I'm running 8.04.1, fully updated, and just compiling the plugin worked fine, without the need to update compiz, so the impatient can jump straight to the "git clone ..." part.

---

### Post by keefy777 on 2008-08-14
Ok how do i get this to install its there in home directory but i cant go any further

---

### Post by ZarathustraDK on 2008-08-14
> **keefy777 said:**
> Ok how do i get this to install its there in home directory but i cant go any further

I've edited the walkthrough a bit to make that clear. You need to open up a terminal and write "cd screensaver" (without the quotes) to get into your /home/(your name)/screensaver-directory. Then write "make && make install" (again without quotes) once inside that directory in the terminal.

---

### Post by keefy777 on 2008-08-14
Ok thanks for that something else that i know how to do now.
One thing though i cant seem to iniate the screensaver not even after the alloted time.
Any ideas.

---

### Post by ZarathustraDK on 2008-08-14
> **keefy777 said:**
> Ok thanks for that something else that i know how to do now.
One thing though i cant seem to iniate the screensaver not even after the alloted time.
Any ideas.

Hmm...that sounds strange.

Acouple of questions:

1. Which Compiz-fusion version are you using (I think it's a bit jerky with 0.7.4, at least that's what I've heard).

2. Did you remember to restart Compiz (as in kill every process with "compiz" in it in the system-monitor, then start it again)?

3. Did you configure an initiate-key in the screensaver-plugins tab in CCSM?

If it's not one of those then I'm pretty stumped for answers.

---

### Post by keefy777 on 2008-08-14
Your a star its working and looking cool Thanks very much.:KS:KS:KS:guitar:

---

### Post by Sam324 on 2008-08-15
This has worked so far.  How do I restart Compiz-Fusion without rebooting?  I guess I'll just reboot for now.

---

### Post by Sam324 on 2008-08-15
I followed all the instructions exactly, but the screensaver never launches upon command or after a period of time.  It just launches the default Ubuntu screensaver.  Is there any way to disable that?

---

### Post by ZarathustraDK on 2008-08-15
> **Sam324 said:**
> This has worked so far.  How do I restart Compiz-Fusion without rebooting?  I guess I'll just reboot for now.

Easiest way is to add the panel-application "System Monitor" to your panel. Then, whenever you want to shut down something, click the app, and kill whatever process you desire (in your case anything that has "compiz" in its name.

---

### Post by ZarathustraDK on 2008-08-15
> **Sam324 said:**
> I followed all the instructions exactly, but the screensaver never launches upon command or after a period of time.  It just launches the default Ubuntu screensaver.  Is there any way to disable that?

Did you remember restart compiz?

Your 'normal' screensaver has nothing to do with compiz' screensaver. You can disable it in System->Preferences->Screensaver, otherwise it might start up before the compiz-one and, well, make everything superfluous :)

---

### Post by raynevandunem on 2008-09-04
I ran into a snag when compiling:

```
owner@owner-laptop:~/screensaver$ make && make install
convert   : screensaver.xml.in -> build/screensaver.xml
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema    : build/screensaver.xml -> build/compiz-screensaver.schema
compiling : screensaver.cpp -> build/screensaver.loscreensaver.cpp: In function ‘void screenSaverSetXScreenSaver(CompDisplay*, int)’:
screensaver.cpp:223: error: cannot convert ‘const char*’ to ‘CompDisplay*’ for argument ‘1’ to ‘void compLogMessage(CompDisplay*, const char*, CompLogLevel, const char*, ...)’
screensaver.cpp: In function ‘int screenSaverInitDisplay(CompPlugin*, CompDisplay*)’:
screensaver.cpp:361: error: ‘screensaverSetInitiateKeyInitiate’ was not declared in this scope
screensaver.cpp:362: error: ‘screensaverSetInitiateButtonInitiate’ was not declared in this scope
screensaver.cpp:363: error: ‘screensaverSetInitiateEdgeInitiate’ was not declared in this scope
make: *** [build/screensaver.lo] Error 1
```

---

### Post by poodpood on 2008-09-04
me too, same error!!!

---

### Post by JECHO on 2008-09-04
Just so you guys know...

I have the cylinder plugin installed on my compiz and when i tried to compile the screensaver plugin it worked but had some glitches... i wouldnt recommend compiling if you use the cylinder.

---

### Post by ZarathustraDK on 2008-09-04
Hmm... I really don't know about those compiling-errors, I'm pretty green in this myself, and those error-messages doesn't light any bulbs in my head.

Perhaps it's because they added something broken to the repository, it's not an official repository so that's a possibility.

Try doing the "make && make install" on the screensaver source attached to this message. It's the ones I used to to make my screensaver work.

---

### Post by santiagoward2000 on 2008-09-04
Well, thanks for the tar. I've been having the same errors with the git files. :(

---

### Post by Brain-free on 2008-09-07
Yes, I can confirm that the tarball solves the problem. 

BTW, does anyone know a site - kinda like sourceforge - in which all these user-plugins are gathered? Because I've done a search in compiz forums but haven't found anything...

---

### Post by Brain-free on 2008-09-07
Sorry for the double post but I think it's useful. Not 2 hours after I asked, I stumbled upon the site in which the unsupported plugins of compiz are stored. It's [http://gitweb.compiz-fusion.org/]("http://gitweb.compiz-fusion.org/"). 

And since the plugins in it are not official, use it at your very own risk...

---

### Post by Shazaam on 2008-09-08
Installed and working great on Gutsy. Got this error during make but like I said it works...
```
make: *** No rule to make target `build/screensaver.lo', needed by `c-build-objs'.  Stop.
```
Causes this to happen...
Movement during raising and lowering of windows is a little stuttery now (best description I can think of) but managable. Also, it takes about 15-20 seconds longer to load the full desktop after login (background picture loads first- cairo-dock and desktop icons load later). Reverts back to normal if plugin disabled. Installed git version and your tar; same thing happens with both.
My pc:
Amd Athlon XP3200, 2gigs ram, GeForce 7800GS agp.

---

### Post by fluhartz on 2008-09-08
Hello All,

I can't get this to work. I thought I had done everything the correct way, but it doesn't show up in my extras. When I try to put in the "make && make install" I get an error.  Can anyone figure out what I am doing wrong by what the error says?

I just usually try to figure things out by reading posts and google, and am usually successful....but this one is winning.....
Any help will be appreciated..Hopefully a simple fix....

Thanks,
Flu

---

### Post by Brain-free on 2008-09-09
That's because you have to use the tarball in the middle of page 2. Extract it to desktop, go to the extracted folder with
```
cd ~/Desktop/screensaver
``` 
then do 
```
make $$ make install
```
and finally
```
sudo reboot
```
for the changes to take effect

However, from my experience in Hardy, this plugin is still not ready as only the up and down sides of cube are transparrent.

---

### Post by jeepers on 2008-09-09
Thank you for this...works a treat after i used your .tar.gz...the git one didn't work. i add a key binding for it works beautifully..although the Flying windows are a bit fast...i'm messing about trying different settings to see if i can slow them down.:)

cheers

---

### Post by ZarathustraDK on 2008-09-09
I've added the packaged file to the how-to post explaining that sometimes the git-files doesn't work.

---

### Post by ZarathustraDK on 2008-09-09
> **jeepers said:**
> Thank you for this...works a treat after i used your .tar.gz...the git one didn't work. i add a key binding for it works beautifully..although the Flying windows are a bit fast...i'm messing about trying different settings to see if i can slow them down.:)

cheers

Yeah I experience that too sometimes. I think it mostly happens when you position several windows right on top of each other (like putting all windows in the upper-left corner). Then one or two windows takes off at hyperspeed when you enable the screensaver. I think it's because the windows are set to repel each other at close distances, and that function goes exponential or something in certain window-constellations.

---

### Post by fluhartz on 2008-09-09
Brain-free,

thanks for the reply..  I am at work now and will try this as soon as I get home today.

Flu

---

### Post by fluhartz on 2008-09-09
> **Brain-free said:**
> That's because you have to use the tarball in the middle of page 2. Extract it to desktop, go to the extracted folder with
```
cd ~/Desktop/screensaver
``` 
then do 
```
make $$ make install
```
and finally
```
sudo reboot
```
for the changes to take effect

However, from my experience in Hardy, this plugin is still not ready as only the up and down sides of cube are transparrent.


I did this and still nothing... After make $$ install I get 
"no rule to make target'7114'. stop."
I tried rebooting anyway and it's not in Extras.....

Any ideas

Thanks
Flu

---

### Post by HippyRandall on 2008-09-09
> **fluhartz said:**
> I did this and still nothing... After make $$ install I get 
"no rule to make target'7114'. stop."
I tried rebooting anyway and it's not in Extras.....

Any ideas

Thanks
Flu
```
 make [COLOR=Red]**&&**[/COLOR] make install
```
is correct usage not $$

Hope it helps,
Hippy

---

### Post by fluhartz on 2008-09-09
Hippy,

Awesome.....that was it....

Thanks again
Flu

---

### Post by EnlistedSquire on 2008-09-14
Hi, I'm a bit late here because I used this how-to weeks ago and it worked a treat. Thanks.

The reason I'm posting now is that I noticed some people are having problems with windows flying too fast. I had this same problem and found a patch [[COLOR="Blue"][COLOR="Red"]here[/COLOR][/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=4673") that limits the maximum velocity of the windows. Works a treat.

---

### Post by aidave on 2008-09-29
This tutorial didnt work, I got:

```

compiling : screensaver.cpp -> build/screensaver.loscreensaver.cpp: In function ‘void screenSaverSetXScreenSaver(CompDisplay*, int)’:

screensaver.cpp:223: error: cannot convert ‘const char*’ to ‘CompDisplay*’ for argument ‘1’ to ‘void compLogMessage(CompDisplay*, const char*, CompLogLevel, const char*, ...)’

make: *** [build/screensaver.lo] Error 1


```

And it also removed all my desktop backgrounds, and removed the functionality from Compiz to have multiple backgrounds!!

How do I undo this tutorial?

---

### Post by bunglehaze on 2008-10-03
I am also getting the above error when trying to setup the screensaver. I am a recent convert from Opensuse 11 so I am trying to Ubuntu-ise myself as I go along :D

Any help getting the screensaver working would be excellent.

cheers

leigh :D

---

### Post by ZarathustraDK on 2008-10-03
To aidave and Bunglehaze, did you use the source-code provided at the end of the first post or did you download it from git?

The stuff in the git-repos can be pretty volatile at times (ie. doesn't work) as it usually contains the latest stuff added.

If you did, then try out the source I attached, that should work with an out-of-the-box compiz install.

---

### Post by dugalz on 2008-10-04
I've followed this tutorial using the original git files but I couldn't get it to compile.  I've now used the tarball provided by ZarathustraD (post #18 ) but keep getting hung up with the following error:

doug@us-bet-d-siglnx:~/screensaver$ make && make install
compiling : screensaver.cpp -> build/screensaver.loscreensaver.cpp: In function &#8216;void screenSaverSetXScreenSaver(CompDisplay*, int)&#8217;:
screensaver.cpp:223: error: cannot convert &#8216;const char*&#8217; to &#8216;CompDisplay*&#8217; for argument &#8216;1&#8217; to &#8216;void compLogMessage(CompDisplay*, const char*, CompLogLevel, const char*, ...)&#8217;
make: *** [build/screensaver.lo] Error 1
doug@us-bet-d-siglnx:~/screensaver$

Other than deleting the original screensaver directory made by the git files and then unpacking the tarball on post #18 for the install do I need to do anything else.  I keep thinking I'm missing a step.  BTW I'm on Hardy.  Any suggestions would be greatly appreciated!

---

### Post by dugalz on 2008-10-05
Update - went back through and did step 3 then did make install and it compiled correctly.  I can't figure what the difference was this time around.:???:  I believe that the only difference was compiz was not running at the time i compiled, so maybe that made the difference.  In any case I'm up and running thanks to the posts at this forum.  As a new user to Ubuntu it's great to have a resource and a community like this.

---

### Post by dugalz on 2008-10-06
Back again with another question.  I've successfully installed this for my default user but I have a few users which regularly sign on.  I see the additional screensaver item listed in the CCSM but when I sign in under any of the other users the screensaver item is not there.  What is the easiest way to extend this screensaver option to other users?  Do I need to do a full install over again using the users home directory?

---

### Post by ZarathustraDK on 2008-10-06
> **dugalz said:**
> Back again with another question.  I've successfully installed this for my default user but I have a few users which regularly sign on.  I see the additional screensaver item listed in the CCSM but when I sign in under any of the other users the screensaver item is not there.  What is the easiest way to extend this screensaver option to other users?  Do I need to do a full install over again using the users home directory?

That's a pass on my part, not so spiffy yet with the whole uderland vs. root thing. It sounds strange though, as the files should've been installed when you do the "sudo make && make install".

Somebody else enlighten me :)

---

### Post by Blackwolf_Oz on 2008-10-07
just run this in terminal :)

sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc x11proto-scrnsaver-dev libxss-dev
wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f' mkdir -p  ~/compiz/
tar -xf '/tmp/screensaver.tar.gz' -C ~/compiz/
cd ~/compiz/screensaver
make
make install

---

### Post by loomsen on 2008-10-09
[quote="BrainFree"]
and finally
Code:
[s]sudo reboot[/s]
for the changes to take effect[/quote]

Completely $YOUR_NICK unless you either updatet your kernel and cant wait to boot it. For everything else, simplay restarting the X-server is more than enough.

> "sudo make && make install"

which should more accurately be:
```

make && sudo make install        ##or, more elegant
make && sudo checkinstall    

```
if you don't want to mess up your build directory, which in my case is located in my home directory.
Typing sudo first will chownage of any files built to root, which is not nice at all.
Actually, you don't even need the last sudo (unless you already made this fauxpas earlier and everything is messed up anyway), which, for example would let you install any custom compiled apps to ~/bin (thats what I use to do).
Or specify a prefix as an installation option (--prefix=~/bin) or sth like that, and then simply create a symbolic link to /usr/bin or so. Everything better than root- & sudoing around in your $HOME




```

wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
sudo -i
echo deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./ >> /etc/apt/sources.list.d/compiz.list
yup && yum compiz-fusion-all 
**exit**

```
Don't forget to finish everything with the exit cmd to log root out again!


*edit*
Just seen, the 2nd-last line might surprise...
I specified aliases in my ~/.bashrc, add following to your ~/.bashrc if you want to do so too:

alias yup='sudo apt-get update'
alias yum='sudo apt-get install'
alias yur='sudo apt-get remove'
alias yus='apt-cache pkgnames'

are my apt-related alias'. Just make sure to find sth unique, so it won't mess up with our commands...

And please, don't be too generous with the sudo command. It actually makes sense that a superuser exists :)

---

### Post by raiderleaf on 2008-10-10
This is what I am getting, and none of it works:
argiesey@argiesey-laptop:~$ sudo apt-get install compiz-bcop compiz-dev compizconfig-settings-manager build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-dev is already the newest version.
compizconfig-settings-manager is already the newest version.
build-essential is already the newest version.
libtool is already the newest version.
libglu1-mesa-dev is already the newest version.
libxss-dev is already the newest version.
libcairo2-dev is already the newest version.
git-core is already the newest version.
The following packages were automatically installed and are no longer required:
  libfreebob0 libbtctl4 libkbluetooth0 libjack0 libdvbpsi4 python-qt4-dbus
  libdbus-qt-1-1c2 libdvdnav4 libmodplug0c2 libgnomebt0 libebml0 libmpcdec3
  libmatroska0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  compiz-bcop
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
109 not fully installed or removed.
Need to get 0B/9596B of archives.
After this operation, 127kB of additional disk space will be used.
(Reading database ... 120681 files and directories currently installed.)
Unpacking compiz-bcop (from .../compiz-bcop_0.7.4-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-bcop_0.7.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/bin/bcop', which is also in package compiz-fusion-bcop
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-bcop_0.7.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
argiesey@argiesey-laptop:~$ git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
destination directory 'screensaver' already exists.
argiesey@argiesey-laptop:~$ cd screensaver/
argiesey@argiesey-laptop:~/screensaver$ make & make install
[1] 31711
compiling : screensaver/rotatingcube.cpp -> build/screensaver/rotatingcube.locompiling : screensaver/rotatingcube.cpp -> build/screensaver/rotatingcube.lo/usr/bin/libtool: line 1283: build/screensaver/rotatingcube.loT: No such file or directory
mkdir: cannot create directory `build/screensaver/.libs': No such file or directory
make: *** [build/screensaver/rotatingcube.lo] Error 1
/usr/bin/libtool: line 1283: build/screensaver/rotatingcube.loT: No such file or directory
mkdir: cannot create directory `build/screensaver/.libs': No such file or directory
make: *** [build/screensaver/rotatingcube.lo] Error 1
[1]+  Exit 2                  make

---

### Post by loomsen on 2008-10-10
Quite a while ago now, but there have been problems with 0.7.4 and hardy. There's a special howto for this compiz version somewhere in the compiz-fusion board.

You may follow this, or just really update compiz to 0.7.9, which I got from shames repo. However, since 0.7.6 it worked just fine for me, tho I ran debian back then. But not much of a difference ever since, running Intrepid now, but still using the debian sources. Works just fine.

*edit*

Fast reading your last couple of lines, it seems that the screensaver really begs you to install libtool :) 
Give it a try, might make it work.

---

### Post by higashi on 2008-10-21
i followed the instructions and got this error message:

> me@my-desktop:~/screensaver$ make && make install
convert   : screensaver.xml.in -> build/screensaver.xml
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema    : build/screensaver.xml -> build/compiz-screensaver.schema
compiling : flyingwindows.cpp -> build/flyingwindows.lo
compiling : rotatingcube.cpp -> build/rotatingcube.lo
compiling : wrapper.cpp -> build/wrapper.lo
compiling : matrix.cpp -> build/matrix.lo
compiling : screensaver.cpp -> build/screensaver.loscreensaver.cpp: In function ‘void screenSaverSetXScreenSaver(CompDisplay*, int)’:
screensaver.cpp:223: error: cannot convert ‘const char*’ to ‘CompDisplay*’ for argument ‘1’ to ‘void compLogMessage(CompDisplay*, const char*, CompLogLevel, const char*, ...)’
make: *** [build/screensaver.lo] Error 1


---

### Post by lean1984 on 2008-12-01
> **higashi said:**
> i followed the instructions and got this error message:

Same error here :confused:

---

### Post by keeanrunt on 2009-01-06
keean@keean-laptop ~ $ cd ~/screensaver
keean@keean-laptop ~/screensaver $ make && make install
Makefile:48: *** [ERROR] Compiz not installed.  Stop.
keean@keean-laptop ~/screensaver $ 

a bit stumped
anyhelp?

---

### Post by frogotronic on 2009-03-11
> **higashi said:**
> i followed the instructions and got this error message:

1) Delete the "screensaver" directory.

2) **_TURN OFF COMPIZ_**

3) Untarball screensaver

4) Follow instructions

5) Reboot

You can't compile the screensaver plugin while compiz is running.   :)

---

