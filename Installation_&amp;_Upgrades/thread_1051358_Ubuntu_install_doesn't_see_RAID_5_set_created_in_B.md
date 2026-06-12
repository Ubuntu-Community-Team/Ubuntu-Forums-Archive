---
title: "Ubuntu install doesn't see RAID 5 set created in BIOS"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by zonekeeper on 2009-01-26
I've just built a AMD Phenom X4 system, 4 gb 1066, with 4 320 gig HD's, with 3 set up as a raid 5 set, with the 4th installed but unused in the case of a drive failure (this motherboard RAID doesn't support hot-spares...) The motherboard in question is a Gigabyte GA-MA790GP-DS4H 790GX R.  The odd thing is this...when I go to install Ubuntu, it sees all the drives as separate drives, as though no RAID was ever configured. However I have verified and at every boot screen the RAID ROM shows that the Raid is configured as RAID 5 (2+1) and shows the standalone drive.  CD-ROM is SATA, attached at another position (6 total SATA connections) and is working correctly.

Why would Ubuntu see the drives independently and not as the RAID set that I have created in the motherboard BIOS?  I've not see this before... Now granted I plan to eventually use an actual add-in RAID card with more features, but would like to know why I can't get this to work, for instance if I wasn't eventually planning a different RAID card.  Mainly, because with if this problem will replicate on that setup as well?

Any insights?  Thanks.  :o

---

### Post by doglover56 on 2009-01-26
I believe the answer is:

1. Ubuntu does not use the motherboard bios, so it won't see the motherboard RAID you created.
2. Use the Ubuntu Alternate Disk, and build your RAID that way.

IMF

---

### Post by zonekeeper on 2009-01-26
Interesting.  I didn't know the OS could just ignore the BIOS like that. I'm d/ling the alternate disk now.  I'd be interested to know how that works, the OS not recognizing certain aspects of the BIOS.

---

### Post by srt4play on 2009-01-26
This type of raid setup is referred to as "fakeraid." See [here]("http://en.wikipedia.org/wiki/Fakeraid#Firmware.2Fdriver-based_RAID") for more info on fakeraid and [here]("https://help.ubuntu.com/community/FakeRaidHowto") for Ubuntu-specific documentation.

---

### Post by doglover56 on 2009-01-26
I believe the answer is:

All operating systems have to use the bios in the very, very beginning to get started. And add-in cards have their own bios to get recognized and started. But at some point, most modern operating systems install their own drivers to take over control of the hardware, and no longer use the bios settings. That is why, for instance, that on an old computer with an old bios, the bios won't see all of a large hard drive, but linux will see it just fine. So, the bios probably presents the raid at first, but when ubuntu gets up and running and installs its own drivers and takes over the hardware, it will then ignore the bios and do whatever it is programmed to do.

IMF

---

### Post by zonekeeper on 2009-01-27
Well here is what I posted in toms hardware a bit ago about my dilemma...maybe it will help someone here give some direction/info as to how to pursue a true raid setup/solution:

> 
PCIe x16 and PCIe x8 at the same time?? CONFUSED!


I have a question that I seem to find conflicting information from in the manual and the specs online for the GA-MA790GP-DS4H that I just got. Online specs say that you can have both a x16 card in and an x8 card at the same time. I want to put my GeForce 7950 GT (x16) and install a new RAID card that does RAID 5 (Areca, most likely, or Adaptec). They call for an x8 slot. Now the manual for the mobo says I can use either the 1 PCIe 16x slot or use both slots and get 2 PCIe X8 out of them. Which is it? :??:

Don't want to drop the 350 on the card only to find out it doesn't work.

I really appreciate any insight any one can provide. ;)



Thanks all.

---

### Post by srt4play on 2009-01-27
> **zonekeeper said:**
> Well here is what I posted in toms hardware a bit ago about my dilemma...maybe it will help someone here give some direction/info as to how to pursue a true raid setup/solution

I think your best bet is to try to get Ubuntu to recognize the array as it stands, using the howto I posted earlier.

---

### Post by zonekeeper on 2009-01-27
Oh I did look at those. I was just asking about the lane width division on that motherboard, as from what I understand, a true raid will give much more flexibility and performance enhancements over the 'fake' as you call it (and I agree that it is) that is built into this and other mobo's.  I've already downloaded the alternate disk, just haven't had a chance yet to try it.  And as we are in the middle of an ice storm here, I'm not worried about it too soon, unfortunately. Haven't lost power or net yet (DSL), but others have and its supposed to get worse before it gets better. :(

---

