---
title: "[SOLVED] Compaq Presario SR1500NX and USB boot question"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by Interestedinthepenguin on 2007-09-28
Can a Compaq Presario SR1500NX boot from a USB device?

**EDIT:**  No, it can't.

---

### Post by bobosity on 2008-02-23
The Compaq Presario SR1500NX 3000+ DOES boot from the usb. You may have to set it in the bios but it does work.

---

### Post by Interestedinthepenguin on 2008-02-25
Really?  

I don't know if I have the 3000+ version...  How do I check?  

The only options that I see in the BIOS are:  'Floppy group', 'HDD group', 'CD-ROM group', 'Network group', and 'Disabled'.

---

### Post by bobosity on 2008-02-26
I'm sure there is a program that will tell you the specs but look in the bios under the advanced tab. It will have everything right at the top.
Go to your boot sequence and move CDROM  group ahead of HDD. That's the only setting I see in my bios and it boots usb just fine.

---

### Post by Interestedinthepenguin on 2008-02-29
Oh; I thought there was supposed to be an option for USB booting...

Thanks a bunch!:)  

Btw: I found out that my Compaq is a 3000+ by looking at the CPU section of the output of ```
sudo lshw
```.

I currently don't have any USB devices to test the booting, but I'm sure it'll work.

---

