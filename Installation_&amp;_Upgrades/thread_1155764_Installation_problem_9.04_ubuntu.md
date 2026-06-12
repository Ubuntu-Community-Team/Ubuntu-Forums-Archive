---
title: "Installation problem 9.04 ubuntu"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Krupkee on 2009-05-11
hey, im a first time user of linux, busted my hard drive using our welder and just got a new one, thought id try something different.
 
anyways i bought a new usb key with live ubuntu 9.04 on it, got new hdd in, started it up, got to the install menu thing so i installed it , went through the settings questions etc..
 
got to the main screen with the dropdown things on the top. thought it was done but turned out was just frozen, waited about 20 minutes, nothing happened, so went ahead and rebooted the computer
 
now it went to the install menu again, thought it was weird so i tried installing it again, and now shows the error;
 
VFS cannot open root device "NULL" in block 104,1
 
and has a kernel panic so not sure what the problem is, im not so good with the programming code side of computers, just the hardware so any answers will have to be in simple terms, thanks in advance :)

---

### Post by Peter09 on 2009-05-11
Check that your hard drive is connected properly. Does it boot into the liveCD ok or is this error during the liveCD boot rather than the install?

---

### Post by Timpotten on 2009-05-11
I also had problems with 9.04  desktop(on upgrade).

First T flirted with Mint (it's nice, but has a special bootloader that ignores the DVD first BIOS, which took me days to overcome) and XP (horrible!) 

Eventually I loaded the LTS  8.04 desktop version, (Long term support - to April 2011) and apart from needing some 343-odd updates, this seems to be stable. 

9.04 caused me lots of aggro for days and was very slow. 8.04 with basic Gnome and some kde apps is my preference for now. to get both is easy: 

Assessories>terminal> 
sudo apt-get update; sudo apt-get install kubuntu-desktop

The new apps (Konsole etc) appear in the menus, and use Synaptic to tidy up or add more!

---

### Post by Krupkee on 2009-05-11
it is definitely during the installation, boots up fine
 
i tried 8.04 but power was cut off while it was doing the formatting of the drive and now it wont recognise it during the install :(
 
tried killdisk but wont let me run that without an OS i dont think
 
anyone else have ideas on how to "reset" my hard drive so i can start again?

---

### Post by Peter09 on 2009-05-11
Try running gparted from the LiveCD

---

### Post by Krupkee on 2009-05-11
cheers for that, run it, came up with "no devices detected" on bottom left of the gparted window thing. searched for this for a while but no real answers for it

---

