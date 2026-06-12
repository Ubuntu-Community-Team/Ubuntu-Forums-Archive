---
title: "Fresh install 9.10 help"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by wiredbeatbox on 2009-11-11
Hello,

I am looking for someone to help me get through installing Ubuntu 9.10 on my custom built machine with grub (Vista already installed). I have tried twice already and failed. i have been looking in many different forums, reading all the posts i can for the past 2 weeks now, still I can't figure this out. I'm not a computer noob so it shouldnt be a hassle to help me.

About the problems i have installing, i assume that it is a graphics driver problem, the whole install process worked fine, it installed, i get the the login screen (for first time log in), i can move the mouse around, i can hit the shut down button, but if i click the login button, it freezes.

My configuration: Asus Motherboard, (i dont remember the model, if it is needed i will get it)
AMD 64 X2 Dual Core Processor 3800+ 2.0Ghz
3 GB pc3200 RAM
Nvidia GeForce 7800 GT Graphics card (256mb dedicated)
2 hard drives, (250gb SATA with vista installed) (60gb PATA for ubuntu installation)
dynex usb 2.0 pci card with 2 external hard drives and magic jack plugged in.
linksys wireless g pci card
sony dvd/cd rw drive

so to not make this any longer, is this a plausible setup? I want to basically try ubuntu out, i dont want to use vista anymore but i have to since i am a developer and me and my company use microsoft technologies, so i have a windows 7 laptop that i use now, and am way happier with that than vista. i was interested in putting ubuntu on here to try it out because of all the apps you can get, and maybe start developing with it some day, but i also make music and do graphic design and video production on my spare time and things of this sort.

Sorry this is long, but it is kind of important to me, if anybody can help here through the forum, or have some time to spend with me on IM, i would greatly appreciate it and please let me know.

Thanks!!

Wired

---

### Post by PRC09 on 2009-11-11
Dont Know about the 2 external drives connected but Magic Jack has no support in Linux.Unplug it and the external drives and reboot and try without them plugged in.....

---

### Post by werdberd on 2009-11-11
If you haven't tried this already, you might want to boot from the Ubuntu CD and pick "Check CD for defects" just to make sure there's nothing wrong with the disc you burned.

---

### Post by davidryderuk on 2009-11-12
Hi,
A quick google search brought up the link shown below. 

[http://www.surlyjake.com/linux/karmic-install-cannot-login-gdm-freezes-nvidia/](http://www.surlyjake.com/linux/karmic-install-cannot-login-gdm-freezes-nvidia/)

This is supposed to fix your problem by installing the nvidia proprietary driver, which will replace the open source one running by default. 

Hope the command line isn't too bad, just make sure to double check everything you type for mistakes.

---

