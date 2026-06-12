---
title: "Minimalizing HDD usage - hdd suspend (kjournald,  hdparm, dirty_writeback_centisecs)"
date: 2009-04-14
forum: Hardware
---

### Post by LimCore on 2009-04-14
I'm trying to allow my laptop to sleep it's hard drive, here are some informations.
The problem I have is that:
  * kjournald is writing data too often.
  * JFS is flushing data often, perhaps this kauses kjournald activity?


This is for at least medium advanced users, BE CAREFUL TO NOT BRAKE SYSTEM.  Commands here should be run as root.


We assume:
[LIST]
[*] hard disk: /dev/sda (try /dev/hda if this doesn't work)
[*] ram: this is intended mostly for computers with lots of free RAM 
(2GB+)
[*] laptop - better not use it on desktop PC, because there pausing hdd often damages it as opposite to laptops (read below)
[/LIST]

Goal: in order to save energy/batteries (and btw let hdd cool a bit - probably good for lifetime) we want to allow 

Here I present some facts, and below the questions that remain to be solved.

First, set the file system to write data only each few minutes, not each 5 seconds (default).
This is the** filesystem commit time option**, configured in /etc/fstab by ,commit=600 for example.
**WARNING** this means that you can loose up to X-minutes (instead of default 5 seconds) of data in case of sudden power loss etc.
You can set it to 10 minutes on laptop (600 seconds) or to for example 1 hour on desktop (3600 second) - **because too frequent power on/off cycles for desktop-type hard drive will damage it**, therefore setting 10 minutes (600 seconds) for commit for PC desktop is too low (assuming it will result in HD going to sleep too often).

For laptop (assuming that sda6 is for home/ and that it is in ext3)
*/dev/sda6* /home           ext3    defaults,nodev,noexec,noatime,commit=600
For PC with no UPS and with some important data
*/dev/sda6* /home           ext3    defaults,nodev,noexec,noatime,commit=10
For PC with fully configured UPS 
*/dev/sda6* /home           ext3    defaults,nodev,noexec,noatime,commit=3600



Make your hard drive auto-sleep after 20 minutes of inactivity,
and make system use swap less:

  sysctl  -w vm.swappiness=15
  sysctl  -w vm.dirty_writeback_centisecs=60003
  sysctl  -w vm.dirty_expire_centisecs=30001
  hdparm -B 240 /dev/sda 

also edit (as root) /etc/syslog.conf and add "-" to all file targes (read man syslog.conf first) and restart it /etc/init.d/sysklogd restart.

(sysctl options are saved to /etc/sysctl.conf and preserved over boot,  hdparm -B is probably saved to the HDD device itself and preserved)



See if your hard drive is sleeping now:
  hdparm -C /dev/sda 
Put hard driver to sleep NOW:
  hdparm -y /dev/sda 



The problem is that the hard drive is often waken up, even though I have >1GB free ram, and all files I'm using could be cached/buffered.

Debug the problem:
  echo 1 > /proc/sys/vm/block_dump
  while true ; do dmesg -c | grep WRITE | grep sda ; done
this will run in loop, showing when ever something accesses physically the hard drive.

I see that often kjournald is accessing the disc:
  [70809.469131] kjournald(2337): WRITE block 241504 on sda9

Also, JFS tries to often write data, I am not sure if this is problem, but where to fine-tune this?
  [70836.762379] jfsIO(4370): WRITE block 42914176 on dm-0

Btw, I use dm-0 for /home (LUKS devmapper), so here we can see that actually jfsIO is not causing (directly) physical hard drive access (but perhaps it tells kjournald to flush?)

Other tips:
after bootup, you can do something like
  find /usr/bin -maxdepth 9
  find /home -maxdepth 2
and so on to help pre-cache at least some often used files into cache.


Some links:
* about load/unload cycles in hdd: [http://www.pcguide.com/ref/hdd/perf/qual/featuresHead-c.html]("http://www.pcguide.com/ref/hdd/perf/qual/featuresHead-c.html")

---

