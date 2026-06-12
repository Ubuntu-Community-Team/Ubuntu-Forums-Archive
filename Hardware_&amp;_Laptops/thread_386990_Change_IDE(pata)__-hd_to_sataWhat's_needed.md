---
title: "Change IDE(pata) / -hd to sata?What's needed?"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by Anagonda on 2007-03-17
Ok, my problem is:

I need to get a new hd for my xbox(old one said "bam" and then there was silence), but I was thinking that it would be much nicer to get a bigger hd to my pc. I could swap my pc's old ide-hd to xbox and buy a new sata hd to my pc. I don't want a pata hd, thats "old" you know.

So is it possible to somehow transfer the whole root system to new hd. Last time I changed hd I tried cp -some command(maybe -a?). Can't remember exaclty, but it didn't work. I lost my devices on the move and after few tries lost my nerves. So I formatted the disk and installed ubuntu from scratch. But it's almost 3 years ago and I have customized my system in the time (running enlightenment etc).
So now I don't want a fresh install. Or maybe if thats the last thing to do...

So is there a app for linux to clone my hd? Or any other way? I like the easy way, but reliable ofcourse.
I'm thinking I am in a little problem when changing from pata to sata hd. Or maybe I just remember too much of the old, not so good times, with mandrake and red hat(with scsi-systems and first sata drives)...

Any one have done this? Did it work?

EDIT: Oh, and I tried search. Didn't find correct search words or there isn't this kind of threads?

---

### Post by Anagonda on 2007-03-20
Ok, thanks for your answers :lolflag: 


But I did change the hd. Everything went ok. Except the famous bluez-utils bug in ubuntu. I'm using Logitech bt-keyboard and when I tried to start ubuntu from live cd it forces bluez utils to start. And then keyboard or mouse doesn't work.

So I could not run the DD in any way.

So I found "ghost 4 linux" boot cd image from sourceforge and did it with that. It wen't fine. 250gb did about 5 hours to copy. And because I removed all pata disks grub went fine. I only changed /etc/fstab and mtab to correct disks. And thats all for now.

---

