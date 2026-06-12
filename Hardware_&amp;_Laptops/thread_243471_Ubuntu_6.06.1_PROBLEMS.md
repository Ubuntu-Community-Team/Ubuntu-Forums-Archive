---
title: "Ubuntu 6.06.1 PROBLEMS"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by JKoder on 2006-08-25
Hello
After i have installed the new release of Ubuntu ( 6.06.1 ) i have sound and network problems.
Sound is working but is VERY slugish something like uuuubbbbuuuuuunnnnttttuuuu. And my network takes about 5-10 minutes to be up.

Before this release everithing was JUST FINE. 
PLEASE anyone help me cause i whant the new release !!!!

Thank you

---

### Post by -PANDA- on 2006-08-25
Hmm... try to install ubuntu again maybe that would work?

---

### Post by JKoder on 2006-08-25
Installing Ubuntu 6.06 is OK. everihing runs fine. But i what Xubuntu now and i only get the new release.
And i what to know how to solve this problems .. because otherwise i will alwais have problems .. whenever i will do an update

---

### Post by Miguel on 2006-08-25
Hi guys,

Actually, ubuntu 6.06.1 is identical to a 6.06 that has gone through all the upgrades. You said that a clean 6.06 install was working OK. What are the updates you have after a clean 6.06 install? Because it might be a regression in one of the packages.

Anyway, it would be good if you told us your hardware.

---

### Post by JKoder on 2006-08-29
Hi.
First of all. I did a little test. I have installed 6.06 and update all packages that Update notifier told me to BUT i did not update linux kernel. Now Everithing is ok. If i update Linux Kernel ... everithing is much much slower. The problem is that 6.06.1 uses that new kernel and i cannot use any new Ubuntu distro :((


Please help

Hardware:
Fujitsu Siemens Amilo L7300
1,5 GH Intel Celeron Mobile
256 RAM
on Board Via video card

---

### Post by manfromthezoo on 2006-08-29
Yep, I own an L7300 too and had exactly the same issues. Likewise with 6.0.6, no problems at all. Specifically, when the little bongo sound plays when you get the main "Ubuntu" log-in screen, it loops again and again and again and.....well, you get the idea. The machine slows to a crawl and is unusable. Unfortunately, this laptop is used by my parents and they needed it back - so I had to re-Ghost XP back onto it, pending me researching this issue and finding a solution.

Ok, so it looks like a kernel update that's done it. But personally I want to be able to keep the kernel up-to-date. Anyone know if a bug report has been filed for this?

It's a pity, I love Ubuntu and want my folks to use it....AAARR.

---

### Post by manfromthezoo on 2006-08-29
Yep, I own a Fujitsu-Siemens L7300 too and had exactly the same issues. Likewise with 6.0.6, no problems at all. Specifically, under 6.0.6.1 when the little bongo sound plays when you get the main "Ubuntu" log-in screen, it loops again and again and again and.....well, you get the idea. The machine slows to a crawl and is unusable. Unfortunately, this laptop is used by my parents and they needed it back - so I had to re-Ghost XP back onto it, pending me researching this issue and finding a solution.

Ok, so it looks like a kernel update that's done it. But personally I want to be able to keep the kernel up-to-date. Anyone know if a bug report has been filed for this?

It's a pity, I love Ubuntu and want my folks to use it....AAARR.

---

### Post by JKoder on 2006-08-30
> **manfromthezoo said:**
> Yep, I own a Fujitsu-Siemens L7300 too and had exactly the same issues. Likewise with 6.0.6, no problems at all. Specifically, under 6.0.6.1 when the little bongo sound plays when you get the main "Ubuntu" log-in screen, it loops again and again and again and.....well, you get the idea. The machine slows to a crawl and is unusable. Unfortunately, this laptop is used by my parents and they needed it back - so I had to re-Ghost XP back onto it, pending me researching this issue and finding a solution.

Ok, so it looks like a kernel update that's done it. But personally I want to be able to keep the kernel up-to-date. Anyone know if a bug report has been filed for this?

It's a pity, I love Ubuntu and want my folks to use it....AAARR.
It's good to know that someone elese has this problems..... mabye in this way someone will find the bug or let us know what to do

---

### Post by Miguel on 2006-08-30
Well, if your problem is kernel-related, you have to do two things:
[list=1][*] Fill a bug report
[*] Use apt to force a previous version
[/list]

You can install the original dapper kernel by issuing the command
```

sudo apt-get install linux-image-2.6.15-23-386

```

Of course, if you need the restricted modules or the headers, repeat the command above after substituting "image" with "restricted-modules" or "headers" respectively.

*EDIT: If you never delete this old kernel, it will always be available at boot time with grub*

---

### Post by Miguel on 2006-08-30
Anyway, I have to make you a question. When you launch Ubuntu with the new kernel, what is the output of the following command?
```

sudo hdparm -tT /dev/hda

```

First have a look at "man hdparm" so you know what this command does. Please note that if you have a SATA disk, you will have to replace /dev/hda with /dev/sda. Also, the first run is usually slower, so repeat it a few times. My output, with a 5400rpm HD (laptop) is:
```

$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   2244 MB in  2.00 seconds = 1121.93 MB/sec
 Timing buffered disk reads:  100 MB in  3.02 seconds =  33.11 MB/sec

```

Thanks

---

### Post by JKoder on 2006-08-31
> **Miguel said:**
> Anyway, I have to make you a question. When you launch Ubuntu with the new kernel, what is the output of the following command?
```

sudo hdparm -tT /dev/hda

```

First have a look at "man hdparm" so you know what this command does. Please note that if you have a SATA disk, you will have to replace /dev/hda with /dev/sda. Also, the first run is usually slower, so repeat it a few times. My output, with a 5400rpm HD (laptop) is:
```

$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   2244 MB in  2.00 seconds = 1121.93 MB/sec
 Timing buffered disk reads:  100 MB in  3.02 seconds =  33.11 MB/sec

```

Thanks

Hu right now i am using the old kernel so i can past the current command output and as soon as i will install the new kernel again i will past again 

/dev/hda:
 Timing cached reads:   1572 MB in  2.00 seconds = 785.73 MB/sec
 Timing buffered disk reads:   56 MB in  3.17 seconds =  17.65 MB/sec

---

