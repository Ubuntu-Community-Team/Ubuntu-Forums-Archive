---
title: "need help install ubuntu 9.04 on fake raid"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by Hossein309 on 2009-05-19
Hi guys
I want install ubuntu 9.04 on a fake raid0 drive
I used following instruction: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
I can install dmraid, create partitions on my raid drive and install ubuntu without install boot loader ( according to the instruction ) but i can't Install boot loader after installation because when i try to mount raid disk i get an error !
my command :
$ sudo mount /dev/mapper/isw_beeaakeeaa_five5 /target/ 
the error :
mount: can't find /dev/mapper/isw-name of my raid partition/ in /etc/fstab/ or /etc/mtab
someone can help my ?

---

### Post by Hossein309 on 2009-05-19
anybody can help me ?

---

### Post by ken_vh on 2009-05-26
> $ sudo mount /dev/mapper/isw_beeaakeeaa_five5 /target/ 

This is what you did wrong. You're not supposed to fill in the exact same isw_ source as the one from the tutorial.

Do this:

ls -l /dev/mapper/

This will list your isw_ devices.
You will have the correct source and then(if I recall correctly) one for each partition that you created earlier: they have the same name but will have a postfix with a number: 0, 1, etc.

Use the correct isw_ source for the above command.

---

### Post by Kallistelija on 2009-10-06
For all of those who like me found this thread while trying to find simple instructions on how to install raid in Ubuntu 9.04 (rather than wasting time in figuring it out). I googled a bunch of pages with more or less detailed instructions, but they all ended up in a more or less non-working raid. This is the first one I found that actually worked (for Ubuntu 9.04), just follow the instructions:

[http://sonniesedge.co.uk/?p=80](http://sonniesedge.co.uk/?p=80)

(I do not recommend using raid-5 though)

---

