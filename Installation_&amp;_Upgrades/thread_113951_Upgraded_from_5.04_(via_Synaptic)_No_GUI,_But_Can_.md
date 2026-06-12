---
title: "Upgraded from 5.04 (via Synaptic): No GUI, But Can Still Log In"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by Wolfey on 2006-01-07
I originally posted about this in the [Users and Groups: Cannot Log In with Newly-Created User](http://ubuntuforums.org/showthread.php?t=109589) topic in the Desktop Support forum for Ubuntu 5.04.  However, this issue was (somewhat) unrelated to the topic's original issue, so I thought it would be more appropriate to mention it in this forum instead, especially since I'm technically running Ubuntu 5.10 now:

> I just tried upgrading to Breezy (following the instructions provided in the [BreezyUpgrade]("https://wiki.ubuntu.com/BreezyUpgrade") Wiki, upgrading via Synaptic), and after restarting, I don't have a graphical interface anymore :(

I have absolutely **no** idea what went wrong - I followed those instructions, restarted the laptop, and when I try to boot into Ubuntu, it brings up a blue screen that says:

[quote]I cannot start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

<Yes> <No>
But I cannot select either of those, as it immediately brings up two more lines, with white text on a black background:

> Ubuntu 5.10 "Breezy Badger" lc2464 tty2

lc2464 login:
I can still log in with the root username/password, but am left at the command line - I don't know what can be done to restore what was broken as a result of the upgrade :cry:[/quote]

---

### Post by Wolfey on 2006-01-14
(Bumping topic...)

Has anyone experienced the issue I have described here?

---

### Post by h3xx3r on 2006-01-14
have you tried 

dpkg-reconfigure xserver-xorg

---

### Post by Wolfey on 2006-01-16
I just did, now...But even after answering all of the questions it asked, followed by a restart, it had no effect on this problem :(

(I also recently noticed this line when it was starting up:

> /dev/hda3 on /boot type ext3 (rw,errors=remount-ro)
That is the only one mounted as read-only; the rest are mounted with read and write access...Could that have anything to do with the problem I have here?)

---

### Post by Herman on 2006-01-16
Here's a link to a previous thread with some possible solutions to a similar problem, will any of the  suggestions in there be applicable?

[http://ubuntuforums.org/showthread.php?t=90497&highlight=black+screen+install](http://ubuntuforums.org/showthread.php?t=90497&highlight=black+screen+install)

---

### Post by dcstar on 2006-01-16
[QUOTE=Wolfey](Bumping topic...)

Has anyone experienced the issue I have described here?[/QUOTE]
Looks similar to people who still have incompatible (5.04) Nvidia video drives in their system.

Manually change all of the /etc/apt/sources.list repository entries from "hoary" to "breezy" and do another apt upgrade (can't remember the command line for this).

---

### Post by Wolfey on 2006-01-17
[QUOTE=Herman]Here's a link to a previous thread with some possible solutions to a similar problem, will any of the  suggestions in there be applicable?

[http://ubuntuforums.org/showthread.php?t=90497&highlight=black+screen+install](http://ubuntuforums.org/showthread.php?t=90497&highlight=black+screen+install)[/QUOTE]
Except for *sudo apt-get install ubuntu-desktop* (which I already tried out earlier, without success), nothing I tried there has any effect on this problem :(

[QUOTE=dcstar]Looks similar to people who still have incompatible (5.04) Nvidia video drives in their system.[/quote]
But my laptop uses ATI video drivers (ATI Radeon 9700, according to my laptop's specifications)...Could I have installed the nVidia drivers by mistake, and if so, could that be causing this issue?

[QUOTE=dcstar]Manually change all of the /etc/apt/sources.list repository entries from "hoary" to "breezy" and do another apt upgrade (can't remember the command line for this).[/QUOTE]
Would it be possible to edit that file with the use of a text editor on a live CD?  If not, I'll have to do this from the command line (if it's even possible), and I have *no* idea how I'd edit the file there :confused:

**[size=1][EDIT: Fixed a few coding mistakes I made earlier when typing up this reply.][/size]**

---

### Post by dcstar on 2006-01-17
[QUOTE=Wolfey]
.......
Would it be possible to edit that file with the use of a text editor on a live CD?  If not, I'll have to do this from the command line (if it's even possible), and I have *no* idea how I'd edit the file there :confused:
[/QUOTE]
Log in:

sudo nano /etc/apt/sources.list

And after that:

sudo dpkg-reconfigure xserver-xorg

And select the VESA driver (just to get some basic video functionality to get you going)

then:

sudo reboot

---

### Post by Wolfey on 2006-01-17
[QUOTE=dcstar]Log in:

sudo nano /etc/apt/sources.list[/quote]
I checked, and except for the first commented-out line at the top, every instance of "hoary" was already changed to "breezy", as I made sure to change those lines prior to the upgrade.

[QUOTE=dcstar]And after that:

sudo dpkg-reconfigure xserver-xorg

And select the VESA driver (just to get some basic video functionality to get you going)[/quote]
I tried that, but when I actually try it out, the screen looks like - as best as I can describe it - multiple (garbled and stationary) screens represented on the monitor, and it doesn't work :(

Also, looking around recently, I just thought of this: since the problem I'm having is apparently related to the X server, would the "Xorg.0.log" file possibly help to shed light on what the problem may be?

---

### Post by dcstar on 2006-01-18
[QUOTE=Wolfey]
.......
Also, looking around recently, I just thought of this: since the problem I'm having is apparently related to the X server, would the "Xorg.0.log" file possibly help to shed light on what the problem may be?[/QUOTE]
Yes, you need to look at the log files to try and find what/where the problem is.

The VESA driver should give you a basic graphics login, but you may have to manually specify refresh rates/resolution/colour depth and pick basic values to get going.

---

### Post by Wolfey on 2006-01-23
[QUOTE=dcstar]Yes, you need to look at the log files to try and find what/where the problem is.[/QUOTE]
Looking through it, it seems the problem is with the paths to the font directories.  I'm going to search for information about it to see what might work to fix this problem.

Also, I've attached the X.org log file (compressed as a .zip archive), in case there's anything else I should look at, that I didn't notice at this point in time.

[QUOTE=dcstar]The VESA driver should give you a basic graphics login, but you may have to manually specify refresh rates/resolution/colour depth and pick basic values to get going.[/QUOTE]
All right, then - I'll try it again, this time configuring all of the values manually (according to what the specifications for my laptop are) to see if it will work this time around.

---

### Post by Wolfey on 2006-01-25
I got the GUI working again! \\:D/

The first thing I did was search around for any issues related to the errors I saw in the log file - the big one being the missing 'fixed' font - and found the information I needed to fix the problem on this page:

[http://wiki.colinux.org/cgi-bin/coLinuxIAQ#A4](http://wiki.colinux.org/cgi-bin/coLinuxIAQ#A4)

I tried out the following instructions that were listed there, in this order:

[list][*]apt-get update
[*]apt-get install xfonts-base
[*]apt-get install xutils
[*]update-fonts-dir misc[/list]
After that, I tried starting xfs with **/etc/init.d/xfs start**, but it stated that it did not exist.  To fix this, I then ran **apt-get install xfs** and started it again - this time it worked.

I then tried restarting the GNOME Desktop Manager with **/etc/init.d/gdm restart**, and although it flickered when starting it up (like it did the previous times, none of which were successful), it successfully brought up the logon screen this time :)

After logging into Ubuntu as root, I noticed that the display resolution was off - it was set at 1024 by 768 instead of 1280 by 800, and I could not reset it.  To fix this, I tried out **dpkg-reconfigure xserver-xorg** one more time, reconfiguring it with the selections it thought were correct (and when asked for a selection, I used the default one listed), and selecting 1280 by 800 in addition to the resolutions that were already selected by default.

After doing this, followed by restarting the system, booting into Ubuntu, and logging in, the screen resolution was fixed, and everything looks fine now :D

---

### Post by Morbett on 2006-03-04
Hello everybody.

I've got the same problem.  Just upgraded from Hoary to Breezy and, upon finishing the upgrade, system crashed and now X Server will not run. 

I've tried the following:

apt-get update

apt-get install ubuntu-desktop

apt-get -f install

dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm restart

That is to say, I've tried most of what was proposed in the thread : [http://ubuntuforums.org/showthread.php?t=90497&page=2&highlight=black+screen+install](http://ubuntuforums.org/showthread.php?t=90497&page=2&highlight=black+screen+install)

I still can't get my X Server to run.  I don't have an nVidia card by the way, it's just the basic factory card.  (I think a SiS card, because that's what the dpkg-reconfigure xserver-xorg seemed to autodetect.  Let's hope that it was correct.)

I have a feeling that my problem is **installing ubuntu-desktop** through apt-get, because I am getting a whole lot of dependency problems at the end of the attempt to install it.  There are a few packages that aren't configured.  At the very last part of the install attempt, it reads:

> Errors were encountered while processing: 
postfix 
lsb-core
lsb-graphics
lsb-cxx
lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)

So do I need to do some tinkering with some files?  I'm a newbie and don't know much about the advanced stuff so, I would love if someone could walk me through as clearly as possible.  Thanks in advance.   ;)

---

### Post by Morbett on 2006-03-04
I got Xserver running somehow.  I did some of what Wolfey said in the last post, and just tried startx.  I don't know what i did this time to make it work.

I'll post again here if there are any more problems..

---

### Post by Morbett on 2006-03-04
Maybe I should make a new thread about this, but now that I have GNOME up and running after updating to Breezy, I have some updates.  However I get some errors when I try to update as well as try opening synaptic.

I get :

> Failed to run /usr/sbin/synaptic:
 Unable to copy the user's Xauthorization file.
and 


> Failed to run /usr/bin/update-manager:
 Unable to copy the user's Xauthorization file.

Any idea how to fix this?  

(Also, I noticed that when I go to System -> About Ubuntu, that it still says "Welcome to Ubuntu Linux 5.04 : The Hoary Hedghog".  Does this mean I didn't upgrade to Breezy ?


**EDIT: Started new thread about this at [http://ubuntuforums.org/showthread.php?t=139757](http://ubuntuforums.org/showthread.php?t=139757)**

---

