---
title: "I can't copy to my hard drive in ubuntu 7"
date: 2008-06-06
forum: Hardware
---

### Post by Salvagluque on 2008-06-06
Hello

The situation is this, I installed a new HD disk 250gb sata and formatted to ext3. Is not my OS disk, and I have to mount it any time I start ubuntu. But It doesn't let me copy things into it. 

I searched already but nothing seams to work. This is what I have found:
[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)
[http://ubuntuforums.org/showthread.php?t=480853](http://ubuntuforums.org/showthread.php?t=480853)

When I look in the properties of the disk, in the permissions tab, comes with the message: "You are not the owner so you can not change the permissions".

Thanks in advance.

---

### Post by NilsE on 2008-06-06
In a terminal enter

gksudo gedit /etc/fstab

Then add the following line at the bottom  

/dev/sdb3   /media/SHARED     ext3  auto,user,sync,exec,uid=1000,gid=1000,umask=007 0 0

just change the following to whatever yours is - dev (sdb3 part) and mountpoint name (/media/SHARED/ part)

Then reboot

---

### Post by NilsE on 2008-06-06
I forgot to mention a simple alternative and that is to go into a terminal and run

gksudo nautilus

and you will have root permissions in the file browser.  My first post makes you the owner all the time.

---

### Post by Salvagluque on 2008-06-09
Hello

I tried the first solution but I don't know exactly what to put in the part of the mountpoint, maybe because I labeled the Hard disk. Then I tried  gksudo nautilus and that one worked excellent.

Thanks

---

