---
title: "Install on external hard drive - Ubuntu will not boot."
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by phiabell on 2009-04-24
*To start - I am a total linux newbie - I have spent the last couple of days trying to get a dual boot working with xp on my internal hard drive and ubuntu on my external, I tried 8.04 and Linux Mint and these kinda worked but had no support for my wireless card, I thought I would go with the most recent Ubuntu since I had heard it should support my wireless out of the box.*

Now I have installed Jaunty on my external hard drive, during install I put the boot loader onto the external since not doing that last time seemed to mess it up - but now when I restart the computer, with the BIOS set to boot from the USB HDD first, it just goes straight into XP with no menu, no black screen or grub error just boot as if Ubuntu was not there. Can anyone help me get Ubuntu booting? If it came to it, I really wouldnt be fussed if I had to plug and unplug the hard drive when I wanted to change between Ubuntu and XP, as long as they both work!

Thanks

---

### Post by phiabell on 2009-04-24
Apologies if I have not included enough info, I am not sure what else is relevant to the problem.

---

### Post by 5nak3 on 2009-04-24
This may or may not be relevant, but maybe if you post the make and model of your external hdd, bios / motherboard maybe it could help lead to a solution quicker.

---Edit---

I'm probably not going to be able to help you as I am not too hot with linux, and usually require a lot of help especially when it comes to terminal, but I thought just to give you a little hint as to what else might be of use

---

### Post by phiabell on 2009-04-24
Well thank you for popping your head round anyway! Extra info (from Belarc)

System Model
Acer Extensa 5220 0100
System Serial Number: LXE870Y2618091F0112000

Main Circuit Board 
Board: Acer Columbia Rev
Serial Number: LXE870Y2618091F0112000
Bus Clock: 133 megahertz
BIOS: Phoenix Technologies LTD V1.32 02/01/2008

Drives
HTS54106 0G9AT00 USB Device [Hard drive] (60.01 GB) -- drive 1 (External)
TOSHIBA MK8046GSX [Hard drive] (80.02 GB) -- drive 0

---

### Post by Dan_Dranath999 on 2009-04-24
I'm trying to make an USB external Hard Disk installation with a similar (or maybe it's the same model) Toshiba 2.5" 80Gb drive!

The Jaunty cd, installed without issues, but can't boot it on my desktop or my laptop...

I have a custom desktop with a **MSI K8T Neo2-f motherboard** which has a boot menu, and recognizes the Toshiba Disk, but fails to boot. (just keeps going to the internal HD)

I tried the same on a **toshiba satellite a110-179** and this one gave more info: it said the partition table was incorrect.

---

### Post by phiabell on 2009-04-24
Hi Dan

If you really are having the same problem as me, check out this thread.

[http://www.linuxforums.org/forum/ubuntu-help/145306-install-external-hard-drive-ubuntu-will-not-boot-help-please.html#post689583](http://www.linuxforums.org/forum/ubuntu-help/145306-install-external-hard-drive-ubuntu-will-not-boot-help-please.html#post689583)

I got a quick answer there.

You probably know how to put GRUB on the mbr but in case you don't just google it and you will find guides, its a couple simple steps.

Hope it works for you, too.

---

### Post by Dan_Dranath999 on 2009-04-25
Thanx.

Yeah, i thought it would be GRUB giving me the hard time. So i re-installed and checked GRUB to install in the proper drive...(something i have done before but not this time)

Still no luck on my desktop. 
I'm gonna check that thread, now.

---

