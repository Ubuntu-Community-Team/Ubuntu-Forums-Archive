---
title: "I can't use my whole hardisk"
date: 2010-02-13
forum: Hardware
---

### Post by someone235 on 2010-02-13
I have a hardisk with 320GB in my PC, but if I check what is the capacity of my hardisk in "Disk Usage Analyzer" I see just 290.6GB - I have no access to almost 10% of my DISK!
Someone has any idea how can I solve this problem, and what is its reason?
thx in advance
someone235

---

### Post by peterroots on 2010-02-13
I have not done the maths but what size GB was used to describe your hard drive and what size is your disk usage analyser using?

Traditionally a kilobyte was 1024 bytes a megabyte 1024 kilobytes and a gigabyte 1024 megabytes but now they have gone decimal (well the problem is some people think they have and others don't agree)
This gets confusing! (it is a bit like British and US English speakers trying to communicate - we understand what the other is saying but we don't understand it in the same way they do)

Technically Kilo Mega and Giga should now refer to multiples of 1000 while
Kibi Mebi and Gibi refer to the binary multiples of 1024

My guess is that your 'missing' hard drive space vanished in a differnece of interpretation of 'Gigabyte'

---

### Post by howefield on 2010-02-13
You'll also use some of the space in the formatting / file system.

A 320 gigabyte disk (or any disk for that matter) won't give you 320 gig of free space.

---

### Post by kgarbutt on 2010-02-13
View it in gparted. If you don't have it (it is in Ubuntu repositories), you can install it with 'sudo apt-get install gparted' from the terminal. Also if you have a Ubuntu live CD, you can boot that and use gparted from the live cd to view your hard-drive. I would just install it because it useful for other things like formating fash-drives, SD cards, etc.

---

### Post by someone235 on 2010-02-13
> **howefield said:**
> You'll also use some of the space in the formatting / file system.

A 320 gigabyte disk (or any disk for that matter) won't give you 320 gig of free space.
OK, I calculated it, and 320GB in the binary schale equals 298GB in the decimal scale, but where is the 8 GB?
8 GB is a lot of disk space, and I don't think the filesystem need it...

---

### Post by oldfred on 2010-02-13
You typically lose about 5% to the file system. Usually it is hidden to keep track of the journaling so you can recover from an error.

[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

---

### Post by someone235 on 2010-02-14
ok, thx guys

---

