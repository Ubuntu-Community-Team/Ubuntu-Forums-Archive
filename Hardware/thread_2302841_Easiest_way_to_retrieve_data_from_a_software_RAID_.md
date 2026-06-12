---
title: "Easiest way to retrieve data from a software RAID array"
date: 2015-11-13
forum: Hardware
---

### Post by gallantchicken on 2015-11-13
Hi - I used madm to create a RAID 5 array with 4 hard disks of 2 TB each. After this I moved and I was able to carry the hard disks, but I don't have the desktop computer hardware anymore. What is the cheapest way for me to retrieve data in the disks? Is there an external enclosure that I could buy that natively understands Linux software RAID arrays?
Thanks in advance!

---

### Post by weatherman2 on 2015-11-14
It shouldn't be hard to find a generic desktop PC with four SATA ports, even an old one.  (Though if the PC is old and the SATA ports are only SATA I / 1.5GBps, data transfer may be slow of course; if the disks are GPT not MSDOS partition tables, I suppose a really old PC may have issues with those too.) You'll need four SATA data cables and a power supply with four SATA power plugs, though; if the power supply has only two power plugs, you'll have to snag some adapters.

Once you get the four drives plugged into a PC, boot Linux from a live USB and use mdadm to re-build your array.  Then plug in an external hard drive and copy the data off to it.

---

### Post by gallantchicken on 2015-11-16
Thanks weatherman2. I don't have access to a generic desktop PC. I could build one if that's the only way out. I was wondering if there was any off-the-shelf hardware I could buy to accomplish the same. Any ideas? For example: could I buy one of [these]("http://www.amazon.com/gp/product/B003X26VV4?keywords=raid%20enclosure&qid=1447715553&ref_=sr_1_2&s=pc&sr=1-2"), load up all my hard disks, connect to my laptop running Ubuntu and recover the data.

---

### Post by weatherman2 on 2015-11-16
Sure, one of those enclosures would probably work.  But, what's your goal here?  Do you want to get your data off of the array and then be done with it, or do you want to keep using the enclosure as a data storage box with your RAID inside?

If you want to keep it, go for the enclosure.

If you just want your data off the RAID one time and done, I'd look for an old PC with four SATA Ports myself.  No need to go build one - just find an old used one.  Even an ancient Pentium 4 with SATA I ports should work, as long as you can boot Linux on it.  (MAYBE an issue if the disks have GPT partition tables, maybe not; should not be any problem with MSDOS partition tables.)  You might find someone willing to give you one or even loan you one.

I tend to be frugal so I'd probably go for the "old PC" approach, but getting that enclosure is probably easier, I suppose.

---

### Post by mastablasta on 2015-11-17
or maybe a PCI  sata card would also do

---

### Post by gallantchicken on 2015-11-18
My primary goal is to retrieve the data on those disks. Secondarily, if I'm able to make use of the disks to keep some data around, that'd be great. So when you mean one of those enclosures "could probably" work, what are the variables? What should I look for to ensure that it works? :-)

---

### Post by weatherman2 on 2015-11-18
I say "probably" because am not familiar with this exact enclosure.

If you had four individual USB enclosures and connected them at once, you would be able to RAID them and get your data.  Does this single enclosure act that way (with one USB connection)?  I'm not sure.  I read a little more on the Amazon page and it seems it CAN work that way, but I'm not sure if that means a software driver (WIndows?) is required to make that work.

If I were buying this thing, I'd probably read all of the "answered questions" on the Amazon page and look for references to Linux support.  And look at the return policy; maybe you can try it and get your money back if it doesn't do what you hope.

---

