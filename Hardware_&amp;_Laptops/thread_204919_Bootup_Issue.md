---
title: "Bootup Issue"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by walkerx on 2006-06-27
I currently have 3 hard drives on my system, but removed 2 to install Ubuntu 6.06 to ensure nothing got wiped.

This is my usual setup

1) IDE-M - 200gb (WIndows Vista 64bit Beta & Windows XP Gaming Setup)
3) IDE-S - 40GB (Ubuntu 6.06 64bit)
2) SATA-M - 250gb (Windows XP Pro Office Setup)

Usually my 40gb isn't plugged in so boot of SATA and use dual-boot options to get into both versions of XP. If I want to boot to Vista I press F11 on startup and select the Vista HDD and it boots without problems

When I installed Ubuntu I set it up as though the drive was the master and works fine by itself, but I need to add it permantly and then choose the option to boot from it from startup, but when I do this it starts loading then says reading filesystem and doesn't go futher.

can anyone offer a best solution, but i need to have all operating systems available to boot to without affecting the others by using dual booting options

thanks in advance
walkerx

---

### Post by mrashley on 2006-06-27
[QUOTE=walkerx]
1) IDE-M - 200gb (WIndows Vista 64bit Beta & Windows XP Gaming Setup)
3) IDE-S - 40GB (Ubuntu 6.06 64bit)
2) SATA-M - 250gb (Windows XP Pro Office Setup)

When I installed Ubuntu I set it up as though the drive was the master and works fine by itself, but I need to add it permantly and then choose the option to boot from it from startup, but when I do this it starts loading then says reading filesystem and doesn't go futher.
walkerx[/QUOTE]

It would seem to me that if you installed it as a master device the software would have set it up as such. So when the software looks for /dev/hda expecting your 40gig ubuntu drive and your 200gig windows drive is what it finds, that's where you're running into trouble. 

I'd suggest using your ubuntu bootable cd to boot up. Then log into a shell and mount your ubuntu drive. Once it's mounted you can go into to it's root folder and 

sudo chroot . 

to make your ubuntu's actual root folder your new current root folder. (rather than the one that the cd sets up when it boots) From there if you 

sudo /sbin/grub-install

It should automatically sort out the correct partition labels.

Finally if you use 'fdisk' to make your ubuntu drive the bootable partition and change your BIOS to reflect the same, then you'll be able to use GRUB as the boot loader before your windows bootloader.

:-) I hope that's at all helpful.

---

### Post by walkerx on 2006-06-28
My main bootable disc is the SATA, and when I want to boot into Vista, I would restart the machine, then press F11 to select which device I wish to boot from, so I don't have to mess with changing settings in the bios.

I don't want the drives to be setup as dual boot as I'm always swapping between the different OS and changing stuff. The way I got the 2 different versions of windows to work without messing was first installed the OS on the SATA with no other drives in, and done the same for Vista on my IDE. I then modified the boot.ini on each drive to link to the correct partitions if both drives were installed and this works without any problems.

Now I want to do the same for the Ubuntu disk, so when boot I press F11 and select the correct disk to boot from so that becomes the new master disk.

If I follow the instructions you mention will this overwrite any of the boot loaders for the other drives or will it just do it for the Ubuntu drive.

Also would it just be the command 'mount /dev/hda' (or whichever drive it is listed as) to actually mount it

thanks
walkerx

---

