---
title: "USB Flash Memory"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by Neanderage on 2008-02-05
Hello, 
I have Ubuntu 7.10 and when I try to insert my USB Flash Memory, for one second it shows at "My Computer" and then it disapears. 

Thanks in advance.

---

### Post by Neanderage on 2008-02-05
Please, somebody.... I have been working on my own to fix it for days but no result... so I need your help...

---

### Post by rrsodl on 2008-02-05
> **Neanderage said:**
> Please, somebody.... I have been working on my own to fix it for days but no result... so I need your help...

I guess you have followed the guide to install ubuntu 710 in the USB memory stick.

Well, your next step is to go into the Bios and make sure you can boot from a USB. 

The second step is to insert the USB memory stick in the USB port and turn on your pc. If you go directly to windows then you probably cannot boot from USB.

In some PC's you can press F8 while booting to select a booting device.

There is a guide in wwww.pendrivelinex.com  on  how to boot from a floppy disc for pc's that cannot boot directly from USB


Rick

---

### Post by Neanderage on 2008-02-06
sorry,

Actually I have installed Ubuntu on my system, and everything is works fine except USB Flash Memory.

when I insert any USB flash memory into my system, Ubuntu does not read it and it's not listed in "my computer".

please help out...

---

### Post by froy02 on 2008-02-06
Does it mount in Windows?  Did you at one time booted up with it plugged in?

---

### Post by Neanderage on 2008-02-07
It has always been working and still does using any windows os, but not on Ubuntu. 

could this be realted to File System? I formated it using Fat, Fat32 and NTFS but none is found by Ubuntu

---

### Post by kesman on 2008-02-07
Have you tried if it appears to the desktop in the LiveCD?

---

### Post by Neanderage on 2008-02-07
I have tried it using Ubuntu LiveCD, and still did not show up on Desktop or Places>Computer.
I have inserted it even to other usb ports on the case, but no differences.
The only place I can kindof see it is using GPared but can not do anything with it....

---

### Post by notwen on 2008-02-07
After you plug in your USB flash drive, did you ever check the contents of your /dev or /media folders to see if your USB drive is showing up.  I know in Feisty USB drives are auto-mounted by default, I would assume they are also in Gutsy, I cannot verify.  If not you may simply need to mount it after plugging it in, I'm sure there is a way to enable this as well.  Just wondering off the top of my head do you use any other USB devices while you're running Ubuntu?

---

