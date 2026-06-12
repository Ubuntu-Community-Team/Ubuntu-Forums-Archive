---
title: "Logitech Quickcam for Notebook Deluxe, cannot open /dev/video0"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by dexterBoyGenius on 2006-11-06
Dear fellow Ubuntu users,

I have a problem installing a USB webcam, possibly concerning the udev configuration. Maybe someone can help me?

I just bought a Logitech Quickcam for Notebooks Deluxe (USB-ID 04d7:08d8) for my Laptop, which is running Kubuntu 6.06.1.

I found a driver for the cam, namely the gspca driver, which says explicitly to supports my model. I compiled and installed the driver correctly with no errors and can modprobe it.

dmesg output:
[17396298.524000] Linux video capture interface: v1.00
[17396298.596000] usbcore: registered new driver gspca
[17396298.596000] /home/dexter/src/compile/gspcav1-20060925/gspca_core.c: 
gspca driver 01.00.04 registered

However, when I plug in the cam, I only get the following message:
[17396405.892000] usb 1-1: new full speed USB device using uhci_hcd and 
address 5

There is no message about /dev/video0 coming up on inserting the module, no message in dmesg about a Quickcam found. My Quickcam is not recognized at all by the USB system.

The file /dev/video0 in udev exists, however, but is not readable by xawtv or just a "cat /dev/video0".

Can someone help me on this? I am not an expert on udev.

I would be very happy to hear from anyone.

Thank you and best regards,
        Dexter

---

### Post by amhirsch on 2006-11-08
I have the same QuickCam and just got it working.  I utilized:  [http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz)  

See this thread [http://ubuntuforums.org/showthread.php?t=205782&page=2](http://ubuntuforums.org/showthread.php?t=205782&page=2) for more information.

I hope this helps!

---

### Post by dexterBoyGenius on 2006-11-09
Hey!

Thank you for your reply! So Michel Xhaard has already updated the code, I guess. 

In the mean time, I had looked into the source code of gspca_core.c and saw, that no entry for our cam existed. I wrote him about this and he told me, that the compatibility list on his page shows our cam already, but the code was not included yet into the driver.

So, now I will try that link right away. :-)

---

### Post by dexterBoyGenius on 2006-11-09
Dear Amhirsch (are you german? ;-) ),

the cam works fine now!

Did you also get your mic working? I tried gscpagui and audacity and could not access it.

Best regards!

---

### Post by dexterBoyGenius on 2006-11-09
Okay, the mic also works in principle. It cannot be selected in gspca and audacity, but I could select it as input device in Ekiga (formerly known as gnomemeeting).

On the other hand, no video setting does anything in Ekiga, except the contrast and the program also only seems to use a lower resolution mode of the cam.

---

### Post by amhirsch on 2006-11-10
It's in the blood somewhere! :)

I haven't even played with the mic yet, but will this weekend.  

Thanks and good luck going forward!

---

### Post by dexterBoyGenius on 2006-11-22
The mic should in principle be accessible as /dev/dsp1. The hardware can even be seen and controled in kmix.

The resolution must be supplied by the program, so it seems. The tv driver of mplayer works fine with the video part of the cam, you can do:

mplayer tv:// -tv driver=v4l:height=480:width=640
or
mplayer tv:// -tv driver=v4l:height=240:width=320

to see your face.

---

### Post by Tuxoid on 2008-04-04
I have been working with the same webcam. It works out-of-the-box in gutsy. There is, though, an issue with built-in mic on the cam. I can record audio from it, but it's scratchier than voice samples on the Sega Genesis. I've been looking around the board, but I can't find any type of solution.

I am under Ubuntu 7.10 using Cheese to test the cam. Resolution is decent, just need better sounding audio recording from the cam's internal mic.

---

