---
title: "Help plz total n00b to ubuntu/linux os!"
date: 2008-08-14
forum: General Help
---

### Post by LukeRocksALot on 2008-08-14
hey guys i decided to try out ubuntu,so i installed wubi threw xp.and now im on ubuntu....i have some major problems with it though, i cant change the screen resolutions it only goes up to 800X600, i cant install the driver for the video card.i cant use the "extra"on visual effects" i cant install flash/java.so when i try to open the .run for the nvidia driver it wont open it will say "could not open",same thing with any other thing i need to install,i cant install any program it seems....  i feel that xp is so simple now.the screen resolution is horrible..could any1 help me out? My pc specs,sli EVGA 9800 gtx,evga Nforce 780i,4gb RAM,and e8400....id also like to learn how to install compiz/baryl...thanks

---

### Post by jerome1232 on 2008-08-14
Sounds like you downloaded the installer from Nvidias website, that way will be hard for someone who is new to Linux in general, your card is really new and I've heard of some problems with the 9XXX series but the way most likly to work for you is envy.
To get your card installed open a terminal (applications>>accessories>>terminal)
```
sudo apt-get install envyng-gtk
```
Compiz comes installed and in use by default, however if you want the most eye candy you need to configure it a bit, install the manager.
Applications>>Add remove programs>>Where it says show select all avaible applications do a search for compiz, you should see the advanced desktop effects settings manager seletc that one and and apply.

Now you will have a New item under system>>preferences to toy with

---

### Post by LukeRocksALot on 2008-08-14
kk,did that.still idk how to fix this resolution. i think the max for mine is 1440x900,and is there like a ultimate n00b guide to ubuntu?ive been using windows for about 10 years,and im just totally new to all this

---

### Post by LukeRocksALot on 2008-08-15
.bump

---

### Post by Duckyspetrie on 2008-08-15
Hey, look Eric, a virgin!

Nerds!

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.Hey, look Eric, a virgin!

Nerds!

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

---

### Post by Drone4four on 2008-08-15
> **LukeRocksALot said:**
> kk,did that.still idk how to fix this resolution. i think the max for mine is 1440x900,and is there like a ultimate n00b guide to ubuntu?ive been using windows for about 10 years,and im just totally new to all this

LukeRocksALot: Welcome to Linux.

Try this at the command line: ```
sudo envyng-gtk
```  This should start the GUI program, EnvyNG, that jerome1232 had you install.  With EnvyNG, you can practically click next a few times to install the latest nvidia drivers with no hasstle.

---

### Post by LukeRocksALot on 2008-08-15
cool this is great i got my screen resolution up and running,not sure yet how to get that cool 3d cube,and i was able to play music and movies earlier,but now i cant..and also youtube works...sorta it will load then pause,and will have no sound

---

### Post by dragos240 on 2008-08-15
hmm.... I got flash from [this]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") think and it worked fine.
As for java i got it from java.com. Try that.

---

### Post by blazercist on 2008-08-15
In the future the name of the thread should have something to do with your actual problem.  Thread titles like "Please help im a n00b" don't explain the problem and are usually ignored.

---

### Post by LukeRocksALot on 2008-08-15
it wont let me install it,it will open and bring up the folder thats it

---

### Post by dragos240 on 2008-08-15
> **LukeRocksALot said:**
> it wont let me install it,it will open and bring up the folder thats it

Try opening the terminal from the applications tab and accessories. Then find out where it is, type in cd location. Then type in sudo -s, and type in your password, then make install. That should do it.

---

### Post by LukeRocksALot on 2008-08-15
tried that,didnt work

---

### Post by dragos240 on 2008-08-15
Really? Hmm..... could you display any errors you got and ill explain them and hopefully help you.

---

### Post by LukeRocksALot on 2008-08-15
only errors i got are that when i try to go on youtube it will load the video start,then pause ,no sound also,i also tried to listen to music from my external and it wouldnt play,thats about it anyway, ive been up for about 30 hours,thanks for all your help,night bbl!

---

### Post by dragos240 on 2008-08-15
MY seggestions:
1. Update from the yellow window up on top
[s]2. Get some rest, 30 hours will realy mess you up.[/s]
didnt see that night part. Have a good sleep.

---

### Post by jerome1232 on 2008-08-15
I would actually suggest starting a new thread with a descriptive title about your audio/video issues, more people will take a look ;)

Check the mixer applet (top right of your screen looks like a speaker) and make sure no playback channels are muted.

For some reason I wasn't getting notices that this thread got replies... maybe I was just asleep though.

(I forgot to say, Welcome to the forums :) )

---

### Post by dragos240 on 2008-08-15
> **jerome1232 said:**
> I would actually suggest starting a new thread with a descriptive title about your audio/video issues, more people will take a look ;)

Check the mixer applet (top right of your screen looks like a speaker) and make sure no playback channels are muted.

For some reason I wasn't getting notices that this thread got replies... maybe I was just asleep though.

(I forgot to say, Welcome to the forums :) )
I'm going to have to agree with you, but 1337 does attract some people. It would attract more people to help.

---

### Post by LukeRocksALot on 2008-08-15
> **dragos240 said:**
> MY seggestions:
1. Update from the yellow window up on top
[s]2. Get some rest, 30 hours will realy mess you up.[/s]
didnt see that night part. Have a good sleep.

i got the sound working,video working,youtube working..i didnt see any yellow window on top though,this looks awesome how would i go about getting something like this on my comp lol, [http://www.youtube.com/watch?v=pTRsLW0eet0](http://www.youtube.com/watch?v=pTRsLW0eet0)

---

### Post by jerome1232 on 2008-08-15
It's actually very easy to get that
[http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/](http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/) tells you how to update to the newest compiz

---

### Post by LukeRocksALot on 2008-08-15
well i follow those instructions,and whenever i check :dedsktop tube" it will uncheck a second later...it also says it requires a plugin

---

### Post by Drone4four on 2008-08-15
> **blazercist said:**
> In the future the name of the thread should have something to do with your actual problem.  Thread titles like "Please help im a n00b" don't explain the problem and are usually ignored.

LukeRocksALot, to build on what blazercist is saying, for the future, it would be helpful to you and other users on this message board if you *_[asked questions the smart way]("http://www.catb.org/~esr/faqs/smart-questions.html")_*, as Eric S Raymond explains.

Coincidentally, _**[I seem to be struggling with a very similar audio problem]("http://ubuntuforums.org/showthread.php?t=890446")**_ on Ubuntu at the moment.  If my problem is like your problem, LukeRocksALot, then you won't need to start a new thread, just reply to mine. =D

---

### Post by LukeRocksALot on 2008-08-15
> **Drone4four said:**
> LukeRocksALot, to build on what blazercist is saying, for the future, it would be helpful to you and other users on this message board if you *_[asked questions the smart way]("http://www.catb.org/~esr/faqs/smart-questions.html")_*, as Eric S Raymond explains.

Coincidentally, _**[I seem to be struggling with a very similar audio problems]("http://ubuntuforums.org/showthread.php?t=890446")**_ on Ubuntu at the moment.  If my problem is like your problem, LukeRocksALot, then you won't need to start a new thread, just reply to mine. =D

i got my audio fixed,i just wanna figure out to get something like this on ubuntu, [http://www.youtube.com/watch?v=pTRsLW0eet0](http://www.youtube.com/watch?v=pTRsLW0eet0) tried checking that box for desktop cube,and will uncheck a sec later,i think i need a plugin..and not sure how to get 3d wallpaper...

---

### Post by LukeRocksALot on 2008-08-16
this is what happens whenever i enable the 3d cube...

[http://i16.photobucket.com/albums/b15/LukeRocksALot/S8001727.jpg](http://i16.photobucket.com/albums/b15/LukeRocksALot/S8001727.jpg)

Thanks!

---

### Post by thestig_992 on 2008-08-16
Thats called cube unfold...
normally crtl+alt+(direction) will rotate the cube, but i think the default setting for unfold is down...but cube only works with one row of workspaces anyway...

To manually rotate cube, go to compiz (ccsm) -->  Rotate Cube --> Bindings --> Rotate Cube --> Initiate
then bind keys...i have mine set to crtl+alt+mouse 1, which works fine, but you can also use mouse 3 (which is click in the scroll wheel i think..)

---

### Post by LukeRocksALot on 2008-08-16
i ran the command for installing atlatis plugin,so i can get the cool fish like in the youtube video a few posts up..but i cant find out how to enable it.i had it installed through the terminal but i cant find out how to make it work, i tried going through ccsm,but i still couldnt find out how to enable atlantis. this is what i got so far 
[http://i16.photobucket.com/albums/b15/LukeRocksALot/1.png](http://i16.photobucket.com/albums/b15/LukeRocksALot/1.png)

[http://i16.photobucket.com/albums/b15/LukeRocksALot/2-1.png](http://i16.photobucket.com/albums/b15/LukeRocksALot/2-1.png)

---

### Post by LukeRocksALot on 2008-08-16
would any1 know how to start the plugin?also i got another problem,when i minimize firefox or any other program it will hide in the panel.the process still exists,but i have to alt+tab to maximize it again..how can i get the programs that are minimize in the panel?

---

### Post by jerome1232 on 2008-08-16
Well if you successfully compiled that plugin you have to restart compiz before it will show up under the settings list (log out then back in)

---

### Post by LukeRocksALot on 2008-08-16
should it just start the atlantis thing automatically? do i have to search somewhere to enable it?

---

### Post by LukeRocksALot on 2008-08-17
bump

---

### Post by LukeRocksALot on 2008-08-17
any1?where do i find the plugin once its installed?

---

### Post by LukeRocksALot on 2008-08-18
also how do i enable sli?

---

### Post by LukeRocksALot on 2008-08-18
bump

---

