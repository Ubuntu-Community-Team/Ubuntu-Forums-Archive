---
title: "Stop my hard-disk from spinning! How?"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by rootware on 2008-01-16
Hi,

I would like to stop my hard disk from spinning in the night, because I sleep next to it and I can't sleep because of the noises. How can I do that?

PS: The laptop remains connected in the night on Pidgin.

I am using Ubuntu 7.04

Thank you.

---

### Post by jerrykenny on 2008-01-16
One of the main things to do would be to temporarily disable logging . . . . youd probably also want to change the schedule of any processes run by your schedule monitor.

Have a look at System/Administaration/services.

Proceed with caution !   easy thing to do is put the display on full screen, then take ascreenshot to remember what should be checked by default.

Also have a look at the klogd configuration files . . . make a backup

Good luck

---

### Post by rootware on 2008-01-17
OK, so there's no utility for doing that? 

I mean, I have to check/uncheck the options every time?

---

### Post by Yellow Pasque on 2008-01-17
Get a quieter hard disk or quiet your hard disk by soft-mounting it (isolating from the chassis by suspension or other means). I have a Samsung 321KJ resting on foam and can't hear it across my small bedroom, even with the case open. What kind of hard disk do you have?

---

### Post by rootware on 2008-01-18
> **Temüjin said:**
> Get a quieter hard disk or quiet your hard disk by soft-mounting it (isolating from the chassis by suspension or other means). I have a Samsung 321KJ resting on foam and can't hear it across my small bedroom, even with the case open. What kind of hard disk do you have?

Temüjin, thanks for your advice, but i would like a software sollution...

The idea is that I own a laptop, it's not a desktop system...

---

### Post by rootware on 2008-01-19
> **rootware said:**
> Temüjin, thanks for your advice, but i would like a software sollution...

The idea is that I own a laptop, it's not a desktop system...

Nobody? :confused:

---

### Post by Daelyn on 2008-01-19
```
 hdparm -Sxxx /dev/xxx 
```
Sets timeout for standby where xxx stands for the seconds.

```
 hdparm -y /dev/xxx 
```
puts drive in standby

```
 hdparm -Y /dev/xxx 
```
sets drive in sleep.

Try play with those, but, everything that needs to access HDD will wake the HDD up from sleep/standby. 

Maybe increase the write cache so it only wakes up once every few hours to write/read the data and then spins down again once the timeout comes in effect. Have forgotten the command for it though.

EDIT:
FIrst of all. Setting to laptop-mode will help you on the way, but, if you use ReiserFS it will prohibit you it seems.
```
 sudo laptop-mode start
```
```
 sudo laptop-mode stop 
```
self explanatory ? :P

Set "noatime" option in your mount of file system will decrease unnecessary writing to HDD, hence, decrease wake-ups.


increase VM Dirty write back time to decrease disk wakeup? 
```
 echo XXXX > /proc/sys/vm/dirty_writeback_centisecs 
```
where XXXX is time in milliseconds (15secs=1500ms) 


Use the no flush daemon maybe?
some info: [http://www.penguin-soft.com/penguin/man/8/noflushd.html](http://www.penguin-soft.com/penguin/man/8/noflushd.html)


Reduce swap usage:
```
 sudo sysctl -w vm.swappiness=5 
```


Set up swap space in RAM?
some info found: 
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

---

