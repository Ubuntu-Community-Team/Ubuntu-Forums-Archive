---
title: "SMART hardware-test predicts harddisk failure"
date: 2010-09-25
forum: Hardware
---

### Post by Boulemans on 2010-09-25
Today I got the following error on my 3 years old Dell Vostro 1000 laptop about the only hard disk of 80 GB (os: Ubuntu 10.04)

(roughly translated from the dutch text)

Failure at SMART test:
[B]
Number re-assigned sectors[/B] - failure (normalized 34; lowest 34; threshold: 36; value: 2676 sectors 
   when the hard disk discovers a read, write or verification error, the sector is marked "re-assigned" and moved to a special reserved area.

**Airstreamtemperature**: Defect in the past; normalized 76; lowest 41; threshold 45 value: 24°C/75°F

** Current Pending Sector Count ** - warning: normalized 1, lowest 1, threshold 0, value 2078 sectors
   Number of sectors waiting to be remapped. If the sector waiting to be remapped is subsequently written or read successfully, this value is decreased and the sector is not remapped. Read errors on the sector will not remap the sector, it will only be remapped on a failed write attempt.

Now, a few months ago I did had problems with the cooling of my laptopsystem. I bought an external laptop ventilation (such as [here]("http://www.google.com/imgres?imgurl=http://www.slipperybrick.com/wp-content/uploads/2007/01/belkin-laptop-cooling-stand.jpg&imgrefurl=http://www.slipperybrick.com/2007/01/belkin-laptop-cooling-stand/&h=300&w=500&sz=32&tbnid=WGWS119foYQ1aM:&tbnh=78&tbnw=130&prev=/images%3Fq%3Dlaptop%2Bcooling&zoom=1&q=laptop+cooling&usg=___cpl7ujehc5w3ZJZgh9xjf77wYs=&sa=X&ei=tG-eTIHLEOeHOLb3naIM&ved=0CDkQ9QEwAw")) And the problem was fixed for me. Maybe it can be an explanation for this. 

Another explanation can be: it's a 3 years old laptop ... maybe it is his time to leave me (its my pet?).

But the most important question: does this matter? Will I lose my laptop or can I use it for another year? Or can my problems be solved just by replacing my laptop hard disk?

---

### Post by mrhhug on 2010-09-25
yes this means your hard drive is about dead, get a new hard drive and using imaging software you can (hopefully) just image the failing drive to the new drive

you can be sure by booting into a "hard drive fitness test" and running that

this error means the longer that hard drive spins, the closer it is to death, try to leave the system off untill you can replace that drive

---

### Post by darkstarbyte on 2010-09-25
Well I had a similar problem, and it would seem some of cells on the hard drive you have are going out.( I had a dell laptop with a similar problem.)
I would suggest getting a new hard drive.( Back up your files first.) I had more than one problem like this and there is a way to check how many bad sectors there are but I would suggest that you use a live cd first so you don't damage data.

[SIZE="5"]<Warning this code can damage mounted partitions so be very careful! Also I would advise a live cd! This code can be very dangerous  if not used properly.> [/SIZE] 

[SIZE="4"]<This code will check for damaged blocks, but can be dangerous.>[/SIZE]

What OS are you using, and Laptop model also modifications so I can make sure this code will work right.

```


fsck -t ext4 /dev/hda2


```

---

### Post by darkstarbyte on 2010-09-25
> **mrhhug said:**
> yes this means your hard drive is about dead, get a new hard drive and using imaging software you can (hopefully) just image the failing drive to the new drive

you can be sure by booting into a "hard drive fitness test" and running that

this error means the longer that hard drive spins, the closer it is to death, try to leave the system off untill you can replace that drive

His a approach is better you don't know how long it will last.

---

### Post by Boulemans on 2010-11-06
I've bought a new Hard Drive - problem 'solved' :-)

---

