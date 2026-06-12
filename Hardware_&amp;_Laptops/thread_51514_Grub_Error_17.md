---
title: "Grub Error 17"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by sameedha on 2005-07-24
how do you solve  grub error 17 problem?i have loaded ubuntu 5.04 on ibm thinkpad r40  which has win xp pofessional loaded on it.after installing ubuntu on a free partition of 3.2 gb  grub hangs at stage 1.5 with error 17. live cd works fine .

---

### Post by dwbird on 2005-07-24
Install Windows First then install Ubuntu

---

### Post by sameedha on 2005-07-24
windows was already installed. now i can not access any of the os.

---

### Post by eeried on 2005-07-24
Hello sameedha,

Though I don't know why you got that error in your particular, I may be able to help youI to fix it, since I had the same error after experimenting with partitioning using qtparted.

Error 17 (and 15) mean Grub can't find the boot partition.

The best thing to do since you can't boot (quite naturally) is to get a Linux Live CD (Ubuntu or Knoppix will do fine) and boot the CD, and wait until you get the desktop (gnome or KDE).

First you can type : sudo fdisk -l to see your partition table (your partitions)

Then you need to edit the file /boot/grub/menu.list as sudo or root. 

Mount the partition where ubuntu is installed, make it writable (right click and see the contextual menu in KDE).

Open a new console and type sudo gedit /boot/grub/menu.list

You must make sure the  lines starting with root and kernel are correct, that is they reflect your partition table:
```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

root		(hd0,1) : grub counts from 0; so 1 means hda2 as you see in the next line: here change 1 to the number hda? on which ubuntu is installed

kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet  (here change the number to reflect the right partition.

If Windows is in hda1 just one C: partition), Ubuntu is probably installed on hda3 (if the swap is on hda2!)

Let us know how you manage!

BTW while you're at it you can aslo make the splash screen less black and white. This is so easy.

Go up the same file and find 
```
# Pretty colours
#color cyan/blue white/blue

```
Uncomment the line #color cyan/blue white/blue, that is, delete the hash sign #.

Save the file in the same place. Choose "reboot", remove the Live-cd before rebooting. on reboot things should be okay and nicely blue and white.

Please report on the outcome. Hope it works with you as it worked with me.
\\:D/

---

### Post by sameedha on 2005-07-28
still status quo ,unable to boot.grub menu list is as you suggested

---

### Post by sameedha on 2005-08-12
reinstalling windows followed by reinstalling ubuntu solved the problem  (dwbird had already    suggested this )

---

