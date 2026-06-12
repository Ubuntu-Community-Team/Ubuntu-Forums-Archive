---
title: "[resolved] Ubuntu on Compaq Presario SR1103WM"
date: 2004-12-25
forum: Hardware &amp; Laptops
---

### Post by krrh on 2004-12-25
I've tried numerous boot commands, including failsafe boot, to get the installer CD and LiveCD to load on this machine. All attempts have failed, naming a kernel panic and idle task as the culprits during hardware detection.

The system also fails to boot the Fedora FC2 installer and Knoppix disks. 

Has anyone had luck with this system? It's a cheap buy from Wal-Mart that came preloaded with XP. Here is a [link](http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&tool=prodinfoCategory&lc=en&product=424182&dest_page=prodinfoCategory&cc=us&docname=c00063244) to the motherboard specs. I've not found much information online about this system running linux, but other HP and Compaq models using this motherboard appear successful.

Thanks for your help.

---

### Post by tweek888 on 2005-01-02
i have the same system ive also been unable to run linux or bsd on it. =(
i think its the hard drive personaly  o.0,

---

### Post by krrh on 2005-01-03
I found that my system would boot after removing my video card, which was an after-market upgrade.  Boot also required acpi=off added to the boot string.

However, I haven't been able to figure out how to boot with the video card still installed It's not an option for me to use only the onboard Intel video, which can't be disabled in BIOS or through jumpers.

Any ideas with this one?

---

### Post by sduba22 on 2006-03-21
I have the same machine at home to power my wife's daycare. In order to install Ubuntu and other Linux and UNix distros, there's a command to type at the install prompt. This won't work for all distros, and doesn't work for the Dapper Drake version. Type this after the install cd boots...

linux acpi=off

the hit return

This should start the installer.

---

