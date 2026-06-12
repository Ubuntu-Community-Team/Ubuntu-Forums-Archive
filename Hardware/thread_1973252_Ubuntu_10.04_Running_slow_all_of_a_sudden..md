---
title: "Ubuntu 10.04 Running slow all of a sudden."
date: 2012-05-04
forum: Hardware
---

### Post by fqowehf on 2012-05-04
Okay so like 4 weeks ago I re-installed Ubuntu since 11.04 was seriously slow and severly fragmented. And now, after the re-install, it went very fast, the programs opened in like a second, and ever since yesterday, their all taking excessive time.

Take note that my computer is usually on almost 24/7 since I run 4 servers on it, web, ssh, minecraft, and mysql.

And also my computer does not get forced shutdown.
I always go to power menu and click shutdown.

Here are my specifications:

2 GB SDDR3 RAM (w/ 4 GB swap)
Intel Atom N550 dual-core @ 1.67 GHz (w/ 64-bit computing)
Intel GMA 3150 @ 900 MH
250 GB ATI Hard drive @ 26000 rpm
Ubuntu 10.04 Netbook Remix
Broadcom STA 802.11g Wireless Card

Here is when I started noticing when my computer started going slow today:
```

2012-05-04 10:21:21 [INFO] CanaryMod: Loaded 27 plugins.
2012-05-04 10:21:23 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:21:28 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:21:35 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:21:40 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:21:46 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:21:51 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:21:55 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:21:59 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:02 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:06 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:10 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:15 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:19 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:22 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:25 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:29 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:32 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:36 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:42 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:46 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:49 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:54 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?
2012-05-04 10:22:58 [WARNING] Can't keep up! Did the system time change, or is the server overloaded?

```

And before it started going slow:

It never said any overload messages, took a short time boot up, excessively fast shut down (~1.92 sec), and all programs took only 1 ~ 10 seconds to open, now they take around 4 ~ 20

Is it the HDD being fragmented again? 
Is it that my HP Mini is being used too much? (had it for over a year and 3 months)
Is it that my CPU is too slow for any linux distro?
Or is it that I need a new computer? (No I am not one of people that think just because their computer is new, they think its better than yours)

Now instead of Ubuntu 10.04 running like Ubuntu with 4 GB ram now acts like Windows Vista with 512 MB RAM! :(

---

### Post by gordintoronto on 2012-05-04
The first potential culprit is using the swap file, because you are "out of memory." Run Top to see if the swap is being used.

---

### Post by ahallubuntu on 2012-05-04
I have a very similar server with an Atom CPU running FreeBSD as a web/email server.  Mine runs fine, but I don't have a Window manager running on mine.  Those take up more resources that I'd prefer to devote to web and email serving.  But that means I can only access/administer the server via a terminal/ssh.  I'm comfortable with this.

As noted, check the swap file.  Check the drive's S.M.A.R.T. status too with 

```
sudo smartctl -a /dev/sda

```

assuming sda is your primary hard drive.

In the future, consider not running netbook remix on this thing or any window manager - just use the server edition of Ubuntu and that will reduce the resource use on this Atom server.

---

### Post by fqowehf on 2012-05-05
But you do not understand, I have a server running on this computer, but I use also for home and business uses.

Or should I stop running it on my computer and just run it on a dedicated machine?

---

### Post by fqowehf on 2012-06-17
> **gordintoronto said:**
> The first potential culprit is using the swap file, because you are "out of memory." Run Top to see if the swap is being used.


swap isnt being used at all.
Only around 400 MB of RAM and 52.91 KB of swap

---

### Post by NetworkEngineer on 2012-06-26
Looks like those messages are from your minecraft (MC) console/log.  It's likely that your CPU is overloaded at the point when those messages are generated. I see the same on my minecraft server immediately after the service starts up from its daily backup/upgrade check. After googling the full message text surrounded by double quotes "[WARNING] Can't keep up! Did the system time change, or is the server overloaded?", and reading a number of different forum threads from those results, I'm pretty sure that in both our cases it is related to CPU utilization and the inability of the MC server to do all of its needed processing in the 50 ms tick required. Check this link for more info: [http://minecraftserverhq.com/blog/can't-keep-up/]("http://minecraftserverhq.com/blog/can't-keep-up/")

What you do about it would likely depend on your own priorities. E.g. if you or your MC users experience unacceptable lag or other issues, then you may want to consider using a dedicated machine for your MC server.  For me, I am choosing to just ignore those messages since I only see them right after the MC server service starts up.

PS - I also am running this on my personal system, but have much beefier HW specs. However, I am running the MC server in a dedicated Ubuntu server (12.04 server edition) virtual machine using virtual box. Though that machine has plenty of memory, and I am using a pretty fast SSD hard drive, I am thinking that in my case the overhead of the VM processing and running it under a VM is causing the MC server lag on startup.

---

