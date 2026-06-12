---
title: "Hey !! help me as fast as you can ...please..."
date: 2009-11-30
forum: Hardware
---

### Post by pandeylavakesh on 2009-11-30
How should I edit the boot menu that appears on the start of OS. I mean, I want to change the name of my OS that appears while bootinbg....How to edit it?????
Thanks in advance.....!!!!...  :)  ;)  :P

---

### Post by ubername on 2009-11-30
are you using grub or grub2:

Check in /boot/grub. If you have menu.lst you are using grub, and you can edit that file. If you have grub.cfg you have grub2 and you can edit that file, although it says not to. In both cases you need to have root privileges, and with grub.cfg you need to set the permissions on the grub.cfg file to allow root to read/write. Note that either of these files will get reset if you run update-grub.

---

### Post by doas777 on 2009-11-30
yes. we'd better reply quickly, or else... everything will work fine...?

---

### Post by Iowan on 2009-11-30
You want to change the default boot OS - or just the splash screen?

Hmmm... guess I waited too long.

---

