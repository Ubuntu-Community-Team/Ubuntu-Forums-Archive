---
title: "Primary Master Drive Fails"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by OKKARE on 2009-03-11
I just swapped hard drives between computers. I switched a 40 gig and an 80 gig. I'm having trouble on the one that now has the 40 gig drive. I installed Server Edition on it, but now it will not boot properly. The installation went fine, twice, except that it hung at 2% at the final stage of loading the software, for close to an hour. But it eventually continued and finished without errors.

But now when I boot from the hard drive it says "Primary master fails    Press F1 to continue, DEL for SETUPS"

I've been poking around in the setup for ages, and can't find a fix. It seems to detect the dive correctly, as a Samsung SP0144N, and I have it listed in the boot order. I've trued it with the defaults reset too.

Although, sometimes it seems to detect the drive, sometimes it doesn't. I'm trying to figure out what makes the difference.

I've checked the connections and the jumper. Right now it's set on cable select, but I've tried it extensively on single master mode too.

Any suggestions welcome.

---

### Post by martrn on 2009-03-11
It sounds like a hard-ware problem.  Look for some software to test the drive a bit more, or a motherboard problem that doesn't detect the hard drive either in time or two late or bad cable or faulty hard drive.

---

### Post by OKKARE on 2009-03-11
Can anyone suggest a boot CD with the right tools?

---

### Post by martrn on 2009-03-11
The BIOS is (according to the Award and Pheniox) manuals are reporting to you that your hard drive has failed before it has booted anything at all.  So you either have a faulty hard drive or a faulty motherboard (see manual), or it is not set up properly.  It should be set to boot as master if the only hard disc in the workstation, and am sure you did this.

Ask samsung [URL="http://www.samsung.com/us/support/download/supportDown.do?group=&group_cd=&type=harddiskdrives&type_cd=05040000&subtype=spinpointpseries&subtype_cd=05040200&model_nm=SP0411N&dType=D&mType=&model_cd=&menu=download&prd_ia_cd=05040200&disp_nm=SP0411N&isEqualsY="]
http://www.samsung.com/us/support/download/supportDown.do[/URL] for their recommended low level utilities for their hard drives, or search on a specilist forum for this type of hardware problem.

I can/would only reccommend a book called [Upgrading and Repairing PCs]("http://www.google.co.uk/search?hl=en&safe=off&as_qdr=all&num=100&q=Upgrading+and+Repairing+PCs&btnG=Search&meta=")

---

### Post by OKKARE on 2009-03-11
Thanks for the reply.

I have done a number of tests using a boot CD called the Ultimate Boot CD. The hard drive passed them all so far.

I can even use a linux boot thing to view all the files on the system, and presumably change them, but I just can't boot. 

I wonder if the setup partitioned the drive with correctly. Maybe I will try again and do it manually.

---

### Post by OKKARE on 2009-03-12
Well well well, the drives boots up fine when it's in another computer. And other drives boot up fine in this computer.

I have everything set up to default on both. I've played around with other settings. Guess I'll just keep mashing buttons at random.

---

### Post by martrn on 2009-03-12
If that's the case then, and the drive is OK, then its your BIOS.  Maybe try updating your BIOS or visiting the manufacture of the BIOS, to make sure that any problems with the BIOS since your motherboard was released has been addressed.

Also don't discount fault cables or if you didn't swich them around ATA100 vs ATA133 / ATA66 problems (or the equivelent SATA1/SATA2 type problem) / differences and some hardware doesn't work with some motherboards, so check the motherboard manual site.

---

### Post by OKKARE on 2009-03-12
I'm still trying to get the BIOS updated. I've tried putting it on a floppy, but Ubuntu says the floppy is read-only. I've tried putting it on USB, but I don't think if I can read a USB from DOS, which I access via a boot CD.

I also tried loading Ubuntu again, this time setting up that partitions manually, and still no joy.

This has set me way back yet again. I haven't slept in about a day. Any ideas appreciated! :P

---

### Post by martrn on 2009-03-12
> **OKKARE said:**
> I also tried loading Ubuntu again, this time setting up that partitions manually, and still no joy.

This has set me way back yet again. I haven't slept in about a day. Any ideas appreciated! :P

I hope you get your BIOS updated somehow.

If your are installing your partitions manually, and having problems use the alternative CD for installing.  The alternative CD is there because sometimes you don't need everything switched on and X11 running to install ubuntu.  The alternative CD is always a good cd to have it should boot up and work on more systems, than the live CD.

Ubuntu has the latest and greatest on the CD fall back to a different version, if that fails, for example use 8.04LTS (alternateCD) if you have any problems with 8.10 etc.

---

### Post by cariboo on 2009-03-12
This may seem like a dumb question, but have you checked to make sure the jumpers are in the correct place on the drive?

Jim

---

### Post by OKKARE on 2009-03-12
> **martrn said:**
> I hope you get your BIOS updated somehow.

If your are installing your partitions manually, and having problems use the alternative CD for installing.  The alternative CD is there because sometimes you don't need everything switched on and X11 running to install ubuntu.  The alternative CD is always a good cd to have it should boot up and work on more systems, than the live CD.

Ubuntu has the latest and greatest on the CD fall back to a different version, if that fails, for example use 8.04LTS (alternateCD) if you have any problems with 8.10 etc.

I'm installing Ubuntu server, so there is no X11 as it is.

> **cariboo907 said:**
> This may seem like a dumb question, but have you checked to make sure the jumpers are in the correct place on the drive?

Jim

Yes, and I've tried every other jumper option for good measure.

---

### Post by OKKARE on 2009-03-12
I've just discovered that this is a problem with Ubuntu Server, not my hardware. As other hard drives also fail when Ubuntu Server is installed on them.

I tried the old hard drive, which worked fine with XP and fine with Ubuntu on the Desktop, but with Ubuntu Server on the Server, it won't boot.

I really hope someone has some information that can bring me closer to getting this server up and running.

---

