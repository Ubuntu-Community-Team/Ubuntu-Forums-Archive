---
title: "How to update BIOS without floppy?"
date: 2008-10-10
forum: General Help
---

### Post by YigalB on 2008-10-10
I have ASUS P4P800-SE MB, and I want to update my BIOS.
The problem is that the ASUS is guiding to install via Floppy.
However, I have no floppy installed, and the OS is Ubuntu.

How can I update the BIOS?

---

### Post by dburnett77 on 2008-10-10
> **YigalB said:**
> I have ASUS P4P800-SE MB, and I want to update my BIOS.
The problem is that the ASUS is guiding to install via Floppy.
However, I have no floppy installed, and the OS is Ubuntu.

How can I update the BIOS?

What I did was burn the update to a CD, then used Free DOS to load the flash utility, since mine happened to be DOS based.  The Free DOS website is:

[http://www.freedos.org/](http://www.freedos.org/)

It's a little different than DOS you might be familiar with, but it's not that difficult.

---

### Post by YigalB on 2008-10-10
1- Can i do it with DiskOnKey?
2- Can i do it from the Linux boot ?

---

### Post by lukjad on 2008-10-10
May I ask why you wish to update the BIOS? It can be very dangerous to do so.

---

### Post by drs305 on 2008-10-10
I just updated an ASUS BIOS yesterday. (I had a day to waste should things go bad ;-) ). Does your motherboard support EZ-Flash.

If so, format a usb pen drive as fat16 or fat32. Download the BIOS folder and put it on the pen drive. Insert the usb device and boot the computer into the BIOS setup screen. Go to EZ-Flash and it should allow you to update it from the pen drive.

As the previous poster said, you should have a good reason to update BIOS before doing so.

---

### Post by YigalB on 2008-10-10
Thanks. You are right, of course.
I wouldnt think of updating BIOS just for fun.

I had big problems adding a secondary hard disk (the BIOS recognized it, but the Ubuntu refused to allow me using it, soI suspected the BIOS.
Now that I succeded convincing Ubuntu to let me use it, I will not update the BIOS.

I will also never add secondary hard disk to Ubuntu as well. It's not really supported as it should be (ease of use).

---

### Post by lukjad on 2008-10-10
Ok! I know of people who update the BIOS everytime they find a new driver.

---

