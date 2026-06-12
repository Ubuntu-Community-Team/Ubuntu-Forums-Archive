---
title: "[GRUB] Update Manager, download tries to update my menu.lst grub file - query"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by libertarian on 2009-02-04
Hello, 

I have a DELL latitude D630 laptop and was trying to install Ubuntu 8.04 onto an external 250 GB IOMEGA hard disk drive.  It was impossible to install onto the laptop HDD directly as this is a company computer.  Initially,  I tried to install using the LIVE CD which inadvertently erased the Windows MBR on hd(0,1).  When I tried to boot normally the windows with no USB External HDD attached I got booting problems as the system was looking for linux and did not boot windows.  This was covered in thread: [COLOR="RoyalBlue"][http://ubuntuforums.org/showthread.php?t=993238](http://ubuntuforums.org/showthread.php?t=993238)[/COLOR] and was resolved using the Live CD.  After the trauma of abusing company property I left Linux to one side for a month or two.

The other day I took another look at the install on the external USB HDD,  using the Live CD.  I resolved to tinker around with the /boot/grub/menu.lst file.

I set it as the following:

```


## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root(hd1,5)		
kernel		/vmlinuz-2.6.24-19-generic root=/dev/sdb6 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root(hd1,5)
kernel		/vmlinuz-2.6.24-19-generic root=/dev/sdb6 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root(hd1,5)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

My query is the following:

Upon rebooting the system, I opened the download manager and started to update my system.  However I got a number of notification dialogs opening in regards to the GRUB menu.lst.  The pop-up appeared to give a number of options, such as: update the menu.lst file,  view changes side by side, merge changes etc...

I cannot exactly remember precisely what this was about,  but was I too hasty to keep the settings I have above? 

Maybe is nothing but I just wanted confirmation that it is not a security problem or the way my menu.lst file is configured isnt bad or could result in future problems ?


Best regards all/
Libertarian

---

### Post by dstew on 2009-02-04
The Update Manager installed a new kernel, and wanted to know if you wanted to leave the old kernels in your grub menu (update menu.lst) or make a new grub menu with only the new kernel. Usually, you want to just update the menu.lst. If you told it not to change menu.lst at all, you will not see the new kernel in your menu. If you want to get the new kernel in the menu, you can run ```
sudo [update-grub]("http://pwet.fr/man/linux/administration_systeme/update_grub")
```from the terminal command line.

By the way, I think there should be a space in your grub root commands. I am not sure that makes a difference, but that is usually how I have seen it: **root (hd1,5)** instead of root(hd1,5)

---

### Post by libertarian on 2009-02-06
Thanks dstew worked fine and rebooted ok.

---

