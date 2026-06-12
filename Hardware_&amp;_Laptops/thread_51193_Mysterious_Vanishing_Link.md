---
title: "Mysterious Vanishing Link"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by mojorising on 2005-07-22
I just bought a DVD burner for my system. The install went fine but in order to use the "Open DVD" feature in Kaffeine and other DVD players I had to type ln -sv /media/cdrom1 /dev/dvd . 

The problem is every time I reboot, the symbolic link goes away. 

What can I do to prevent this?


Thanks, 

Mike

---

### Post by timetunnel on 2005-07-23
[QUOTE=mojorising]I just bought a DVD burner for my system. The install went fine but in order to use the "Open DVD" feature in Kaffeine and other DVD players I had to type ln -sv /media/cdrom1 /dev/dvd . 

The problem is every time I reboot, the symbolic link goes away. [/QUOTE]

Don't set a link from the mounted folder to the device. Check /etc/fstab, it should look like this (my DVD-Player is at /dev/hdc):

```
/dev/hdc        /media/cdrom1  udf,iso9660 ro,user,noauto  0       0
```
In the shell do:
```
ls -l /dev/dvd 
lrwxrwxrwx  1 root root 3 2005-07-23 16:39 /dev/dvd -> hdc
```
That's the location of the link on my system, /dev/dvd is /dev/hdc actually. This setup works fine for me and has been created by the ubuntu installation automatically. I use it with Xine-UI and Kaffeine.

Jens

---

### Post by mojorising on 2005-07-25
Thanks! 

I haven't had a chance to try it yet but I'll reply again to let you know how it goes. 


Mike

---

