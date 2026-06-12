---
title: "Just re-installed XP on separate hard drive, Ubuntu no longer loads"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by jcorden on 2009-01-23
History:

PC initially had Vista on a 150GB drive. Got hacked off with this so added new 12GB hard drive and installed Ubuntu 7.04 on this.

The 12GB hard drive filled up so I deleted Vista completely and installed Ubuntu 7.04 on the 150GB drive. Have operated like this no problem for a year.

Last night I deleted the original Ubuntu install on the 12GB drive, re-formatted the entire drive and installed XP on the 12GB drive.

When I boot up, Ubuntu no longer loads. I get the message err2err3 in the top left hand corner of a blank screen and the PC then boots into XP. I have gone into the bios/boot menu and requested that it boot first from the 150GB disk but this doesn't solve the problem. I have booted Ubuntu from my original installation CD-ROM and this confirms that the original installation is still on the 150GB drive.

This is clearly a problem with the boot settings but is beyond my expertise.

Any advice appreciated

---

### Post by karanpals on 2009-01-23
boot loader has gone corrupt you just need to repair it.

boot from the ubuntu cdrom and try these steps, it should fix the loader

 open the terminal window and run following commands
##########
 sudo /bin/bash  #this command will open the shell with root privileges
 
 grub            # the boot loader stuff it will show you grub> prompt
 
 root (hd0,0)    # this you have to type on grub> prompt to select the first partition
 
 setup (hd0)     # setup boot loader on master boot record of first disk
 
 quit            # to exit

#### Hurray you are done###
now reboot the system and boot happily from ubuntu.
Hope this will help.

---

### Post by jcorden on 2009-01-23
I tried the above and it solved the problem half way. The available operating systems now display when I boot up but when I select the choice at the top of the list (the Ubuntu installation) I get the message Error 17 - cannot mount selected partition.

in the boot/grub folder device.map is as follows

(hd0) /dev/hda (the 12GB drive, now with XP on)
(hd1) /dev/sda (the 140GB drive with Ubuntu on)
(hd2) /dev/sdf (a 500GB external hard drive)

so in grub I did

root (hd1,0)
setup (hd1)

this resulted in menu.lst as follows

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75410dda-0539-4472-93fe-ffe0bd79459e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75410dda-0539-4472-93fe-ffe0bd79459e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=75410dda-0539-4472-93fe-ffe0bd79459e ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=75410dda-0539-4472-93fe-ffe0bd79459e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=78afedf0-1c9d-45ef-9f86-57e88f654b73 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=78afedf0-1c9d-45ef-9f86-57e88f654b73 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 7.10, kernel 2.6.20-16-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=78afedf0-1c9d-45ef-9f86-57e88f654b73 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=78afedf0-1c9d-45ef-9f86-57e88f654b73 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 7.10, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


Is there any way I can re-run grub so it looks at which operating systems I have installed as it still thinks I have Ubuntu installed on hd0 and it hasn't recognised that XP is installed

---

### Post by caljohnsmith on 2009-01-23
If you are booting the 150 GB Ubuntu drive on start up, then that drive is (hd0) on start up regardless of whether it is sda, sdb, etc once you get into Ubuntu. That means your Ubuntu entries should probably use (hd0,0) and not (hd1,0), but it looks like your menu.lst has multiple Ubuntu installations. In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

