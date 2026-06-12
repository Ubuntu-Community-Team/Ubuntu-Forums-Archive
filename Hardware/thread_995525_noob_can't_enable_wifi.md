---
title: "noob can't enable wifi"
date: 2008-11-27
forum: Hardware
---

### Post by weed_eater_guy on 2008-11-27
Hey yall,

I've been fiddling for the past few days with getting Ubuntu 8.10 on my old lappy (a Compal CL56 with an Intel Pro/Wireless 2200bg wifi chip embedded).  I've been raised on Windows since I was a 7-year-old dinking around on my family's first computer, which sported a 486DX and Windows 3.x.  A Linux fanboy friend of mine convinced me to give this a shot, so I'm trying, and failing misrably, to get my laptop to have wifi.
   
So it didn't work at first.  After scouring forums, I found out about acerhk, which supposedly lets the physical wifi switch on my CL56 work.  I learned that acerhk is in, but needs to be enabled, where Jono's page helped with that.  

[http://insidethebrackets.blogspot.com/2008/02/acerhk-and-ubuntu-update.html?showComment=1227838680000#c5594851858512423322](http://insidethebrackets.blogspot.com/2008/02/acerhk-and-ubuntu-update.html?showComment=1227838680000#c5594851858512423322)

I followed the instructions without incident, and Ubuntu is updated, but I can't get the wifi to run!  What gives?  I even reinstalled Ubuntu and let it update itself before performing this step (I trashed the file system a number of times using other people's fixes, which include attempting to bypass the physical switch, etc. etc.).

It's frustrating.  I even tried an old linksys wifi card based on a Broadcom chip, and after the firmware supposedly updated, still no wifi on either the embedded Intel or the card Broadcom.  

By not getting wifi, I mean that the network manager doesn't even let me enable the wifi, so it's not a signal thing (the other computers in this house are running off this wifi router just dandy).

Can anyone give me some pointers?  I'd like to not give up on this, I'd hate to abandon what otherwise looks like a fun OS, and a welcome change from Windows.

Oh, and fun, now the screan is going schitzo on me... I see a display driver hunt in my future, great...

---

### Post by CobaltSS on 2008-11-27
Have you tried using Hardy 8.04? it is very stable. I tried 8.10 on my laptop but it is still buggy so I am sticking with 8.04. Try it and let me know.

---

### Post by HoppingWombat on 2008-11-27
Is the driver loaded? Go to System -> Administration -> Hardware Drivers and see if the device is even being detected.

---

### Post by weed_eater_guy on 2008-11-28
Nope, hardware driver for the Intel isn't detected there, however I remember doing something in terminal (as part of a previous attempt to fix it) that showed that it was detecting the Intel hardware, but that the radio switch was off, no matter what position the switch actually was.

I'll try 8.04, we'll see what happens there.

---

### Post by weed_eater_guy on 2008-11-28
yeah... you know what... my laptop is displaying staticy garbage now, even in BIOS.  I don't know if my laptop just spontaneously broke, or if Ubuntu completely f-ed up my lappy, but for now, bye bye Ubuntu.  I'm sticking to windows.  Thanks yall for the help anyway.

---

### Post by CobaltSS on 2008-11-28
is your picture still screwed up? if it's happening in BIOS it has nothing to do with any operating system. as standard vga drivers are loaded at BIOS. if it this is still happening 1. you may either have dust inside need to spray dust remover. 2. a problem with your video card. 3. a bad connection between the video card and screen and have to replace the cable (this one happened to me). 
if it is #3 best thing to do is buy a nice external monitor it costs the same as getting that cable replaced.
My laptop screen still displays everything just in weird colours. It's from me opening and closing the lid all the time which wore out the cable jacket. That's what you get for trying to keep your screen dust free. lol.

---

### Post by ljerabek on 2008-12-21
Ubuntu 8.04 and 8.10

Here are the steps to get a Compal CL56 Laptop wireless working.

Open a terminal window and do the following steps.

Add acerhk to /etc/modules by the following command:

sudo gedit /etc/modules

Goto the last line in the file... and add the text "acerhk"

Save and Exit

Should look something like this:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
acerhk

Now you need to create an init script in /etc/init.d

sudo gedit /etc/init.d/acerhk_on

Add the following to it:
#!/bin/sh
echo 1 > /proc/driver/acerhk/wirelessled

Save and Exit

Now you need to add this to run at runlevel 2

cd /etc/rc2.d
sudo ln -s ../init.d/acerhk_on S99acerhk_on

You are all done now.

Reboot

Let me know if you have any other questions.

---

### Post by ljerabek on 2008-12-21
Oh my comment before works on the base install. If you have hosed your system it may not work. I have had 100% success with this when on a core 8.04 and 8.10 build for Compal CL 56

---

