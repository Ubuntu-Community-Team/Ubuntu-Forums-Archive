---
title: "Installation errors"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by fillostein on 2009-02-24
Hi,
I am having a few problems installing Kubuntu 8.10 on my Dell Latitude  E5500 laptop with 2GB of RAM.

I downloaded the kubuntu-8.10-desktop-i386.iso image and checked the md5 hash and got the following result:
82c02dc7386dfb6858a9ec09a5059e1e
this is correct.

I booted from the CD and ran the memory test - no problems (took ages to run).

I ran 'Check CD for defects' and I saw 12 errors at the start all like this:,
[ 126.342211] end_request: I/O error, dev sr0, sector 1432152
[ 126.342260] Buffer I/O error on device sr0, logical block 179019
(six of each type of error)
but eventually the test said:
Check finished: no errors found

after a reboot i choose 'try Kubuntu without any changes...'

the twelve errors that came up before come up again, but each error is reported six or more times.

I have tried reburning the CD using a couple of burners at low speed and i am using branded 700MB CDRs. 

after a while, the system starts, it seems to be OK...

Is it safe to go ahead and install, or should I try to correct all of the errors first?

If I try to install from inside windows (XP) it gets 99.9% of the way through checking then reports 'Could not access the CD' clicking 'retry' starts the checking off again from 0%

David

---

### Post by Pumalite on 2009-02-24
Clean the lens, change burner or burn your CD on a different computer. Try the CD on a different computer

---

### Post by fillostein on 2009-02-24
I have tried the CD burner on my laptop - with IMG burn it just fails immediately. With Roxio Creator DE it burns 62MB then freezes.

On my desktop pc I use Nero. I set it to the slowest speed and it reports no errors, but the 3 CDs that i have burned this way all fail at the same point when i try to install

---

### Post by Pumalite on 2009-02-24
Try downloading ImgBurn:
[http://www.imgburn.com/](http://www.imgburn.com/)
Install. Go to Mode>ISO>Burn
Select 1x as your speed of burn.
I still think you need a new burner if the md5sum was O.K.
Do not use CD-RW

---

### Post by fillostein on 2009-02-24
Problem Solved!

I had already tried ImgBurn, Roxio and Nero on three different burners and at the slowest speed possible. 

I switched blank CDs - i was using 'expensive' branded Imation CDRs, when i ran out of Imation disks i used some unbranded CDRs that i had - they worked perfectly. 

Using the unbranded CD i get no errors and everything installed first time

Thanks

---

### Post by Pumalite on 2009-02-24
You got a bad batch.

---

