---
title: "Speed issue with external hd"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by Sibiatus on 2006-08-06
Hi everyone !

This is my first post but i've been wandering here for a few months, looking for answers to my questions,and today, damn !, i haven't found any solution to my problem here yet !
So I decided to bring a little newbie question : please help the young padawan to become a jedi :razz: 
So here's the trouble : I'm running Kubuntu Dapper, with Kde 3.5.4, and I've got an external usb drive. When I copy files from the external drive to an internal one, the transfer speed is around 20-25 Mo/s, so everything's fine, but in the other way, from the internal drive to the external one, speed is only 1 or 2 Mo/s (not really fine... :sad: )

So I tried
```
hdparm -Tt /dev/sda
```
and I get :
```
/dev/sda:
 Timing cached reads:   1432 MB in  2.00 seconds = 715.96 MB/sec
 Timing buffered disk reads:   78 MB in  3.02 seconds =  25.86 MB/sec
```
I don't really understand why my transfer speed is not the same in both ways...

I also checked if my two internal hard drives are using udma and it's ok :
```
hdparm -d /dev/hda
```
gives me
```
/dev/hda:
 using_dma    =  1 (on)
```
and same for hdb

Any ideas ? :confused:

---

