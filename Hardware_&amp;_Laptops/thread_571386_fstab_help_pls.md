---
title: "fstab help pls"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by mad chey on 2007-10-09
Hi

i am currently setting up my teenage sons pc with feisty

and have hit a little snag

ive given him a small partition for him to keep all of his music and pictures in and did the usual make directory in /media with the idea that it would mount automatically on boot up

tested it using terminal

sudo mount /dev/hda4 /media/Music\ and\ Pictures

this mounted the drive perfectly, with it displayed on the desktop as 

Music and Pictures

perfect i thought

now heres the snag, tried to edit /etc/fstab to auto mount on boot up

entered the line

/dev/hda4       /media/Music\ and\ Pictures    ext3    defaults   0   0

and when i sudo mount -a i just get the error that the line i have entered is bad


so guys where have i gone wrong, i know i can just change the mount point to be a name with no spaces but i got it to mount using terminal so why can i not get it to mount using fstab

any help mucho appreciated 

thanks in advance

---

### Post by nick_h on 2007-10-09
From the man page of fstab:
"If the name of the mount point contains spaces these can be escaped as `\040'."

---

### Post by Linicks on 2007-10-09
Seriously, I would never create a directory with spaces... use something like:

/media/music_and_pictures

Nick

---

### Post by mad chey on 2007-10-13
took your advice and put the underscores instead of the spaces, works a charm cheers dude

---

