---
title: "Ubuntu installation freezes due to initramfs"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by xelxel on 2009-04-08
Hello!

I have been a loyal ubuntu user for a long time now, and decided i would get a bit experimental and install ubuntu 9.04. I downloaded unetbootin and the corresponding .iso file with said ubuntu version, and copied over everything to my USB memory stick (8GB). I have made sure all the files are there, but once i reboot and try to install ubuntu 9.04 it goes south.

I get the unetbootin screen, chose default, and then the loading bar of ubuntu shows up - the one for ubuntu 9.04. It will however not continue on from there. Insteads it keeps flashing, then i get some message of a module.dep file. The file or directory cannot be found. Below is a commandline with "Initramfs". Any typing i do is taken as commands, and since i'm still stuck in my windows thinking i can't make it past this stage.

Does anyone have any suggestions on how to fix this?
Of course i realise 9.04 is BETA currently, but i suspect the installation part should be pretty stable - or perhaps it's an errounous assumption on my part.

Anyway,

Thank you in advance!

//Erik

---

### Post by dandnsmith on 2009-04-08
You haven't mentioned anything about the PC configuration - especially the RAM size and type.

I have this initramfs> prompt with a laptop which almost certainly doesn't have enough RAM (at 256MB).

You might get a bit more detail if you put nosplash instead of splash on the lines activating the kernel and initrd. It will be in an xxx.cfg file - detail depends on exactly what you did to make the usb.

---

### Post by xelxel on 2009-04-08
dandnsmith,

The laptop configuration is acer extensa 5420.
1.59Ghz AMD, with 4GB Ram and 160HD.
GPU is ATI, unfortunately, but since i dont play games
it doesnt matter much. It has so far always worked to run
ubuntu on this laptop. 

I will return with the logg report.

---

### Post by xelxel on 2009-04-08
OK, i have no idea how to do that log thing, sorry :(

I downloaded unetbootin and installed it. Then dowloaded the Jaunty jackalope iso file. I formated the USB memory stick and tried ext2,ext3,FAT16 and FAT 32 filesystems.

Then i opened unetbootin, punched in the file path and it copied over files to the memory stick. As far as i can see, it went without any glitches. Except for when trying to install ubuntu 9.04. 

I had to rename ISOLINUX to SYSLINUX when doing this process for Ubuntu 8, and then it worked. But that tactic does not appear to be working this case.

---

### Post by xelxel on 2009-04-08
Bump

---

### Post by Cerberus108 on 2009-04-17
Same problem with me, although it seems to happen only on my newer machine, an AMD/ATI one, with Phenom processor, and a 780 chipset by AMD. In my older computer, AMD Sempron, GeForce 4200, blah blah, it seems to work, with the same usb stick, and obviously with the same contents.

I have no clue why this happens, in my older computer it didn't tell me about that modules.dep thing..

---

