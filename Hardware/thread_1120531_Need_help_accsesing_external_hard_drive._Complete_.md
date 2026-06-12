---
title: "Need help accsesing external hard drive. Complete stranger to linux."
date: 2009-04-09
forum: Hardware
---

### Post by flyandspider on 2009-04-09
If anyone could help me access the files on my external harddrive that would be great. I have a sea gate 250GB external. It shows up at the places tab but when I click message "Cannot mount volume" appears. Need simple step instructions I am a complete noob when it comes to linux. THANKS.

---

### Post by coolcupid on 2009-04-09
Is it a NTFS filesystem?
use ntfs-3g

---

### Post by coffeecat on 2009-04-09
> **coolcupid said:**
> Is it a NTFS filesystem?
use ntfs-3g

**coolcupid**, Do you really think that's helpful to someone who describes themself as a 'complete noob'?

**flyandspider**, I've come across a few threads where people experience trouble mounting a Seagate USB drive which mounts OK in Windows. Every different make of USB drive I've ever plugged into Ubuntu has been mounted fine, so I suspect there may be some issue with the Seagate firmware that's interfering with the Linux USB driver. I don't have any direct experience because I have a severe allergy to all things Seagate. :wink:

Anyway, let's do some investigation. Normally, when you plug a USB drive in, an icon will appear on your desktop and a file browser window will open automatically. Have you got another USB drive (a flash stick would do fine), to test this to make sure this functionality isn't broken somehow?

Next, plug in your Seagate drive, and open a terminal (Applications > Accessories > Terminal). Type in this command:

```
sudo fdisk -l
```You'll be prompted for your password which won't be echoed to the screen. (Don't worry - it is going in.) Now post the output. You can copy and paste but the keyboard shortcut for copy in the terminal in Shift-Ctrl-C. And enclose the output in [noparse]```

```[/noparse] tags to preserve the formatting.

---

### Post by flyandspider on 2009-04-10
Disk /dev/sda: 3791 MB, 3791241216 bytes
255 heads, 63 sectors/track, 460 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x239c2192

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         433     3478041   83  Linux
/dev/sda2             434         460      216877+   5  Extended
/dev/sda5             434         460      216846   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

This is the message that shows up when I plug in the code you gave me

---

### Post by coffeecat on 2009-04-10
This is the way Linux sees your Seagate drive:

> **flyandspider said:**
> Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

It is formatted with the Windows NTFS filesystem, which fairly recent versions of Ubuntu should have no difficulty accessing. But clearly it is not being automounted otherwise both an icon and a file browser window would open on your desktop when you plug it in. Before we go on, two questions:

Which version of Ubuntu are you running, 8.04 or 8.10? Or another version?
Did you try the system with another USB (not Seagate) device? This is important to ensure that automounting is functional in your system.

These are two possible reasons why your drive is not being mounted:

- An issue with Seagate drives specifically. I don't know whether this is so, but there are a lot of threads like yours involving Seagate drives.

- The drive was not cleanly unmounted when you last used it with Windows. If Linux detects an unclean unmount in a NTFS filesystem, it will not mount it. This is to prevent filesystem damage.

Try these steps.

1 Plug the drive into the Ubuntu system and click on Places as you describe in your first post. You'll get the 'Cannot mount volume' message, but somewhere in that message window will be a 'more' or 'advanced' (or something - I'm going from memory here) little arrow. If you click that it will give you more details. Post the details. They are important.

2 Now plug the drive into a Windows system. Let Windows mount it. Now 'safely remove' it. Don't just pull the plug out. The procedure is different in XP and Vista. I'll leave that one to you.

3 Now plug it into your Ubuntu system. If, after 'safely removing' in Windows, it now mounts, then OK. If not, open a terminal (Applications > Accessories > Terminal), and type these two commands in:

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```You will be prompted for your password after the first command. It will not be echoed to the screen. It is going in. After the second command, one of two things will happen. Either the drive will be mounted and a file browser will open, or you will get an error message. If an error message, please post all of it.

---

