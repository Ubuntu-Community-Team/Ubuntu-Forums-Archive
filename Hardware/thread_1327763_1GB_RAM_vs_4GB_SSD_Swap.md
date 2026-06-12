---
title: "1GB RAM vs 4GB SSD Swap"
date: 2009-11-15
forum: Hardware
---

### Post by Vostrocity on 2009-11-15
1GB RAM vs 4GB SSD Swap. Which option do you think would give a bigger performance boost? I only have 2GB RAM with no swap space right now and that seems to be my system bottleneck since I frequently go over 90%. I could either bump my RAM up to 3GB or get one of those mini-PCIe 4GB SSDs pulled from netbooks ([like this]("http://cgi.ebay.com/DELL-STEC-4GB-Mini-PCIe-SSD-for-Netbooks-R832H-MINI-9_W0QQitemZ350274222026QQcmdZViewItemQQptZPCC_Drives_Storage_Internal?hash=item518df877ca")) to use as swap. The SSD is slightly cheaper but I'm not concerned with price in this case.

---

### Post by hansdown on 2009-11-15
Hi Vostrocity.

I have 2GB of ram with Jaunty, and I don't think my swap has been used.

---

### Post by gertjan_hofman on 2009-11-15
like all good OS'es Linux will always eat up 100% or RAM. This is a good thing.  Without swap eventually the OOM killer will take care of keeping the system alive. So unless you have noticed apps spontaneously being killed, you have no memory problem.

G

---

### Post by mikewhatever on 2009-11-15
Since you want more speed, add more RAM. I really doubt swap would noticeably speed things up.

---

### Post by Vostrocity on 2009-11-15
I have rarely actually ate up all 100% of RAM, though it has happened and when it does everything slows to a major crawl (due to lack of swap space). The thing is, when I see my memory up at 95% (I have the System Monitor applet on my panel) I know to stop opening more processes and to start closing some stuff. However if I wasn't aware that my memory usage was almost full I would still need to work on some more stuff. And another thing, I know for a fact that I use more RAM than the average person. I frequently have around 100 web browser tabs open. :D Since my understanding is that swap is just an overflow area for open processes that don't fit in RAM, I was wondering whether having more slower memory (4GB SSD swap) is better than less faster memory (1GB RAM).

---

### Post by shaggy999 on 2009-11-15
First off, about mini-PCI Express Hard drives:

> 
Some netbooks (notably the Asus EeePC and Dell mini9) use a variant of the PCI Express Mini Card for flash or SSD. This variant uses the reserved and several non-reserved pins to implement SATA and IDE interface passthrough, keeping only USB, ground lines and maybe the core 1x bus intact.[5] **This makes the 'miniPCIe' flash and solid state drives sold for netbooks largely incompatible with true PCI Express Mini implementations.** Also the typical Asus miniPCIe SSD is 71mm long, causing the Dell 51mm model often being (incorrectly) referred to as half length.

Source: [http://en.wikipedia.org/wiki/PCI_Express#PCI_Express_Mini_Card](http://en.wikipedia.org/wiki/PCI_Express#PCI_Express_Mini_Card)

Translation: You can only use mini-PCI Express SSD drives in netbooks, and only those netbooks designed for them.

Secondly, even the *fastest* SSD hard drive (I'm talking the $1000+ Intel Performance SSDs and not the crappy $14 first-generation drives like the one you showed) is going to be many orders of magnitude *slower* than RAM speed. It is only used for when you're out of RAM and stuff has to get swapped in and out so it also means stuff is getting copied out and copied back in in order to be used. I really can't think of ANY situation where using an SSD drive (or any other drive, for that matter) would be faster than using more RAM.

---

### Post by chrisme52 on 2009-11-15
well said, just curious what are you doing to use that much ram?

---

### Post by JBAlaska on 2009-11-16
Get more RAM, boot Knoppix with the "toram" boot parameter and load the whole OS in ram.. It seems I saw somewhere how to hack Ubuntu to do this..but I forget where.

---

### Post by Vostrocity on 2009-11-16
> **shaggy999 said:**
> First off, about mini-PCI Express Hard drives:


Source: [http://en.wikipedia.org/wiki/PCI_Express#PCI_Express_Mini_Card](http://en.wikipedia.org/wiki/PCI_Express#PCI_Express_Mini_Card)

Translation: You can only use mini-PCI Express SSD drives in netbooks, and only those netbooks designed for them.

Secondly, even the *fastest* SSD hard drive (I'm talking the $1000+ Intel Performance SSDs and not the crappy $14 first-generation drives like the one you showed) is going to be many orders of magnitude *slower* than RAM speed. It is only used for when you're out of RAM and stuff has to get swapped in and out so it also means stuff is getting copied out and copied back in in order to be used. I really can't think of ANY situation where using an SSD drive (or any other drive, for that matter) would be faster than using more RAM.
Thanks for the info, I was unaware of that. I guess that closes the issue since RAM seems to be my best and only choice. I also remembered about the not-very-popular technology that is [Intel Turbo Memory]("http://en.wikipedia.org/wiki/Intel_Turbo_Memory"). My laptop model happens to be compatible, as it has an empty mini-PCIe slot specifically labeled Turbo Memory and it was also offered as a factory option. However it's designed to take advantage of Vista and 7's ReadyBoost/ReadyDrive technology, and ended up with [bad reviews]("http://www.anandtech.com/mobile/showdoc.aspx?i=3009&p=8"), so I'll stick with the RAM option.

> **chrisme52 said:**
> well said, just curious what are you doing to use that much ram?
Lots and lots of browser tabs, music player, word processor, GIMP at the same time. ;)

---

