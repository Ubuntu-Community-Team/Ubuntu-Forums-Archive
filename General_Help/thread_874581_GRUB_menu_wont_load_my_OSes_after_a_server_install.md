---
title: "GRUB menu wont load my OSes after a server install"
date: 2008-07-30
forum: General Help
---

### Post by zeroblitzt on 2008-07-30
Hi everybody.

I took a break from my computer - probably because my motherboard had died and I didnt get a replacement for 2 months! - and I recently came back to my Ubuntu installation when I got my mobo replacement. I found, besides the massive amount of updates, that a lot of my hardware wasn't recognized anymore, due to the new motherboard. I struggled for a bit to get my video card working again, but for some reason the driver wouldn't "stick", so I decided to start over. I chose to do this by getting the Ubuntu server edition, starting with a command line and building up from there.

Unfortunately, after I got my system installed, I found I cant boot it through Grub for some reason! Luckily, I have Super Grub Disc, so I could get in through there by manually booting, but for some reason my attempts to run "update-grub" in terminal, and trying to fix it through Super Grub Disc have failed. It still gives me the problem of "not being able to load the OS", or for my Windows installation, the "file is not an executable".

My questions are: has anyone ever had an issue like this, and is there an easy fix? Alternately, could I use my regular Ubuntu desktop CD, install it, and then strip down all the components and start from scratch like I want to (because I know my Ubuntu Desktop CD works)?


Sorry if any of this is confusing; I'm really tired, its 3:37AM where I am and I've been trying to fix this for a while now.

Thanks in advance for any help from a fellow Ubuntu-er.

---

### Post by caljohnsmith on 2008-07-30
It sounds like it could be a simple problem with your Grub's menu.lst file. Please post the output of:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by zeroblitzt on 2008-07-30
```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=ee707e6d-b950-4feb-b80b-2365b28c11a9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=ee707e6d-b950-4feb-b80b-2365b28c11a9 ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

Everything else except the timeout is commented out.

---

### Post by caljohnsmith on 2008-07-30
OK, but I think you forgot to post the output of:
```
sudo fdisk -l
```
:)

---

### Post by zeroblitzt on 2008-07-30
My bad, didnt see that you asked for that before.

```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033d5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19331   155276226   83  Linux
/dev/sda2           19332       19457     1012095   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c5a9c5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17636   141661138+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xf2a16280

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      155058    78149200+   7  HPFS/NTFS

```

---

### Post by caljohnsmith on 2008-07-30
According to fdisk, you have NTFS partitions on both your sdb and sdc drives. So since your Windows doesn't boot when Grub points to (hd1,0) which would be your sdb drive, try your sdc drive:
```
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```
I believe that's the correct syntax--I don't have three HDDs, so I don't have to worry about mapping them like that to get Windows to run.

But before modifying your menu.lst, I would first try manually entering the changes above in Grub at boot time. Just select the Windows entry and hit "e" when you get the Grub's menu at startup, and follow the directions to modify it. Basically you select the line "root (hd1,0)", hit "e" to edit that, change it to (hd2,0), and hit return. Do the same for the map statements, and once everything looks like it should, hit "b" to try and boot it. If it works, you can make the changes permanent by putting them in your menu.lst.

I would recommend doing the same to boot your Ubuntu partition. Select the "Ubuntu 8.04.1, kernel 2.6.24-19-server" entry in Grub at startup, hit "e" to modify it; the "root (hd0,0)" should be correct according to your fdisk output, so maybe there's a problem with the kernel and initrd lines. You can use TAB completion to help figure out how to modify them. In other words, I would partially delete the file in the kernel line to read "/boot/vmlinuz-" and then hit TAB to see which kernels are available.

Give it a try and let me know of any problems, and please be specific with errors and such.

---

### Post by zeroblitzt on 2008-07-30
My SDC drive is storage, and doesn't have anything to do with booting my Windows drive. I will try the Live Grub editing you suggested, however.

Edit: OK, I think I found the problem. I think when Ubuntu installed GRUB to the MBR, for some reason it switched my drives in the boot menu. I changed my Ubuntu selection to hd(1,0) in the live bootup edit, and it booted right into my Ubuntu system. I'm going to edit the file now and switch them to what SHOULD be right, and hopefully I'll be able to get into both Ubuntu and Windows.

---

### Post by caljohnsmith on 2008-07-30
I've heard of that problem being caused by Grub not seeing the order of HDDs the same as BIOS does. Your workaround will certainly do the trick, but I just thought I would mention that you can edit your /boot/grub/devices.map file so that it agrees with how BIOS perceives the order of your HDDs. That way your menu.lst might seem a bit more logical. :)

---

### Post by zeroblitzt on 2008-07-30
Wow, I never knew that. That would make more sense. Thanks!

---

