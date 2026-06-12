---
title: "New hardware(motherboard, processor, memory) installed"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by ifeelcool.com on 2006-03-29
Hello, i have installed new hardware(motherboard, processor, memory) and now ubuntu breezy isn't booting. After splash screen i get the console.
How do i restore my ubuntu installation? Without loosing my current setup(software, documents, images)? 

**Old configuration:**
asus a7v, amd duron 650, sdram 133mhz 256Mb

**New configuration:**
asus a7a266, amd duron 900, ddr 266mhz 1Gb

Any help would be appriciated!

---

### Post by ifeelcool.com on 2006-04-05
Ok, self helping .........


I have been looking around while trying to boot my ubuntu system with new hardware. The following problem has occured: After grub bootloader it is trying to load de linux boot image/modules from hde4, but because of the new motherboard this is not hde4 any more. Instead it is hda4!! 
Is there any way to change this, so the system will try and boot from hda4 instead of hde4?

Any help would be appreciated................

---

### Post by Zeroedout on 2006-04-06
If that is infact the only problem, press esacape at the grub loading screen, highlight your kernel and press "e" on the keyboard. you'll get to the commands grub uses to boot. Change those as needed. If you need further help with grub, look up on the net, theirs a wealth of info, or post back.

---

### Post by ifeelcool.com on 2006-04-06
In fact i have booted with a linux rescue system cd, used the *command: **fdisk*** to find out the new partition settings for the motherboard. It was changed from /dev/hde to /dev/hda.
So i had to replace /dev/hde in /dev/hda in de following places:
I started mounting (mount /dev/hda) and edited in /boot/grub/diskmap.xxx and changed the /dev/hde to /dev/hda. And edited /boot/grub/menu.lst changed /dev/hde1-4 to /dev/hda1-4.

I also changed the settings in /etc/fstab replaced all the /dev/hde1-4 with /dev/hda1-4.

Ubuntu then booted normal!

After i did a full apt dist-upgrade to dapper drake, the grub entries where changed back to /dev/hde instead of /dev/hda

**So where can i find the default settings so i can change /dev/hde to /dev/hda for ever?**

---

### Post by Zeroedout on 2006-04-07
[quote=ifeelcool.com]In fact i have booted with a linux rescue system cd, used the *command: **fdisk*** to find out the new partition settings for the motherboard. It was changed from /dev/hde to /dev/hda.
So i had to replace /dev/hde in /dev/hda in de following places:
I started mounting (mount /dev/hda) and edited in /boot/grub/diskmap.xxx and changed the /dev/hde to /dev/hda. And edited /boot/grub/menu.lst changed /dev/hde1-4 to /dev/hda1-4.

I also changed the settings in /etc/fstab replaced all the /dev/hde1-4 with /dev/hda1-4.

Ubuntu then booted normal!

After i did a full apt dist-upgrade to dapper drake, the grub entries where changed back to /dev/hde instead of /dev/hda

**So where can i find the default settings so i can change /dev/hde to /dev/hda for ever?**[/quote]

Heh, had no idea that could be done, i'll be sure to keep it in mind, really cool. This is a complet guess, but could it perhaps be done with ```
sudo base-config
```? I would think this is where it could be changed, but, I could be wrong

---

### Post by ifeelcool.com on 2006-04-13
Hello Zeroedout,

I first tried to run base-config, it wasn't installed. So i tried to install this by synaptic. Synaptic wants to uninstall a lot off packages to try and install base-config so i don't think using base-config is an option!

Do you have more options?

---

