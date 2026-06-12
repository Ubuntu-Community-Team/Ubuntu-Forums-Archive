---
title: "Removing windows drive...how to make Ubuntu boot?"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by stallman000 on 2005-08-18
My dual boot setup currently is:

Master drive with XP, grub boot loader on MBR
Slave drive with Ubuntu

I am getting rid of the master XP drive, and want the slave drive to be the only drive in the system, booting Ubuntu.  If I just hook it up this way it says "Error loading operating system" because of course there is no MBR on the slave drive.

How do I fix this?

---

### Post by audax321 on 2005-08-18
Just put the Ubuntu install CD in and boot from it. When you get to the prompt type:

        rescue

and hit enter. At the next prompt type:

       grub-install /dev/hda

assuming that /dev/hda is the path to the drive, which it probably is if it is set to master and connected to ide1. That should get grub set up for you to boot into Ubuntu. Although you may need to load up a live distro and edit /etc/fstab to adjust the /dev names (you might be able to do that at the rescue prompt as well, but I'm not sure). If you can get access to /etc/fstab at the rescue prompt you can enter the relevant line as follows:

echo "line you want to append" >> <path to mounted drive>/etc/fstab

where the line you want to append if you are using ext3 as the filesystem is (change /dev/hda1 to reflect the partition containing the root partition on your hard drive):

/dev/hda1 / ext3 defaults 0 1

I'm pretty sure the rescue prompt will have the drive mounted somewhere, probably in /mnt or /media

You might need to specify the swap as well, but just try booting without it and when you get into Hoary finish fixing the /etc/fstab file there and after another reboot you should be good to go.

---

