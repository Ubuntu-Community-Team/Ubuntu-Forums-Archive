---
title: "Why is hdd sdc instead of sda?"
date: 2010-09-29
forum: Hardware
---

### Post by CLCressman on 2010-09-29
I have 3 hdds, 1 sata and 2 pata. I am dual booting XP and Ubuntu 10.4. I updated grub2 to add nomodeset, and XP refused to come out of hibernation. I tried some Windows utilities to see if I could find a solution.

Now when I boot from LiveUSB 10.4.1, the hdd that was sda is now sdc. I would like some pointers on how to look for a solution, or simply a fix would be fine.

Thanks in advance.

---

### Post by robsoles on 2010-09-29
Have you unplugged and plugged drives back in? You may have crossed cables and plugged them in in a different order.

Have you fiddled with boot-order in BIOS? Some BIOS shift the drives around in terms of mapping to manage boot-order.

I don't know of functionality to reassign the drives (at that level) once the system has booted into OS.

---

### Post by CLCressman on 2010-09-30
The only disk that I plugged or unplugged is a flash drive that I put the LiveUSB on.

If I boot to BIOS setup with the usb drive plugged in it comes up in the hdd group to boot from. The change I made to BIOS was to move the usb drive to the top of the list. I removed the usb drive and double checked the the order of my BIOS hdd group and it is exactly the original order.

I just now burned Super Grub2 Disk to a cd. I booted from the cd and chose to detect grub2 install. It found my normal grub menu and I booted Ubuntu from the hdd. I did update-grub and it found my XP installed on sdc. I tried rebooting without the cd and it would not boot. I rebooted with the cd, chose to detect grub2 install, from grub on hdd chose XP on sdc, XP came out of hibernation. :)

I used Super Grub2 Disk to boot into Ubuntu on hdd and did grub-install. Now everything works as before, except grub says XP is on sdc instead of sda.

How does Ubuntu determine which disk is sda, sdb, and sdc?

---

### Post by Grenage on 2010-09-30
> **CLCressman said:**
> How does Ubuntu determine which disk is sda, sdb, and sdc?

I had always believed it was order of initialisation.  That's why it's recommended that one uses UUIDs in fstab, if the drive is permanent.

---

### Post by CLCressman on 2010-09-30
I just had sda swapped with sdc, and I would like to know why.

---

### Post by SlugSlug on 2010-09-30
which ever is picked up first by the BIOS is sda  second sdb etc

boot up prioty can change this

---

### Post by Grenage on 2010-09-30
Double-post [http://ubuntuforums.org/showthread.php?t=1584678](http://ubuntuforums.org/showthread.php?t=1584678).

Reported for merge.

---

### Post by s.fox on 2010-09-30
Threads Merged.  Please only create one thread detailing your problem. Thank you.

---

### Post by CLCressman on 2010-09-30
I am sorry for the double post. I thought maybe I had asked the wrong question in the wrong forum.

I guess maybe I should put it this way. Why would a simple update-grub to add nomodeset change the order of the drives? Grub was somehow messed up because that drive failed to boot. Consequently the second drive in the list was attempting to boot, but it was XP originally installed in another computer and was not successful. After I reinstalled grub everything works, but somehow sda swapped with sdc in grub and Ubuntu. My /etc/fstab file:```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7d8b2828-c87c-47a6-a0a6-494e164f6181 /               ext4    errors=remount-ro 0       1
# /Win_C was on /dev/sda1 during installation
UUID=22087855087829C5 /Win_C          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /Win_F was on /dev/sdb1 during installation
UUID=48F05363F05355F2 /Win_F          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /Win_H was on /dev/sdb6 during installation
UUID=A4B8584FB85821DA /Win_H          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /Win_I was on /dev/sdb7 during installation
UUID=D0645BC4645BABCA /Win_I          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=3a15ab91-6588-456a-87d8-617685869920 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```I will do some research on fstab and see if I can change it back to what it was.

Thanks for the pointers. I did not know how search for the answer without an intelligent question.

---

### Post by sisco311 on 2010-09-30
Device names (sd#*) are assigned at boot time. udev loads kernel modules by utilizing [coding parallelism]("http://en.wikipedia.org/wiki/Parallel_computing") to provide a potential performance advantage versus loading these modules serially, so the kernel usually just assigns unpredictable device names based on the order of discovery. Meaningful symlinks provide a way to reliably identify devices based on their properties or current configuration (i.e. UUID or LABEL).

As you can see in your fstab, the partitions are identified based on their UUIDs. The UUID of the partition will remain the same until you manually change it or reformat the partition. 

For more info, take a look at:
[http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev)
[uhelp]community/UsingUUID[/uhelp]
The Arch & Gentoo wiki pages are usually good:
[http://wiki.archlinux.org/index.php/Udev](http://wiki.archlinux.org/index.php/Udev)
[http://www.gentoo.org/doc/en/udev-guide.xml](http://www.gentoo.org/doc/en/udev-guide.xml)

---

