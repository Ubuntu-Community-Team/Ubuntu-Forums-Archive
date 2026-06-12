---
title: "Running from SD or USB"
date: 2014-06-04
forum: Hardware
---

### Post by Ben_Farrell on 2014-06-04
Hey everyone,
I just got Ubuntu 14.04 running from a micro sd card. I love the fact that I can do this, but I'm faced with tons of lag here and there. Definitely poor performance compared to when I had 14.04 installed straight on my SSD as I had before (which was just rock solid and smooth).

So my question is this...
I'm presuming that I just have slow read/write speeds. Looking up my Lexar 32GB micro SD card online, it advertises 10MB/s. I'm assuming this is just too slow and I should buy a USB 3.0 thumbdrive. What advertised speeds should I be looking for when I buy to run Ubuntu and not notice any lag during normal use?

thanks!

---

### Post by sudodus on 2014-06-04
Welcome to the Ubuntu Forums :-)

You are right, the speed of the drive (and the connection to the drive) is important. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/")

[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

I'm quite happy with Sandisk Extreme 16 GB and 32 GB for installed systems.

---

### Post by oldfred on 2014-06-04
Faster hardware always helps, but you can turn off a few settings to reduce writes.
And if you have lots of RAM, everything is cached in RAM, so if you do not change to other larger apps much system is mostly running from RAM.

I turn off journal, that allows better or faster recovery if damaged, but with a small drive that is mostly system it is worth the risk. If lots of valuable data leave journal on.
 sudo tune2fs -O ^has_journal /dev/sdb1
sudo tune2fs -o discard /dev/sdb1
      
 You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

    
Change to noatime

 After installing, change the fstab so that everything gets mounted with noatime.

A very few apps like mutt may need the noatime, realtime then is a choice.

---

### Post by LastDino on 2014-06-04
If you're using SD cards like me, its usually better to get class10 ones for this, normal (anything below that) would subject to slow speeds. Some card readers can make difference too. I use SD cards to make bootables for install though, I never install on SD card itself.

---

### Post by Ben_Farrell on 2014-06-04
Thanks guys! It's really no big deal for me to buy a better USB/SD card - so I'd rather just get it right from the start. Meaning - I greatly appreciate the advice from oldfred, but I think I'd just want better hardware rather than make concessions for the slow stuff I have.

I have seen the USB ratings before, and I've seen the requirements link for Ubuntu. The requirements link talks a little bit about speed, but I don't see any requirements or recommendations with actual numbers. I'd like to match an IO speed that's recommended/required for Ubuntu with my future purchase. I can guess what might be good enough or go way overboard - but I'd rather get some actual numbers I should shoot for.  Thanks for the help!

---

### Post by Ben_Farrell on 2014-06-04
Actually, nevermind. The SanDisk Extreme 32GB recommendation is good enough for me, and reasonably priced (was almost tempted for the 64GB, but didn't bite).

Thanks for the advice!

---

### Post by oldfred on 2014-06-04
A while back I ran these tests. My motherboard is from 2009 and I only have USB2 ports. My SSD is a Microcenter (inexpensive) SSD from a couple of years ago. Most new ones have rated speed twice mine.

 Older SSD speed -T is cache, -t is device
fred@fred-Precise:~$ sudo hdparm -t /dev/sdd4
/dev/sdd4:
 Timing buffered disk reads: 626 MB in  3.01 seconds = 208.20 MB/sec
Older 160GB rotating drive circa 2006:
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec
USB2 flash drive Microcenter house brand
/dev/sde1:
 Timing buffered disk reads:  50 MB in  3.07 seconds =  16.26 MB/sec

I since have run Microcenters USB3 flash drives in my USB2 ports and they were about 10% faster. Not sponsoring Microcenter but they are a few blocks away and usually lower cost so frugal oldfred likes them. No real problems with their stuff.

---

### Post by sudodus on 2014-06-05
> **Ben_Farrell said:**
> Actually, nevermind. The SanDisk Extreme 32GB recommendation is good enough for me, and reasonably priced (was almost tempted for the 64GB, but didn't bite).

Thanks for the advice!

I think the pendrive will work well for you. Good luck :smile:

---

