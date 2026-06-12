---
title: "DVD-RW drive seemingly non-responsive"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by MonkeyZiggurat on 2007-11-28
When I insert a dvd, or cd of any kind, I get no result whatsoever. I can't find the drive manually, but it is in the list in Preferences -> Hardware Information (IDE Device (Master) - HL-DT-ST DVDRAM GSA-4167B).

I've seen this asked for in other similar threads, so here's the result of "cat /ect/fstab":

:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=72ca26d9-68ac-423e-bc16-b4691f2d0b07 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=a2a81cd8-faf2-4310-87cf-2f76a0374fbb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0




If I cd into /media/cdrom0 or cdrom1 and type "ls" I get no files listed.

I'd appreciate some pointers, because as you can probably tell, I'm new at all this linux malarky and don't know where to start with this.

cheers.

---

### Post by mouseboyx on 2007-11-28
Try:
```

sudo mount /dev/scd0 /media/cdrom0
```
or
```

sudo mount /dev/scd1 /media/cdrom1
```
in a terminal.

---

### Post by MonkeyZiggurat on 2007-11-29
ok, feel like a tool for not trying that already, but it's telling this when I try to mount 'em:

:~$ sudo mount /dev/scd0 /media/cdrom0
mount: special device /dev/scd0 does not exist

:~$ sudo mount /dev/scd1 /media/cdrom1
mount: special device /dev/scd1 does not exist

I actually shouted at my computer and pointed out my CD tray, but it took no notice.

---

### Post by lbarcala on 2007-12-13
I have the same problem. My CD/RW unit worked fine with Dapper Drake. Now I have a clear new Gutsy Gibbon ad the cd does not work.

sudo mount /dev/scd0

mount: special device /dev/scd0 does not exist.

The fstab includes the entry:

/dev/scd0     /media/cdrom0    udf,iso9660  user,noauto,exec  0    0

Any solution to the problem?

---

### Post by Hailey Stargazer on 2008-04-10
Did anyone ever find a solution to this problem? I am experiencing the same thing....:confused:

---

### Post by greenstar on 2008-04-10
This thread is pretty old and not watched much, I imagine. If you want help, don't post on the end of someone else's help request thread (old or new). That's kinda like butting in on a conversation or cutting line in the real world. Instead, start your own new thread and quote or add a link to whatever relevant thread(s) or post(s) you find. The exception to this is when someone posts a thread offering help to others. An example of this would be a HowTo thread. Doing so will ensure that you are likely to receive more help of higher quality faster.

Greenstar

---

### Post by lbarcala on 2008-04-14
In my case the problem was that the unit has crashed just after ubuntu installation. The hardware unit have dead due to a hardware problem. It was a rare coincidence but it was truth.

---

