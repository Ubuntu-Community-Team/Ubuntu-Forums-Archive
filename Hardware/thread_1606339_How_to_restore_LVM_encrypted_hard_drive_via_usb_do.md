---
title: "How to restore LVM encrypted hard drive via usb docking station"
date: 2010-10-26
forum: Hardware
---

### Post by dimadimi on 2010-10-26
Hi!

I have WD800BEVS hard disk on my other computer. I can't boot that computer anymore, most probably because hard reset i committed.

It either started with black screen with sound of hard disk trying to start but then stopping, or said "no init found. Try passing init= bootarg." I managed to run fsck once with live usb with the instructions on [this]("http://ubuntuforums.org/showthread.php?t=1200023&page=2") page (post #17). The next time I started up there was no "no init found.." but Kernel Panic instead. I tried to run fsck again, 'cus I wasn't sure if it had run properly, which was difficult 'cus the computer seldom managed to run live usb, and if it did it crashed shortly after. Eventually I got to run fsck but it showed some error message and aborted every time.

I don't really care anymore if I can get that system up and running, but I have few very important documents on that hard drive which I hadn't backed up (yes, I know) and I'd like to recover them.

I now have SATA HDD docking station and another computer with Lucid Lynx. My plan was to mount that hard drive and rescue the files, but apparently that can't be bode unless I manage to repair the hard drive first. If I try to just open it it says "Unable to mount 80 GB Encrypted One or more block devices are holding /dev/sdc5"

I've got few ways I've been trying to solve this problem, but so far I haven't gotten none of them to work. If anyone could help me I'd be really grateful.

I've installed the cryptsetup lvm2:
```
apt-get install cryptsetup lvm2 
```And I've loaded the kernel packets. I've done this with both the the schemes, although I don't really understand if this is necessary and if it's enough to do this just once.

```
modprobe dm-mod
```** Scheme #1 - Running fsck via usb docking station**

#1
```
  ls /dev/sd*
```I figured out that the encrypted drive is /dev/sdc5, and opened the crypt with command:

#2
```
sudo cryptsetup luksOpen /dev/sdc5 computer
```next I ran pvscan and vgscan

#3
```
sudo pvscan
sudo vgscan
```Result of the pvscan:   [PHP]/dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 79768190976: Input/output error
  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 79768309760: Input/output error
  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 0: Input/output error
  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 4096: Input/output error
  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 77468729344: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 77468786688: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 4096: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 2298413056: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 2298470400: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 4096: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 0: Input/output error
  PV /dev/mapper/computer   VG ink-spots   lvm2 [74,29 GiB / 0    free]
  Total: 1 [74,29 GiB] / in use: 1 [74,29 GiB] / in no VG: 0 [0   ][/PHP]Result of the vgscan:   [PHP]Reading all physical volumes.  This may take a while...
  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 79768190976: Input/output error
  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 79768309760: Input/output error
  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 0: Input/output error
  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 4096: Input/output error
  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 77468729344: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 77468786688: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 4096: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 2298413056: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 2298470400: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 4096: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 0: Input/output error
  Found volume group "ink-spots" using metadata type lvm2[/PHP]Those scans didn't give errors when I ran 'em on live-usb.

Next I activated the volume group:
4#
```
sudo vgchange -a y ink-spots

```And again I got few errors:  [PHP] /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 0: Input/output error
  2 logical volume(s) in volume group "ink-spots" now active[/PHP]Logical volume scan and results:
5#
```
sudo lvscan
```[PHP]  /dev/mapper/udisks-luks-uuid-511b56a2-f06c-4074-a671-13dc78076747-uid1000: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/root: read failed after 0 of 4096 at 0: Input/output error
  /dev/ink-spots/swap_1: read failed after 0 of 4096 at 0: Input/output error
  ACTIVE            '/dev/ink-spots/root' [72,15 GiB] inherit
  ACTIVE            '/dev/ink-spots/swap_1' [2,14 GiB] inherit
[/PHP]I don't know if those results are the reason I can't get further, but this is where I can't get any further. I try to next command:

```
sudo fsck -yvf /dev/ink-spots/root/

```which says [PHP]fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/mapper/ink--spots-root
Could this be a zero-length partition?
[/PHP]I think I've wrong path, but I've been trying countless different paths and I dont understand what I should put in the place of "ink-spots" and "root"


[B] Scheme #2 - Mounting the hard drive via usb docking station

[/B]Pretty much the same as previous attempt, butI've been root and after step #5 I've done:
```
mkdir /media/root
```And:

```
mount /dev/ink-spots/root /media/root
```Again I think the problem is with the paths, but I can't figure how it should be..

**Scheme #3 -** using ```
"shutdown -r -F now"
```This I haven't tried, 'cus I have dual boot with windows 7 on the other half and a) I dont know if that affects the usb-hd and if it damages the windows partition.

---

### Post by dimadimi on 2010-10-27
I'm not sure if I put this in the right category, though.

---

### Post by dimadimi on 2010-11-01
Sorry for upping this, but I'm desperate.

---

### Post by swallowtail on 2010-11-28
I don't really know what I'm doing, but I'll tell you what worked for me.

First of all, there are two separate issues: i) mounting and accessing your data on the failing hard drive, and ii) repairing the damage done to your file system.  I can't help you with the second problem.

----- Short version: -----

 (If you removed the hard drive from the computer, put it back.)

1) Boot up the dying computer using the ubuntu alternate installer CD that you can get from ubuntu.org  (I've no idea whether the regular liveCD works for this.  I was using the 10.04 installer, but I don't think it matters.)

2) At the main menu, select
"Rescue a broken system"

3) Enter the drive's password when eventually prompted.  (I'm assuming you have not forgotten the password.)

4) Rather than attempt to boot into the OS that was on the failing hard drive, I just wanted access to a basic shell where I could mount the drive manually and copy only the files I needed off the drive.  So I selected "Do not use a root file system", and then "Execute a shell in the installer environment".

5) Mount the dying hard drive using a command like this:
  mkdir /media/dyingdrive
  mount /dev/mapper/sda5_crypt /media/dyingdrive
(To others who are reading this, you can figure out the name of your encrypted hard drive device by typing "ls /dev/mapper".)
You should be able to read the contents of the dying hard drive now, 

6) You can now mount an external USB drive, and copy data onto it.

Again I'm at a loss if you've done additional damage to the hard drive by trying to repair it when you mounted it earlier.  If you do succeed in mounting a failing drive (regardless of whether it's encrypted), try to access only the essential files you need before accessing the rest of the hard drive or trying to repair the file system.

----- Additional help on step 6) -----

These instructions are aimed at novice users (like myself) who browse here because of the same problem.

Okay, to mount an external USB storage device:
First you need to figure out it's device name, so plug it in and type:
ls /dev/sd*
(In my case, this printed out number of choices: sda, sda1, sda2, sda5, sdb, sdb1.  Knowing that all of the "sda" choices refer to the dead drive, and that the name should be at least 4-characters long, I picked "sdb1".  Of course, for you it might be different.)

Then mount it using a command like this:
mkdir /media/usbdrive
mount /dev/sdb1 /media/usbdrive

Then copy files over to /media/usbdrive/ using a comand like this:
cp -r /media/dyingdrive/home/USERNAME/importantfile /media/usbdrive/

I tried to copy the entire user directory, but the computer froze up when  I hit a bad sector on the encrypted disk and I had to hold the power button down and start all over again.  (This then damaged the USB drive's FAT32 filesystem.  I copied what I could off of it onto another drive and reformatted the USB drive.  As such, if you're copying a lot of data, it's helpful to have another disk, and another computer handy.)  In summary, I'd try copying individual files or small directories (incrementally), starting with the important ones first.

---

