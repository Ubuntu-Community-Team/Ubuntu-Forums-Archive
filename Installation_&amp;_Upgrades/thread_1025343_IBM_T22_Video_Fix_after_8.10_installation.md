---
title: "IBM T22 Video Fix after 8.10 installation"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Nigel-NZ on 2008-12-30
This post is just sharing my experience (rather than asking a question).

I have been running my Thinkpad T22 on dual boot with Ubuntu 8.04 (and prior to that 6.06) and Windows XP, but it finally got to the stage where more hard disk space was needed and I finally took the plunge and dropped XP.

I decided to start from scratch an install 8.10 from fresh.

The installation went reasonably OK, but the screen resolution after install was not good and the best screen resolution I could get was 800x600 (4:3). The text was large and out of focus. Definitely a backward step from 8.04.

After some searching I cam across a blog at the following link:
[http://freegnu.blogspot.com/2008/05/ubuntu-or-kubuntu-on-ibm-thinkpad-t21.html](http://freegnu.blogspot.com/2008/05/ubuntu-or-kubuntu-on-ibm-thinkpad-t21.html)

I had worked out (thanks to another post on the Ubunu forums) that my T22 had a Savage Video Card. 

I went ahead and implemented the following change to my xorg.conf file:
[INDENT]Section "Device"
    Identifier    "Configured Video Device"
    Option        "AGPMode"        "2"
    Option        "AGPSize"        "8"
    #Option        "ShadowStatus"        "true"
    #Option        "ShadowFB"        "true"
    #Option        "NoAccel"        "true"
EndSection[/INDENT]

A reboot, and I was able to set the screen resolution to 1024x768 (4:3).
(Note: I did also change the BIOS from PCI to AGP prior to the reboot).

All is now good. Small, sharp text and more screen real estate.


I hope this may help someone in the future.

---

### Post by ramon457 on 2008-12-30
i have a t22 also except mine has windows 98 can i install ubuntu onto it?

---

### Post by Nigel-NZ on 2009-01-01
A quick update:

Since my original post, I have had issues with the laptop locking up (blank screen or freeze of video) for no apparent reason. :(

I have modified the xorg.conf file as follows:

    Section "Device"
    Identifier "Configured Video Device"
    Option "AGPMode" "2"
    Option "AGPSize" "8"
    #Option "ShadowStatus" "true"
    #Option "ShadowFB" "true"
    [COLOR="Red"]**Option "NoAccel" "true"**[/COLOR]
    EndSection

So far (after approx 4 hours of use), there has been no further freezes or lockups. :)

---

### Post by Nigel-NZ on 2009-01-01
> **ramon457 said:**
> i have a t22 also except mine has windows 98 can i install ubuntu onto it?

I don't see why not. It works for me (but then I am no expert).

One thing that I have done though is upgrade the memory on the laptop. I now have 384 Mbytes of RAM.

---

### Post by louieb on 2009-01-01
T30 here. Two good sites for thinkpad owners. 
[ThinkWiki - Linux ThinkPad Wiki]("http://www.thinkwiki.org/wiki/ThinkWiki")
 
[ThinkPad Forum ]("http://forum.thinkpads.com/")

---

### Post by emeraldgirl08 on 2009-04-14
Hi everyone!

I'm new here and am the owner of an T30. It's got 768 MB of RAM and has the 1.8 ghz P4 in it. I was very curious about Linux and decided to order the Intrepid Ibex disc. I got it two weeks ago and decided to play around with it yesterday.

:KS

I'm pretty excited that something that's free is able to run pretty well. I haven't installed it but did the LiveCD test-run. I am expecting a HD from a friend this week. I am thinking of buying an Ultrabay HD adapter and installing the Linux on it! Like I said I'm new here and if anyone has any advice for me I'd really appreciate it!

Thanks guys 	:cool:

---

