---
title: "USB flash drive won't mount"
date: 2014-01-02
forum: Hardware
---

### Post by temporos on 2014-01-02
I plugged my phone into the USB port to transfer some music. It didn't work. That was odd, because I've done it before with the same phone and Lubuntu installation (13.04). So, I tried my USB flash drive, and it wouldn't mount, either. I'm lost on this one. Can someone tell me what's going on?

Results of *fdisk -l*:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     1406975      703456   17  Hidden HPFS/NTFS

```

Results of *lsusb*:
```
Bus 001 Device 008: ID 08ec:0008 M-Systems Flash Disk Pioneers TravelDrive 2C
```

Results of *dmesg | tail*:
```
[92089.376668] sd 5:0:0:0: [sdb] Write Protect is off
[92089.376688] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[92089.377434] sd 5:0:0:0: [sdb] No Caching mode page found
[92089.377451] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[92089.382715] sd 5:0:0:0: [sdb] No Caching mode page found
[92089.382741] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[92089.384395]  sdb: sdb1
[92089.388946] sd 5:0:0:0: [sdb] No Caching mode page found
[92089.388972] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[92089.388996] sd 5:0:0:0: [sdb] Attached SCSI removable disk
```

---

### Post by mikewhatever on 2014-01-03
Nothing seems to be out of the ordinary. What exactly do you mean by "didn't work" and "wouldn't mount"?
Any errors?

---

### Post by temporos on 2014-01-03
Well, I remember when I plugged these devices in before, they would automatically mount and then appear on my desktop. Now, nothing happens when I plug them in. There's no icon on the desktop, the file manager doesn't ask what to do with them, and there isn't anything in */media/<user>*. Trying to manually mount does this...

```
<user>@<host>:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/<user>
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

---

### Post by temporos on 2014-01-05
Anyone? I need this USB drive functionality, since it's the only way I have to backup files and install the latest versions of Ubuntu. None of these devices have changed since I last used them on this same system. Lubuntu has simply stopped recognizing them.

---

### Post by temporos on 2014-01-09
I can't back up my files or install the latest versions of Ubuntu without USB drives. Can anyone help. None of the articles I've found have addressed this specific issue.

---

### Post by adrian89 on 2014-01-10
Does any of the following applications detect the usb devices: Gnome disk manager, Gparted, Gsmartcontrol?
You can get them from the software center.

---

### Post by temporos on 2014-01-10
Fdisk will detect only a few devices, and will mount none of them.

Gnome disk manager will detect all but one device, and will mount only a few of them.

Gparted does the same as Gnome disk manager.

It seems the devices that will mount are completely random. They'll all mount fine on my sister's Windows 7 machine.

The device that isn't detected by any of them is my phone (T-mobile Concord). The phone will respond to being plugged in, but nothing happens on the linux end. I've noticed that fdisk and Gparted take a *long* time to finish if I have the phone plugged into the USB port. That same phone mounts just fine on my sister's Windows machine.

I don't get it. Some devices will mount, but I have to always do it manually, and I never know which ones those are. My Android phone can't be detected at all&#8212;which is odd, considering it's a Linux device.

---

### Post by adrian89 on 2014-01-12
I've tested 5 same android tablet models with android 4.0.4 and 3 of them worked when hooked up to my laptop while 2 didn't both on Ubuntu and Windows 7(they were just recharging) .

It might be that the usb is not working properly. Look at my post [http://ubuntuforums.org/showthread.php?t=2198633](http://ubuntuforums.org/showthread.php?t=2198633) , this is why I believe it is a USB issue(I had it from rack, and the symptoms where similar to yours) and seeing that the devices work on your sister's machine.

You can try and plugin a live cd with a different distro or and plug in the devices and see if they are detected.If you have the same issue try your sister's machine booted up with the same live cd/usb.

I would recommend using a live cd/usb of ubuntu 12.04(or other lts derivate) because i believe it should be the most reliable since it is a LTS but either distro should be fine.If then it is ok, then you must consider reinstalling your current OS.

One more thing when you installed lubuntu 13.04, it was a clean install?Or a upgrade?

---

### Post by sudodus on 2014-01-12
I suggest that you start with *adrian89*'s tips.

Are you able to mount devices manually? I mean devices that are detected by for example fdisk.

Try something like this

```
sudo mount /dev/sdb1 /mnt
```

A problem might be that the directory that you call **[FONT=courier new]/media/<user>[/FONT]** has bad permissions or the wrong user. You can also try
```

sudo chmod ugo+rwx /media/<user>
```

---

