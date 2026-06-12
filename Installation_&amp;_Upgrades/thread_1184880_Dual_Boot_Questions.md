---
title: "Dual Boot Questions"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by thisnamestoolong on 2009-06-11
I have Kubuntu Jaunty x64 installed on the main SATA drive in my laptop. I also have a second hard drive that is not installed at the moment, formatted as NTFS with WinXP on it. Is there any way I can simply install the second hard drive and reconfig GRUB to be able to choose between the two O/S'es at startup? Is this a really bad idea?

---

### Post by dstew on 2009-06-11
No, that's a good idea. You will need to re-configure or possibly re-install grub to boot the second hard drive, assuming it's a bootable drive. I assume the Windows XP was installed into the same laptop before. Unlike Ubuntu, an XP installation will not work in a system that is different from the one it was originally installed to. So, if you pulled the XP drive from a different laptop, with different hardware, it may not work. But, it is worth a try.

After you put it in, try to boot. If you get the grub menu, and can boot Ubuntu, all you have to do is edit the grub menu to put in the Windows boot commands. In Ubuntu, open the file for editing by hitting alt-F2 to get a command line, then```
gksudo gedit /boot/grub/menu.lst
```Add the following lines to the menu, at the bottom:```
title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```Save the file and reboot, then try the new menu item.

If, after you install the second disk, grub doesn't work, or gives an error, then you will probably have to re-install grub before editing the menu.lst file. See [this thread]("http://ubuntuforums.org/showthread.php?t=224351") for information on re-installing grub.

---

