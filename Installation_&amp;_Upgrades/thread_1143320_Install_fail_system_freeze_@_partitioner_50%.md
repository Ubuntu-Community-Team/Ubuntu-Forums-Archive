---
title: "Install fail: system freeze @ partitioner 50%"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by thepaan on 2009-04-29
I am trying to install Ubuntu because supposedly 'it just works'. I also want to address all of my RAM which means 64-bit (although I have come to understand 32-bit Linux can be modified to recognize it as well).
 
I first tried to install 8.04 x64 and all goes well until step 3 of the setup. The partitioner begins scanning drives and the bar moves to 50% then stops. The animation continues for several seconds then the entire system stops responding (freezes). I then tried 8.10 x64 but the same thing happens. I did some reading and found that my motherboard+Ubuntu only works with the SATA controller mode set to AHCI (Windows will only recognize the HDD in IDE or RAID modes). I changed the mode to AHCI but the same thing happens. I then did some more reading and found that some people had to use a specific release of Ubuntu. I then tried 8.10 x64 alternate which seemed to make some progress but still froze during partitioning, and 9.04 x64 which also did the 50% partitioner freeze. After more reading I tried manually partitioning using GParted per some thread on this forum which I can't find at the moment but that yielded the same results. I then tried 9.04 x64 alternate then 9.04 x86 both with the same results. I then tried chaning the SATA controller mode to RAID then IDE and back to AHCI but all had the same results.
 
My hardware is below. There is nothing else but what is listed at the moment. I planned on swapping the HDD with the velociraptor from my old machine and installing the video card from the same after I got this working.
 
Motherboard: P5Q-EM
CPU: Core 2 Duo E8500 Wolfdale
RAM: 2x2GB Corsair PC2 6400
HDD: WD Raptor (74GB)
Optical: Samsung DVD-ROM
 
Any help would be much appreciated.

---

### Post by upchucky on 2009-04-29
download and burn the bootable versions of gparted and partedit, where one partition editor fails the other should be able to pick up and complete.

remember to only do one task at a time so the editor does not get confused.

after you have the drive partitions set up the way you want then do the install.

make sure the live cd actually boots up to a graphical display before you do the actual install, this tells you that the display will work and you may only need to set the resolutions to get a display.

---

### Post by thepaan on 2009-04-29
I have already tried partitioning with GParted but after that the install of 9.04 x64 still freezes at the same place.

---

### Post by thepaan on 2009-04-30
I know it's kind of tacky to reply to one's own thread without any prompt to do so, but I thought this important.
 
Here are some links to what I believe to be exactly the same problem I am experiencing. As the post in the last link I'm going to try the 8.04 alternate since I have not tried that version before.
 
[http://ubuntuforums.org/showthread.php?t=958145](http://ubuntuforums.org/showthread.php?t=958145)
[http://ubuntuforums.org/showthread.php?t=220086](http://ubuntuforums.org/showthread.php?t=220086)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/305793](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/305793)

---

### Post by AaronLS on 2009-10-20
Ever have any luck with this?  I am experiencing the exact same issue.

---

