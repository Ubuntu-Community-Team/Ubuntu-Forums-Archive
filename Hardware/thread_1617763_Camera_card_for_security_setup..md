---
title: "Camera card for security setup."
date: 2010-11-09
forum: Hardware
---

### Post by outleradam on 2010-11-09
I bought a "Netrome Security Black Box".   It has a camera card.  It was designed to operate in windows.  The rest of my network operates on Ubuntu.  I installed Ubuntu on the computer.

The card is supposed to set up 8 camera devices for access by security software.

The card creates floppy disks in my /dev folder when I install it.
```
fd0 fd0u1040  fd0u1120  fd0u1440  fd0u1600   fd0u1680  fd0u1722 fd0u1743  fd0u1760  fd0u1840 fd0u1920  fd0u360  fd0u720   fd0u800    
```Here is the output from dmsg, ls /dev, and sudo lspci -v with the card in the computer:
[http://pastebin.com/8iuihm4j](http://pastebin.com/8iuihm4j)
I think it is the 01:00.0 Multimedia video controller: Device 1999:a900 (rev 01)

and here is the output from dmsg, ls /dev, and sudo lspci-v with the card not in the computer:
[http://pastebin.com/9aBmFWNY](http://pastebin.com/9aBmFWNY)


I broke my warranty to get these pictures, in hopes that some guru may be able to tell me something by looking at the card.
[IMG]http://i236.photobucket.com/albums/ff111/DrivingTibNaked/Mobile%20Uploads/IMG_0396.jpg[/IMG]


[IMG]http://i236.photobucket.com/albums/ff111/DrivingTibNaked/Mobile%20Uploads/IMG_0395.jpg[/IMG]


[IMG]http://i236.photobucket.com/albums/ff111/DrivingTibNaked/Mobile%20Uploads/IMG_0394.jpg[/IMG]


[IMG]http://i236.photobucket.com/albums/ff111/DrivingTibNaked/Mobile%20Uploads/IMG_0393.jpg[/IMG]


[IMG]http://i236.photobucket.com/albums/ff111/DrivingTibNaked/Mobile%20Uploads/IMG_6619.jpg[/IMG]





So, what do you think?  How should I go about making those floppy devices into cameras?  What else can I check?  What can I do?  What can I try?

---

### Post by outleradam on 2010-11-09
There are two of these on the board [http://www.alibaba.com/product-free/246437867/Video_Decoder__Nextchip_NVP_1104.html](http://www.alibaba.com/product-free/246437867/Video_Decoder__Nextchip_NVP_1104.html)

> 
 			Nextchip: NVP 1104
NVP1104 is the specialized Video Decoder  for surveillance systems including 4-Ch Video Decoder and 4-Ch Voice  Codec. 4-Ch Video Decoder delivers high quality images. It accepts  separate 4 CVBS inputs from Camera, TV, VCR and the other video signal  sources. It digitizes and decodes NTSC/PAL video signal into digital  video components which represents 8-bit CCIR656 4:2:2 format with 27MHz  or 54MHz/108MHz multiplexed. 4-Ch Voice Codec is 4-Ch PCM Voice...

---

### Post by outleradam on 2010-11-09
The samsung 722
K4S643232H-UC60
chips are 64 megabyte memory chips.

The ALogics
AM-7209 chip is a video processor chip which handles up to 16 streams at a time.

There is one more,  
The A.Logics
APC-912 chip..  It is unknown.  I cannot find a datasheet or information anywhere.



So...  Out of all of those chips...
[http://i236.photobucket.com/albums/ff111/DrivingTibNaked/DSCN0557.jpg](http://i236.photobucket.com/albums/ff111/DrivingTibNaked/DSCN0557.jpg)
[http://i236.photobucket.com/albums/ff111/DrivingTibNaked/DSCN0561.jpg](http://i236.photobucket.com/albums/ff111/DrivingTibNaked/DSCN0561.jpg)

It seems like the most important one is the NVP 1104.  I think if I can find a driver for a product which has another NVP 1104, I may be able to adapt it to my card.


I'm going to start by building a kernel without floppy drive support.

---

### Post by outleradam on 2010-12-11
This is moving very slowly and I am getting nowhere.

lspci -vvknn says this:
```

-01:00.0 Multimedia video controller [0400]: Device [1999:a900] (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at d2000000 (32-bit, prefetchable) [size=1K]

```

So there is no module assigned to the device, but however, it still registers as a series of floppy block devices.

Maybe if I could figure out a way to mount the block device as a read-only charactor device it could work somehow?

---

