---
title: "NTFS partition disconnects when accessed"
date: 2014-02-08
forum: Hardware
---

### Post by phaerel on 2014-02-08
Hello!

Whenever I try to access my internal hard drive (meaning I actually do something with it, not only browsing through with the file browser. eg. updating mpd db, compressing data, writing data), it works for approx. 1 second,
then it just "freezes" (the point where the drive gets unmounted) and I get an input/output error. But the fact that the drive works fine whenever it gets used on Windows and the S.M.A.R.T. values are more than just fine lets
me guess that this is a software problem.

I am using Ubuntu 13.10, but I had this problem in previous versions too. It seems like I only get this error with Ubuntu (although I can be remembering wrong).
The drive is an WD Caviar Green 2TB one.

I researched online and tried to perform a "hdparam -s 0 /dev/sdx", which disables the standby option of the drive (atleast I got it like that).
This unfortunately didn't help. I also tried to add the drive to the /etc/fstab, just to try it out. Didn't help either.

I really hope someone could help me get this fixed, since I seriously don't want my data to be unusable with Ubuntu (or GNU/Linux generally).
If you need some data about the drive or other things, let me know.

Thank you in advance
phaerel

---

### Post by tfrue on 2014-02-09
I would like to see your boot-info URL, follow the directions on this website and then post the URL here.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by phaerel on 2014-02-09
Hello tfrue,

[here]("http://paste.ubuntu.com/6902691/") is the requested BootInfo output.

Thank you
phaerel

EDIT: After some testing I found out that the drive only ejects/unmounts whenever there is an reading action going on (eg. updating mpd db). That kind of wonders me.

---

### Post by phaerel on 2014-02-14
Hello,

I hope that a bump is allowed after this time.

Thank you,
phaerel

---

### Post by tfrue on 2014-02-15
Hey sorry, I completley missed this showing up in my feed :(. I'm currently going through the boot-script, but I probably won't be finished until Sunday or Monday. I have to work tonight and Sunday night, but I just wanted to let you know I haven't forgotten about you.

---

