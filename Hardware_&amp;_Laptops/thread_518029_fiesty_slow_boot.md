---
title: "fiesty slow boot"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by Ffuzzdaddy on 2007-08-05
i just recently switched to ubuntu. the problem is when i start my computer it goes to the ubuntu load screen loads halfway and sits there for about 2 mins, then starts to load again. i tried ubuntu before with the windows installer and it booted perefctly. should i reinstall or do i need to change some thing? any help would be great.

---

### Post by tgalati4 on 2007-08-05
Hit Alt-F1 during the boot screen and take note of the last few messages before it pauses.

---

### Post by Ffuzzdaddy on 2007-08-05
kinit no resume image doing normal boot

[         14.959653] FWH not detected

- it sits there for about a min, then resumes booting

---

### Post by tgalati4 on 2007-08-05
I don't know what FWH is but it looks like the hardware detection algorithm is getting hung up and then times out (thank goodness) to resume booting.  Did you make any hardware switches lately?  Perhaps move a CD ROM drive or an internal card?

---

### Post by Ffuzzdaddy on 2007-08-05
no its a laptop, i havent changed anything. it does have an ati graphics card though.

---

### Post by tgalati4 on 2007-08-05
From a terminal, post the output of:

>lsmod

>lspci -vv

and

relevant portions of

>dmesg | more

---

### Post by tallankybstrd on 2007-09-05
I also have the same problem on a Dell Latitude D420.  I suspect because there is no internal CD-ROM drive (there is an external one that plugs into the back) that it might be searching for that?  Does your computer have the same type of CD drive?  I will try later to see what happens when I plug it in.

---

