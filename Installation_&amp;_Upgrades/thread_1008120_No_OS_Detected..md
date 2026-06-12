---
title: "No OS Detected."
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by Will Murray on 2008-12-11
I am installing the latest version on my laptop.

The installation seems to go smoothly, I am using the whole hard drive on the laptop as the system drive. After installion finishes ubuntu starts (I am assuming it is running straight from the install disc). After removing the disk and restarting the laptop, it claims I have No OS.

SATA 80GB HDD
GeForce Go 7400
Intel(R) Core(TM) 2 CPU T5500 @ 1,6 GHz
1 Gb RAM ( 2 512mb sticks)

BIOS Version: Q3A24

Will update with other hardware stats when I find them.


Thank you in advance for any help.

---

### Post by pietjanjaap on 2008-12-11
Check your bios if you boot from your harddisk?

Wenn booting you will see grub, press "esc", you will come in a menu(grub), then press "e" to change the harddisk number.(the first ubuntu)
hd0,0
hd0,1
hd0,2
hd0,3
hd1,0
hd1,1
etc, first number is harddisk number and second number is partition number.
After changing the number then press "b" to boot, if it does not work try a different number.
It is possible that because of usb things connected that the number is wrong.

If you do not have grub, then install with "super grub" grub again, this is a bootcd you can download.

---

### Post by Will Murray on 2008-12-14
Thank you for the help but I am still having trouble.

I have no external usb devices connected, the only boot device is my system drive. 

I used super grub but I only seem to get errors with that, is it possible that my hardware is not supported? thanks for any help in advance.

---

### Post by bulldog on 2008-12-14
Boot in to the live cd,open a terminal,and perform ```
sudo fdisk -lu
``` and copy the output to the forum please.

---

### Post by puneetsoni on 2008-12-15
I am facing the same problem.
i have compaq v3000 laptop and i want to install ibex. 
After a clean install i get no options in grub menu except for memtest86+ option which starts automatically whenever i restart the computer setting to boot from hard disk.
plz help me i am a newbie to linux and it is my first experience with ubuntu.

---

### Post by puneetsoni on 2008-12-15
on giving command 
sudo fdisk -lu
i get output

Disk /dev/sda: 80.0GB 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors units = sectors of 1* 512 = 512 bytes
disk identifiers: 0x37793778

Device  Boot    Start      End     Blocks     Id    System
/dev/sd1   *    63     153340424  76670181   83     Linux
/dev/sd2    153340425   156296384  1477980     5    Extended
/dev/sda5  153340488    156296384  1477948+    82   Linux Swap/Solaris

---

### Post by caljohnsmith on 2008-12-15
Puneetsoni, how about booting your Live CD, downloading the attached "boot_info7.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info7.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will help clarify your setup and what your problem might be.

---

