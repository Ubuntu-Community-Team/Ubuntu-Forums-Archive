---
title: "Wrong disc size?"
date: 2013-01-03
forum: Hardware
---

### Post by marjoh05 on 2013-01-03
I have just installed a rsync backup server with ubuntu server 12.04.

I had to wait for the 2TB hdd to arrive, so i used a 80gb disc to set the system up.

when the disc arrived, i used clonezilla with samba to clone the image over to the 2TB disc.

Still, after changing image my disk shows the size of 72gb.

What to do ? :) My guess is after i used clonezilla, the computer doesnt know it has a bigger disc.

---

### Post by marjoh05 on 2013-01-03
Forgot to tell wich computer i use.

Its an old Lenovo/ibm pentium 4 thinkcentre.

The disc is conneted with sata, but in bios it still tells me its a IDE.

Bios update maybe?

---

### Post by howefield on 2013-01-03
I think there is an option in Clonezilla "Expert" mode that allows you to clone from a smaller disk to a larger disk which will use all the space on the destination drive.

If it were a desktop I'd use gparted to resize the cloned partition to fill the disk.

---

### Post by marjoh05 on 2013-01-03
Ok, i will download the image with expert settings if no solution comes up.

Thanks!

---

### Post by marjoh05 on 2013-01-03
Didnt work.

It was not that much work, starting over:)

---

