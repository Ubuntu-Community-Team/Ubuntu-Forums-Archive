---
title: "Bootloader Help Needed !!"
date: 2008-07-13
forum: General Help
---

### Post by the_red_devil on 2008-07-13
Hello guys, this my first post on this forum and i hope you i will get help. 
Though i am a Ubuntu fanatic, i have a problem with the GRUB bootloader.......i have Vista installed and then I installed Ubuntu, but now it is not recognizing my Vista installation.......how to make it recognize it ? 

Thanks in advance:guitar:

--the_red_devil

---

### Post by jefe on 2008-07-13
Edit /boot/grub/menu.lst and uncomment this
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
Uncommment I mean delete every # . You can change title to whatever you like i.e. Windows Vista, but remember to change root from (hd0,0) to the real, where your windows is installed. Tip: (hd0,0)=sda1, (hd0,1)=sda2 (hd1,0)=sdb1 and so on.

---

### Post by sandysandy on 2008-07-13
have a look here

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

