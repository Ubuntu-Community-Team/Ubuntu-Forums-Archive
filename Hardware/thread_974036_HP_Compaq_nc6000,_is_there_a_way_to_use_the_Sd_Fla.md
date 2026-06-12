---
title: "HP Compaq nc6000, is there a way to use the Sd Flash card reader?"
date: 2008-11-07
forum: Hardware
---

### Post by maurertodd on 2008-11-07
I'm using 8.10, I'd like to know a method to allow my embedded SD flash card ready to work.  I'm suspecting that it is NOT a USB device as with a card inserted the lsusb command doesn't show the card.

I've found some 4 year old posts that suggest that I'll need a special driver.  Any hints on how to figure out which one would be appreciated.

---

### Post by maurertodd on 2008-11-07
Okay, some progress.  At least I know more and am starting to find other people with a similar problem as mine.  The HP Compaq nc6000 uses on internal card reader that can be seen with the commands lspci.

That shows a Mirco, Inc. OZ711Mx 4-in-1 MemoryCardBus.  Now I need to see if I can get it to work!

Todd

---

### Post by kreichl on 2008-11-09
> **maurertodd said:**
> Okay, some progress.  At least I know more and am starting to find other people with a similar problem as mine.  The HP Compaq nc6000 uses on internal card reader that can be seen with the commands lspci.

That shows a Mirco, Inc. OZ711Mx 4-in-1 MemoryCardBus.  Now I need to see if I can get it to work!

Todd

I'm using an external USB CardReader to overcome, however, it would be cool reading SD Cards with the builtin nc6000 HW.

I've tried it __without__ success on:
* Ubuntu Intrepid (and older versions)
* Debian Lenny (and older versions)

The device is simply not recognized on the nc6000 with default
driver settings!

My daughter's laptop does the following on card insert:

lshal -m
  
Start monitoring devicelist:
-------------------------------------------------
16:21:57.030: pci_1524_751_mmc_host_mmc_card_rca58916 added
16:21:57.377: storage_serial_0x80517fb1 added
16:21:57.471: volume_uuid_64A5_F009 added
16:21:57.613: volume_uuid_64A5_F009 property volume.mount_point = '/media/disk'
16:21:57.623: volume_uuid_64A5_F009 property volume.is_mounted = true

where lshal -m on the nc6000 does nothing.

Maybe somebody knows about the O2 Micro MemoryCardBus driver.

Best regards,
Klaus
--
If somebody needs a tester, I stay tuned.

---

### Post by maurertodd on 2008-11-10
Thanks for the response.  I'm finding lots of people who tried to make is work, but none that have posted a solution since 2.something.  Even found a freeware site that allows people to commit $$ if someone will code a solution where someone has pledged 40 euros to a solution.

Yes must people in this dilema give up and buy a PC Card or USB reader.  Perhaps I'll find a need for this solution someday. 

I will say I am very happy with 8.10 out of the "box".  It configured the NC6000's WIFI automatically without having to go find the drivers and controllers myself as in previous versions.   The only thing I don't see 8.10 supporting on the nc6000 is the SD reader.   In all honesty I hadn't noticed the slot till recently.

Todd

---

