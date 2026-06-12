---
title: "BOOTING HElP"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by dharmil007 on 2009-10-08
i Have 2 OPERATING SYSTEMS.
1} Win 7
2} UBUNTU 9.04
& Recently i updated UBUNTU.

So now Whenver i start my PC, There it shows 6 CHOICES of OSes.
They are :
1} UBUNTU KERNEL 9.0.15
2} UBUNTU KERNEL 9.0.15 {recovery mode}
3} UBUNTU KERNEL 9.0.14
4} UBUNTU KERNEL 9.0.14 {recovery mode}
5} UBUNTU MEMTEST+
6} WIN 7.

i Dont want all these options.

i Just WANT 2 SIMLE THINGS. i.e 
1}  UBUNTU 
2} WIN 7.

How can i do this thing ?

Can anybody PlS. help me out

---

### Post by dstew on 2009-10-08
The easiest thing to do would be to edit /boot/grub/menu.lst and "comment out" the offending entries. From Ubuntu, press alt-F2 to get a command line, and do```
gksudo gedit /boot/grub/menu.lst
```Just put a # in front of the lines for the menu items you don't want to see. Or, you can remove the lines. After you make the changes, save the file and exit the editor. But, I would keep the recovery mode items in the menu.lst file in case you needed to use that mode in the future.

---

### Post by presence1960 on 2009-10-08
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-13-generic
[COLOR="Red"]
#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic[/COLOR]

title		Ubuntu 9.04, memtest86+
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1
```

there are my OSs in menu.lst
Note those in red are preceded by #
Those will not show in the GRUB menu if commented out with #

If I were you I would leave the most recent kernel and it's recovery mode along with windows. You never know when you will need recovery mode!

To edit menu.lst boot into Ubuntu , open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

scroll down to the OSs and place # before the ones you do not want to show in GRUB menu at boot like I did.

---

### Post by mikewhatever on 2009-10-08
You can edit the boot menu by hand or install startupmanager from the repositories. It may also be a good idea to remove some of the older kernels you don't need. Search for linux-image in Synaptic, just be careful not to remove the latest one.

---

### Post by presence1960 on 2009-10-08
LOL dstew

---

### Post by BigBadWoofer on 2009-10-22
Simple, direct, elegant. Found this after searching every keyword I could think of. Thanks!

---

