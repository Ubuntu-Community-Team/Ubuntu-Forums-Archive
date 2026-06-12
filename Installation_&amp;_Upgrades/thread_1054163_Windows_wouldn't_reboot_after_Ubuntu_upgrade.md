---
title: "Windows wouldn't reboot after Ubuntu upgrade"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by Mickser_52 on 2009-01-29
I have a dual boot system with windows XP and Ubuntu. This morning I was working in windows and when I was finished I put windows in hibernate mode and restarted in Ubuntu. I got a message that there were updates available so I downloaded and installed them with update manager. I did not note what the updates were but when finished a message appeared saying that it would be necessary to restart the system. Either then or just before I was given a pop up option to either continue with existing menu or use newly downloaded one (not sure about the exact wording)it didn't mean anything to me but being adventurous I chose the latter. Ubuntu restarted and there appeared to be some problem producing yet another choice i.e to continue with boot or try and fix broken? package. Eventually after many lines of text on a blue background Ubuntu restarted and appeared to be working normally (As it still is). 

The problem (which I am finally getting to) happened when I shut down Ubuntu to reawaken XP from hibernation. The grubstartup menu appeared but there was no longer a Windows option. Returning to Ubuntu, I opened grub menu.lst and discovered that the windows segment was no longer present. After exploring blind alleys about windows being in hibernation, I eventually discovered a launchpad Bug #21175 (from 2005) from which I could copy the missing lines from grub menu.lst. I pasted them into my menu.lst and on rebooting could again restart Windows.

While the problem seems to be resolved, What caused it in the first place? Perhaps this may help somebody in a similar situation in the future.

---

### Post by cariboo on 2009-01-29
When a /boot/grub/menu.lst is created, there is always a backup file ususlly name /boot/grub/menu.lst~. You can open up the backup and just copy and paste the windows section from the backup to the new file.

Jim

---

### Post by dstew on 2009-01-29
The Ubuntu update probably included a new kernel image. When the update has a new kernel, the program update-grub is run, to put the new kernel menu item into the menu.lst. This program may update a previous menu, or create a new one. If you tell it to create a new one, it can only create a menu with linux kernels. That is because update-grub cannot detect the presence of the Windows system. Only the linux *installation* program can detect Windows.

My guess is that you told update-grub to create a new menu. In that case you would have lost your Windows menu item. But, as you see, it was not hard to fix. And, as the poster above says, you could have used the back-up menu.lst~ file too.

---

### Post by Mickser_52 on 2009-01-29
Many thanks for your replies, some useful information there. I found two backup files, menu.lst~ which was a copy of the changed menu but also menu.lst.backup which was a copy of the original grub menu.lst.

Would you know if it is possible to mount the boot directory (windows files) while xp is hibernating. I only noticed this after this morning and don't know if this was always the case.

Again,
Thank you!

---

### Post by ddeile on 2009-01-29
I sorta have the opposite problem.  When I updated the kernel I did not let it update menu.lst.  Of course this now means that I do not have the option to boot into the new kernel.  what should be added to the menu.lst to get the new kernel option?  Or should I remove the new kernel and reinstall?

---

### Post by Mickser_52 on 2009-01-30
Here is what my menu.lst now looks like after yesterday. If your's is different you could try adding the extra lines and see if that helps.

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		e276248b-17d9-4132-bac8-61db2fbd92f2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e276248b-17d9-4132-bac8-61db2fbd92f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e276248b-17d9-4132-bac8-61db2fbd92f2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e276248b-17d9-4132-bac8-61db2fbd92f2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
uuid		e276248b-17d9-4132-bac8-61db2fbd92f2
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e276248b-17d9-4132-bac8-61db2fbd92f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
uuid		e276248b-17d9-4132-bac8-61db2fbd92f2
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=e276248b-17d9-4132-bac8-61db2fbd92f2 ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e276248b-17d9-4132-bac8-61db2fbd92f2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e276248b-17d9-4132-bac8-61db2fbd92f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet



title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e276248b-17d9-4132-bac8-61db2fbd92f2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e276248b-17d9-4132-bac8-61db2fbd92f2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e276248b-17d9-4132-bac8-61db2fbd92f2
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


title Microsoft Windows
root (hd0,0)
savedefault
makeactive
chainloader +1
```

---

### Post by ddeile on 2009-01-31
Thanks.  I manually edited my menu.lst and added the new kernel.

---

