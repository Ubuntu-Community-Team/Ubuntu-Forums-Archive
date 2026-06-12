---
title: "Old Laptop experiment: Gateway Solo 2000"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by duus on 2005-11-20
I have an old windows 98 laptop--a Gateway Solo 2000--that does nothing but collect dust, so I thought I would try to but linux on it and maybe use it to display pictures or something.

I'm aware it doesn't meet the minimum system requirements, and stuff, but the alternative is the trash heap :)

Anyway, it boots off the install cd (Hoary, I'll admit...but Breezy wouldn't be particularly better, right?) and it says it's installing in Low Memory Mode.  And then it gets to Retrieving nic-extra-modules-2.6- something and then gets stuck on 0% and eventually dies.  Thoughts?  Thanks!

---

### Post by dbott67 on 2005-11-20
What are the specs?  I've got Breezy installed on a P2-300 with 256 MB RAM and an 8 GB Hard drive.  A little sluggish, but once I switched to Opera & Abiword, it's become quite a functional little laptop.

CPU info:
```
dbott@breezy:/proc$ cat cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 5
model name      : Pentium II (Deschutes)
stepping        : 2
cpu MHz         : 299.973
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
bogomips        : 593.92

```
RAM memory info:
```
dbott@breezy:/proc$ free -o -m -t
             total       used       free     shared    buffers     cached
Mem:           250        244          5          0         16         54
Swap:          203         78        125
Total:         454        323        130
```
Hard drive info (dual-boot with Hoary from when I installed the Breezy preview):
```
dbott@breezy:/proc$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             3.8G  2.1G  1.6G  58% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  114M  10% /lib/modules/2.6.12-9-386/volatile
```
-Dave

---

### Post by duus on 2005-11-20
ah, yes, your machine would blow mine away.

32 megs of RAM, GenuineIntel Pentium I processor, and two 2 gig harddrives.  32 megs!  I didn't know it was so low until you prompted me to check.

---

### Post by PaganHippie on 2005-11-21
I don't think you're going to get very far in Ubuntu with only 32MB of RAM, though you might check out [Ubuntu Lite]("http://ubuntulite.org").  You might also want to consider one of the smaller/light distros, such as [Vector ]("http://www.vectorlinux.com")(Slackware-based) or [DamnSmallLinux]("http://www.damnsmalllinux.org") (Debian-based so you can still use apt-get).

---

### Post by quietglow on 2005-11-21
I'll second the VectorLinux: I've run it on a machine with 64m of ram and it ran very well. I believe at that time its default w/m was Ice--or maybe Blackbox?

---

### Post by adam.tropics on 2005-11-21
>  maybe use it to display pictures or something.

if poss why not get wireless, presuming you run another slightly more musclebound machine, and set it up as an access point somewhere in your house for whatever...music, photos, weather reports!!??
presumably running as a session from another machine must share some of the load and reduce the necessary install a fair bit?

---

