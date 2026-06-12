---
title: "fstab"
date: 2004-12-03
forum: Hardware &amp; Laptops
---

### Post by tarugo on 2004-12-03
how do you edit fstab? when i openit its in ro (read only) i would like to mount my fat32 partition to save file. the entry is something like this: /dev/hda5/   /mnt/my_win_dir    vfat    rw,noatime,uid=500,gid=500,user   0 0

thanx in advance

---

### Post by MatthewMetzger on 2004-12-03
Hello,

you need to have root privaleges to edit system files in the root group. use this command:

sudo gedit /etc/fstab

I hope this helps.

MatthewMetzger

---

### Post by MatthewMetzger on 2004-12-03
Also, check out the unofficial ubuntu howto.  I have found it to be invaluable.

[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)

---

### Post by tarugo on 2004-12-03
[QUOTE=MatthewMetzger]Hello,

you need to have root privaleges to edit system files in the root group. use this command:

sudo gedit /etc/fstab

I hope this helps.

MatthewMetzger[/QUOTE]

i did that but still i can't save it. i am a linux noob so i hope you guys are patient.
is there a way you can edit that in gui. change that ro thing?

---

### Post by tarugo on 2004-12-03
[QUOTE=MatthewMetzger]Also, check out the unofficial ubuntu howto.  I have found it to be invaluable.

[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)[/QUOTE]



thanx much.....i am 2work right now i'll try it @home

---

### Post by jdong on 2004-12-03
[QUOTE=tarugo]i did that but still i can't save it. i am a linux noob so i hope you guys are patient.
is there a way you can edit that in gui. change that ro thing?[/QUOTE]

sure. ALT+F2, **gksudo gedit /etc/fstab** (isn't that a mouthful).

I recommend that you learn how to use some simple text-based editors, like **nano** (come on, CTRL+X... that's the only keystroke you need to learn!). In the uneventful situation that you're stuck in console land, a text editor is your best buddy.

---

