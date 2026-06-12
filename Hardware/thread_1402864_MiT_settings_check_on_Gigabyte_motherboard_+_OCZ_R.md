---
title: "MiT settings check on Gigabyte motherboard + OCZ RAM"
date: 2010-02-09
forum: Hardware
---

### Post by Naiki Muliaina on 2010-02-09
Okis, my fourth PC build has been a lil bit fail. Ive been having epic memory problems in Linux (and Windows) with 3d apps and even a couple of times repos and firefox failing dramaticaly.

I spoke to a fella at the Aria techy support and he suggested checking the MiT on my motherboard. Sure enough, my ram is 1600mhz, the MiT was set to auto detect and was detecting 10666mhz.

Ive upped that but theres a stack of other settings set to auto underneath. Posting in hope someone knows what they should be

Motherboard : [Gigabyte GA-MA790XT-UD4P AMD 790X + SB750 Socket AM3 Motherboard]("http://www.aria.co.uk/Products/Components/Motherboards/Socket+AM3+%28AMD%29/Gigabyte+GA-MA790XT-UD4P+AMD+790X+%2B+SB750+Socket+AM3+Motherboard+?productId=34883")

Ram : [2 x OCZ PC3-12800 Obsidian 4GB Dual Channel Kit]("http://www.aria.co.uk/Products/Components/Memory/DDR3/DDR3+1600+%28PC3-12800%29/OCZ+Obsidian+4GB+%282x2GB%29+DDR3+PC3-12800C9+1600MHz+Dual+Channel+Kit+?productId=38422")

Would anybody happen to know what all the MiT settings should be for that RAM / Motherboard combo

Thankies in advance!

Current settings below :

[IMG]http://farm5.static.flickr.com/4062/4343747265_bab44706bd.jpg[/IMG]

[IMG]http://farm5.static.flickr.com/4050/4343747237_889e68084f.jpg[/IMG]

---

### Post by gordintoronto on 2010-02-09
According to the Aria web site, that RAM has timing of 9-9-9-24, but your CMOS setting is to have CAS latency of 7.  That might account for your memory problems.

What CPU do you have?  The 1666 speed memory is an "overclock" setting and probably depends on both the motherboard and the CPU.  Have you tried running at 1333?

If I were you I would ask these questions on PCMech, since it's pure hardware, nothing to do with Ubuntu.

---

