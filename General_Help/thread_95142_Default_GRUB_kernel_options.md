---
title: "Default GRUB kernel options"
date: 2005-11-25
forum: General Help
---

### Post by hazza96 on 2005-11-25
The default kernel options in grub are " ro quiet splash" and I add vga=788 to the end. That's all well and good but every time I download and install a new kernel I lose the vga=788 part.

Where are those options set? I want to add vga=788 to them so that when I install a new kernel and the grub menu gets recreated automagically it already has the vga=788 on it.

---

### Post by Xian on 2005-11-25
This is what I would do...just create a personalized grub entry.
Then use the kernel and initrd symlinks.
That way you'll never have to update it or worry about it being changed.

Something like this (just change the partition locations):

# Boot Ubuntu Linux 5.10
title		Ubuntu Breezy
root		(hd0,7)
kernel		/vmlinuz root=/dev/hda8 ro quiet splash vga=788
initrd		/initrd.img

---

### Post by hazza96 on 2006-01-14
I found the answer myself, I had a closer look in /boot/grub/menu.lst. I found a line that looks like this:
> # nonaltoptions=quiet slash
All I did was add 'vga=788' to the end, it now adds that as an option to the end of the boot entry when ever it re-creates the menu.lst.

---

