---
title: "Ubuntu hanged at Grub"
date: 2008-09-15
forum: General Help
---

### Post by rsun on 2008-09-15
I've installed Ubuntu 8.04 on my Toshiba notebook. It's been running great until recently. It hanged at grub boot up and won't go any further.

HDD partition of my notebook:
80GB SATA Toshiba HDD.
40GB with Windows Vista
40GB with Ubuntu 8.04

I can still boot up Vista from Grub without any problem. However, when I tried to boot up Ubuntu normal or safe mode it simply hanged.

I've tried booting up with LiveCD trial. Same thing it hanged.

When try to re-install, it hanged at step 3 of 7. Therefore, it can't even run GParted to re-install Grub.

I installed the HDD in an USB enclosure, I was able to boot up with LiveCD. I can mount the Vista partition. However, when I tried to mount the Linux partition, it gave me a "can't access error".

I want to retrieve some file from my home folder before I zero-wipe the HDD. Any suggestion on how to gain access to the Linux partition?

---

### Post by Pro-reason on 2008-09-16
If your Ubuntu is installed on an ext2 or ext3 partition (which it is by default), you can install ext2 drivers on Windows and do some repairs from there.

---

### Post by caljohnsmith on 2008-09-16
From your Live CD, run an fsck on your Ubuntu partition and see if that helps:
```
sudo fsck /dev/sdXY
```
And replace sdXY with the Ubuntu partition. Let me know how it goes.

---

### Post by C.S.Cameron on 2008-09-16
You can reinstall grub using the Live CD.
Boot the Live CD and follow caljohnsmith,s instructions at:
[http://ubuntuforums.org/showthread.php?t=920993](http://ubuntuforums.org/showthread.php?t=920993)

---

### Post by rsun on 2008-09-16
> **C.S.Cameron said:**
> You can reinstall grub using the Live CD.
Boot the Live CD and follow caljohnsmith,s instructions at:
[http://ubuntuforums.org/showthread.php?t=920993](http://ubuntuforums.org/showthread.php?t=920993)

I tried to re-install GRUB from LiveCD as instructed from the threat above. It simply hanged at Step 3; partition the drive. It just hanged there. CD spinning stopped and I can't reboot, cancel, close. I had to hold down the Power button to shut it down.

---

### Post by Toxicity999 on 2008-09-16
This sounds like a kernel or lower level boot issue.... do you have any other ubuntu entries on grub to try? If not, short of difficult measures, I recommend backing anything up and reinstalling... ensure that your CD is proper with an integrity test first.

---

### Post by rsun on 2008-09-16
> **Toxicity999 said:**
> This sounds like a kernel or lower level boot issue.... do you have any other ubuntu entries on grub to try? If not, short of difficult measures, I recommend backing anything up and reinstalling... ensure that your CD is proper with an integrity test first.

Yes, I have other kernal versions, I've tried them all. I can't boot up any of the them normal or safe mode. The only system that I can boot up without hanging is Vista which is at the bottom of the list under others.

I suspect it's a corrupted boot sector issue, but I have no problem booting up Vista :confused:

How do I back it up if I can't even mount or access the partition?

From fdisk -l, I can see all the partitions are there, just can access the Linux partitions.

I'll try installing ext2 driver on Vista and see if I can access from there. Stay tune.

---

### Post by Toxicity999 on 2008-09-16
alright, so that makes me think your init system is shot, fixable. but honestly, if you have nothing that can't be backed up, just reinstall.

Just start a livecd, and mount it from there, the partitions should be viewable in nautilus under "Computer" a simple double click mounts them. as far as windows, if you want to back up from there, use what the previous poster was talking about.

---

### Post by rsun on 2008-09-17
> **Toxicity999 said:**
> alright, so that makes me think your init system is shot, fixable. but honestly, if you have nothing that can't be backed up, just reinstall.

Just start a livecd, and mount it from there, the partitions should be viewable in nautilus under "Computer" a simple double click mounts them. as far as windows, if you want to back up from there, use what the previous poster was talking about.

LiveCD can only boot up if I have the HDD in an USB enclosure therefore making it an USB-drive. When USB-drive is detected only NTFS partition can be mounted. I can't mount or access any Linux partition at all.

I can see the partitions using fdisk -l from LiveCD and only when the HDD is a USB-drive.

If Linux partition cannot be mounted, I can't back up the drive. So, back to square one.

---

### Post by Toxicity999 on 2008-09-17
A live cd can be booted even with no HD active/connected at all, that shouldn't matter, unless it's actively causing a boot issue in its current configuration.

---

### Post by rsun on 2008-09-17
> **Toxicity999 said:**
> A live cd can be booted even with no HD active/connected at all, that shouldn't matter, unless it's actively causing a boot issue in its current configuration.

Yes, absoulutely.
The only way I can boot up my computer with a LiveCD is to remove the corrupted HDD, put it in a USB enclosure and make it a USB-drive without the HDD in the computer.

I can then plug the USB-drive with the corrupted HDD after LiveCD boot up. It detected the USB-drive and displayed an USB-drive on the Desktop. When I opened the USB-drive, only the NTFS partition is mounted. I was not able to mount the Linux partitions, therefore, cannot backup.

---

