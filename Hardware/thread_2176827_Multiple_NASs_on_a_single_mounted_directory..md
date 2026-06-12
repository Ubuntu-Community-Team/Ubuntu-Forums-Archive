---
title: "Multiple NASs on a single mounted directory."
date: 2013-09-26
forum: Hardware
---

### Post by mildenhall on 2013-09-26
I have a WD Mybook NAS that is SAMBA and NFS compatible. Everything works an absolute dream in Ubuntu 13.04. I mount the drive on bootup using an entry in FSTAB.

I am about to run out of space on my NAS and a double sized NAS is a bit expensive. A cheaper option could be to buy an identical sized NAS, and use two drives. I could add a 2nd entry in FSTAB and have two directories mapped to my two NASs. However.... could I mount BOTH the drives onto a single directory so the two NASs would appear as one single mapped/mounted directory?

TIA

---

### Post by LewisTM on 2013-09-28
You should try **mhddfs** (in the repos). It's very simple to use and has few options; most operations are done intelligently. It will merge two mount points into a third.
It can be run by a user or used in the context of fstab.
Example of a commandline:
```
mhddfs /nfs/mount1 /nfs/mount2 /mergednfs
```
See [FONT=Courier New]man mhddfs[/FONT] for more info.
Cheers!

---

### Post by mildenhall on 2014-01-14
Thanks! Sorry for taking so long to reply, I've only just bought my 2nd NAS. mhddfs looks like just what I need. I'll try it when I get home.

---

