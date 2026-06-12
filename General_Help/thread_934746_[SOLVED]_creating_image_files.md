---
title: "[SOLVED] creating image files"
date: 2008-09-30
forum: General Help
---

### Post by cowboyup8606 on 2008-09-30
is there a program on ubuntu that lets u make a image file from a cd or files off ur hard drive ??

---

### Post by hansdown on 2008-09-30
Hi cowboyup8606.

Have you tried brasero?

It's in synaptic packsge manager.

---

### Post by cowboyup8606 on 2008-09-30
yea thats the one that ur can burn a audio cd or data project or copy a disk or burn an existing iso image right ?? ... i need to creat an image file

---

### Post by Meow27 on 2008-09-30
yes you can create an ISO image file with that.

(click Data Project in brasero)

---

### Post by Fixman on 2008-09-30
Or you can right click the unit->copy disk->to hard drive

---

### Post by cowboyup8606 on 2008-10-01
if i do that and i burn it as a data cd will i still get the auto run when i put the cd i burn it to in the computer???

---

### Post by airtonix on 2008-10-01
yes because that operation will result in an ISO file.

**What is an ISO file ? **
[http://en.wikipedia.org/wiki/ISO_image](http://en.wikipedia.org/wiki/ISO_image)

**How can I create ISO files in Ubuntu ? **
several ways, via some gui programs, Nautilus, or the terminal.

 **Gui Programs**
   Install any one of the cd management programs available in the repositories : 
    Brasero, KB3, etc etc.

 [B]Nautilus
[/B]   1 - Insert the cd-rom into the cd-drive
   2 - wait for the cd-drive icon to appear on your desktop
   3 - Right click the cd drive, click "Copy Disc..."
   4 - in the drop-down menu at the top select "File Image"
   5 - Click Write, then choose a place to save the ISO file.

** Terminal**
   1 - Open a terminal : press alt+f2 then type "gnome-terminal" or "xterm"
   2 - Insert the cd-rom into the cd-drive
   3 - Enter one of the following commands : 
for dvd: ```
dd if=/dev/dvd of=dvd.iso
```
for cdrom :  ```
dd if=/dev/cdrom of=cd.iso
```
if cdrom is scsi : ```
 dd if=/dev/scd0 of=cd.iso
```

If you come up with errors wit the dd command then have a look at these two pages : 
+ [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
+ [http://ubuntuforums.org/archive/index.php/t-6509.html](http://ubuntuforums.org/archive/index.php/t-6509.html)

---

### Post by cowboyup8606 on 2008-10-01
ok ty for the hlp

---

