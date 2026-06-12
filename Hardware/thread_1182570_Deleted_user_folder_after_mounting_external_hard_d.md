---
title: "Deleted user folder after mounting external hard drive"
date: 2009-06-09
forum: Hardware
---

### Post by umeboshi80 on 2009-06-09
Hi!

I am not sure what I did, but the consequence was drastic (I have posted to general help already but did not get an answer, so sorry for double posting). I wanted to gain write access to my external hard drive and searched the forum. One thread said to look for where the drive was mounted and I checked it with fdisk. The I did the following (following the instructions from the thread):

sudo mkdir /media/external
sudo mount -t auto /dev/sdb1 ./external

I got no error messages but when I cd to my home folder and then my user....IT IS EMPTY. I cannot start Nautilus, I cannot do ANYTHING.

Can anyone please tell me what happened and how i can fix it?

Very much appreciated (since in panic mode)...

Hadassa

---

