---
title: "IBM NetVista 8303-21G slow HDD work after 12 - 24h"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by dimitar_giormov on 2007-01-25
Hi,

I have recently installed Ubuntu 6.10 to IBM NetVista 8303-21G everything works ok at the beginning, but after 12h or more the PC becomes incredibly slow. If it stays in that condition it freezes. 

What is interesting: I can ping it from other machine. When I check the logs after restarts it turns out it has stopped logging several hours before the pinging.
When the machine is slow it is more like 2,3 min of freeze until the command is executed then the speed is normal again, which led me to the conclusion that when access to the HDD is required there is some problem. 
The CPU is cold the temp of the HDD is normal.

I have run every possible diagnostic utility by IBM against the hardware. I have replaced the hard drive, with no success.

After restart everything works ok for another 12 - 24h.
I have tried to add the noapic in grub also. And I do not know what to try next.

Any ideas are welcome :)

thanks,
Dimitar

---

### Post by DrKillPatient on 2007-03-01
I am having the exact same problem with a new CentOS 4.4 (RH 4 AS based) installation. Slows down after about 12 to 24 hours. I have no answer yet, but I am actively searching for a resolution. I will re-post as soon as I get some more info. If you find anything, let me know.

---

### Post by DrKillPatient on 2007-03-03
I have been up now for 13 hours with no slowdown (a record) on my 8303-SB3. I don't know if this is the final solution, but I'd thought I'd share what I have.

Updated my 8303 BIOS to the latest version. This can be downloaded from the IBM/Lenovo web site as an ISO which can be burned to CD and booted directly (less chance of messing up). My bios was from 2003. Latest is from 2005.

I have the following on my fedora 6 installation.

I was required to install with ide=nodma option or it would error at /sbin/loader (CD media has no fedora files) for reasons still unknown. 
The ide=nodma  has been removed from the grub line.

set hdparm -d1 -k1 -c1 /dev/hda (may eventually try hdparm -d1 -k1 -c3 /dev/hda)

added pci=noacpi to my grub line.

In the IBM BIOS:
Turned off all the APM management functions. 
Left the fan setting to "normal" (always on).
Disabled hard drive sleep (for now I have disabled pretty much anything that might cause a hibernate/idle).

I will eventually (if this actually is the fix) try to turn on a few of the APM functions to see if I remain stable.

I'll be looking back at the bios to see if I misssed posting anything.

---

### Post by marxav on 2007-03-12
I am glad to see I am not the only one having this problem.  I have an IMB Netvista 8307-47U that has the same exact problem.  I tried tons of linux distros, and all freeze after a random period of time I found.

I will be glad to know the outcome of your tests.  About updating the bios,  how do you handle the exe file that they propose here : [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42952](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42952).  According to them, I need to run the exe to get the ISO...  no idea how to do it.

UPDATE:  I learned something today, cabextract filename.exe does the trick...

---

### Post by miltiad on 2007-05-04
> **DrKillPatient said:**
> I have been up now for 13 hours with no slowdown (a record) on my 8303-SB3. I don't know if this is the final solution, but I'd thought I'd share what I have.

Updated my 8303 BIOS to the latest version. This can be downloaded from the IBM/Lenovo web site as an ISO which can be burned to CD and booted directly (less chance of messing up). My bios was from 2003. Latest is from 2005.

I have the following on my fedora 6 installation.

I was required to install with ide=nodma option or it would error at /sbin/loader (CD media has no fedora files) for reasons still unknown. 
The ide=nodma  has been removed from the grub line.

set hdparm -d1 -k1 -c1 /dev/hda (may eventually try hdparm -d1 -k1 -c3 /dev/hda)

added pci=noacpi to my grub line.

In the IBM BIOS:
Turned off all the APM management functions. 
Left the fan setting to "normal" (always on).
Disabled hard drive sleep (for now I have disabled pretty much anything that might cause a hibernate/idle).

I will eventually (if this actually is the fix) try to turn on a few of the APM functions to see if I remain stable.

I'll be looking back at the bios to see if I misssed posting anything.

I have the same problem. Did it work ?

---

### Post by thornelawler on 2007-05-07
I am experiencing the same fault on a whole flock of NetVista machines, under Dapper, Feisty and RHEL.  Right now it's happening on an 8303-21A.
I can ssh in (after a long delay) and some commands seem to run with no grief. dmesg returns no messages since about an hour after boot up, when I unplugged a USB thumb drive. Likewise /var/log/kern.log, var/log/syslog and /var/log/messages; they just show regular 'MARK' entries. It is now 18 hours since boot up (according to 'uptime') and there are several things which seem to get completely stuck:
- top just doesn't start.
- the command 'sudo find /' produces no output after you enter your password, and just hangs, indefinitely.
- 'sudo apt-get update' gets stuck for a minute or three at several points, but does eventually finish.
- The console goes blank, and never returns. Killing the getty processes has no effect: they respawn, but the console remains blank.
- USB appears to have died: I plug a USB keyboard in, and it remains inert, no caps-lock LED or any other LED, and no apparent effect from keystrokes. no indication in dmesg or any other log to show that anything was plugged in.
- vi hangs intermittently, but eventually unfreezes.

As described by other posters, the CPU is cool, system emitting no unusual noises.

We have a lot of NetVista machines (hundreds) here, and we would be running Linux on many of them if it would just stay up. I thought IDE drive support in Linux was considered 'stable'...? And besides, how can this kind of thing happen with no warnings or error messages of any kind?

---

### Post by miltiad on 2007-05-08
> **thornelawler said:**
> I am experiencing the same fault on a whole flock of NetVista machines, under Dapper, Feisty and RHEL.  Right now it's happening on an 8303-21A.
I can ssh in (after a long delay) and some commands seem to run with no grief. dmesg returns no messages since about an hour after boot up, when I unplugged a USB thumb drive. Likewise /var/log/kern.log, var/log/syslog and /var/log/messages; they just show regular 'MARK' entries. It is now 18 hours since boot up (according to 'uptime') and there are several things which seem to get completely stuck:
- top just doesn't start.
- the command 'sudo find /' produces no output after you enter your password, and just hangs, indefinitely.
- 'sudo apt-get update' gets stuck for a minute or three at several points, but does eventually finish.
- The console goes blank, and never returns. Killing the getty processes has no effect: they respawn, but the console remains blank.
- USB appears to have died: I plug a USB keyboard in, and it remains inert, no caps-lock LED or any other LED, and no apparent effect from keystrokes. no indication in dmesg or any other log to show that anything was plugged in.
- vi hangs intermittently, but eventually unfreezes.

As described by other posters, the CPU is cool, system emitting no unusual noises.

We have a lot of NetVista machines (hundreds) here, and we would be running Linux on many of them if it would just stay up. I thought IDE drive support in Linux was considered 'stable'...? And besides, how can this kind of thing happen with no warnings or error messages of any kind?

Hi happy to read someone alive.

top is starting after 5 min for me.

Just put the noacpi option in GRUB today I'll check the result tomorrow (in 8 hours). I'll let you know the results of my tests.

If you have any success let me know.

---

### Post by miltiad on 2007-05-08
I used the pci=noacpi command and the end of my GRUB line and it did the trick !

Let me know if it help.

---

### Post by thornelawler on 2007-05-09
Following up from my earlier post, updating the firmware using this image:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42952](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42952)

seems to have fixed the problem, at least so far. Will follow up if the fault comes back.

Note: No kernel params, just a firmware update and Ubuntu Feisty Server.:)

---

### Post by miltiad on 2007-05-09
> **thornelawler said:**
> Following up from my earlier post, updating the firmware using this image:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42952](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-42952)

seems to have fixed the problem, at least so far. Will follow up if the fault comes back.

Note: No kernel params, just a firmware update and Ubuntu Feisty Server.:)

I already have this BIOS version no choice for me with the noacpi option but it's still working fine after 2 days.

---

