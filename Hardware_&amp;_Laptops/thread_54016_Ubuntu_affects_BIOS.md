---
title: "Ubuntu affects BIOS?"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by BobH on 2005-08-03
I'm a completely new user (attempted user) of Ubuntu. I currently use Windows XP and I'm running a P4 Processor and MS-7043 ATX motherboard with Via PT880 chipset.
I've been looking for a Linux that I can use and came across Ubuntu. It seems to get very good reviews.
I have a removeable hard disk and so I changed it for a blank one and started up the DVD installation of Ubuntu 5.04
All went well (albeit very slowly compared to other Linux versions that I've had a look at), until installation was complete and I got a message saying that my monitor was "out of timing".
No problem, I then booted up using the "Live" option and got the Ubuntu desktop.
Performance was horrendously slow but this forum points me at my NVIDIA graphics card drivers so that can be solved too.
Eventually I tired of trying to install it and turned off my PC, removed the (now Ubuntu) hard disk, replaced my XP Boot disk, and rebooted.
My XP boot was unbelievably slow, as was my XP performance. On getting my desktop I checked processor performance and found that it was always at 100% (even when I had nothing running in the foreground)
After spending much time trying to find out why, I gave up, turned off my PC and shorted the BIOS. On rebooting I set the BIOS options and carried on with XP. Performance was exactly as I was used to.
I couldn't believe that this was the reason and so happily intstalled Ubuntu again the following day, this time a server install (just trying different options at this point).
Not much success so replaced my hard disk with the XP one again and rebooted.
To my surprise I got exactly the same result as the day before. So I once again turned off the PC and shorted the BIOS. Lo and behold, everything worked fine again.
Can anybody tell me what's happening because I'm completely in the dark now. I'm loathe to try Ubuntu again for obvious reasons, but I'd like to.

---

### Post by az on 2005-08-03
I have never heard of this.

The next step woud be to see if this is reproduceable.

Perhaps it was not Ubuntu (the install should be really really quick, in comparison with other distributions - and Windows) but a hardware problem?

---

### Post by BobH on 2005-08-04
One day on and I tried to install Ubuntu 5.04 from the CD (instead of the DVD). No problems at all. Fast and smooth  install and fast smooth desktop. It didn't even quibble about my graphics card. Good performance all round.

For additional information to anybody that's interested in this problem. I did try the DVD install a third time, this time meticulously checking all the BIOS settings before and after the installation. The BIOS settings remained apparently unchanged, but I still had major performance problems with both Ubuntu and XP until I reset the BIOS. Then my XP performance was back to normal. 

I've just realised that there's one thing I haven't tried. I didn't boot from my newly installed Ubuntu hard disk after reseting the BIOS. I'll try that and post the results.
Up to now I've just closed down Ubuntu, replaced my XP boot disk and experienced the same performance degredation until I reset the BIOS.
 
I may download the DVD iso again in case it was a duff copy that I made.
I'm still wary about my BIOS problem though, but as long as I'm able to reset the BIOS it shouldn't cause any permanent problems. But I'd really like to know what's happening because I've never heard of anything like this.

---

### Post by BobH on 2005-08-06
All is now well.

I downloaded the Ubuntu install DVD again and did a complete new install to a blank disk. It now works perfectly.

The install was fast and smooth and the there are no performance problems with either Ubuntu or XP.

Neither do I have any video problems.

It seems that the problem was in my download or burn of the install DVD.

So far as I'm concerned this problem is now closed. Thanks to anybody who has been trying to reproduce it to find out what was happening.

I still don't know what the install was doing, but on the basis that it now works I'm going with that. The duff DVD is in the bin.

---

