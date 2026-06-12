---
title: "Hard drive adapter no work-gives beep"
date: 2013-02-10
forum: Hardware
---

### Post by sofasurfer on 2013-02-10
I have one of these... [http://www.ebay.com/itm/Brand-New-USB-2-0-to-IDE-SATA-5-25-S-ATA-2-5-3-5-Adapter-Cable-fa-/221100435775?pt=US_Drive_Cables_dapters&hash=item337a9ce93f](http://www.ebay.com/itm/Brand-New-USB-2-0-to-IDE-SATA-5-25-S-ATA-2-5-3-5-Adapter-Cable-fa-/221100435775?pt=US_Drive_Cables_dapters&hash=item337a9ce93f)

Had trouble getting it going and then I learned that you need to plug it in, power up and wait for spin-up and THEN plug in the usb. Using this method I was using it for a while. 

After not using it for some time I tried to hook it up again. I get NO response except that the pc gives a beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....beep.....

Any idea what I need to do? 

My original drive is a SATA and on the drive it says "no jumper required for master or alone". My extra drive that I want to hook up is a ATA (thus, the adapter) and has the next to last row jumpered for slave.

---

### Post by Mark Phelps on 2013-02-10
From what I recall, you can't hook up an IDE drive as "slave" -- unless there is also a "master"; so, either jumper it as Master or remove the jumper.

---

### Post by dabl on 2013-02-10
I've got one of those adapters too.  AFAIK, when connected to a USB port, the IDE/PATA drive is just another "USB mass storage device", as far as the computer is concerned.  Rules about the IDE controller are N/A.  Probably you can remove that last jumper -- it may or may not be part of the problem.

I have never had the computer go into that beeping mode though.  Do you have other USB devices that you could test with?  Do all other USB devices work correctly?

Then the next questions would be related to the drive -- what is the filesystem, does it have a good partition table on the MBR, etc. etc.?

---

### Post by ahallubuntu on 2013-02-10
~

---

