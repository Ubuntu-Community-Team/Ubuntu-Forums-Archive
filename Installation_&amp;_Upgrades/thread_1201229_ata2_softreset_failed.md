---
title: "ata2 softreset failed"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Sankou on 2009-06-30
I was trying to install the amd 64 bit version and run into this error.

Asrock a780gxe mobo
amd athlon 7750 am2+ black edition 64 bit processor
2gb ddr2 1066 ram
pci express 2.0 video card ati radeon hd 4670
1 sata drive
1 ide drive

I'm trying to install it on my secondary ide drive...

---

### Post by Sankou on 2009-06-30
As expected, the error was referring to my sata hard drive which is plugged into port #2...

This however is irrelevant because I'm trying to install onto my secondary IDE hd.

After the error I'm brought to a command line instead of a gui. At first I thought the issues were related, but I was wrong. It's some sort of video related issue. 

I tried my onboard video and video card- same result.

I also tried safe graphics mode. No help.

I'm brought to a command line....
[Iniframfs]

I guess there is a way to install from here... but that wouldn't help at all if there is still video related issues.

So I'm stuck. I know there are drivers available for both my video card and onboard video. Is there a way to 'slipstream' my graphics card drivers into the disk before installation? Any other solutions?

---

### Post by Sankou on 2009-06-30
I'm trying to install ubuntu 9.04... or any version for that matter. I try the option to test it first and run into a command line. I tried to install. I get the same command line. I even tried safe graphics mode. I tried my on board and video card and get the same result. Can I install from the command line and then boot up to the gui later? or will it still run on a command line? 

I know drivers exist for my video card (radeon hd 4670) and on board video, is there a way to 'slipstream' the drivers onto the disk before instalation? I'm stuck and really have no solution... Any help would be greatly appreciated.

---

### Post by LepeKaname on 2009-07-01
I suggest you to install it first in command only. If it fails to load the GUI, then you can try "vesa" driver until you fix the problem. Usually it may be related to the video driver.

---

### Post by Sankou on 2009-07-01
I was able to get it installed. I don't know why this method worked, but it did o.0

I installed Ubuntu from windows by mounting the image with daemon tools and selecting that option. Then I chose the partition on the secondary drive that I set aside for it. It installed and I was able to boot up to it. It went through everything from there and now works fine. 

I'm still not sure why that method worked... I figured it was a video driver issue but it should have still failed if that was the case. I don't know, at least it's working now! :)

Now for the fun part of driver installation ;)

---

