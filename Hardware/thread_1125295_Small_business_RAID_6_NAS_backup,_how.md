---
title: "Small business RAID 6 NAS backup, how?"
date: 2009-04-14
forum: Hardware
---

### Post by batfastad on 2009-04-14
Hi everyone

I'm planning a new NAS unit for our small business.
At the moment we're using an old crummy Lacie Ethernet disk 400GB which is easy enough to back up these days.

I'm planning a 7 drive RAID 6 (with 1 drive hot-spare) array based on a 3Ware 9690 SATA/SAS card.
7 x 1TB drives in a RAID 6 will give us around 4.5TB of usable space.
This will be shared out using Samba and Netatalk. I've done some test configurations (Ubuntu server) and I've already got that down, so now just need to buy the hardware.

But my question is this... how can I back this up?
I could build an identical system and copy the data overnight. But that only covers us for on-site and it's expensive and inefficient.

Is there any way to do offsite backups with this amount of data?

I suppose I could just get the person responsible to take 5 1TB HDDs back each night, but my experience is that if backups are even slightly difficult/annoying to do... then people don't do them.

With 5TB of data, backing up over our ADSL connection is out of the question :(

But is there any way to do an incremental backup?
So you have 5+ 1TB HDDs stored offsite with a full backup
Then you take 1 1TB drive away each evening, containing all the changes to the filesystem made during the day.
Then the next day you bring a different one in which gets the next days changes etc.

Is something like that possible?
Ideally I'd like to stay away from tape, they just freak me out.

Any comments / suggestions?
Cheers, B

---

### Post by bgerlich on 2009-04-14
Rent a server and do the backup through a VPN. If the 5 TB of data is not recreated every day, the data transfered off site will be significantly lower than 5 TB thanks to rsync for example.

---

