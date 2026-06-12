---
title: "Three steps forward, three steps back... (long)"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Ginsu543 on 2009-11-03
I finally got Karmic installed and running on my rig, and it has been a mixed bag.

Steps forward:

1) My system has been as fast as advertised

Now bootup only takes 40 seconds from pushing the ON button to login screen and 20 seconds from login to desktop. That's 1 minute from 0 to 60! WAAAYYY faster than my Jaunty setup and I love my Jaunty setup.

2) Karmic with its ATI restricted driver fixed all the minor glitches I've had with video in Jaunty

3) Unlike many here, my sound works as it should out of the box

However, I so much prefer the way sound configuration was handled in Jaunty. You no longer can individually control each audio channel. Which kinda sucks because for whatever reason my right rear channel is slightly weaker than my left rear channel. I used to be able to compensate for that in Jaunty but can't in Karmic.

4) All my TrueType fonts now show up as thumbnails in Nautilus

In Jaunty, only a few would show up as thumbnails. The rest would show up as generic TrueType icons.

5) I didn't have to add as many repositories through Software Sources because more programs I use regularly are in Karmic's Universe (one example is ScribusNG)

Steps backward:

1) While I've got Karmic up and running on one of my Raptors, it does not play nice with the other one

It's like Karmic treats the drives as if they went through a bitter divorce. At first, the installer would only see them as a married couple (RAID array) but now they can't seem to coexist. If I plug in the other Raptor, Karmic won't boot. If I disconnect the other drive, Karmic boots like a banshee.

**I found a solution to this problem. I figured out that when I installed Gparted, it installed dmraid again (which I had previously removed) which prevented my drives from playing nice. Once I removed dmraid again, I was able to boot with both drives connected.**

2) Certain programs refuse to launch

a) System Monitor
b) Gparted
c) Screenlets

Funny thing is, almost everything else is working great. For example, Karmic's Disk Utility works, but Gparted doesn't. I have already tried uninstalling the packages in Synaptic and reinstalling them. For both System Monitor and Screenlets, when I launch them from the Menu I can see their icons on my AWN dock but then they fade away and nothing happens. Gparted will bring up the administrative permission dialog but then it won't do anything.

**I found a solution to this problem as well. I found out that these programs were conflicting with the Global Menu applet I had installed (0.7.7.1), which only works for Jaunty but not for Karmic. Once I removed Global Menu, everything was aces.**

3) Firefox appears to lag a bit

I know its subjective, but Firefox doesn't seem to bring up web pages as quickly as it did in Jaunty.

4) FFMpeg will not recognize the libfaac codec

After I installed libavcodec-unstripped-52 in Karmic, I compared its package contents with the package contents of libavcodec-unstripped-52 in Jaunty's repositories. I noticed that the package in Jaunty contains libfaac0 but the one in Karmic does not. However, Synaptic shows that libfaac0 is already installed on my system. Yet, FFMpeg will not recognize it.

**Still no luck figuring this one out. Any help would be appreciated.**

I would really appreciate it if anyone has any idea how I can work around the problems I've listed above. For five days I was pulling my hair trying to install the thing, and now that I've got it up and running, it's even more frustrating because I'm so close to having it work as I need it to.

---

