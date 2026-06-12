---
title: "GRUB on root parititon"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by nucleuskore on 2009-11-05
Hi All
I use GAG as my primary bootloader (MBR)
My partitions are as follows

/dev/sda1 - win ntfs
/dev/sda2 - win ntfs
/dev/sda5 - swap
/dev/sda6 - /
/dev/sda7 - /home

I specified that GRUB be installed to /dev/sda6 in the Advanced options. The grub-install ran at the end of the install process, but GAG gives me an invalid bootsector error when attempting to boot the partition.

I tried deleting the GAG entry and adding a new one, that did not work too.

I then booted with the live cd, mounted /dev/sda6 to /mnt and did a grub-install with the parameter --root-directory=/mnt /dev/sda6

Grub is refusing to install with the following error
Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
error: Cannot read `/boot/grub/core.img' correctly

Any help will be much appreciated
Thanks !

---

### Post by oldfred on 2009-11-05
I am using chainbooting from legacy grub to several installs of linux. When I installed Karmic alpha I installed grub2 as you did to the partition and got the same message. It has worked fine for me. 

It also gives the same message on every update since it runs the grub update command several times during the update.

The developer does not recommend this for some reason, but I also found others who say there is nothing wrong with blocklists. It has something to do with jumping to fixed locations that if you reconfigure your system the jump to may change, but many other system changes also seem to cause other problems so I plan to stay with Grub2 in the partition until they fix it or it breaks so it does not work.

---

### Post by nucleuskore on 2009-11-05
So you have legacy GRUB on your MBR which points to your GRUB2 on your root? I could do that but I'm dual booting with Vista, and legacy GRUB an Vista loader don't work well together.

---

### Post by nucleuskore on 2009-11-05
**Update:** I followed this howto

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

and installed grub **without errors**.

I am however still not able to boot the partition using GAG, getting same error, invalid boot sector.

---

### Post by nucleuskore on 2009-11-05
I finally got a workaround for the above problem. I installed lilo to /dev/sda6 by slightly modifying the above howto. It's not as good as grub but at least it boots! I am outlining the steps for the benifit of other GAG users:
[list][*] Install Ubuntu with bootloader in your root partition (/dev/sda6 in my case)

[*]After install boot into a live Ubuntu session from the cd (Try Ubuntu without making any changes to the computer)

[*]Click Applications->Accessories->Terminal
[*]**sudo fdisk -l**
Here is mine
-----------------------------------------------------------------------
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd09c4d14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25220   202579618+   7  HPFS/NTFS
/dev/sda2           38097       38913     6562080    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           25221       38096   103426470    5  Extended
/dev/sda5           25221       25481     2096451   82  Linux swap / Solaris
/dev/sda6           25482       28031    20482843+  83  Linux
/dev/sda7           28032       38096    80847081   83  Linux

Partition table entries are not in disk order
--------------------------------------------------------------------------

My root partition is /dev/sda6

[*]Now to mount the root partition, and dev and proc filesystems
[B]sudo mount /dev/sda6 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc[/B]

[*]**sudo gedit /etc/fstab**
mine looks like this
-------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=31e51132-d471-476b-9cf0-ccbf4cdd692a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=96f36ede-edf8-42b8-ba8b-7c7012e1796d /home           ext4    defaults        0       2
# /windows/c was on /dev/sda1 during installation
UUID=22CA32C7CA32974F /windows/c      ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=ac5466f0-2b0b-432e-bb62-eee81ef59718 none            swap    sw              0       0
-------------------------------------------------------------------------

[*]Look for the line with your root partition, /dev/sda6 in my case, and duplicate it
-------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=31e51132-d471-476b-9cf0-ccbf4cdd692a /               ext4    errors=remount-ro 0       1
UUID=31e51132-d471-476b-9cf0-ccbf4cdd692a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=96f36ede-edf8-42b8-ba8b-7c7012e1796d /home           ext4    defaults        0       2
# /windows/c was on /dev/sda1 during installation
UUID=22CA32C7CA32974F /windows/c      ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=ac5466f0-2b0b-432e-bb62-eee81ef59718 none            swap    sw              0       0
--------------------------------------------------------------------------

[*]Uncomment one line and change the UUID-blah blah in the other line into your root partition, in my case /dev/sda6. This is how it will finally look
--------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
#UUID=31e51132-d471-476b-9cf0-ccbf4cdd692a /               ext4    errors=remount-ro 0       1
/dev/sda6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=96f36ede-edf8-42b8-ba8b-7c7012e1796d /home           ext4    defaults        0       2
# /windows/c was on /dev/sda1 during installation
UUID=22CA32C7CA32974F /windows/c      ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=ac5466f0-2b0b-432e-bb62-eee81ef59718 none            swap    sw              0       0
--------------------------------------------------------------------------

[*]Click save and close gedit.
[*]**sudo chroot /mnt**
You will now get a root shell, no need to type sudo before every command.
[*]**apt-get update**
[*]**apt-get install lilo**
Alternatively, if you do not have an internet connection and you have installed the 64 bit distro, you can simply download the two required files from below (see end of this howto).
[*]After lilo is installed liloconfig runs automatically (in case it doesn't just type liloconfig and hit ENTER). It will prompt you to install lilo in the partition, accept, it will also prompt you to install on the mbr, default for me was no. make sure you click no to avoid overwriting GAG on the mbr
[*]After lilo is installed Ctrl and D to exit the root shell
[*]Unmount filesystems
[B]sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt[/B]
[*]Reboot
**sudo reboot**

Add the OS to GAG and enjoy[/list]

Here are the two files (64 bit ubuntu) that were downloaded:
[http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca4c00191b1fa91892](http://www.mediafire.com/?sharekey=8b50ec8c0aafc4e8ab1eab3e9fa335ca4c00191b1fa91892)

---

### Post by nucleuskore on 2009-11-12
I noticed that grub packages were upgraded in a recent update. So I uninstalled lilo and installed grub.

Didn't work and I'm back with LILO.

---

