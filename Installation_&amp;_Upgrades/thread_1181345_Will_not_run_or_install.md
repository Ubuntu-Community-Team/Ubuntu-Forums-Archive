---
title: "Will not run or install"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by smurph82 on 2009-06-07
I have used Ubuntu in the past and this is the first time I am installing it on my new computer. It is custom built, and I don't know if that is the reason why I can not run or install Ubuntu 9.04 on my system.
I have:
Processor: AMD Phenom X4 9850 Black Edition
DVD-RW: ASUS 2014L1T
MB: ASUS M3N-HD/HDMI
ChipSet: nForce 740a Sli
Memory: 8GB OCZ (OCZ2RPR10662G)
Hard Drive: 3 * 500 GB Western Digital running in a RAID (5) Array
The system has very little over Clocking done to it.

When I run the Ubuntu disc that I downloaded (ubuntu-9.04-desktop-amd64.iso) it starts to run and gets to the screen where you select to either to run the disc live, install, check the disc, or boot to the first HD. When I click on any of them it just sits there for as long as I leave it running and I have to press the Reset button on my computer to get out of the screen. The light on the DVD drive is flashing but nothing is happening. I would be greatful for any help. Thank you.

---

### Post by merlinus on 2009-06-07
Did you do a checksum on your .iso, and burn it at a slow (4x or less) speed?

---

### Post by smurph82 on 2009-06-07
Thank you that work I just had to re-burn the disc and the disc ran great. Now I have another problem. Since I have my system set up with a RAID 5 array, the Ubuntu disc does not recognize my RAID array. It does see all three of my drive but if I install it it will corrupt my array and that would not be good. Is there a way to get Ubuntu 9.04 desktop version to see the array that is already there. Thanks again.

---

### Post by ronparent on 2009-06-08
Do the install with the alternate cd found at the same site as the standard install cd. The alternate cd will recognize a raid set. The standard set doesn't unless you do an apt-get install mdadm.

Also sometimes you can get a kernel freeze, ironically, with the newer mb's. Hit F6 on the first screen of the live cd to select noapic, nolapic.

---

