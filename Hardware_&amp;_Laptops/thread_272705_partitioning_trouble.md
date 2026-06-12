---
title: "partitioning trouble"
date: 2006-10-06
forum: Hardware &amp; Laptops
---

### Post by icehac on 2006-10-06
I hope this is the right place to post, and I'm sorry if it isn't.  But here's my problem. I was given a dell poweredge 2300 by a friend of mine for free. When I got the box it has CentOS on it, but I've always used ubuntu for a desktop OS, so I thought i'd isntall it on this box as well. Well, the very 1st time I installed Ubuntu it worked totally fine, no errors at all (this is using the live cd). Now I want to install a LAMP Ubuntu server, and now when I try to partition my SCSI drive (I have 3 btw, all 9 gigs), it hangs. It hangs on every OS I try to install, including windows. I really need some help here guys :(.

---

### Post by wieman01 on 2006-10-06
This does not sound right... Seems like a hardware failure if even Windows cannot install.

Have you tried formating the HD using the Live CD and GParted which comes along with it? Guess that's the ultimate resort...

---

### Post by icehac on 2006-10-06
that's the thing though, right when I tried to install the Ubuntu server it didn't work, but right before I did install it I was on ubuntu desktop. But I will give the gparted a go.

---

### Post by wieman01 on 2006-10-06
> **icehac said:**
> that's the thing though, right when I tried to install the Ubuntu server it didn't work, but right before I did install it I was on ubuntu desktop. But I will give the gparted a go.
Guess the Live CD will help. Fire up Gnome Partition Editor (GParted) and give it a try. If you have no success, there may be on other option.

[http://www.sysresccd.org/Download]("http://www.sysresccd.org/Download")

---

### Post by icehac on 2006-10-06
I tried sys rescue as well, it wouldn't exec qt_parted because "ash: can't access tty; job control turned off", what could be the cause of this?

---

### Post by icehac on 2006-10-06
bumpty bump

---

### Post by wieman01 on 2006-10-07
> **icehac said:**
> I tried sys rescue as well, it wouldn't exec qt_parted because "ash: can't access tty; job control turned off", what could be the cause of this?
Went offline. Sorry, mate. But as for this one, beats me. :-(

---

### Post by NoTiG on 2006-10-08
can you tell us output of $ sudo fdisk -l

---

