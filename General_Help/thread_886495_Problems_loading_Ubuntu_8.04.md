---
title: "Problems loading Ubuntu 8.04"
date: 2008-08-11
forum: General Help
---

### Post by Benno123 on 2008-08-11
Hello

I'm having trouble booting into Ubuntu 8.04. I seem to have problems with all versions of Ubuntu for some reason, however this is a new computer. I have absolutely no trouble with any versions of Kubuntu though.

Anyway, after it loads the kernel and the loading bar comes up, after a few seconds it goes to the console screen and just shows this:
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)_

I have no clue what this means and I have no clue what to do. I'm not exactly that advanced with Linux and the command lines and all that, but I do know how to use Linux fairly well.

Just incase you need it, I have a Dell Inspiron 530 with an Intel Core 2 Duo 2.4ghz processor with 2gb ram. Vista Home Premium SP1 is installed however I know how to partition the HDD and all that.

So, any ideas what to do? What to type in? All help would be greatly appreciated. I didn't know if it should've been posted in the Dell section or not but this seemed more appropriate.

Thanks again!

---

### Post by Mgiacchetti on 2008-08-11
try this
1.Press Esc during Grub boot delay to access the boot menu.
2.Select your actual Ubuntu boot line and press "e" to edit it.
3.Select the "kernel" line and press "e" to edit it.
4.At the end of the line, remove "splash" and "quiet" and press "enter".
5.Type "b" to boot the custom boot line.

---

