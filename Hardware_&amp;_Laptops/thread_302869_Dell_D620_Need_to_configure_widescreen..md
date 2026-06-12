---
title: "Dell D620: Need to configure widescreen."
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by Jamie Jackson on 2006-11-19
Can someone please respond with a concise step-by-step for getting widescreen going on my Dell D620 in Ubuntu Edgy?

Problem: There are lots of threads on this, with endless tangents, dead-ends, red herrings, and misinformation.

There's got to be just a few steps to this. Can anyone be so nice as to lay them out?

I'll get the steps started with what (I think) I know to be true:

1. Open a terminal (applications>>accessories>>terminal).
2. Set up apt to be able to get the 915resolution package:
```
sudo gedit /etc/apt/sources.list
```
3. In the file you just opened, uncomment (remove the "#" from the start of the line of) the two sources:
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
```
Save the file
4. Install 915resolution package:
```
sudo apt-get install 915package
```

To be continued by a nice Ubuntu forums member.

Thanks,
Jamie

---

### Post by ReaderRat on 2006-11-19
**[http://ubuntuforums.org/showpost.php?p=1699507&postcount=2](http://ubuntuforums.org/showpost.php?p=1699507&postcount=2)**
This is what I found...please let me know if it works (or if it doesn't)..

---

### Post by Jamie Jackson on 2006-11-19
Nope, when I restart Gnome, I get the same old resolution 1024x768).

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=5c
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=
```

UPDATE: I was wrong. I guess I didn't know how to restart Gnome at the time. (You go to the desktop and hit cntrl-alt-backspace keys all at the same time.)

---

### Post by Jamie Jackson on 2006-11-19
[SIZE="4"]Detailed Solution for enabling wide-screen in Edgy/Dell D620[/SIZE]

I've got it solved (for me, anyway)

1. Open a terminal (applications>>accessories>>terminal).
2. Set up apt to be able to get the 915resolution package:
```
sudo gedit /etc/apt/sources.list
```
3. In the file you just opened, uncomment (remove the "#" from the start of the line of) the two sources:
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
```
Save the file

4. Install 915resolution package:
```
sudo apt-get --assume-yes install 915resolution
```
5. Edit the 915resolution configuration file:
```
sudo gedit /etc/default/915resolution
```
6. Change the MODE, XRESO, and YRESO lines to the following:
```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=54
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1280
YRESO=768

#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=

```
Save the file

7. Restart Gnome (go to the desktop and hit cntrl-alt-backspace keys all at the same time)

I hope it helps someone. :D

---

### Post by zman58 on 2006-11-26
You will need to make sure the 915resolution program is being run before X starts. This should be done during initialization and can be controlled using the init.d script called 915resolution.

I happen to be running MEPIS, which is based on UBUNTU, so I expect this information would be valid for UBUNTU as well.

The 915resolution deb package comes with a start script, named as you might expect "915resolution". If you have the 915resolution package installed in your system, then you should already have this script located at /etc/init.d/915resolution. You need to enable it for the runlevel you are operating in. Just add a symbolic link to /etc/init.d/915resolution for the proper runlevel which is runlevel 5 on my system.

The symbolic link for run level 5 that I added to my system is S00resolution and looks like this...

cd /etc/rc5.d/
ls -l
[...]
lrwxrwxrwx 1 root root 23 2006-11-22 09:37 S00resolution -> ../init.d/915resolution
[...]

The 915resolution script uses the 915resolution default file located at:
/etc/default/915resolution

In this 915resolution default file on my system (DELL D620 w/Intel GMA 950) I have the following information:
#
# 915resolution default
#
# find free modes by /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
#
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=24

I had to edit in the XRESO, YRESO, and BIT settings. The 1440x900 mode works great on my system.

As the man page for 915resolution states, you can find supporting information at:
/usr/share/doc/915resolution/README.Debian


The remainder of this post details how I got Open GL working...

Furthermore, To get Open GL working on this DELL D620, I found out that I had to add a "VideoRam 128000" setting into /etc/X11/xorg.conf like so:

[...]
Section "Device"
Identifier "Card0"
Driver "i810"
BoardName "unknown"
VideoRam 128000
[...]

It seemed that the system needed to be completely cold-started once these changes were made. Perhaps by repetetivly restarting X, I may have confused the chipset trying multiple other VideoRam value settings before doing a man i810 and reading that the i810 can manage only up to 128MB of VideoRam.

Video support seems to be working now; That is to say, I have Open GL support at 1440x900 with the Intel GMA 950 video chip.

---

### Post by Jamie Jackson on 2006-11-26
What's a good test for whether I've got OpenGL support configured? I can tell you that my GL* screensavers are all working properly. Is that a good enough test?

Thanks,
Jamie

> **zman58 said:**
> 
Furthermore, To get Open GL working on this DELL D620, I found out that I had to add a "VideoRam 128000" setting into /etc/X11/xorg.conf like so:

[...]
Section "Device"
Identifier "Card0"
Driver "i810"
BoardName "unknown"
VideoRam 128000
[...]

It seemed that the system needed to be completely cold-started once these changes were made. Perhaps by repetetivly restarting X, I may have confused the chipset trying multiple other VideoRam value settings before doing a man i810 and reading that the i810 can manage only up to 128MB of VideoRam.

Video support seems to be working now; That is to say, I have Open GL support at 1440x900 with the Intel GMA 950 video chip.

---

### Post by Xtyn on 2006-11-26
Hm...I had the same problem, I just installed 915resolution from synaptic and on restart, it worked. If it doesn't work, try System-Preferences-Screen Resolution, you should see 1280-800, I think that's your resolution. Good luck.

---

### Post by Jamie Jackson on 2006-11-26
My issue is resolved, but thanks for posting. I actually got my display working fine, and gave the steps in [the fourth post of this thread]("http://ubuntuforums.org/showpost.php?p=1779994&postcount=4").

I left the thread open, in case anyone had questions, but I don't think I (personally) need any more help on my machine.

However, zman58 made me wonder if I had some unnoticed problems remaining, but I don't think so. I think my OpenGL support *is* working, so I don't think his xorg.conf tweak is necessary. I think my little [HowTo]("http://ubuntuforums.org/showpost.php?p=1779994&postcount=4") is sufficient.

Thanks,
Jamie

---

### Post by justjim on 2007-09-17
hi guys

not to glog up the forum with useless chatter but... (I'm gonna do it anyway)

FIRST DAY with Ubuntu here

and this forum (so far just passive reading) has already been a huge help in migration!!!

I'm in kind of a funny position b/c I have a CS background (back in the day when the USPTO didn't recognize CS as an engineering field and CS was part of the math college in Uni)

So, for me, a lot of it isn't "how do computers work", but rather "so, how did you guys decide to arrange the standards?" -- a position, I often find, unwelcome as it is neither fish nor fowl

here, I feel pretty welcome

so 

MY COMPLIMENTS TO THE UBUNTU COMMUNITY

and

Thanks for helping nudge personal computing back to a direction I think has a lot of promise

---

### Post by Jamie Jackson on 2007-09-17
Welcome, justjim. I started using Ubuntu because I wasn't learning anything new on a day-to-day basis in Windows. The pace of learning sure has picked up since switching to Ubuntu!

---

