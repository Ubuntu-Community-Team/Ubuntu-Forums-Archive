---
title: "usb external HD vs. large capacity flash drive"
date: 2014-12-06
forum: Hardware
---

### Post by michael-piziak on 2014-12-06
My HD is about 220 gigs.  I've been downloading many PCSX games, and they start to take up gigs of space - about 2 games equals one gig.

I know an external usb HD would be great to store the Roms on, but I came across some high capacity flash drives that are more affordable and hold a lot now.  Another advantage of the flash is that I can take the games with me to my sisters house, where I've installed Ubuntu also.

Please comment if you think the flash drive would be fine to run the PCSX games from the flash drive.  Or would it be too slow or have some other problem(s).  Also, is there a limit to the size of the flash drive one can use (in Ubuntu 12.04 lts 64 bit).

For example, here is a 128GB flash drive for $30:  [http://www.amazon.com/PNY-Attach%C3%A9-128GB-Flash-Drive/dp/B00CE5QOIG/ref=sr_1_2?ie=UTF8&qid=1417922639&sr=8-2&keywords=128gb+flash+drive](http://www.amazon.com/PNY-Attach%C3%A9-128GB-Flash-Drive/dp/B00CE5QOIG/ref=sr_1_2?ie=UTF8&qid=1417922639&sr=8-2&keywords=128gb+flash+drive)

---

### Post by carl4926 on 2014-12-07
Honestly, it's not a great idea IMO
Portable USB HDD's are really not much different in price and far better I/O

---

### Post by michael-piziak on 2014-12-07
Thanks for the reply.
I just tested a few games on my 8 gig flash drive, and they seemed to load the same from the flash drive.  I'm not sure what the disadvantage would be.
I'll research the prices of external HD usb 2.0 drives, but I'm not sure I can find 128 GB for $30 like the flash drive.

Marking this thread as solved.

---

### Post by oldfred on 2014-12-07
Think about USB3 even if current system is USB2 only.

I have a MicroCenter store nearby which is a problem. Every time I go there the price of their house brand flash drives is lower or larger size. So I buy another one. 
A time or two ago, the USB3 was only a $1 more for the size I was buying so I said I would try it. I did find it to be about 10% faster on my USB2 ports and then with new computer and USB3 ports will be a lot faster.

Also we have seen various hard drive USB caddy that either do not support USB3 or do not work with newer very large (over 2TB) drives. Best again for future compatibility even if not now required. So check specifications carefully.

---

### Post by michael-piziak on 2014-12-07
> **oldfred said:**
> Think about USB3 even if current system is USB2 only.

I have a MicroCenter store nearby which is a problem. Every time I go there the price of their house brand flash drives is lower or larger size. So I buy another one. 
A time or two ago, the USB3 was only a $1 more for the size I was buying so I said I would try it. I did find it to be about 10% faster on my USB2 ports and then with new computer and USB3 ports will be a lot faster.

Also we have seen various hard drive USB caddy that either do not support USB3 or do not work with newer very large (over 2TB) drives. Best again for future compatibility even if not now required. So check specifications carefully.

Thanks for the advice.  So USB 3 flash drives will run at USB 2.0 speed since my system only supports USB 2.0, right?

---

### Post by oldfred on 2014-12-07
This could be from other changes, but shows about 10% faster for buffered reads. Cached, assume is out of memory so I would expect those to be the same.

 fred@fred-Precise:~$ sudo hdparm -tT /dev/sde
# my 32GB USB3 on USB2 port
/dev/sde:
 Timing cached reads:   7326 MB in  2.00 seconds = 3668.54 MB/sec
 Timing buffered disk reads: 104 MB in  3.02 seconds =  34.44 MB/sec

   fred@fred-Precise:~$ sudo hdparm -tT /dev/sde
# my 16GB USB2 on USB2 port
/dev/sde:
 Timing cached reads:   7192 MB in  2.00 seconds = 3600.81 MB/sec
 Timing buffered disk reads:  94 MB in  3.04 seconds =  30.93 MB/sec

Some flash drives are just better than others.
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)

---

### Post by michael-piziak on 2014-12-08
I guess my dilemma now is that I can't find a USB 3.0 flash drive in the same price range as the USB 2.0 drive.  I'm looking at a 128 GB flash drive.
Again, this 2.0 USB 128 GB drive is around $30:  [http://www.amazon.com/PNY-Attach%C3%...gb+flash+drive]("http://www.amazon.com/PNY-Attach%C3%A9-128GB-Flash-Drive/dp/B00CE5QOIG/ref=sr_1_2?ie=UTF8&qid=1417922639&sr=8-2&keywords=128gb+flash+drive")

---

### Post by oldfred on 2014-12-08
Even Microcenters USB 3 at 128GB is $50.

I was buying 32GB. Current price for USB3 is $13 and USB2 is $10.

I have not had any issues with Microcenter house brand, but have not used them a lot nor know how they really compare on speeds.

For those kind of prices for larger flash drives a USB hard drive then makes more sense.

---

