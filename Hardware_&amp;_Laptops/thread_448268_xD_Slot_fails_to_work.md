---
title: "xD Slot fails to work"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by CSMatt on 2007-05-18
I have an ASUS V6Va with in integrated multi-card reader (SD/xD/MMC) built into the PCI bus.  SD cards are recognized in Ubuntu (although they require a reboot to be recognized and hot-swappable), but xD cards are ignored completely.  The Device Manager lists three seperate controllers for Memory Sticks, SD/MMC/MS/MSPro, and xD.  I've included an attachment.  However it appears that only the SD/MMC/MS/MSPro works, considering that it has something else branching off of it.

Is there any way I can fix this?  I realize that I haven't given much information, but I also am unaware of many specifics of this laptop.  I can tell you that the Device Manager lists the PCI bus as being made from Intel however.  All three controllers appear to be made by a company called Ricoh.

---

### Post by pebo on 2007-05-19
According to [this]("http://ubuntuforums.org/showthread.php?t=420721&highlight=sd+card+reader") thread there are no drivers yet. And don't hold your breath - I've been on the lookout for a couple of years :)

---

### Post by CSMatt on 2007-05-19
That only talks about card readers made by Texas Instruments though.

I haven't tested SD cards in Edgy or Dapper because I didn't own one yet, so SD cards might have not have worked then either.

---

### Post by CSMatt on 2007-05-20
Could I use a USB card reader then?  Theoretically the USB card reader will mount the cards using the USB Mass Storage Device class, right?

---

### Post by CSMatt on 2007-05-21
Never mind.  Apparently some do and some don't.  I found one that does.

---

