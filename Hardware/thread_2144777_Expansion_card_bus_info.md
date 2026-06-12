---
title: "Expansion card bus info"
date: 2013-05-13
forum: Hardware
---

### Post by awacs on 2013-05-13
Any way I can tell, without cracking the box open, which expansion slots I have? lspci, maybe? 
In particular, I'd like to place an adaptec 39160, which seems to require a 64 bit 3.3v PCI slot. I have a lot of boxen which *might* fill the bill, but it's pain to power them down and open them to see what's inside. Ideas?

---

### Post by SJR Dorset on 2013-05-13
Have a look at the support section of the Computer or Main Board manufacturer's website. They should have the information there.

---

### Post by awacs on 2013-05-13
Yes, but how would I tell which main board I have in my white box?

---

### Post by SJR Dorset on 2013-05-14
Is the computer made by a specific manufacturer such as Dell or HP?

---

### Post by awacs on 2013-05-14
Some are, some aren't.

---

### Post by SJR Dorset on 2013-05-14
The best thing I can do is give you a couple of examples on how to find the information:

(1) The computers I look after at work are made by Dell. Each of them has an Service Tag Number which I can use on the Dell support site to find out the specifications of each individual computer.

(2) My home computer was built by myself. If I press the DEL key during boot I can go into the BIOS which tells me that the main board is a ASUS Sabertooth 990FX R2.0. If I look at the ASUS website I can get the specifications including the expansion slots:
[URL="http://www.asus.com/Motherboards/SABERTOOTH_990FX_R20/#specifications"]
http://www.asus.com/Motherboards/SABERTOOTH_990FX_R20/#specifications[/URL]

If your computers are too new I doubt that they will contain the 64 bit PCI slot required by the Adaptec 39160. They are usually only found in servers and higher end workstation type computers that were made a few years ago. For example the older Dell Precision 530, 650 and 670 workstations contain them were as the newer Dell Precision T7500 and T1600 ranges do not.

---

### Post by Yellow Pasque on 2013-05-14
dmidecode is useful... the "-t slot" option will help whittle the output to the part you're interested in.
```
sudo dmidecode
sudo dmidecode -t slot
```

> If your computers are too new I doubt that they will contain the 64 bit PCI slot required by the Adaptec 39160. They are usually only found in servers and higher end workstation type computers that were made a few years ago.
+1

---

### Post by Yellow Pasque on 2013-05-14
Just to mention it, that Adaptec card claims to be functional/compatible with regular 32-bit PCI slots, but it probably won't give you the speed you're looking for with SCSI RAID.

---

### Post by SJR Dorset on 2013-05-14
> **Temüjin said:**
> Just to mention it, that Adaptec card claims to be functional/compatible with regular 32-bit PCI slots, but it probably won't give you the speed you're looking for with SCSI RAID.

You also have to check the clearance behind the slot. Some of the mainboard components might get in the way.

---

