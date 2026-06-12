---
title: "Memory query - 16gig machines shows 15.7 in Ubuntu 12.04"
date: 2013-12-08
forum: Hardware
---

### Post by AD-RS1600i on 2013-12-08
Hi everyone,

I have a 16gig RAM systems that under Windows is listed as 16gig but under Ubuntu is listed as 15.7 gig machine. I am guessing the OS is pinching 300mb for a crash kernel or similar but I would really like to know for sure from the experts :)

As an experiment I created a 8gig Ubuntu 13.x machine in Virtualbox that listed itself as 7.8gig so I am guessing there is a logical explanation rather than hardware fault :)

Brilliant OS by the way, I've been using Ubuntu now as my sole OS for over a year, and made a donation accordingly on downloading the latest 12.04 ISO for my new build.

Thank you in advanced,

Adrian

---

### Post by AD-RS1600i on 2013-12-08
free -m

total       used       free     shared    buffers     cached
Mem:         16048       1276      14772          0         34        452
-/+ buffers/cache:        788      15259
Swap:        16379          0      16379

I believe 16 gig of RAM is 16384mb :(

---

### Post by The Cog on 2013-12-08
I have read before (can't remember where) that free doesn't list the memory occupied by the kernel, and as such will always show around 300M less than is physically present (it can never be free).

---

### Post by sanderj on 2013-12-08
If you want to see the RAM that Windows is reporting, do this:

```
sudo dmidecode | egrep -A8 -i -e "Memory Device" | grep -i MB | grep -vi range

```

Example:
```
$ sudo dmidecode | egrep -A8 -i -e "Memory Device" | grep -i MB | grep -vi range
	Size: 2048 MB
	Size: 2048 MB
```

HTH

---

### Post by Will_McDade on 2013-12-08
Well I have 4 gig ram and it says i have 3.2 gigs because my system has dedicated some to graphics, and other, etc

---

### Post by AD-RS1600i on 2013-12-09
Hi everyone,

In the first instance, many many thanks for taking time to reply I really appreciate it!! :)

I agree with everyone above that this is standard Linux behaviour as today on a really big machine, I created a virtual machine with 16384mb then ran Ubuntu from the live CD and again it reported the machine as having 15.7gig. I am relieved, it means my hardware is ok :)

Thank you everyone - I bet the kernel has it! :)

Adrian

---

### Post by drmrgd on 2013-12-09
Color me learned!  I never realize that the system did this, and just assumed that what it needed would show up in as buffered memory.  Sure enough, though, it's true:

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:         32151      31372        778          0       3122      23967
-/+ buffers/cache:       4282      27868
Swap:        15258          0      15258

$ bc <<<32*1024
32768

```

This is good to know for future reference!

---

