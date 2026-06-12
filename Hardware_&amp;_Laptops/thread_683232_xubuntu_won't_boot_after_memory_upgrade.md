---
title: "xubuntu won't boot after memory upgrade"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by RiTarDid on 2008-01-30
I recently intstalled xubuntu gutsy on an old HP7917 desktop.  I comes with 128 megs of ram.  I added another 128 megs prior to install and everything went well.  Gutsy has been a very effective samba server and seedbox for my home network.
My problems started when I replaced the 2x128 DIMMs with 2x256.  The xubuntu progress bar ony goes about 10% of the way across and the keyboard lights begin to flash at me.  I checked the BIOS menu and it recognizes the both modules and reports 511 megs ok (this board steals one meg for the base onboard video).  I have checked with HP's specs and they say this board supports up to 512 megs...I'm baffled.

Being something of a Linux n00b, I was hoping this attentive community had some advice or tips to get my ram upgrade working...thanks in advance.

HP Pavilion 7917
2x128 (for now) 133 Mhz 186-pin RAM
Celeron 1.1Ghz (socket 370)
Intel 810 chipset (onboard sound, video, NIC)
basic monitor, mouse, keyboard
40 gig hard drive
Xubuntu gutsy installed on ext3 partition.

---

### Post by overdrank on 2008-01-30
> **RiTarDid said:**
> I recently intstalled xubuntu gutsy on an old HP7917 desktop.  I comes with 128 megs of ram.  I added another 128 megs prior to install and everything went well.  Gutsy has been a very effective samba server and seedbox for my home network.
My problems started when I replaced the 2x128 DIMMs with 2x256.  The xubuntu progress bar ony goes about 10% of the way across and the keyboard lights begin to flash at me.  I checked the BIOS menu and it recognizes the both modules and reports 511 megs ok (this board steals one meg for the base onboard video).  I have checked with HP's specs and they say this board supports up to 512 megs...I'm baffled.

Being something of a Linux n00b, I was hoping this attentive community had some advice or tips to get my ram upgrade working...thanks in advance.

HP Pavilion 7917
2x128 (for now) 133 Mhz 186-pin RAM
Celeron 1.1Ghz (socket 370)
Intel 810 chipset (onboard sound, video, NIC)
basic monitor, mouse, keyboard
40 gig hard drive
Xubuntu gutsy installed on ext3 partition.

HI and can you take the live cd and do a memory test?

---

### Post by RiTarDid on 2008-01-31
here are some of the results:

with 2x128 - tested 100%
with 1x128 & 1x256 - test started, screen went all screwy (100's of color pixels everywhere) and lockup.  repeated with other ram modules and in different order with same results.
with 1x256 system beeped repeatedly, can't even get to cmos setup screen
with 2x256 system refused to initialize bios memory test, would not boot or go to cmos screen

i have a selection of (3) 256mb modules and (3) 128mb modules...mixing and matching makes no difference whatsoever.  Inability to reach the bios setup made me check the board specs again (maximun 512mb) and flash my bios (pheonixbios was v3.06 now v3.07...most recent i can find for it); but no change in results.

---

### Post by lsmobrian on 2008-01-31
Other than making sure they have the correct number of pins, it sounds like the 256 ram is bad.  Last time i read about beeping at startup and no bios, it usually meant bad ram

---

