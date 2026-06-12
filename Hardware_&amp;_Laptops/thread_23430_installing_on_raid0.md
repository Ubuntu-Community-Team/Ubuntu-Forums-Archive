---
title: "installing on raid0"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by octothorpe on 2005-04-01
is there anyway i can install ubuntu on my raid0 config? please help :(

---

### Post by Dracontopes on 2005-04-02
I've tried this a couple of times, but the thing is, if you use a normal/cheap RAID controller then linux will see it as a normal SATA controller, with single HDD's etc. It's because those RAID cards are 'software' RAID adapters, which need drivers from the OS to run properly. And that is where the problems start :-| For 2.4 there were Medley drivers I thought, don't know if those work. The best thing to do is make a RAID set within Ubuntu (software raid) and boot from that, OR recompile the kernel with built-in drivers, but I haven't tried that ;)

---

### Post by TheGodFather on 2005-04-04
[QUOTE=octothorpe]is there anyway i can install ubuntu on my raid0 config? please help :([/QUOTE]
 It's possible because I've installed a Debian sarge on my raid system but you need a third disk where you can install the distro and then move everything on the raid after making some configurations, take a look at my reply here:
[Re: Dual Boot (Weird HDD configuration)](http://ubuntuforums.org/showthread.php?p=115364#post115364)

---

