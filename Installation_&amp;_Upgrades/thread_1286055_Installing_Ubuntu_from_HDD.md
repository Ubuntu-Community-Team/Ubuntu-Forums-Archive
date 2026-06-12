---
title: "Installing Ubuntu from HDD"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by blindvic on 2009-10-08
I do not have CD-ROM and i am failing to boot from USB stick. So I am trying to install &#1050;Ubuntu from hard drive - but there are problems.
So, i did this:
1. Went here: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) . Chose "The CD approach"
2. Downloaded &#1050;Ubuntu iso image: "kubuntu-9.10-beta-alternate-amd64.iso"
3. Downloaded "grub4dos-0.4.4.zip"
4. Created on drive &#1057; foldersc:\boot\, c:\boot\grub\, c:\boot\kubuntu_iso\
5. From archive "grub4dos-0.4.4.zip" extracted files c:\grldr and c:\boot\grub\menu.lst
6. Extracted content of "kubuntu-9.10-beta-alternate-amd64.iso" in folder "c:\boot\kubuntu_iso\"
7. Edited file "c:\boot.ini":
> [boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
c:\grldr="Install Ubuntu"
8. Edited file "c:\boot\grub\menu.lst". Added at the beginning> title Install Ubuntu
root (hd0,0)
kernel   /boot/kubuntu_iso/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd   /boot/kubuntu_iso/install/initrd.gz
9. Restarted. Choose "Install Ubuntu", then again "Install Ubuntu". Installation begins. But stops at step "Detect and mount CD-ROM", but i don't have one.
[img]http://img21.imageshack.us/img21/1944/dsc04920c.jpg[/img]
[img]http://img210.imageshack.us/img210/2540/dsc04921o.jpg[/img]
[img]http://img210.imageshack.us/img210/2405/dsc04922w.jpg[/img]

The same happens when using UNetbootin.

Am i doing something wrong? Or the problem is with iso image?

---

### Post by makno on 2009-10-08
i had the same problem, tried with .iso on hd and on usb drive but nothing. In the end i opted for this method:

[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)

obviously because i have a second pc with windows, there are also guides for linux. hope this helps

---

### Post by blindvic on 2009-10-09
Thanks for the reply. It looks to be a complicated solution to me. I'll try other methods.

---

