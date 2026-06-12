---
title: "URL for USB drive"
date: 2009-03-15
forum: Hardware
---

### Post by berryboy on 2009-03-15
for the life of me i can not figure this out, i have a folder on the usb drive called "downloads" but im unable to cd to it.

cd media/disk/downloads
or 
cd dev/sda1/downloads

i can view the folder just fine by using the button on the pannel.
but my main issue is that i want to add this drive to apache, just how do i link to it?  in windows it was just E:/downloads, 

thank you again :)

BB

---

### Post by .nedberg on 2009-03-15
Try

cd /media/disk/downloads

---

### Post by jelle_ on 2009-03-15
1. make sure /media/disk is the usb-drive
2. make sure the folder is called downloads and not Downloads or something like that

---

### Post by berryboy on 2009-03-15
heh how silly am i

cd /media/disk/downloads

all i did was miss the / 

thank you both for your responses though!

BB

---

### Post by .nedberg on 2009-03-15
No problem!

I have done lots of those myself... And probably will do lots more :)

---

