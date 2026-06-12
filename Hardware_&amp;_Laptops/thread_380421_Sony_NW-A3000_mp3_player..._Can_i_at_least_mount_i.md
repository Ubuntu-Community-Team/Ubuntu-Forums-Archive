---
title: "Sony NW-A3000 mp3 player... Can i at least mount it?"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by 3ntity on 2007-03-09
Hello,
I have a Sony NW-A3000 MP3 player, which i use as an external hard drive as well as an mp3 player. I don't know how to mount it (Dapper 6.06). I was able to access it when running the Ubuntu 6.06 liveCD, when it was automounted as soon as i plugged it in. When i go to 'Places -> Computer' it is shown as 'SONY HDD WALKMAN' but i can't access the files on it.

I won't even ask whether i can upload songs onto it through ubuntu :P

Thanks in advance :)

---

### Post by 3ntity on 2007-03-09
**Update:** I believe it's listed under /dev as sdb [sda being my (only) SATA drive], but i can't get it to mount:
```
mount /dev/sdb /media/mp3player/
mount: you must specify the filesystem type
```

and:

```
mount -t vfat /dev/sdb /media/mp3player/
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

and: 
```
mount -t usbfs /dev/sdb /media/mp3player/
```
returns no errors, but does not allow access to the files, instead it shows 4 folders with 1 or 2 files each, all of no use (see attached screenshot).

Hmm... any ideas?

---

### Post by Munken69 on 2008-05-01
Hello

Just use Jsymphonic

HOWTO here:

[http://ww.ubuntuforums.org/showthread.php?t=716477](http://ww.ubuntuforums.org/showthread.php?t=716477)

But for me i did not work before i shutdown and restarted with the nw-a3000 connected.

Now I just love it.

Simpel but very usefull, and stabel.

---

### Post by Munken69 on 2008-05-01
By the way it seems to work for all Sony mp3 player of newer date.

---

