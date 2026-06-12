---
title: "how do i open grub menu.lst in XP"
date: 2008-09-01
forum: General Help
---

### Post by BlackLLama on 2008-09-01
yes, i am trying to boot ubuntu from my EXT HDD on my Xp computer, how do i open the grub menu.lst file and what do i add to the entry

---

### Post by bingoUV on 2008-09-01
Did you install Ubuntu on your EXT HDD? How did you install? Did you deliberately skip installing bootloader when installing Ubuntu on EXT HDD?

Unless you did something special, you don't have to edit menu.lst. Just make your system boot from the EXT HDD.

---

### Post by BlackLLama on 2008-09-01
i installed it with another computer, which it works fine on there, im trying to boot it on another computer

---

### Post by bingoUV on 2008-09-02
> **BlackLLama said:**
> i installed it with another computer, which it works fine on there, im trying to boot it on another computer

That doesn't matter. As long as you installed it properly, Ubuntu should boot when you boot from the EXT HDD. Some hardware would not be configured properly as drivers are installed only for the another computer, but that is an after boot issue.

---

### Post by Luke771 on 2008-09-02
Q: how do i open grub menu.lst in XP?

A: Provided that you can access menu.lst from Windows (a copy of the file, or using the ext2/3 drivers for windows - google that), all you have to do is to select Notepad from the 'Open with...' list.

However, as DOS/Windows and Unix-based systems use different 'new line' encoding, your menu.lst will look weird when opened in notepad: instead of new lines, you'll see weird charachter looking like a rectangular 'thingy', and the whole content of the file will be one long line, very difficult to read.

This is easily solves as long as you can still access your Linux system (or access it through a live CD): install the software 'Tofrodos' from repositories (*), then run this line

```
$ sudo todos /boot/grub/menu.lst
```

Now you can open menu.lst in Notepad and it will look right.
In my experience, you don't need to revert the encoding back to *nix for configuration files such as menu.lst to do their job; however, in case you want to, the command to revert the encoding is

```
 $ sudo fromdos /boot/grub/menu.lst
```

Anyways, IMHO you're doing it wrong: if you set your external HDD to boot first in BIOS, that should do the trick... but you may experience some hardware problems if the two boxes aren't exactly identical: the system will expect to find some hardware but will actually find something else, that's a recipe for problems.
Also, when fixing systems you can't boot, use a liveCD, not windows:fixing stuff from a compatible system is always better than trying to do that from a system that's built specifically for being incompatible with all *nix.


(*) Yes you can install software on a liveCD, for instance the live CD integrated in the Ubuntu install CD has access to repositories and you can even enable universe/multiverse (edit /etc/apt/sources.list as root and uncomment all the lines that begin with 'deb')
BUT
As all the changes are written in a RAM disk, they won't be persistent: next time you boot your liveCD the programs you installed won't be there any more and you'll have to install them again if you want to use them (or you can make your own customized liveCD/USBdrive, but that's another story)

---

