---
title: "Ubuntu Installation/Live Demo Freezes"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Stabgotham on 2009-06-29
Hello,

I wanted to test out and install Ubuntu on a second PC I have.  I burned Ubuntu 9.04 x64 onto a DVD and load the "Try Before You Install" demo.  When I clicked on Firefox, the demo froze.  After three attempts, I figured that it may have been a bad burn, I burned another copy (after downloading another ISO) and tried again.  Same issue.  The next time, I tried booting the demo from a USB stick.  Same thing.  

Thinking maybe it was an issue with the demo, I decided to just install Ubuntu.  Once the installation screens first load up (and I mean, the very first screens...step 1 of 7), it freezes.  I tried this with both DVD's and the USB drive.  

Lastly, I figured, okay, let me just install through Windows.  The install went fine from the Windows environment, but when I go to boot the OS, it again freezes.  Not sure what is going on.  The PC meets the specs by far.  And I know the disks and USB drive have to be good because they work on my other machine just fine.  Here they are:

ASUS A8N-SLI Deluxe (socket 939)
AMD Athlon 64 3700+ San Diego
2GB G.Skill DDR 800
WD Caviar 500GB HDD
NVidia 7800GT
Memorex DVD-Burner

Any ideas?

---

### Post by Stabgotham on 2009-06-30
Tried different things:

[LIST]
[*]Tried one stick of RAM at a time.  Didn't help.

[*]Unplugged the DVD-Burner and tried USB install.  No effect.

[*]Ran diagnoztics on the HDD.  Running great.

[*]Tried different video card.  No effect.
[/LIST]

Not really sure what else I should be doing.

---

### Post by Stabgotham on 2009-06-30
I've still got nothing.  Not sure what the deal is but I'm ready and willing to try anything here....anyone?

---

### Post by gamera on 2009-06-30
I have a similar problem with 9.04 xubuntu Jaunty Jackalope. 
I installed and upon reboot it stopped on the loading screen. I then ran diagnosis on the cd and it was fine.
Tried running as a live cd and again it froze in the same place.

Was using the 9.04 alternate previously and it works fine apart from an issue with the wireless networking. which is why I wanted to try the stable release.

I doubt its the hardware or media used. Which leaves me with the actual release as the alternate version works.

---

### Post by gamera on 2009-06-30
After waiting for 5mins or so after the freeze I got a message:

*Preparing restricted drivers...
*Starting kernel event manager...
*Loading hardware drivers...
udevd-event [2224]: '/sbin/modprobe -b pci:v0000123Dd00001978sv00000E11sd0000B112bc04sc01i00' abnormal exit


So a driver error looks to be causing my issue. Any advise on how to fix it or should I just go back a release.

---

### Post by gamera on 2009-07-01
Ok so whilst waiting for a responce I had a chat with a few people that could not offer any advice. Did some searching on the net...

Live CD would actually start under the safe display drivers option. When loading the CD hit F4 at the install prompt. Select the safe mode and bang it works. Also my wireless issue is also fixed.

Installing from live now.

---

### Post by gamera on 2009-07-01
The full install would not have a bar of it.
Now I am really getting frustrated. 

9.04 fails to install/startup properly.
9.04 alternate installs fine but has wireless issues.

No advice from anyone here which is a let down.
well i think ill be going back a release or back to centos.

---

### Post by gamera on 2009-07-19
I think I figured it out.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357724](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357724)

It would seem that the maestro upgrade is the issue. 
Intrepid 8.10 installed just fine on my E500.
Applied the edits to the blacklist and am now upgrading the kernel.
Will reply soon with the result.

---

