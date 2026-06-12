---
title: "Wiped Ubuntu Partition, Grub Error 17"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by lokisdottir on 2009-10-17
I installed Ubuntu as a dual boot to a Windows XP netbook. Then I wanted to reinstall Ubuntu (trying to manually install the Netbook Remix components resulted in being unable to switch back to the original desktop layout). Not wanting to mess up the Grub menu with multiple Ubuntu listings and being fed up with spending so many hours messing around with this, I decided to simply wipe the entire Ubuntu partition with gparted liveCD. My (erroneous) calculation was, this would erase Grub along with the Ubuntu installation.

This resulted in disaster, however, when it turned out during bootup that Grub was still on the system. Only now it was giving Error 22, and not letting me boot up the original Windows XP either. Now I had this completely useless computer on my hands that wouldn't load any operating system, including the restore partition which also stops at Error 22 on boot.

I figured that if I reinstalled Ubuntu, Grub would stop giving the error and I could go back to booting up normally. No such luck, however, because the Ubuntu LiveCD bootup now throws the following error and prompt.

> [    3.304021] ata3: Softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

Loading, please wait...

BusyBo v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)This same USB stick worked the first time I installed Ubuntu. Maybe it had something to do with what I did to the original Ubuntu partition.

Searching for a solution to this installation problem, I found that the working solutions came in two main flavors. One was changing the SATA setting from IDE to something else (moot for me, since my BIOS does not support any change there), and the other was to add all_generic_ide to the Grub boot options. I tried to do the latter, but even when I press esc during the bootup I don't get the boot options screen and just get the same Error 22. (Edit: It was originally Error 17, but when I tried deleting the original Ubuntu partition in addition to formatting it, the error went to 22.)

I also can't use the fixmbr fix because I don't have a Windows XP CD, just the restore partition which also does not boot up as mentioned above.

Is there any way I could get the Ubuntu install to work, to solve the Grub error, or alternately to remove Grub altogether and at least get my original XP machine back? I love Ubuntu, but this whole process has been one disaster after another. This was my second Ubuntu install (and in fact I'm writing this post from Ubuntu on an older computer), but I guess installing with the USB is a whole new ball game. Any help would be greatly appreciated.

---

### Post by Shazaam on 2009-10-17
Try the SuperGrubDisk. It has the capability to run fixmbr on a hard drive.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by lokisdottir on 2009-10-24
Thank you so much! That worked perfectly. After running fixmbr, I was able to reinstall windows. (Previously, the GRUB error had prevented me from booting to the restore partition as well.) There were a few reboots after that where I could ONLY boot from the restore partition, but once I went to the help menu and reactivated the Windows partition (for laptops), I am now setting up my Windows installation. And now to retry the Ubuntu install. :)

---

