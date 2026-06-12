---
title: "Using Gparted &quot;Live&quot;"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by lsutiger on 2008-04-10
Is there anyway to use Gparted "live"? I want to shrink my / folder and modify my /home folder.
Other than booting off a cd?

I am guessing not, but worth a try asking the brainiacs out here :D

---

### Post by metalf8801 on 2008-04-10
both of these live CDs have G parted on them 

[http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)
and
[http://distrowatch.com/systemrescue](http://distrowatch.com/systemrescue)

there are a lot of others but these are the 2 that I know for sure 
I use Systemrescue

---

### Post by RTrev on 2008-04-11
> **lsutiger said:**
> Is there anyway to use Gparted "live"? I want to shrink my / folder and modify my /home folder.
Other than booting off a cd?

I am guessing not, but worth a try asking the brainiacs out here :D

Please forgive my nosiness, but I'm curious what's wrong with booting from a CD to run GParted?

The only other way I can think of would be to boot *another* Linux system on the same machine, and do it from there.  But the only difference would be booting from the hard drive rather than the CD to get GParted running.

If you're asking if GParted can operate on a partition which is already mounted and in use, I believe the answer is no.  For example, I don't believe I could boot to a system on my SDA, then run GParted and try to modify SDA.

HTH,
Bob

---

### Post by prshah on 2008-04-11
> **lsutiger said:**
> Is there anyway to use Gparted "live"?
Other than booting off a cd?


If CD boot is NOT an option, USB boot to the rescue; eh? Or have I just totally misunderstood the question?

Or you COULD remove the hdd, put it in an enclosure, boot in another linux system and then use gparted? WARNING WARNING- I just throw it out as a suggestion, don't know if it can be done properly or not.

---

### Post by OmegaBLK on 2008-04-11
> **lsutiger said:**
> Is there anyway to use Gparted "live"? I want to shrink my / folder and modify my /home folder.
Other than booting off a cd?

I am guessing not, but worth a try asking the brainiacs out here :D

Like the other posters, I am not too sure what is that you exactly want to do, but you can install gparted from the main repository to run from within your currect OS instead of booting from the GParted LiveCD.

[http://packages.ubuntu.com/gutsy/gparted](http://packages.ubuntu.com/gutsy/gparted)

---

### Post by OmegaBLK on 2008-04-11
^To add to my post(or reiterate what **RTrev** said above), you will need to umount any partitions that you want to work on.  You can use gparted in a current running OS, but you can't touch any mounted partitions.  And in your case since / and /home need to be mounted you will not be able to perform any resizing operations.  You will need to use the Live CD/USB or you must boot into another OS/installation of Ubuntu which uses a seperate /home and run gparted from there.

Take a look at the docs for more info on your options:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by lsutiger on 2008-04-12
Thanx for the replies! You have confirmed my suspicions! I just have this thing about powering down when I can run for ages on end, unlike M$ {insert version here} :)

Oh well, I guess I'll do it now while I only have 3 days invested in this boot.

---

### Post by BkkBonanza on 2008-04-12
Well you could suspend/hibernate, then remove your hard drive to another system and do the work, then re-install it and try starting up again.

I've never tried that but sounds like it should work. I don't think suspend/hibernate stores the data in a place that can't be found after starting again but I could be wrong.

Anyway, idea just occurred to me so could be totally wacky.

Chris :)

---

