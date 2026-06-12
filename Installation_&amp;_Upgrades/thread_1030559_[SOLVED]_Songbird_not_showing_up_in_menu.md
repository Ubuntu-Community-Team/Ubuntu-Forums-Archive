---
title: "[SOLVED] Songbird not showing up in menu"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Archie69 on 2009-01-04
Hi

So I installed songbird but I had issues so I uninstalled it using:
sudo apt-get remove songbird

I have a .deb package of songbird which seemed to work well on the initial install, but now when i try to re-install songbird after I uninstalled it, it doesn't show up in the applications/sound & video tab, nor does it show up in the user folder.  I have no idea what happened.  Can anyone please help.

I got the .deb file from [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

I'd just like to get it up and running again so I can fix the other issue I have with songbird, which is the gstreamer plugins.  I tried to install the ubuntu hardy plugins, but 1 step at a time.  

Please help.  thanks

---

### Post by mc4man on 2009-01-04
first try this, in a terminal

```
alacarte
```

Then highlight sound & video and see if songbird is listed, but not checked. If so then enable it.

If not you can make a new menu item in sound & video (or elsewhere

edit
If not in sound & video ck. in 'other'

---

### Post by Archie69 on 2009-01-04
Hey,

I've tried that with no luck. Not only is songbird not in the sound & video tab, I'm not able to find it in the user folder to add it.

I'm lost.  This has never happened.

---

### Post by Archie69 on 2009-01-04
I have removed songbird using terminal and this is what I see, and to my knowledge its gone from the computer.  

marco@marco-laptop:~$ sudo apt-get remove songbird
[sudo] password for marco: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libtagc0 python-pyogg libavahi1.0-cil
  linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  songbird
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 51.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135270 files and directories currently installed.)
Removing songbird ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


So, this is the point I'm at now.  Maybe this makes things a little clearer.

---

### Post by mc4man on 2009-01-04
When I installed songbird I just downloaded it from their site, unpacked to home directory and run it from there (created a desktop launcher, see screen

.......................

If you used a .deb it probably installed to /usr/bin, you can ck. by broswing or run songbird from the terminal
```
songbird
```

If it opens and is working ok. (ie. you want to keep it) then in alacarte you can make a new item in sound & video.
Highlight S&V, click 'new item', in the launcher pop up use songbird as command (or browse to it
For the icon you'd have to track it down (possibly in usr/share/app-install/icons.

You can always search songbird in synaptic and in it's properties see what and where things where installed.


edit : missed your post, ignore above 

maybe try just downloading from here, and make launcher 0r add to menu

[http://getsongbird.com/download/](http://getsongbird.com/download/)

---

### Post by Archie69 on 2009-01-04
ok, 

So far what mc4man told me has kinda worked.  I downloaded songbird from the website provided.  I then went to edit menus and added songbird.
However, when I go to open it I get this error message:

Failed to execute child process "/home/marco/Songbird/songbird.png" (Permission denied)

I think I have the worst luck.  Any ideas?

---

### Post by Archie69 on 2009-01-04
any new ideas?

---

### Post by mc4man on 2009-01-04
First of all, does songbird work? Go to where you unpacked the songbird folder ( I believe, home folder/Songbird ), find the file songbird (white file with small blue diamond inside) and double click on it, choose run. (takes 4- 10 secs to start, don't use songbird-bin

---

