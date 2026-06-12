---
title: "Netbootin install puts grub on wrong hdd"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by skozzy on 2008-12-28
I installed ubuntu 8.10 using unetbootin, after a painfull long period right at the end it says its installing grub. when i reboot there is no grub, after switching drives in bios I find grub has been installed to a different drive to the one I have the OS on.

So I read and follow posts about reinstalling grub, tried without success, so i unplug all but the drive I installed ubuntu on to. Run LiveCD from USB Stick, I sudo grub then type root (hd0,0) then find /boot/grub/stage1 and told it can't find the file, well that is cause /boot is on the liveCD. The installed drive isn't mounted when the live cd booted, so I double click the icon on the desktop and it mounts and I can see grub, the device is /dev/hda5, I then try to chroot that drive which seemed to work, but still when I sudu grub then try to find stage1 again im still told file not found.

I also tried a tip on a post to reinstall using livecd upto the partition manager and change the ext3 back to /
but the install won't write the change cause there is files on there.

So I am still stuck, I can't install grub in to the MBR on that HDD.

---

### Post by albinootje on 2008-12-28
> **skozzy said:**
>  So I am still stuck, I can't install grub in to the MBR on that HDD.

Concerning chroot + grub, do you perhaps have a separate /boot partition ?

Can you try with SuperGrub cdrom or usb ?

---

### Post by skozzy on 2008-12-28
At the time of the install I had 1 boot drive in an IDE connector, 3 drives on a Raid Controller. But for some reason Grub was installed to the boot sector of the first drive on the raid controller when it should have been installed to the IDE drive.

If I unplug the raid controller and have only the IDE drive and change bios to boot from USB it won't mount the IDE drive. If I mount it and look in /dev it is called hda5 or if I type just the command 'mount' it shows /dev/hda5 as /media/disk

I guess at this point I should mention Partition 1 is Windows XP, Partition 2 is ext3 (the linux OS) and Partition 3 is swap.

hda1 is Windows XP
hda5 is Ubuntu
hda6 is swap
When the raid card is in I also get
sda for the raid drives but weird enough, linux see's each drive as a seperate drive not a single large drive.

I could just reinstall all over again this time leaving the raid card out, but it took so long to install. I like to try get grub to display instead of just booting straight in to Windows XP.

I have a CDrom on the computer but with several burned CDs of ubuntu none work, so I used a USB memory stick for the LiveCD boot. Does changing drives in bios effect how linux see's them as hda hdb sda etc.. 

Anyhow, I just need some help getting grub boot menu on the ide boot drive.

---

