---
title: "[SOLVED] cpu temp and hard drive temp programs"
date: 2008-07-28
forum: General Help
---

### Post by mikedemario17 on 2008-07-28
Can some one post a link to a program that monitors CPU temp and hard drive temp coz I'm installing new fans and i want to see the difference

---

### Post by brokenLockpick on 2008-07-28
Here's one for hard drive temperature.

I've been using, hddtemp, which is a command line tool that you can get through synaptic, which reads from the S.M.A.R.T. temp sensor if your hard drive is so equipped.

It's pretty easy to use once installed you just type 
```
sudo hddtemp /dev/sda
```
and it gives the temperature reported use /sda for your first sata drive and /sdb for your second sata drive and so on, or /hda if it;s an IDE hard drive. 

I haven't bothered to find a cpu temp program yet because my heatsink has a built in temp sensor that generally reads about 3 degrees Celsius under internal cpu temp based on several programs I used when I ran windows, so I can estimate pretty well. But other people may know of a good linux program for monitoring cpu temp so you can determine if you need more airflow in your case.

---

### Post by mikedemario17 on 2008-07-28
how do i find out if my hard drive has it...the one that ubuntu 7.10 is on is a win 2000 30GB...but i got a 40GB win. XP that might have it yes?

---

### Post by tamoneya on 2008-07-28
my solution is lmsensors + conky
[http://www.lm-sensors.org/](http://www.lm-sensors.org/)
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

---

### Post by mikedemario17 on 2008-07-29
> **tamoneya said:**
> my solution is lmsensors + conky
[http://www.lm-sensors.org/](http://www.lm-sensors.org/)
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)
good finds ^

---

### Post by brokenLockpick on 2008-07-29
> **mikedemario17 said:**
> how do i find out if my hard drive has it...the one that ubuntu 7.10 is on is a win 2000 30GB...but i got a 40GB win. XP that might have it yes?

Easiest way I've found is to get the model number off the outside of the drive and google it to see if it supports S.M.A.R.T. reporting. 
But those drives do seem a little on the small side which makes me think that they are older and therefor less likely to have that feature. But only checking can find out for sure.

---

### Post by mikedemario17 on 2008-07-29
yeah my dads long time friend since pre-school or something like that was a computer programmer that travailed the us/Canada getting a new job every month....well long story short he passed...and i got like all 6 of his PCs and like 4 were 98 and there was like SO many old PC stuff that wasn't used any more....so i got like all the hard drives... i want to be a computer programer some day...some day

---

### Post by articpenguin on 2008-07-31
you can find cpu temp by

> acpi -t

---

### Post by mikedemario17 on 2008-07-31
good find

---

### Post by mpetoven85 on 2008-12-04
thanks you

---

