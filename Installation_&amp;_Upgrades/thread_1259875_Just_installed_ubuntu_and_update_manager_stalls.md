---
title: "Just installed ubuntu and update manager stalls"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by Wydo on 2009-09-06
Hi, a week ago I downloaded the ubuntu iso and installed it on a hard drive.  When I first booted to ubuntu the update manager pops up and I choose to install all the updates.  The updates download and then it goes into install and most of the way the system crashes.  After a couple of hours I push the reset button and reboot to a very unstable ubuntu.  I tried everything that everyone suggested but with no results so I give up.
 
I bought a new hitachi hard drive and I download ubuntu again only with bittorrent then I burned the install cd at 4X the slowest rate that nero will let me. I did a hard drive check and it came out fine.  Then I did the install and it went fine and I booted to a new ubuntu.  After the boot the update manager popped up and downloaded 219 updates then it started to install them and guess what?  The system crashes.  Its been over an hour and it is still there as I write froze up.
 
Does anyone have any ideas of what I should do at this point?

---

### Post by Wydo on 2009-09-06
I need to get back into windows soon and I am just going to have to shut down the computer.  I hope that someone can help soon,

---

### Post by QIII on 2009-09-07
Which version of Ubuntu?

Did you run md5sum and check the disk for integrity?

---

### Post by Wydo on 2009-09-09
9.04 and yes.

I did restart and everything seems fine.  I am installing updates one at a time and it frooze up on one called cup.

---

### Post by drs305 on 2009-09-09
Did you do a "side by side" install with Windows? Do you remember seeing a disk full message.

Take a look at this command in a terminal (Applications, Accessories, Terminal):
```

df -h

```

Does it happen to say your / is 2.3 - 2.5 GB and is near 100% full?

If this isn't the case, try to provide us with any error messages you are getting.
You can try to run the updates with:
```

sudo apt-get update
sudo apt-get upgrade

```
You will be asked for your password. Just type it and press ENTER. You won't see any input as you type.

---

### Post by raymondh on 2009-09-09
> **drs305 said:**
> Did you do a "side by side" install with Windows? Do you remember seeing a disk full message.

Take a look at this command in a terminal (Applications, Accessories, Terminal):
```

df -h

```

Does it happen to say your / is 2.3 - 2.5 GB and is near 100% full?

If this isn't the case, try to provide us with any error messages you are getting.
You can try to run the updates with:
```

sudo apt-get update
sudo apt-get upgrade

```
You will be asked for your password. Just type it and press ENTER. You won't see any input as you type.

+ 1 drs305

---

### Post by RJARRRPCGP on 2009-09-09
Sounds like you may need to reset your modem.

---

