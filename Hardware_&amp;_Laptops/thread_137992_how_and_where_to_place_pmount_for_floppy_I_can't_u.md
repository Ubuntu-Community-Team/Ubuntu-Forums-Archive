---
title: "how and where to place pmount for floppy I can't use?"
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by rolypolycat on 2006-03-01
Hello!

I've  been unable to use my floppy drive except for one time when I tried something and it worked, but only for that session. I keep getting this error message:
Error: Given UID is not a mountable volume
I edited my fstab file to this line:
/dev/fd0   /media/floppy0   vfat  rw,user,noauto 0  0
It didn't work. Double-double clicked the icon-didn't work.
Added myself and hal to plugdev, floppy, media--didn't work.
Tried in terminal: sudo adduser shell (my name) plugdev--told me shell was already a user in plugdev.
I downloaded pmount, and unzipped it once. It unzipped in my download directory, so I tried to move it to /etc. Need more permissions to move it. Same with /dev and /media. Unzipped pmount in Home directory. Still can't use floppy drive; still can't move pmount. Also, it placed an etc and a user folder with files in them that need unzipping in Home. Do I unzip these, too? And where do they go?
 There's no sign of pmount in Users and Groups tab, so I can't move it to /plugdev group, or anywhere else. 
What, where, and how do I use this file? I need my floppy to copy info from scanModem so I can send it to the scanModem folks and get my modem working under linux. Right now I have to use WinXP, then copy to linux, so downloading stuff is a pain.
Any help anyone can give me will be gratefully appreciated! Thank you!:confused:

---

### Post by StefanoCole on 2006-03-01
Hello, the following thread could be useful: [http://www.ubuntuforums.org/showthread.php?t=104259&highlight=howto+floppy]("http://www.ubuntuforums.org/showthread.php?t=104259&highlight=howto+floppy")

Also, from a terminal you could type:
sudo mount /dev/fd0 /media/floppy0 -t vfat 

pmount is a package, you have to install it using "apt" or with:
sudo dpkg -i pmount_0.9.6-1_i386.deb

Stefano

---

