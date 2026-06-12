---
title: "Make winXP reboot with Ubuntu?"
date: 2008-09-15
forum: General Help
---

### Post by Plopper on 2008-09-15
I have both Windows XP (home edition) and the latest Ubuntu installed.

When I'm in Windows XP, I'd like to shut down and make the boot loader choose ubuntu without having to choose it manually in the boot menu.

The reason why this is important for me, is that I'm using the Everun UMPC and Its keyboard is randomly inactive during the BIOS and boot menu episodes of the start up sequence. So the boot menu is half useless to me since I'm only rarely able to move the cursor between the Windows and Ubuntu alternatives. So I hope that the boot menu choice this somehow can be instructed from Windows?

---

### Post by whizbaby on 2008-09-15
Theres a 'no' and a  'yes'.
'no', without adding software or modifying your system setup (a little) it cannot be done.
and 'yes', principally you only need to access the menu.list in /boot/grub on the linux partition. So you can:
1) install a software that can mount an ext3 file system in XP and mount your root partition unless you got a seperate /boot partition already('regular' users  mostly dont have that, but theres no reason).
2) set up a seperate /boot partition formatted to fat32 so that both, linux and windoze can access it. Then you can simply set the boot default in menu.list even having booted to XP.
Idea 2) doesnt incorporate installing any new unknown software, so I would opt for that :)

p.s.: btw, does your ride have a BIOS? Is there any option to 'enable USB support for DOS' or 'native USB device support'? Look in the BIOS, it might help making your cursor more useful at boot time.
Also, you can specify the timeout (default is 2 secs) of GRUB in /boot/grub/menu.list, so you can take your time at hitting the keys if you have a clumsy input device^^

---

### Post by Jonie on 2008-09-15
YOu may do it by using grub savedefault command. I think in your case it would be reasonable to do criss-cross booting (XP saves default to Linux and vice versa). Put savedefault *number* within your GRUB entries, where the number is the number of "the other" entry.

---

