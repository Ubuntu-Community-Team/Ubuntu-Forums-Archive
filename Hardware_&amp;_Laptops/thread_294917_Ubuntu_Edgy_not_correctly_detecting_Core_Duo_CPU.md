---
title: "Ubuntu Edgy not correctly detecting Core Duo CPU"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by garethc on 2006-11-07
Hi all,

I just did a clean install of Edgy on my Dell Inspiron 6400, and found Ubuntu not recognizing my Intel Core Duo T2400 CPU. I only discovered this upon trying to install Network Manager for my wireless, and getting a message to the effect that this program is not designed for the i386! So I went into hardware manager, and saw that although Ubuntu was detecting two processors, it seems not to know what the hell they are. I find this confusing as my last Edgy install (long story) about a week ago successfully detected my Core Duo.

To make things even more confusing, the Live CD process *DOES* correctly detect my CPU!

I have tried reinstalling Edgy (again) to no avail - any ideas!!??

Cheers,
G ](*,)

---

### Post by DHGE on 2006-11-07
```
cat /proc/cpuinfo
```

gives on my machine:

> 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
...


What is your problem with "not detecting"?

---

### Post by garethc on 2006-11-07
Ok,

So obviously I'm misunderstanding the problem here. Why is Network Manager not installing because "it is not designed to run" on my "computer type", defined by Ubuntu as "i386'? My CPU, the Core Duo, is classed as a 686, is it not?

And why is this problem occuring only after install, and not during preview (live CD)?

Cheers,
G

---

### Post by organica on 2006-11-07
Yeah, I got that same error when I tried to install packages from the CDROM without an internet connection.  I had to use the ethernet connection to install the Network Manager which you can find in Add/Remove Programs.

---

### Post by garethc on 2006-11-07
Yeah,

The catch-22: I need and internet connection to get an internet connection! Unfortunately I don't have "wired" access, only wireless.

G

---

### Post by DHGE on 2006-11-08
First: U should file a bug ...

When you have no internet-connection with the target PC get the packages (look for dependencies!) from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and save it on a storage medium you can read on your target.

HTH

---

