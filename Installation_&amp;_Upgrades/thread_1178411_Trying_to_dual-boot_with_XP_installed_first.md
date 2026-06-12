---
title: "Trying to dual-boot with XP installed first"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by kgoosie on 2009-06-04
I have tried to dual-boot with XP installed first for the second time.  I have followed several instructions and have received no solution.  This past time I finally got GRUB to work on booting into kubuntu but not XP.  When it tries to load XP it says "File NTLDR is missing [enter] Press ctrl+alt+del to restart".  I know how to fix that problem but then I know that GRUB will not load.  When I get home I will try to post my grub menu.lst.  In the meantime does anyone have any other suggestions?#-o

---

### Post by presence1960 on 2009-06-04
try this : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

then to restore GRUB :

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

---

### Post by kgoosie on 2009-06-05
presence1960 I appreciate the information but I have tried that before and I still get the same error when trying to boot into windows from the GRUB menu.  "File NTLDR is missing [enter] Press ctrl+alt+del to restart".  I have also tried numerous step from the following [site]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").  If anyone knows of any other tricks please let me know.

---

