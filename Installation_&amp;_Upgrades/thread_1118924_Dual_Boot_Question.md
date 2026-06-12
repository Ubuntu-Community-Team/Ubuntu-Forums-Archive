---
title: "Dual Boot Question"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by Whisp3r on 2009-04-07
Good morning all.

After a few months of being absent, I have returned, with a new box! Hooray! I installed Windows XP, and then put Ubuntu 8.10 on with GRUB as the manager.

When I first booted up after the fresh installs, I had two Ubuntu's and windows XP. Now I have the following after various updates:

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		730fc068-25b2-4c42-b026-d9a92de18e14
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=730fc068-25b2-4c42-b026-d9a92de18e14 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		730fc068-25b2-4c42-b026-d9a92de18e14
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=730fc068-25b2-4c42-b026-d9a92de18e14 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		730fc068-25b2-4c42-b026-d9a92de18e14
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=730fc068-25b2-4c42-b026-d9a92de18e14 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		730fc068-25b2-4c42-b026-d9a92de18e14
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=730fc068-25b2-4c42-b026-d9a92de18e14 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		730fc068-25b2-4c42-b026-d9a92de18e14
kernel		/boot/memtest86+.bin

Can I remove the 2.6.27-7 groups? I don't need to extra lines on my GRUB boot loader? What has happened here? New to all this. MANY THANKS!

---

### Post by Didius Falco on 2009-04-07
> **Whisp3r said:**
> Good morning all.

After a few months of being absent, I have returned, with a new box! Hooray! I installed Windows XP, and then put Ubuntu 8.10 on with GRUB as the manager.

When I first booted up after the fresh installs, I had two Ubuntu's and windows XP. Now I have the following after various updates:

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        730fc068-25b2-4c42-b026-d9a92de18e14
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=730fc068-25b2-4c42-b026-d9a92de18e14 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        730fc068-25b2-4c42-b026-d9a92de18e14
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=730fc068-25b2-4c42-b026-d9a92de18e14 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        730fc068-25b2-4c42-b026-d9a92de18e14
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=730fc068-25b2-4c42-b026-d9a92de18e14 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        730fc068-25b2-4c42-b026-d9a92de18e14
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=730fc068-25b2-4c42-b026-d9a92de18e14 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        730fc068-25b2-4c42-b026-d9a92de18e14
kernel        /boot/memtest86+.bin

Can I remove the 2.6.27-7 groups? I don't need to extra lines on my GRUB boot loader? What has happened here? New to all this. MANY THANKS!

When you ran the update manager and downloaded all the updates, one of them was a newer kernel (the brain of the o/s), and it simply added the settings for it to your menu.lst file, which controls what the Grub menu displays.

You could remove them, but a better way to do it is to just comment out what you don't want to display. That way, if you should run into some trouble with the newer kernel, you have the older one to fall back on.

If you look at your menu.lst file, you'll notice a lot of lines preceded by a #, which prevents them from being displayed. Just add a # to the front of any lines you don't want to be displayed and when you boot it won't show up.

Personally, I like having the backup of an older kernel, just in case of a problem, but then I've always been a "belt and suspenders" guy when it comes to computers.

Here is a link to a pretty good little tutorial to teach you about the Grub menu and what you can do with it:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Enjoy!!

---

### Post by Mark Phelps on 2009-04-07
Whenever you do a kernel update, some of the previous kernel entries are retained in your menu.lst file.  This is done in case the kernel update causes problems.  If that happens, you can reboot and choose a prior kernel version.  

And yes, you can remove the old kernel entries if the current version is working OK.  The best way to do that is with Synaptic.  In there, you will find entries for Linux-headers-2.x.xx-nn and 2.x.xx-nn-generic.  Just select the ones you want to remove and click Apply.

---

### Post by upchucky on 2009-04-07
> Can I remove the 2.6.27-7 groups? I don't need to extra lines on my GRUB boot loader? What has happened here? New to all this. MANY THANKS!



yes you can remove them. In fact you can place a # in front of each line instead of deleting the line that you do not want. Doing this makes it simple to remove the # if you find you need the line again.

the # tells the shell to ignore everything on that line.

this list is contained in the file /boot/grub/menu.lst

to verify what is on your drives download this,

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh
```

A file will be generated on your desktop, post the results of the file here


since you mentioned dual boot and i see no option to boot windows in your boot menu,  assuming that windows is on the first partition of the first hard drive in the sys simply copying this to your menu.lst will work. the above diagnostic file will confirm the location of windows and ubuntu.

you may need to add the following to the bottom of the menu.lst to get windows to boot,

title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

