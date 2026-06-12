---
title: "Samsung 850 EVO SSD stil considered Bad For Linux?"
date: 2016-06-20
forum: Hardware
---

### Post by Nutria on 2016-06-20
Hi,

I've read many articles about the cruddy firmware on these drives and how lack of queued TRIM impacts performance, but they're (relatively) old.

So, are Samsung SSDs still on the no-buy list, or have things improved since then?

Thanks.

---

### Post by Bucky Ball on 2016-06-20
I plopped one in my laptop about a year ago and it's ticking along just fine so I would heartily recommend one. ;)

---

### Post by oldfred on 2016-06-20
I have an older 128GB Samsung SSD 840, but run my own trim script as was suggested before Ubuntu added its own automatic trim. I turn off Ubuntu's weekly and just use the daily one I created.

[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

---

### Post by QIII on 2016-06-20
I haven't looked lately, but I know queued trim instructions needed to be blacklisted by the kernel for 850s.  I don't know if the kernel developers were contrite enough to apologize in public when it was found that the kernel and not Samsung was at fault.  Samsung forwarded a patch.  Don't know if it was applied.  Don't care much at this point since both my 840 and my 850 work just fine in 16.04.

---

### Post by Dennis N on 2016-06-20
I have an EVO 850. Got a great price in Black Friday sale last year. I think the trim runs once a week? I never worry about it and it seems as fast as ever. Very pleased. Don't know what "queued trim" means, however.

---

### Post by oldfred on 2016-06-21
I did not know queued trim either:

See short comings:
[https://en.wikipedia.org/wiki/Trim_(computing)](https://en.wikipedia.org/wiki/Trim_(computing))

---

### Post by j ferguson on 2016-11-05
I have the 850 500 gig.  I have windows 10 on one partition and am running 16.04 on the other. I use 16.04 for almost everything except a CNC design app which only runs on 10, and a couple of other things.  I replaced an Intel 250 gig SSD.  I've had same problem with both.

If i bounce around a lot among folders, pretty soon the access times get quite long.  the cure is a reboot.  lately the Samsung takes about 5 minutes to load the desktop.  i can get at applications like Chrome almost immediately but not the files using the desktop.  I can open a terminal and get at them.  I created an additional user and desktop (metacity in both cases) works fine.

I never had this problem with hard disks.  I'm looking at maybe over provisioning.  maybe that will make the problem go away.

I have complete system backed up to a hard drive.

really strange, though.

john

---

### Post by Kris_M on 2016-11-05
> **oldfred said:**
> I have an older 128GB Samsung SSD 840, but run my own trim script as was suggested before Ubuntu added its own automatic trim. I turn off Ubuntu's weekly and just use the daily one I created.

[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

Thanks @oldfred for that link!!!!  I had never trimmed the Ubuntu partition so did a 
   [FONT=Liberation Mono, monospace][SIZE=2]sudo fstrim -v /
and will do that once every 6 months or so.


For others:
I have used SSDs for a long time on my machines - always Samsung, EVO when they came out. I had trimmed every year or so on the windows partitions.
[/SIZE][/FONT]

---

