---
title: "Dual boot; adding Xp to Ubutu, Starting up...NOT."
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by stillcen on 2009-08-18
I had two drives on the same cable from the mother board.    Have/Had Ubuntu on the distal of the two, the proximal hardDrive was blank.  Disconnected the Ubuntu drive and installed Windows XP on the other drive.  Hooked both drives back up and Ubuntu booted.  Edited the /boot/grub/menu.lst by putting  
 

 title           Window XP
 

 root            (hd1,0)
 

 makeactive
 

 chainloader +1
 

 

 at the very very end.
 

 Reboot the machine, press escape to get the load menu, move the hi-light bar down to Windows XP press enter.   Screen goes black   and  
 

 Starting up . . .
 

 

 appears.  But nothing happens.
 

 XP loads just fine when not going through the unix load menu.  Ubuntu still loads find with both drives hooked up
 

 I have messed around with the;    root   (hd1,0)        by messing around with the numbers tried
 1,0 0,1 0,0 1,1 0,2 1,2     you get the picture  with these numbers get a device or no drive error.
 

 

 Help.
 

 

 As a side note, with both drives hooked up which operating system loads....the OS that booted last.
 Meaning; when I disconnected the Ubuntu drive, Windows loaded, hooked the Ubuntu drive up and Windows loaded.     Disconnected th XP drive Ubuntu boots, hook up the XP drive  start machine and Ubuntu loads.  Interesting.




Ubuntu drive is sda  and xp drive is sdb




Thanks in advance




stillcen

---

### Post by stinger30au on 2009-08-19
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Mark Phelps on 2009-08-19
To boot, Windows must think it's on the first hard drive.  If it's not, you fool it into thinking that as follows:

Presuming that the first HD contains Ubuntu and you boot from that, add the following after the root statement to your menu.lst stanza:

map (hd1) (hd0)
map (hd0) (hd1)

This will make XP think it's running from the first drive.

---

