---
title: "[SOLVED] Boot sector corruption"
date: 2008-06-02
forum: Hardware
---

### Post by Evgeny_N on 2008-06-02
During the boot message appear - something like: boot sector differ than backup, cannot be fixed automatically. How could I fix it?

---

### Post by Zorael on 2008-06-02
I guess you could ask grub to reinstall it properly. Provided you're using grub?
```
$ sudo grub

grub> find /boot/grub/stage1
 (hd**x**,**y**)		*<note what **x** and **y** are, may be (hd0,1), may be (hd4,8), etc>*

grub> root (hd**x**,**y**)

grub> setup (hd**x**)	*<note, no **y**>*

grub> quit

$ sudo update-grub	*<for good measure>*
```
In a terminal, of course.

edit: If you can't boot at all (original post didn't say), do this from a live cd.

---

### Post by Evgeny_N on 2008-06-02
I need to clarify, I ma not so skilled about grub and I wonder if I got dual boot (Ubuntu and MS WXP) will this operation reset dual boot? Thanks, Also I should mention that I can boot.

---

### Post by Zorael on 2008-06-02
It should not, no. It'll only reinstall grub into the master boot record; the [FONT="Courier New"]/boot/grub/menu.lst[/FONT] file - which contains your grub menu options - will only be updated and verified to point to your available kernels. Omit the last command ([FONT="Courier New"]update-grub[/FONT]) if you wish to leave it completely alone.

If you examine the contents of that menu.lst file, you'll see that near the end there's a line that says "### END DEBIAN AUTOMAGIC KERNELS LIST". Any entries below that line will be left alone when doing update-grub. Only the entries above that line will be touched at all.

---

### Post by Evgeny_N on 2008-06-02
Thank you it help

---

