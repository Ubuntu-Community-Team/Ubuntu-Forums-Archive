---
title: "PCI IDE Controller"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by bugboy on 2007-01-06
Anyone had any problems with PCI IDE/ATA133 Controller Cards? I'm looking into buying one to expand my system and break the 137gb limit on my motherboard.

From searching on this forum i found nothing of any real help.

One post did mention that any card shold work as they use the same chipsets [here]("http://www.ubuntuforums.org/showthread.php?t=142416&highlight=ATA+PCI"). Is this right?

If so does that mean i could buy any pci IDE/ATA card and then automount the drive like you would a second drive?

Any advice would be great.

p.s sorry if this is in the wrong forum thought this was the best place.

---

### Post by RandomJoe on 2007-01-06
I have several of these, and they all work fine.  Most of mine were the "freebies" that came with a new hard drive a while back, using a Promise chipset (and cheapest the manuf. could find, I'm sure).  I also bought a SIIG brand card using a Silicion Image chipset - it may just be because I actually shelled out cash for it but it seems to work a bit better than the Promise ones...

---

### Post by bugboy on 2007-01-06
Thanks for this. This is great.

If anyone else has any experience on this that would be great.

---

### Post by Mike'sHardLinux on 2007-01-06
RandomJoe, I have been using the Promise Ultra133 TX2 because they are cheap, and work well. I am curious about the Si based cards. What about them seems better? Are they faster? Have you done any software RAID with any of them?

I'd appreciate any insight.

---

### Post by RandomJoe on 2007-01-06
Like I said, the Promise boards I have are all the "freebies" with hard drives so I'm not sure if that matters...  There isn't any significant benefit to the SiI board, although it does seem to perform just a tiny bit better.  Probably more of a "want" since I actually paid for the thing! :-? 

For a long time it and a Promise board coexisted in my server, connecting 4 drives in software RAID5.  Everything worked fine - on both boards - until my server closet got a bit too warm...  Oops...  There's a reason I use RAID! :rolleyes: One drive crapped out, but I was able to replace it and rebuild.  

I've since switched to a 4-port SATA card and new SATA drives, so the PATA cards are just sitting around right now...  Interestingly, I just checked and the SATA card is a Promise - SATAII 150 TX4 - and it works great as well.

---

### Post by bugboy on 2007-01-07
I've got myself a PCI IDE/ATA controller today. Once i've got it working / or not i'll post my findings. 

Thanks for all the help

---

### Post by bugboy on 2007-01-09
Well just to let you know i got it working and i can see my new drives.

I'll post my specs here as well as in the compatible list.


MS-6863 version 2.1
[more detail here]("http://www.msicomputer.com/product/detail_spec/product_detail.asp?model=VIA_PLE_133_5a_Lan")
running a p3 633mhz and also tried a 933mhz processor

256mb SDRAM 133mhz

Ultra ATA/133 CONTROLLER
[more detail here]("http://www.avlab.com.tw/ultra/1006_0086_000d.htm")
On the chip it says its chip number ite8211af
On ubuntu its saying its chip number ite8212 which is a raid controller.

Ubuntu server edition 6.06.

---

### Post by quimchin on 2007-05-01
Im thinking of getting one to expand my current pc, as I have 2 old ide drives and my new computer is all sata. The MRI one i have been looking at ([http://www.microdirect.co.uk/(13911)MRI-2-port-IDE-ATA133-PCI-card.aspx]("http://www.microdirect.co.uk/(13911)MRI-2-port-IDE-ATA133-PCI-card.aspx") says it breaks the 137gig barrier. Does any one know the max drive size you can attach?
My two drives are 250gig seagate barracudas.

Any help will be very much appreciated.

---

