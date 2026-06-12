---
title: "WD LAN World Edition drive used with Sata"
date: 2008-11-20
forum: Hardware
---

### Post by daveny on 2008-11-20
Hi all!
First of all sorry for my English, I am a Hungarian, so please excuse me for my mistakes.

So, I use two operating systems on my PC. (Vista & Ubuntu 8.10)
And some weeks ago, I bought a WD World Edition 1TB external LAN drive.
I connected it to my router, this World Edition drive uses a linux kernel w/ Samba.
It made me angry that I could only use 2MBps down or up, (even if I connected directly with 100Mbps cable bypassing the router), and after 5GB of data transferred, it went offline and I could not reach the storage drive in it.
I hacked it, used ssh to access, and after 'demsg', it said that the journal system has failed or something.
So I decided to get that 1TB internal SATA drive out of that WD World Edition and put it inside my PC connecting to it via SATA.
I quickly formatted the whole drive with NTFS partition to be able to reach it with Vista.
When I did this, I could be able to copy/remove files to that 1 TB partition.
After I rebooted my computer, Vista could not reach that drive, only a 30MB RAW drive. (I checked it with a partition manager and it showed 30MB for the whole drive too)
The drive did not give a single noise out of it.
However when I rebooted again and booted Ubuntu, the drive started to spin, giving out noise and ubuntu sees the whole 1 TB partition with NTFS format.
In this case when I boot ubuntu and without power off, only restart my computer and boot up Vista, Vista can see that whole 1 TB partition too.
But after power off/power on, I always have to boot ubuntu then restart and boot vista to get vista see that 1TB partition.

The question is, why?
It looks like if Ubuntu knows that this drive is a bit else than the average and gives out a start_WD_drive() or something, while Vista could not do this.
The second question is that what should I do with Vista to get my storage drive working? Any idea?
(there has to be something what linux knows and vista does not)

I wrote a mail to Western Digital about it, but no answer since 2 weeks.

Thanks for the help. David

---

