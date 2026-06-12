---
title: "Triple boot Windows vista, ubuntu and later windows 7"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by tsanchung on 2009-08-28
I know how to setup my hard disk to dual boot Windows vista & ubuntu.
However, I want to install windows 7 when it come out and I am afraid installing it will overwrite the grub bootloader and ubuntu won't boot.
If that happen, do I use ubuntu live cd to repair the grub bootloader?
Then I will have Windows vista, ubuntu & windows 7 triple boot.
If not, then what should I do?

---

### Post by presence1960 on 2009-08-28
Go ahead and install windows 7. if it is installed to the same hard disk that Ubuntu is on, windows will overwrite the MBR with it's bootloader. All you need to do is:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

---

