---
title: "Lost seven years of work and personal data"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by Ububurns on 2005-11-06
Hi there fellow Ubuntu-ians.

A few days ago my computer stopped responding, and after around half an hour I turned it off.  To my utter dismay it has from then on been completely unable to mount my /home partition or any other partition on that drive.  

Having all of my high school work (year 7 through to 12), resumes, photos, uni course information, budgets, letters and personal music recordings on it, I would very much like to be able to recover anything at all.  Anything of that 1GB of data...

Reiserfsck tells me to get a new hard drive (it doesn't even recognise the partition).  Trying to mount it throws out many I/O errors (followed by sector numbers getting higher and higher), as does using dd and dd_rescue (unless I'm using them incorrectly - which I'm reasonably sure I'm not.)

I am able to print the hard disk partitions in fdisk (a sign of hope?) and gparted also lists the partitions on the hard drive - but I am having no luck other than that whatsoever.

Any help would be very much appreciated!

---

### Post by mpettitt on 2005-11-06
Try booting from a rescue system disk and attempting to mount the partitions read only. If you can, grab the data, then scrap the disk. If not, looks like you're resorting to restoring from your backups onto a different drive...

---

### Post by GoA on 2005-11-06
This is the reason to take those backups. If you cannot recover your data yourself and it is valuable to you then ibas can help you. They will recover that data but it will be expensive. 

And the most important thing to remember now if are going to play with the disk by yourself is that DO NOT TRY TO WRITE ON IT because it could overwrite the data.

---

### Post by John.Michael.Kane on 2005-11-06
@Ububurns heres a list of rescue distros you may find one that will be able to help you recover your data..

[http://rescuecd.pld-linux.org/](http://rescuecd.pld-linux.org/)
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)
[http://www.inside-security.de/insert_en.html](http://www.inside-security.de/insert_en.html)
[http://www.sysresccd.org/](http://www.sysresccd.org/)
[http://d-fence.be/](http://d-fence.be/)
[http://biatchux.dmzs.com/](http://biatchux.dmzs.com/)
[http://frenzy.org.ua/eng/](http://frenzy.org.ua/eng/)
[http://www.plop.at/page_en_4.html](http://www.plop.at/page_en_4.html)

---

### Post by az on 2005-11-06
I think the only hope you have is that the media is not damaged and a professional data-recovery service would be able to open the dard drive and transplant the media into a working unit.  They would then copy all the data they could and charge you by the byte....

---

### Post by Ububurns on 2005-11-08
I finally got everything back!

I managed to dd_rescue the partition (backwards), thus making an image from the back to the front of the partition (where there was a conglomeration of errors).  I reiserfsck'ed the image, mounted it and it all worked fine!

Thankyou for all of your help.  If anyone has a similar problem - I can go through it in more detail if you would desire.

---

### Post by Pathogenix on 2005-11-08
I don't have this problem, personally, but I'd be interested to hear how you did it. I'd sleep better at night knowing there was a solution for such crises ;)

---

### Post by nocturn on 2005-11-08
[QUOTE=Pathogenix]I don't have this problem, personally, but I'd be interested to hear how you did it. I'd sleep better at night knowing there was a solution for such crises ;)[/QUOTE]


There is, it's called backups ;-)

Bacula is a great tool BTW, I hear BackupPC is also nice.

Failing that, tar.gz and a CD-R can be sufficient.

---

### Post by BlueNoteMKVI on 2005-11-12
I highly recommend a program called Dirvish [http://www.dirvish.org]("http://www.dirvish.org") to handle your backups.  I manage two remote web servers, two local desktop boxes and three roaming laptops, all of which are essential to my business (and have quite a bit of my personal data as well).  I have an old Pentium II box hiding in a closet that handles incremental backups of each of those machines nightly across the network, keeping at least 7 days of incremental backups at all times.  They've come in handy more than once.  If your setup is not as extensive as mine you can quite easily set up Dirvish to run on a separate partition or a separate disk inside of your existing box.  Give it a look, you won't be sorry.

---

