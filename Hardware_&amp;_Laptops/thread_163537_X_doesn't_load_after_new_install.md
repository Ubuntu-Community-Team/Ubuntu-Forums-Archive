---
title: "X doesn't load after new install"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by Dundjee on 2006-04-21
Hey everyone, 

I've got a question about the installation of Ubuntu Breezy Badger.
I downloaded the cd iso of ubuntu for amd 64, and installed it to a separate HD on my pc. 
The install seemed to be going just fine, and on a given point it asked me what resolutions i wanted to be able to apply. 
800*600 to 1024*768 was already selected, but i wanted to choose 1280*1024 too .. and I think by just hitting enter, it didn't select it and just go on. 

After a reboot, ubuntu started normally and every check was ok, after which it wanted to load the x server and then I got the message that it couldn't load. The log mentioned " no device " I think.
I can't post the log right now, but if necessary, I'll do so later on :)

Could it be because it can't find the right screen resolution ? Or rather smth else...

I would like to try to fix it before doing a reinstall .. 
If I get it to work then, it's much more satisfying :)

Thnx for the help... 

D.

My case: 

DFI Lanparty UT NF4 DR-Expert
AMD Opteron 170 Dual Core CPU
OCZ 2 * 512MB Ultra Low Latency Ram
Artic cooling Freezer Pro 46
XFX GeForce 7900 GT 256 MB Extreme Edition
2 * 160GB SATAII HD
1 * 40 GB ATA HD (Linux)
OCZ Modstream 520 Watt
Thermaltake Kandalf Black

---

### Post by dermotti on 2006-04-21
try **sudo dpkg-reconfigure xserver-xorg** and select the **vesa** driver.

Then reboot or restart X

---

### Post by Dundjee on 2006-04-21
Ok I'll try that when I get home and let you know how it goes .. 

Other than that .. do u think my hardware I listed below is all supported ? :)

I installed ubuntu before on 32bit P4 system and it worked like a jiffy...
I'm kinda won for ubuntu. I tried a few others before, but keep gettin' back ;)

---

