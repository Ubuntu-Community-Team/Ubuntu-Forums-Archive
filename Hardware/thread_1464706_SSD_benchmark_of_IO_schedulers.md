---
title: "SSD benchmark of I/O schedulers"
date: 2010-04-28
forum: Hardware
---

### Post by uid313 on 2010-04-28
By default Ubuntu uses the [CFQ]("http://en.wikipedia.org/wiki/CFQ") I/O scheduler which is great for hard disks.
CFG does smart choices which makes I/O faster for mechanical platter hard disks, but these smart choices while faster for mechanical disks are slower for SSD.

Other schedulers are [noop]("http://en.wikipedia.org/wiki/Noop_scheduler") and [deadline]("http://en.wikipedia.org/wiki/Deadline_scheduler").

I have an Intel X-25M G2 80 gb SSD.
I did some benchmarks between the I/O schedulers using hdparm. I ran the tests three times for higher accuracy.
sudo hdparm -t /dev/sda for timed buffered disk reads
sudo hdparm -T /dev/sda for timed cache reads

> ----------- [COLOR="Red"]cfq[/COLOR]
 Timing buffered disk reads:  630 MB in  3.00 seconds = 209.73 MB/sec
 Timing buffered disk reads:  634 MB in  3.01 seconds = 210.56 MB/sec
 Timing buffered disk reads:  632 MB in  3.00 seconds = 210.64 MB/sec

 Timing cached reads:   6450 MB in  2.00 seconds = 3230.38 MB/sec
 Timing cached reads:   6274 MB in  2.00 seconds = 3141.61 MB/sec
 Timing cached reads:   6534 MB in  2.00 seconds = 3272.91 MB/sec


----------- [COLOR="Red"]deadline[/COLOR]
 Timing buffered disk reads:  636 MB in  3.01 seconds = 211.22 MB/sec
 Timing buffered disk reads:  634 MB in  3.00 seconds = 211.31 MB/sec
 Timing buffered disk reads:  638 MB in  3.00 seconds = 212.34 MB/sec

 Timing cached reads:   8386 MB in  2.00 seconds = [COLOR="SeaGreen"]4200.94[/COLOR] MB/sec
 Timing cached reads:   8396 MB in  2.00 seconds = [COLOR="SeaGreen"]4205.29[/COLOR] MB/sec
 Timing cached reads:   7900 MB in  2.00 seconds = 3956.45 MB/sec


------------ [COLOR="Red"]noop[/COLOR]
 Timing buffered disk reads:  600 MB in  3.00 seconds = 199.96 MB/sec
 Timing buffered disk reads:  646 MB in  3.00 seconds = [COLOR="SeaGreen"]215.02[/COLOR] MB/sec
 Timing buffered disk reads:  646 MB in  3.00 seconds = [COLOR="SeaGreen"]215.00[/COLOR] MB/sec

 Timing cached reads:   7768 MB in  2.00 seconds = 3890.27 MB/sec
 Timing cached reads:   7618 MB in  2.00 seconds = 3815.35 MB/sec
 Timing cached reads:   7932 MB in  2.00 seconds = 3973.19 MB/sec
So if you are using an SSD (or atleast if you're using the Intel X-25M G2) then you should be using either the NOOP or DEADLINE I/O schedulers instead of the default CFQ.

To see what I/O scheduler is currently in use:
$ cat /sys/block/sda/queue/scheduler

If using an SSD, then don't forget to add 'noatime' in /etc/fstab for all your partitions on the SSD. This to save the limited write cycles on the disk.

To switch the I/O scheduler to noop or deadline:
$ sudo gedit /etc/default/grub
Look for GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Change to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=noop"
$ sudo update-grub
Note, this will make Linux use the noop scheduler for ALL disks in the system, including any mechanical disks.

Deadline and noop are better for SSD.
CFQ is better for HDD.

---

### Post by robbel on 2010-04-30
Hi, I just bought the same HD and tried it in my lenovo t61 laptop with kernel 2.6.32/ubuntu 10.04 (no discard option available for that kernel). 

somehow, I max out at ~110MB/s and that is with the cfq scheduler (the others are slower)!
for the cached test (hdparm -T /dev/sda) I get around 6000 MB/s though.

any idea what may be causing my laggy performance for the first test?

Thanks so much,
Philipp

---

### Post by libssd on 2010-05-29
Very helpful tip, as I had been vacillating between noop and deadline. Thanks for the data; most people just say use one or the other, without explanation.

---

### Post by obinine on 2010-10-28
I just installed an OCZ Vertex 2, switched to noop scheduler and set noatime flag, and am getting:

 Timing buffered disk reads:  148 MB in  3.03 seconds =  48.80 MB/sec
 Timing cached reads:   3274 MB in  2.00 seconds = 1638.44 MB/sec

Would it be so much slower than the Intel X25 (above) because of the cheaper quality or am I missing something?

---

### Post by Skip Da Shu on 2011-01-25
> **obinine said:**
> I just installed an OCZ Vertex 2, switched to noop scheduler and set noatime flag, and am getting:

 Timing buffered disk reads:  148 MB in  3.03 seconds =  48.80 MB/sec
 Timing cached reads:   3274 MB in  2.00 seconds = 1638.44 MB/sec

Would it be so much slower than the Intel X25 (above) because of the cheaper quality or am I missing something?

Somethings off as last I checked this was the fastest SATA-II drive generally available... only recently exceeded by the Crucial SATA-III drives.

[http://ssd-reviews.com/]("http://ssd-reviews.com/")

Looks to me like it's still using the default scheduling schema. Run```
 cat /sys/block/sda/queue/scheduler
``` to confirm noop is what is being used.


My Mushkin 40GB SSD(slower than a vertex 2) in my Lenovo netbook with "EXT4, noatime, discard and /tmp mounted to tmpfs" gives me:

Using "deadline" -
buffered 548MB in 3.01 = 182.71 MB/sec
cached 1518MB in 2.00 = 759.52 MB/sec

Using "noop" -
buffered 552MB in 3.01 = 183.14 MB/sec
cached 1492MB in 2.00 = 746.73 MB/sec

Not much of a difference either way. A <1MB buffered adv to noop and 13MB cached adv to deadline. What does a netbook do more of "buffered" or "cached" reading? Not sure I really know the diff. So for now I'm leaving it on deadline which is what it's been since the install of the SSD.


I'll be replacing my SATA-I 74GB 10K WD boot drive next week with an OCZ Vertex 2 64MB so I'll have to run these on that and see the diff.

---

### Post by Skip Da Shu on 2011-01-25
> **Skip Da Shu said:**
> My Mushkin 40GB SSD(slower than a vertex 2) in my Lenovo netbook with "EXT4, noatime, discard and /tmp mounted to tmpfs" gives me:

Using "deadline" -
buffered 548MB in 3.01 = 182.71 MB/sec
cached 1518MB in 2.00 = 759.52 MB/sec

Using "noop" -
buffered 552MB in 3.01 = 183.14 MB/sec
cached 1492MB in 2.00 = 746.73 MB/sec

Not much of a difference either way. A <1MB buffered adv to noop and 13MB cached adv to deadline.

Here's something I just added that made a **diff!**  
It's ONLY an option if using 'deadline'.  

I added ```
echo 1 > /sys/block/sda/queue/iosched/fifo_batch
``` into my /etc/rc.local, rebooted and reran the hdparm tests.

No change that I can see to the -T 'cached' reads but the -t 'buffered' reads got much better:

**buffered 674MB in 3.01 = 223.85 MB/sec**

low was 212.58, high was 224.07 but the other 4 runs were all 223.49 thru 223.98 MB/sec

That's about a 23% increase in buffered read throughput.

Now off to see if there's anything I can do about the -T numbers but I have a feeling that might just be my drive.


PS: UID313 - I'd be **real** interested in you re-running your 'deadline' tests with the fifo_batch set down to 1.

PPS: **MUCH** smaller diff in follow up tests (more runs) posted [**HERE**]("http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=598608&viewfull=1#post598608").

---

### Post by Singtoh on 2012-02-20
> **robbel said:**
> Hi, I just bought the same HD and tried it in my lenovo t61 laptop with kernel 2.6.32/ubuntu 10.04 (no discard option available for that kernel). 

somehow, I max out at ~110MB/s and that is with the cfq scheduler (the others are slower)!
for the cached test (hdparm -T /dev/sda) I get around 6000 MB/s though.

any idea what may be causing my laggy performance for the first test?

Thanks so much,
Philipp

Hello Robbel,

I reakize this is an old thread and you may have found out already, but I will post anyway. The Lenovo t61 BIOS is capped at 1.5 Gb/s so you will only see that speed you are getting. I had the same problem. I found this site [http://forum.notebookreview.com/lenovo-ibm/459591-t61-x61-sata-ii-1-5-gb-s-cap-willing-pay-solution-8.html](http://forum.notebookreview.com/lenovo-ibm/459591-t61-x61-sata-ii-1-5-gb-s-cap-willing-pay-solution-8.html), on page 8 about half way down you can download an un-capped BIOS and this will solve your problem. I have been running an un-capped BIOS from that site for a at least a year or more now with no issues what-so-ever and I am on a T-61 as well using a OCZ-Agility and I get max speed from it. I hope this helps you.

Cheers,

Singtoh

---

