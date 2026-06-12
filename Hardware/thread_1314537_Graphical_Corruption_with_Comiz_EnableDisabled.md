---
title: "Graphical Corruption with Comiz Enable/Disabled"
date: 2009-11-04
forum: Hardware
---

### Post by Alvin Chiu on 2009-11-04
So this seemed to pop up after I installed Karmic on my ThinkPad T40.  I'm starting to notice graphical corruption when I have Compiz enabled.  This is evident when I start moving windows around.
If I disable compiz, everything is good, except for certain programs.  OpenOffice.org will show garbled drop-down selection boxes and buttons, and Adobe Reader will have a garbled scroll bar.  These do not appear if compiz is enabled.

So I've attached two screenshots: one with compiz enabled and one with compiz disabled, along with my xorg.conf file.  My video card is an ATI Radeon Mobility 7500.

**xorg.conf**
[FONT=Courier New]Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2304 768
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection[/FONT]

Thanks in advance,
Alvin

---

### Post by DenysT on 2009-11-04
I have the same problem with the same video. Here is another one that happens with desktop effects set to "None." The ugly box is supposed to be System Monitor.

---

### Post by Alvin Chiu on 2009-11-11
Well, I managed to fix the problem.  The xorg.conf file wasn't configured to fully utilize my graphics card so all the scrambled mess was due to OpenGL not working properly.  Try googling an xorg.conf file that someone has posted for your model video card and copy those extra lines into your own system xorg.conf.  Of course, make a backup of your original first.

Alvin

---

### Post by Troken on 2009-11-22
For the ATI Radeon Mobility 7500, I found a solution:
see the last post of the release notes here:
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

To say it short: in xorg.conf under "Device", add
Option "RenderAccel" "off"

It worked for me!

---

### Post by louieb on 2009-11-22
This is the fix that worked for me. IBM T30 - ATI 7500 mobility radon 
[SOLVED]                          [Notifications and some windows show up black hashed??]("http://ubuntuforums.org/showthread.php?t=1312300&highlight=t30")                                                                                     

> The problem seems to be related to this bug [https://bugs.launchpad.net/ubuntu/+s...ti/+bug/416001]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001") and this one in freedesktop [https://bugs.freedesktop.org/show_bug.cgi?id=23668](https://bugs.freedesktop.org/show_bug.cgi?id=23668).

A potential fix is to edit your xorg.conf as in the Launchpad comment by Grant Bowman. I'm about to try this now.

---

### Post by nippon88 on 2009-11-23
[SIZE=2]Hi, I can't solve adding  "RenderAccel" "off" , and, when I try with Option     "AccelMethod"                "EXA", my system freezes...
Alvin, could you post your xorg.conf, please? I own a mobility radeon x300, but maybe it could be useful.. Thanks![/SIZE]

---

### Post by Troken on 2009-12-02
> **nippon88 said:**
> [SIZE=2]Hi, I can't solve adding  "RenderAccel" "off" , and, when I try with Option     "AccelMethod"                "EXA", my system freezes...
Alvin, could you post your xorg.conf, please? I own a mobility radeon x300, but maybe it could be useful.. Thanks![/SIZE]

I had to add **Option "RenderAccel" "off"** as root, otherwise the xorg.conf would not be altered. It was actually quite a hassle (had to do it from another OS even, Linux Mint, on the same computer), but in the end it worked. Have you looked at the link I posted? The ubuntu team says that it can be trouble with older graphics cards.

---

### Post by nippon88 on 2009-12-10
In your link I see there's an issue with cards with less then 32MB Ram, but mine has 128!
However, adding  **Option "RenderAccel" "off"** is useless.
Very strange..
And  another strange fact is that system freezes with EXA enabled and compiz ...

---

