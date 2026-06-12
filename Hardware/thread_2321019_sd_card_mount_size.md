---
title: "sd card mount size"
date: 2016-04-19
forum: Hardware
---

### Post by netopalis45 on 2016-04-19
I purchased a 64 GB mini SD card for a Raspberry Pi install but when I mount it it shows that it is only 1 MB. I have formatted it using a GoPro camera and a Windows computer but it still only shows that it is 1 MB. Is my card messed up?

---

### Post by sudodus on 2016-04-19
Please run the following commands in a wide window of *Ubuntu*, when the card is plugged in, and post the output within [noparse]```
tags
```[/noparse]in a reply.

```
sudo parted -ls
sudo lsblk -fm
```

---

### Post by netopalis45 on 2016-04-19
Thanks for the reply. Here is the screenshot

---

### Post by frostschutz on 2016-04-19
Please post text as text (in codetags) or use paste.ubuntu.com and link it here. Your screenshot is barely readable...

It seems your device name is /dev/sde, what do you get for `sudo blockdev --getsize64 /dev/sde`?

Sometimes cards go bad and are not detected properly anymore. As for the Raspberry Pi I've heard it can destroy cards if it suddenly loses power while using the card. In that case you just have to get a new card, nothing for it...

---

### Post by sudodus on 2016-04-19
As *frostschutz* indicates, your card might be recognized by /dev/sde, but we don't know yet, and there might be serious problems with it. SD cards are mass-produced and while most of them are good, some of them are bad from the manufacturer. And they are rather easy to damage. But there might be a software problem (bad partition table and/or file system).

I suggest that you try to wipe the first megabyte (remove data, that might disturb reading it), and create a fresh file system with [mkusb](https://help.ubuntu.com/community/mkusb).

See the following link, [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe). Use the menu item "**Standard: create MSDOS partition table with FAT32 partition**"

See also the following link for more details, [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

You can also try to format it again in a computer with Windows. This time make sure you select a **FAT32** file system, and nothing else.

---

