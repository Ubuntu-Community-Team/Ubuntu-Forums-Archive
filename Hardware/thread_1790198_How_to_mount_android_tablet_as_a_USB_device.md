---
title: "How to mount android tablet as a USB device"
date: 2011-06-24
forum: Hardware
---

### Post by fishexe on 2011-06-24
I have an Acer Iconia Tab A500 and the instruction manual said to use it as a USB drive I would just have to plug it in.  Unfortunately, Ubuntu does not automatically do some steps that Windows/Mac apparently do, so, long story short, it did not show up in Nautilus and I did not know how to mount it manually.  The process to do so was a bit convoluted, but I found it in the first post of this thread:
[http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html](http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html)
The only modification to those steps that I needed was to NOT enable "USB debugging" on the tablet.  When "USB debugging" was enabled Ubuntu gave a "Transport endpoint not connected" error.  The instructions in that link are for Acer Iconia and Motorola Xoom tablets but there is a good chance they are applicable to other Android tablets or phones.  If you have to modify the instructions to get yours to work, please post them here so that other people with the same device as you will know what to modify as well.

---

### Post by nicole drake on 2011-10-02
Go to debian download package mtpfs 0.9-3. Then go to ubuntu 11.10 software store and install gmtp 1.2.0. You may get a error message but don't worry the acer a500 will mount it may take a little bit of  play around.

---

### Post by tamouse on 2011-11-21
> **fishexe said:**
> I have an Acer Iconia Tab A500 and the instruction manual said to use it as a USB drive I would just have to plug it in.  Unfortunately, Ubuntu does not automatically do some steps that Windows/Mac apparently do, so, long story short, it did not show up in Nautilus and I did not know how to mount it manually.  The process to do so was a bit convoluted, but I found it in the first post of this thread:
[http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html](http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html)
The only modification to those steps that I needed was to NOT enable "USB debugging" on the tablet.  When "USB debugging" was enabled Ubuntu gave a "Transport endpoint not connected" error.  The instructions in that link are for Acer Iconia and Motorola Xoom tablets but there is a good chance they are applicable to other Android tablets or phones.  If you have to modify the instructions to get yours to work, please post them here so that other people with the same device as you will know what to modify as well.

I'm trying this, and I keep running into the problem with USB debugging. Even though I turn it off, somehow when I plug in the a500 it turns back on.

**Update:** it's now working after I made the following change to /etc/fstab:

Original:

```
mtpfs     /media/a500     fuse     user,noauto,allow_other
```

Change:

```
mtpfs     /media/a500     fuse     user,noauto,allow_other	0	0
```

---

### Post by gnusci on 2012-02-15
The instruction in the OP link worked for me like a charm with a Lenovo Tablet. I can connect with my Ubuntu 11.04 workstation using the USB cable.

Update: tested on Ubuntu 11.10, everything is working fine.

NOTE: Wait about 5 minutes before to mount the tablet, after it is connected by the USB cable.

---

### Post by stephent003 on 2012-07-12
I have ACER A200 Tablet and Ubuntu 12.4.
I did mtpfs and gmtp as per nicoles instructions and it worked fine and easy.

thanks

---

