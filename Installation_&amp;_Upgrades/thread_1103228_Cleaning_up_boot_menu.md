---
title: "Cleaning up boot menu"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by thomasboleyn on 2009-03-22
Hi there, yesterday I bought this laptop [http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@0254720300.1237746546@@@@&BV_EngineID=ccedadegkielddgcflgceggdhhmdgmk.0&page=Product&fm=null&sm=null&tm=null&sku=854274&category_oid=-35054](http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@0254720300.1237746546@@@@&BV_EngineID=ccedadegkielddgcflgceggdhhmdgmk.0&page=Product&fm=null&sm=null&tm=null&sku=854274&category_oid=-35054) (in silver, not pink), and promptly installed Ubuntu on it, which I can confidently say works flawlessly, even the webcam. I wanted to keep Vista on it so I resized with the livecd partion tool, giving the majority of the 250gb hard drive to Ubuntu, but still leaving enough on Vista for games. My question is now whether it is possible to make the initial menu you are greeted with when the laptop is turned on cleaner and nicer. At the moment it looks like this:

Ubuntu 8.10, kernal 2.6.27-11-generic
Ubuntu 8.10, kernal 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, kernal 2.6.27-7-generic
Ubuntu 8.10, kernal 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)
Windows Vista/Longhorn (loader)

I only use the first and last options. Any help would be greatly appreciated :D

---

### Post by AnguishedEnd on 2009-03-22
This is the main reason that I prefered to install Ubuntu 8.10 inside Windows because the Boot Manager is just Windows Vista and Ubuntu 8.10, no other confusing options lol. BUT I can't get Ubuntu to work properly this way! :( So if there is a way to clean it up a little like the OP said and/or maybe even having the option to boot straight into Windows but if you press a key at the right moment for example the boot manager will come up so you can choose. I'll look around too and post if I find a solution.:D

---

### Post by upchucky on 2009-03-22
edit /boot/grub/menu.lst

put a # in front of the lines that have stuff you do not need, save and reboot.

the # is a rem statement, it tells the loader to ignore the line.

if boots fine then it is safe to delete the line.

The example rem statements below stops my Ubuntu 8.04 from booting and showing up in the list of bootable options

# title		Ubuntu 8.04, kernel 2.6.24-16-386
# root		(hd0,5)
# kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
# initrd		/boot/initrd.img-2.6.24-16-386
# quiet

title		Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.24-16-386


title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by upchucky on 2009-03-22
to boot windows on startup automatically just move the entire section for windows to the top of the list

---

### Post by thomasboleyn on 2009-03-22
Thanks for the help everyone. I've cleaned it up so now it just says:

Ubuntu
Windows Vista

Just what I wanted, thanks!

---

