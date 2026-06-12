---
title: "Not copying to SD card..."
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by msikka on 2007-03-28
Hello all,
  
I have a Panasonic CF-73 laptop that has Ubuntu 6.10 on it, and seems to be running just fine. This laptop has an SD card slot on it and when I insert my 2GB Kingston SD card into it, Ubuntu detects it as a MMC card and even displays it's contents. Yesterday I was able to copy some stuff on to it, but it did not finish the process (seemed to go on and on, so I had to kill it). Today when I inserted the card again, and deleted the junk I had on it, I'm not able to copy anything on it. I don't have the permission!

So, on a terminal I tried to change write permissions, and this is what I get:

msikka@obelix:/media$ chmod 777 mmcdisk
chmod: changing permissions of `mmcdisk': Read-only file system
msikka@obelix:/media$ ls -l
total 40
lrwxrwxrwx 1 root   root       6 2007-03-22 18:10 cdrom -> cdrom0
drwxr-xr-x 2 root   root    4096 2007-03-22 18:10 cdrom0
drwx------ 3 msikka msikka 16384 1969-12-31 18:00 mmcdisk
drwxr-xr-x 2 root   root    4096 2007-03-26 18:34 USB20FD


It is reported as a "Read-only" file system? How can I resolve this?

Thanks

---

### Post by Tuksks on 2008-02-20
hi. i got similar problem. I got 2GB Kingston SD card too. I cant copy bigger files e.g. 350MB movie. If i copy some smaller files, its ok. But when i insert card into reader again, the files aren't there. They realy copy there after 10-15 tries :(
As you wrote about your permissions. I got it the same as you, and after i tried to use chmod, nothing happened. I dunno if the Kingston is that problem or what.

---

