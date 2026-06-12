---
title: "Half Speed SATA"
date: 2010-02-25
forum: Hardware
---

### Post by avix on 2010-02-25
my 320 was showing errors so I bought another 500 gig HD to add to my 500 gig HD that I use for archive and storage. did a clean install of the latest version of Ubuntu onto the new 500Gig. now my system is running quite slow. I did the following checks

/dev/sda:
 Timing cached reads:   1574 MB in  2.00 seconds = 786.90 MB/sec
 Timing buffered disk reads:  276 MB in  3.00 seconds =  91.98 MB/sec

sudo hdparm -I /dev/sda | grep SATA
Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6

/dev/sdb:
 Timing cached reads:   1568 MB in  2.00 seconds = 783.68 MB/sec
 Timing buffered disk reads:  310 MB in  3.01 seconds = 103.03 MB/sec

sudo hdparm -I /dev/sdb | grep SATA
Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5

it looks to me as if they are running at half speed or less. anyone have any ideas?

---

### Post by dabl on 2010-02-25
Run the hdparm -tT command on it two or three times in rapid succession to see the "running" performance.  Just use the up arrow and repeat it a couple of times.  The first run sometimes is slow (cache-clearing?  spinning up to speed?  I dunno why ....).

---

### Post by avix on 2010-02-25
/dev/sda:
 Timing cached reads:   1742 MB in  2.00 seconds = 871.42 MB/sec
 Timing buffered disk reads:  284 MB in  3.02 seconds =  94.13 MB/sec
scotty@tux:~$ sudo hdparm -tT /dev/sda 

/dev/sda:
 Timing cached reads:   1742 MB in  2.00 seconds = 870.96 MB/sec
 Timing buffered disk reads:  178 MB in  3.01 seconds =  59.13 MB/sec
scotty@tux:~$ sudo hdparm -tT /dev/sda 

/dev/sda:
 Timing cached reads:   1690 MB in  2.00 seconds = 845.22 MB/sec
 Timing buffered disk reads:  268 MB in  3.01 seconds =  89.15 MB/sec
scotty@tux:~$ sudo hdparm -tT /dev/sda 

/dev/sda:
 Timing cached reads:   1762 MB in  2.00 seconds = 881.23 MB/sec
 Timing buffered disk reads:  278 MB in  3.02 seconds =  92.19 MB/sec
scotty@tux:~$ sudo hdparm -tT /dev/sda 

/dev/sda:
 Timing cached reads:   1776 MB in  2.00 seconds = 888.19 MB/sec
 Timing buffered disk reads:  280 MB in  3.00 seconds =  93.32 MB/sec
scotty@tux:~$ 


/dev/sda:
 Timing cached reads:   1776 MB in  2.00 seconds = 888.19 MB/sec
 Timing buffered disk reads:  280 MB in  3.00 seconds =  93.32 MB/sec
scotty@tux:~$ sudo hdparm -tT /dev/sdb 

second drive

/dev/sdb:
 Timing cached reads:   1782 MB in  2.00 seconds = 891.14 MB/sec
 Timing buffered disk reads:  328 MB in  3.01 seconds = 108.92 MB/sec
scotty@tux:~$ sudo hdparm -tT /dev/sdb 

/dev/sdb:
 Timing cached reads:   1812 MB in  2.00 seconds = 905.91 MB/sec
 Timing buffered disk reads:  328 MB in  3.01 seconds = 108.96 MB/sec
scotty@tux:~$ sudo hdparm -tT /dev/sdb 

/dev/sdb:
 Timing cached reads:   1732 MB in  2.00 seconds = 865.60 MB/sec
 Timing buffered disk reads:  328 MB in  3.02 seconds = 108.78 MB/sec
scotty@tux:~$ sudo hdparm -tT /dev/sdb 

/dev/sdb:
 Timing cached reads:   1768 MB in  2.00 seconds = 883.66 MB/sec
 Timing buffered disk reads:  324 MB in  3.01 seconds = 107.69 MB/sec
scotty@tux:~$

---

### Post by dabl on 2010-02-25
Looks pretty good -- I think they're working fine.

"Raw Signalling Bandwidth" is one thing, and "Data Transfer Speed" is another, as per:

[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

---

### Post by avix on 2010-02-25
ooook. an artical I read was saying threwputs of 1.5 and 3 gigs. guess it was a crap article or I read it wrong.

thanks for the help Dabl!

---

### Post by dabl on 2010-02-25
Unfortunately most of the user-friendly hard drive benchmarking tools are for Windows.  As an example, here's more:  [http://www.raymond.cc/blog/archives/2008/02/28/measure-actual-hard-disk-perfomance-under-windows/](http://www.raymond.cc/blog/archives/2008/02/28/measure-actual-hard-disk-perfomance-under-windows/)

---

### Post by avix on 2010-02-25
ahem <rant mode on> it's a microsoft conspiricy to keep us poor benighted Linux users from having access to the latest and greatest hardware!!!!!! <rant mode off/>

This obligatory rant was brought to you by the League of Extraordinary Penguins

we now return you to your regular non rant channels.

thanks. again Dabl

---

### Post by dabl on 2010-02-25
> **avix said:**
> 
This obligatory rant was brought to you by the League of Extraordinary Penguins



Hah ha ha  :D

You are welcome!  :popcorn:

---

### Post by dabl on 2010-02-26
OK, I've been doing a little testing with my hard drives and now I am not so sure your hardware is performing as well as it should. I'll show you what I am seeing, and then maybe we can figure out why yours is not doing so hot. My /dev/sda drive, which is about a year old, is:

> root@sidbox:/home/dabl# smartctl -ia /dev/sda                
smartctl 5.40 2010-02-03 r3060 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital RE3 Serial ATA family
Device Model:     WDC WD1002FBYS-01A6B0                
Serial Number:    WD-WMATV0438846                      
Firmware Version: 03.00C05                             
User Capacity:    1,000,204,886,016 bytes              
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8                                              
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Feb 26 14:39:06 2010 EST                       
SMART support is: Available - device has SMART capability.           
SMART support is: Enabled    

and its hdparm test output looks like this:

> root@sidbox:/home/dabl# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   5836 MB in  2.00 seconds = 2918.96 MB/sec
 Timing buffered disk reads:  320 MB in  3.00 seconds = 106.50 MB/sec
root@sidbox:/home/dabl# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   5934 MB in  2.00 seconds = 2968.52 MB/sec
 Timing buffered disk reads:  320 MB in  3.01 seconds = 106.23 MB/sec

So, this is an ext4 filesystem, with no particular tweaking.  I happened to run the test from my debian sid OS, with a 2.6.32 kernel, but I'm confident if I booted into Kubuntu 9.10 and ran it again I'd get similar results.  Unless your hard drives are ancient, I would think you should see better numbers from hdparm.

---

