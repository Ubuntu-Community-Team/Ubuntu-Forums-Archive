---
title: "Sucess on an Averatec 3250"
date: 2005-02-04
forum: Hardware &amp; Laptops
---

### Post by manobes on 2005-02-04
I can report that Ubuntu installs well on an Averatec 3250, most of the stuff is supported out of the box.  Two things that needed tweaking

1) I had to compile the wireless drivers (rt2500) by hand.  I'd recommend the 1.1 beta drivers, they work much better than the 1.0 release drivers

2) I had to "modprobe powernow-k7" to get the cpu scaleing to work.  Once that was done though, it works like a charm.

The major outstanding issue is the video (S3/Unichrome).  The VESA driver works fine, but I'm looking forward to the next release as the X.org X server will support the video much better.

---

### Post by Zubir on 2005-03-19
Hi, I'm running Ubuntu on the same laptop. How do I make the powernow-k7 thing permanent, and could you point me in the right direction for the wireless drivers? Thanks.

---

### Post by daniels on 2005-03-19
Unfortunately unichrome support will never be 'good'.

---

### Post by ganatronic on 2005-03-19
Things have been working well for me with this laptop. I'm going to wait for the full hoary release before switching from warty. I hope hoary resolves the issue where usb stops responding after my computer's been left on for a while.

I have wireless problems occassionally (right now), but it usually resolves itself somehow. The problems show up sporadically, which is annoying. Packet error when using dhclient...
*Edit: oop, got it connected. I had to walk into the room with the router and then dhclient. I feel dopey ;p *

Right now, however, I'm trying to get my 2x2 usb midi interface to work. No luck yet, but I just started a few minutes ago. Hopefully at some point I'll be able to play my synth through this computer.

---

### Post by Tomy on 2005-03-23
[QUOTE=daniels]Unfortunately unichrome support will never be 'good'.[/QUOTE]

I finally got dri to work with the current via driver from the unichrome project. Tuxracer now works :) and glxgears reports 550 fps for onboard unichrome on a MSI KM4AM-V. I am hopefull that the 2.6.11 kernel will solve the unichrome problems.

BTW, I think the via driver in the current version of hoary is pretty broken -- it had the shivers so I used the driver from the unichrome project. I am downloading the current hoary cd image and will report back if this is still true.

Tomy

---

### Post by ganatronic on 2005-03-23
I, and other Unichrome users, await your report.

---

### Post by Tomy on 2005-03-24
[QUOTE=ganatronic]I, and other Unichrome users, await your report.[/QUOTE]
I can report that things are as they were:(.

A fresh install from a current hoary cd image (dated 3/17) automagically recognizes the unichrome chip and sets up the via driver. When xorg/gdm brings up the boot screen everything starts to shiver and shake. It is possible to log in but why -- unfortunately the "via" driver is still broken on my MSI KM4AM-V motherboard. A month ago it did work.

The quick fix is to ctrl-alt-f2 and then from the terminal edit xorg.conf changing "via" to "vesa". I then kill the gdm and xorg processes and restart gdm:rolleyes:. I am sure this is not the RightWay, but I am just a user. The "vesa" driver works better than ever. The resolutions and refresh rates that were set up for my monitor and "via" work great.

I should learn how to post a bug report because this should really get fixed before hoary is released.

Gotta go right now -- later I will grab the via driver from the unichrome project and see if just copying it over the hoary driver will fix the problem.

Tomy

---

### Post by rla128 on 2005-06-28
Any luck?

---

### Post by Tomy on 2005-06-28
[QUOTE=rla128]Any luck?[/QUOTE]

Yes, I do have unichrome graphics working on Hoary. I posted a script I use in another thread but it did not work for others.

Last weekend I found I debian package that installed the unichrome pro driver and I got dri to work without too much pain. 

I am at work right now -- when I get home I'll try to summarize what I did. I am an end user so most of what I know (or think I know) is mostly wrong. :?

Tomy

---

### Post by rla128 on 2005-07-01
Sorry to be so nagging, but any progress on that?  I'm sure there are lots of us who could use some help here.

---

### Post by Tomy on 2005-07-04
[QUOTE=rla128]Sorry to be so nagging, but any progress on that? I'm sure there are lots of us who could use some help here.[/QUOTE]

Try this [thread.]("http://ubuntuforums.org/showthread.php?t=37025&page=3&pp=10")

Tomy

---

### Post by Alex08 on 2008-05-08
I have an Averatec 3250 laptop and every time I try to install ubuntu 8.04 the installer crashes. Any advice would be appreciated.

---

