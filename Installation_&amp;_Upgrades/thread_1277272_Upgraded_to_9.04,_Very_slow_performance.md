---
title: "Upgraded to 9.04, Very slow performance"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by chkhurum on 2009-09-28
I used 8.04 for quite sometime and was well used to small problems of Ubuntu world. 

But in order to install mobile internet I had to upgrade to 9.04 and was able to install the internet but that brought lots of other problems. I shall list them separately on separate threads.

1. When I updgraded to 9.04 I found out that that it is very very slow. It boots quicky without any problem but after that it becomes really slow. CPU usage is around 30% ~ 50% or sometime even lower but if I check "Process" tab in System Monitor in total it is only taking  around 5% ~ 10%. Just to give an example when i type in text field the text appears after sometime delay. I am using 
Ubuntu
Release 9.04 (jaunty)
Kernel 2.6.28-15
GNOME 2.26.1

Hardware
Memory 1.9 GB (more than 50% remains free so no problem with memory)
Due core processor L7500 @ 1.60GHz

Any suggestion how to speed this thing up? Unable to attach the kernel log, its too big to attach :)

---

### Post by moster on 2009-09-28
You could install newer kernel :)
But deinstall nvidia/ati proprietary VGA drivers before and read about installing new one apropriate for newer kernel.
[URL="http://kernel.ubuntu.com/~kernel-ppa/mainline/"]
http://kernel.ubuntu.com/~kernel-ppa/mainline/[/URL]
I suggest 2.6.30 and latest nvidia ver.185 (if you have nvidia) I am not sure that for latest kernel have proprietary drivers

Just a friendly suggestion, a wash my hand from any mockup you maybe encounter :D

---

### Post by chkhurum on 2009-09-28
Thanks. It worked. Great help.

---

