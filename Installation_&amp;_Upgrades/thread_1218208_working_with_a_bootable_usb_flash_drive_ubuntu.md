---
title: "working with a bootable usb flash drive ubuntu"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by xeth on 2009-07-20
Hi guys,

I finally got the bootable USB to work. It boots from the usb without any problems.

I have a 16gb flash drive and had it partitioned at 4gb ext4 primary and 12gb fat32 logical.

Is there a need to partition both of them as primary?

My problem is that I can't mount the 12gb fat32. There is a message "Unable to mount location - can't mount file.

using fdisk -l

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 486 3903763+ 83 Linux
/dev/sdd2 487 1988 12064815 5 Extended
/dev/sdd5 487 1988 12064783+ b W95 FAT32

another question is, when I paritioned the fat32, is there a difference when I choose /DOS or /WINDOWS?

Another problem I have is when using my windows vista, my dual monitors work ( my second monitor is a TV connected by S- Video )

When in Ubuntu, there is no option to configure it in the display, preferences. I'm thinking it's not supported

Thanks

---

### Post by dstew on 2009-07-20
Do you have a Linux system on the USB stick? I assume so. Is the fdisk output from the USB-booted system?

How are you trying to mount the FAT32 partition? It should not matter to Linux whether the partition is primary or logical. I am not sure what you mean by /DOS or /WINDOWS. How did you partition the flash drive?

Your dual-monitors may or may not be supported in Ubuntu. I can't get my S-video output to work in Ubuntu, but it works fine in Windows. It is a problem with the display drivers. Check in System --> Administration --> Hardware Drivers to see if you can install a third-party driver for your display adapter. You might need to enable the Universe or Multiverse repository in System --> Administration --> Software Sources. What kind of display adapter do you have? Check it with **lspci**.

---

### Post by xeth on 2009-07-20
The usb was formatted and partitioned by ubuntu.

yes, fdisk was from the usb.

the usb should be mounted by start up, but  doesn't show on the desktop. it does show on the Computers as USB. When I double click it the error pops up.

The /DOS or /WINDOWS is the mount point choice during the partition setup of fat32.

The flash drive was partitioned as

4GB - EXT4, Primary, Mount Point - "/".
12GB - FAT32, Logical, Mount Point - "Windows".

Then it was installed.

I'm thinking maybe because since it is partitioned, when ubuntu booted it already mounted the 4gb and can access the 4gb partition of Ubuntu. It can't mount the 12gb fat32 because it already mounted itself?

Can you mount a device with multiple partitions and still see all of them?

I'll check the display drivers.

---

### Post by xeth on 2009-07-20
ok, i tried a sudo mount /dev/sdd5

the result was:

mount: /dev/sdd5 already mounted or /windows busy
mount: according to mtab, /dev/sdd5 is already mounted on /windows

in the file browser when I type in the address bar /windows I can see the partition.

So why is it "windows" and why can't I see it mounted on the desktop that I can double click.

commonsense tells me because the  mount point during partition was Windows.

---

### Post by dstew on 2009-07-21
When you chose the /windows mount point, you made it so that it would not appear on the desktop. Only things mounted in the /media folder appear on the desktop. You should have chosen /media/windows as the mount point.

However, that is easy to fix. First, create the mountpoint /media/windows:```
sudo mkdir /media/windows
```Then, edit the  /etc/fstab file to change the automatic mount command. Find the line where the device /dev/sdd5 is mounted to /windows, and just edit it so that the mount point becomes /media/windows. Reboot, and now the partition /dev/sdd5 should appear on your desktop.> Can you mount a device with multiple partitions and still see all of them?In Linux, a "device" usually means a disk *partition* that contains a file system, not the whole disk. So, if you mean can Linux mount multiple partitions, the answer is yes. Each partition must have its own mount point. You cannot mount a "disk" in Linux. The confusion has arisen because in Windows, partitions are called "disks". That is, people say "the C: drive", or "the C: disk", but really they should say "the C: partition". The Linux notation is more precise.

---

