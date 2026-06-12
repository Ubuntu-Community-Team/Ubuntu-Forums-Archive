---
title: "Ubuntu 8.10 works fine, then won't boot."
date: 2008-11-25
forum: General Help
---

### Post by articquad on 2008-11-25
So I've had 8.10 installed for a few days now under Wubi, and it's been working great.

I go to boot into ubuntu today, and I get the following:

"GRUB4DOS 0.4.4 2008-10-27, Memory: 631K/1982M, CodeEnd: 0x49210
[ Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename.  ESC at any time exits. ]

grub>

Yeah.  I really don't know what went wrong.  I already tried chkdsk /r on the windows side.

Thanks!

---

### Post by icanfly0307 on 2008-11-26
Are you able to access the Ubuntu folder from Windows? If so, could you please post the output of (path to ubuntu directory)/boot/grub/menu.lst? That would help solve your issue.

---

### Post by articquad on 2008-11-27
From windows in C:/ubuntu/winboot I found menu.lst

Here's what that says:

```
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

```

Thanks again.

---

### Post by icanfly0307 on 2008-11-27
Um, to solve your problem, I actually need C:/ubuntu/install/boot/grub/menu.lst. Could you please post the contents of that file?

---

### Post by CholericKoala on 2008-11-27
In order to look at Linux partitions in windows, download this file and install

[Link]("http://www.fs-driver.org/download.html")

Then you can get the file that he wants.

---

### Post by icanfly0307 on 2008-11-27
He's using Wubi, so he doesn't need to access a specific "Linux" partition. Wubi installs Ubuntu directly onto his FAT32 or NTFS filesystem in Windows.

---

### Post by CholericKoala on 2008-11-28
That's kinda scary

---

### Post by icanfly0307 on 2008-11-28
:lol:

---

### Post by ago on 2008-12-01
Run chkdsk /r from windows, then check that you have the file /ubuntu/disks/root.disk, if you do not see it, look for a hidden folder called C:\found.000 and restore the files in there

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

---

### Post by Cavalero on 2009-01-20
I've got the same problem. When i was browsing the web the screen started to blink and ubuntu crashed. I've manualy turn it off and when i get the menu of ubuntu (after windows bootloader) the above refered by articquad appeared. I've done the chkdsk /r and i didn't find any found.000. Please help

---

