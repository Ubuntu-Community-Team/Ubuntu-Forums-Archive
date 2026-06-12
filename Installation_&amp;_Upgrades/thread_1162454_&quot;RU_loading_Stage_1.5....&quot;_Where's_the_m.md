---
title: "&quot;RU loading Stage 1.5....&quot; Where's the menu.lst file?"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by wklang on 2009-05-17
On my second machine, I have Windows 7, Ubuntu 9.04, and Ubuntu 9.04 Server installed.

On bootup, my screen shows:

Grub loading Stage 1.5

Grub loading...

Followed by the Grub menu showing the three OS's.

I tried editing the /boot/grub/menu.lst file to set the default OS and -- lo and behold I found that that this file contains ONLY Windows 7 and Ubuntu 9.04 (Generic) OS's.

Apparently there's another menu file somewhere else - hence the Stage 1.5 note.

Does anyone know where it is.

I would really like to get rid of the Stage 1.5 notes and put all three OS options in the /boot/grub/menu.lst file.

Thanks,
Wes (newbie......if I even had to mention this!)

---

### Post by wklang on 2009-05-17
Let me add some information I've recently found out:

1. The first OS on the drive was Windows 7; the second, Ubuntu 9.04 generic; the third, Ubuntu 9.04 server.

2. I found all the *1_5 files in the /boot/grub directory in the 9.04 server installation tree.  In the installation process, the Ubuntu 9.04 generic and Windows 7 entries were added during the server installation.

3. I changed my mind about wanting a server installation and used Gparted to delete the Server and its asociated swap partitions.

4. After getting the Grub loading Stage 1.5....Grub loading.... and then an error 22, I used Supergrub to repair the booting of my drive with only two OS on it (Windows 7 and Ubuntu 9.04 generic).

5. I can now edit - and see the effects of editing - my /boot/grub/menu.lst file.

On boot up, I still get a Grub loading Stage 1.5 notation, but I guess I can live with that.

(As you now doubt can see, I am a newbie at this and will probably make other errors in the future.)

Wes

---

