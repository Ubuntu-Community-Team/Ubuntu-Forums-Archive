---
title: "No name USB 2.0 TV BOX - driver needed"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by cmavr8 on 2007-09-06
Hi everybody,
I searched for it but can't find many relative results, so I post:

I have bought a cheap no name usb tv box, called just "TV BOX" on the outside, from Ebay.

There is a label from below that says "MODEL:USB2.0BOX" and has a serial number: "S/N:SVZG06123200B00175"

It works fine on Windows (after messing for a few days with different drivers) but when connected to my Ubuntu laptop it's not recognized as /dev/video0.

lsusb gives (I just give the interesting line):
Bus 001 Device 008: ID 6000:0001  


Any ideas on how to procceed on installing/using?

Thanks

---

### Post by Jimmy The Clown on 2007-09-09
You are most likely going to have a lot of trouble installing this, if it is even possible. What driver did you end up using under Windows? Linux support for TV capture devices tends to be pretty specific and it is best to do some research and find devices that are currently maintained and include drivers in the kernel. For the most part Windows drivers are not compatible with Linux (exception being with emulation like ndiswrapper) and many manufacturers do not develop linux drivers.

sorry :-(

-JTC

---

### Post by cmavr8 on 2007-09-09
Yeah... I experienced the lack of linux support with my laptop... I've got camera and fingerprint sensor just sitting and rotting...

Anyway, I don't know which driver it is... In the device manager it says Sinovideo analog video.

---

### Post by Flasharino on 2008-05-27
I have the same device and after a bit of searching found that the same thing is made by Sabrent ([www.sabrent.com](www.sabrent.com)) as model TV-USB20.  Unfortunately they do not provide any Linux drivers.  Please let me know if you find any and I will do the same.

Flash

---

### Post by Mr_Congeniality on 2008-05-31
I have one of these as well, but I haven't even tried it on linux yet.  Try going to Multimedia Devices Selector (you may have to enable it in edit menu) and change the default video input from V4L to V4L2.  It may work, who knows.

---

### Post by fbifido on 2008-07-09
is there a command line tool to do that
change from v4l to v4l2?

Card: Sabrent USB 2.0 TV Tuner
input: Video-Composite

lsusb
Bus 004 Device 002: ID 6000:0001

sudo lsusb -v | less
Bus 004 Device 002: ID 6000:0001
Device Descriptor:
  bLength      18
  bDescriptorType 1
  bcdUSB          2.0
  ...
  idVendor  0x6000
  idProduct 0x0001
  iManufacturer  16 Trident
  iProduct       32 TVBOX
  iSerial        64 2004090820040908

---

