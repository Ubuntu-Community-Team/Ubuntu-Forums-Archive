---
title: "Trim SSD enable and check"
date: 2013-01-21
forum: Hardware
---

### Post by roten on 2013-01-21
Hi everybody :-)

I have two OCZ-AGILITY3 60 GB SSD drives with ext4 file systems. I bought the second one a few weeks after the first one. I have read some threads about SSD and trim=discard on this forum, and I have looked for information at the internet too

[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567576&viewfull=1#post567576](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567576&viewfull=1#post567576)

[https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu](https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu)

Here they write that sometimes on new SSD drives, the data are not zeroised, so it is hard to know if trim works

[https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)

Here discard is discarded in favour of a cron job with fstrim (or manually)
```
sudo fstrim -v / >> $LOG
```[http://http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

I'm confused, and need help to understand.

I tried to tweak the first drive according to some web page (changing the cylinders, heads and sectors). But it didn't perform better than in the delivered state, similar to what is typically created by gparted, so I tried to change it back and have been using it for some months now. I didn't do any tweaking with the second drive, and until now, I have seen no difference.

I have enabled discard in /etc/fstab and it seems to work, does not complain and indicates that it is active in /etc/mtab, I have also booted from another drive and tested with manual mounting with and without the discard option.

I tested if discard works: I made a file, deleted it and checked the data on the drive space with hdparm. The drives are different ! The first one (that I tweaked and [tried to] reset) shows zeros after delete and sync, but the other one keeps the written data.

I have also tested fstrim on the drive that is not zeroised
```
sudo fstrim -v /
```With discard enabled it did nothing. Without discard enabled it reported
```
/mnt: 19918028800 bytes were trimmed
```- Do you think that discard works also on this drive?
- Do you think that fstrim works on this drive?

- What do you recommend?
. discard or
. cron job with fstrim

---

### Post by sudodus on 2013-01-21
I guess fstrim works (I, too, tested on a drive, that is not zeroized), and it could trim various amounts depending on how much was written and deleted).

Given the feedback from fstrim, it sounds more likely to work. But I leave it to the gurus ...

---

### Post by roten on 2013-01-22
Thanks Sudotus,

Fstrim works like this for me too. Tested on a drive, that is not zeroized, and it could trim  various amounts depending on how much was written and deleted.

But it would be nice to get a clear yes or no from someone who really knows.

---

### Post by pixiq on 2013-01-23
I wouldn't rely on it unless the disk space is all zeros where the file used to be.

---

### Post by roten on 2013-01-26
Does fstrim work even if the drivespace is not zeroized, when it can trim various amounts depending on how much was written and  deleted?

---

### Post by roten on 2013-02-08
Bump :-)

---

### Post by linrunner on 2013-02-08
Not all drives zero out trimmed sectors. 

Afaik there are three distinguishable cases: [http://wiki.ubuntuusers.de/SSD/TRIM#Testen-des-TRIM-der-SSD](http://wiki.ubuntuusers.de/SSD/TRIM#Testen-des-TRIM-der-SSD) (in German, but I hope you get the point)

---

### Post by bantuvez on 2013-02-08
MY RESEARCH:

I can tell you that this

```
/mnt: 19918028800 bytes were trimmed
``` 

message doesn't mean that trim is working. I have a drive with non-working TRIM, but fstrim still reports that it can trim. So this message is useless in this context.

To answer your question:

If both of your drives are TRIM capable and with the same configuration, with the same settings (fstab, fs, etc.) one of them do report zeros after the [check]("https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking") then it has working trim, and the other one with this same config will also have working trim.

---

### Post by roten on 2013-02-09
> **linrunner said:**
> Not all drives zero out trimmed sectors. 

Afaik there are three distinguishable cases: [http://wiki.ubuntuusers.de/SSD/TRIM#Testen-des-TRIM-der-SSD](http://wiki.ubuntuusers.de/SSD/TRIM#Testen-des-TRIM-der-SSD) (in German, but I hope you get the point)
Vielen Dank, linrunner!

Ich habe Deutsch im Schule gelernt, so ich glaube dass is deine link verstehe. Die Antwort von
```
sudo hdparm -I /dev/sdb | grep -i TRIM
``` ist
```
* Data Set Management TRIM supported (limit 1 block)
* Deterministic read data after TRIM
``` und es stimmt mit meine andere Observationen :-)

---

### Post by roten on 2013-02-09
> **bantuvez said:**
> MY RESEARCH:

I can tell you that this

```
/mnt: 19918028800 bytes were trimmed
```message doesn't mean that trim is working. I have a drive with non-working TRIM, but fstrim still reports that it can trim. So this message is useless in this context.

To answer your question:

If both of your drives are TRIM capable and with the same configuration, with the same settings (fstab, fs, etc.) one of them do report zeros after the [check]("https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking") then it has working trim, and the other one with this same config will also have working trim.
Thank you bantuvez,

So I can conclude that both of my SSDs are working with TRIM :-)

I will mark this thread as SOLVED

---

### Post by linrunner on 2013-02-09
Sehr schön :D.

---

