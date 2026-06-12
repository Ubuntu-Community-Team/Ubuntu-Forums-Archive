---
title: "ERROR - No bootable devices"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by SR Cerinus on 2008-12-04
I decided to give Linux ago on a laptop, but on booting up the first time after installation, I get the following error after the Bios splash screen in displayed.

No bootable devices--strike F1 to retry boot, F2 for setup utility

Laptop: Dell Latitude C610, P3 1GHZ, 512MB Ram, 20GB HD, W2Ksp4

Version: Ubuntu 8.04

Steps:
======
1. Copied Ubuntu 8.04 iso image from PC World magaizine DVD to desktop and used Nero to burn image to CD-R
2. On boot up install menu appeared, followed on-screen instructions.
3. Partioned whole drive for Ubuntu, i.e not dual boot, ADVANCED options stated to install bootloader
4. Install went ok, no errors displayed, and Unbutu desktop appears
5. Able to see file struture installed and connect to internet, so laptop hardware all working OK.
6. Exited desktop, removed CD, and rebooted.
7. On boot up error appears

No bootable devices--strike F1 to retry boot, F2 for setup utility

8. Put Ubuntu CD back in, boot up to menu, selected boot from hard drive, same error.

9. Able to get back to desktop via CD

10. Opened terminal and used command
> sudo fdisk -l

Returned expected result showing disk information (sorry cannot show, as at work). But there was no " * " in the BOOT column for any of the device lines displayed.

11. Went into grub, but got error
> sudo grub
grub> find /boot/grub/stage1

Error 15: File not found

12. Tried to install grub to MBR, got error

>sudo mkdir /media/sda5
>sudo mount -t ext3 /dev/sda5 /media/sda5
>sudo mount -t proc none /media/sda5/proc
>sudo mount -o bind /dev /media/sda5/dev
>sudo chroot /media/sda5
>grub-install /dev/sda 

Stated no "/boot/grub/stage1" menu i think after grub-install line.

Can anyone help? I have read many of the threads here, but none seem to lead me in the right direction. Even tried "Super Grub" image boot desk.

---

### Post by caljohnsmith on 2008-12-04
Did you let the Ubuntu installer install Grub to the MBR of that drive? If the drive in question is sda, then that's where Grub would have been installed by default, but did you change any of the Grub settings under the "advanced" button? If you didn't, then fixing your problem might be as simple as marking one of your primary partitions as bootable. Some BIOSes will refuse to boot a drive that doesn't have one primary partition marked as bootable, because the BIOS assumes the drive is then a data drive. Also, since you will be using Grub as your boot loader, it is entirely arbitrary which primary partition you mark as bootable, because Grub will boot a partition/OS regardless of whether it has the boot flag or not. 

If sda1 is your first primary partition, to set the boot flag on it you could do:
```
sudo sfdisk -A1 /dev/sda
```
Then reboot and see if that changes anything. If it doesn't, then how about first posting:
```
sudo fdisk -lu
sudo xxd  -l  2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
```
Note that "-l" is a lowercase L, not a one. We can work from there if you want. :)

---

### Post by jerrykenny on 2008-12-04
This might be a partitioning bug . . . . although few people really do this, its probably safest to partition your hard drive . . . and then reboot and complete the installation. This guarantees that the new partition table will be read and properly used by the installation process

I think its only really a problem where you've deleted a more complex partition-table . . . . and proceeded straight with the installation.

Sorry i'm not really helping you fix the thing, merely suggesting what might have gone wrong.

---

### Post by SR Cerinus on 2008-12-05
Hi caljohnsmith,

Found the problem. It was in the ADVANCED button on the last installation step. Here it sets to install bootloader and the directory. The directory was defaulted to "(h,0)". I changed this to "/dev/sda".

As I was originally just taking all the defaults, I didn't expect to have to alter anything. Plus wouldn't have had a clue to what to change anyway. But now I do, :D.

Thanks for your prompt reply and advice, which was probably on the right track.

Rgds
Peter (aka SR Cerinus)

---

