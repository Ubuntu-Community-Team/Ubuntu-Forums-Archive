---
title: "hdparm -B meaning"
date: 2012-07-31
forum: Hardware
---

### Post by sorooshubu on 2012-07-31
Hi

I found something interesting about my HDD.
I can tell HDD to reduce power consumption when laptop unplunged  
hdparm -B 1

It very cool, HDD temperature fall down 3 degree of C.
here is problem, every 20 30 sec i hear a click form hard drive.
It's park the head and start it again and spin down and spin up every 30 seconds.

I want configure drive to click will not occur  every 30 sec, I cant find some details about -B parameter of hdparm, it get 1 to 127 for sata enables spin down, but what is the unit of this parameter?

and

what is different between -B and -S parameter?
both put drive in sleep after some time, -S more understandable than -B

any help appreciated.

---

### Post by efflandt on 2012-07-31
Either of those is best used for an alternate drive that you are not actively using.  -S allows you to set an actual time until spin down.  My desktop apparently does not support -B, but -B 1 is the most frequent power management when that is supported.

If you are using programs that access data (along with delayed writes), or have a firewall that constantly logs or something else logs regularly, it would be somewhat pointless because your drive will have to regularly spin right back up.  Without anything else reading, writing, or logging, cron just logs hourly.

---

### Post by 2F4U on 2012-07-31
The click is probably caused by applications accessing the drive and you can't really prevent that. Also, even if data is not written immediately to the drive, there comes a time when it has to be written, since else the risk of loosing data would be too large.

For information about available parameters see here:

[http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

---

### Post by sorooshubu on 2012-07-31
> **efflandt said:**
> Either of those is best used for an alternate drive that you are not actively using.  -S allows you to set an actual time until spin down.  My desktop apparently does not support -B, but -B 1 is the most frequent power management when that is supported.


yes, It's most aggressive PM, I am using this parameter for increase my battery life time as long as possible. Hard drive power management is possible without spin down with following parameter:
hdparm -B 128
It's least power consumption without spin down, BTW I must stop loging service and cron and samba and every other process that access periodically to disk, I find this process with this command:
sudo iotop -oa
And some tweak to saying kernel that  postpone write for specific time (in following command is 10 min).
It's kinda dangerous.
echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

Thanks all of you for reply,
soroosh

---

