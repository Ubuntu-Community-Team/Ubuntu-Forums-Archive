---
title: "Raid Card Suggestions?"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by malfist on 2007-07-12
I'm looking to buy a fairly inexpensive raid card for my computer because my harddrive is filling up. Obviously, I'm looking for a card that supports RAID 0, but RAID 1 would be nice too. I need one that will work well with linux and for the inexpensive (less than $50USD) cards from newegg don't seem to work well with linux from what I've seen.
All four IDE channels are used on my computer and I have no SATA. I would like SATA if the card and the motherboard can support it. I have no PCIe slots, yet someday I might, I have the power adaptors in my PSU and I may upgrade my motherboard and CPU in the next year or so.

Any suggestions?


Thanks,
Malfist

---

### Post by fno on 2007-07-12
Unless you feel like paying $400 and upwards for a raid controller, you're only getting "fakeraid". I would recommend you check out the builtin software raid features in ubuntu - working great with great performance!

Since you need more capacity I would suggest you go for a raid-5 volume instead, sacrificing only one disk's worth of capacity but staying safe from failing disks. And when you need more space, you just add another disk, and gain all that added disk space to the raid volume for data storage.

Any SATA controller would do, but getting one with fakeraid onboard gives you more options. Regarding brands I'm not sure what to recommend; I'm using the 6 internal SATA ports on Intel ICH9-equipped motherboard for one raid-1 for the system and one raid-5 volume for data storage.

If you still go for hardware, make sure the controller has an onboard CPU for XOR operations and onboard cache memory for better performance.

---

### Post by malfist on 2007-07-12
What's fakeraid? What's the differance from a real one, how does software raid work?

Sorry, I'm full of questions.

---

### Post by fno on 2007-07-12
No problem, the forums are here for questions to be answered... :)

Fakeraid is a term that describes raid controllers with no processing power on their own, but use the system's CPU instead. See [this little FAQ]("http://linux-ata.org/faq-sata-raid.html") as a reference.

What fakeraid provides is nice BIOS or GUI/CLI-based raid management features, and often nice alerting features when disks fail, and automatic rebuilds when you replace disks. They are usually very easy to understand (as compared to the "difficult" command line world of linux) and presents a single big disk to the system. Normally they require a special driver for the system to see the disks.

A "real" hardware raid controller provides the same BIOS/GUI/CLI raid management features, but also provides very nice performance improvements compared to fakeraid, due to:
1. Onboard processing features like a XOR processor for raid-5 parity calculations and a dedicated cache memory for improved i/o to/from the disks.
2. Due to 1., more of the system's CPU resources are available for processing other stuff.

But, unless you have a lot of demanding processes running on your system, or have extreme performance requirements, a regular software raid, where some of the system's CPU clock cycles are used for raid processing, ought to be more than enough.

A tip would be to play around with mdadm (to manage raid volumes), hddtemp and smartmontools (for monitoring the disks) to see if they might fit your needs. Be prepared to lose data while learning though... ;)

---

### Post by malfist on 2007-07-12
I've used all 4 IDE channels though. If I bought a RAID card I should be able to add more right? Just connect it to the card instead of the the motherboard.

---

### Post by fno on 2007-07-12
Yes, a regular SATA controller or a SATA RAID controller with PCI or PCIe bus would work just fine.

---

### Post by malfist on 2007-07-12
Good, because I just ran out of space on my ubuntu partition :P.
Do you ahve a recommendation for a specific one that will work with linux?

---

### Post by fno on 2007-07-12
Not really, since I only have used internal controllers for many years (got 8x SATA + 2x IDE on this little motherboard of mine), but there must be someone else around to tell...

Otherwise, don't buy the newest stuff, go with something trustworthy and something that specifically supports the 2.6 kernel. Most Adaptec and Promise cards should work, I suppose.

---

### Post by boweeb on 2007-08-02
I agree with fno to stick with proven name brands. The difference in quality between controllers might surprise you.

Check out this article:
[http://www.smallnetbuilder.com/content/view/27840/77/](http://www.smallnetbuilder.com/content/view/27840/77/)

If you really want to go the cheap route, stick with IDE. You can get a quality LSI Logic MegaRAID controller off ebay for less than $100 (and it meets the requirements fno set for a real controller). The drives will be a little cheaper too.

The author of the above article also gives a good argument for a hardware over software controller.

---

