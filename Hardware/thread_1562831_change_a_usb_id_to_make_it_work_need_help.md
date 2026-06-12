---
title: "change a usb id to make it work need help"
date: 2010-08-28
forum: Hardware
---

### Post by lama85 on 2010-08-28
hello 
i have a skystar usb 2 hd and i read a thread that i can install the driver but i did all things but nothing come on,,,they wrote that i must change the usb id how to?

this is the link of wiki
 [http://www.linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_2_HD_CI](http://www.linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_2_HD_CI)

note : device Vendor ID: 14f7 Product ID: 0001
on my pc : vendor id :14f7 product id :0002


so plz need help for this problem

---

### Post by Zimmer on 2010-08-28
I read the link you posted... the first line ..
A DVB-S2 USB 2.0 Device from Technisat It is currently unsupported.

The instructions that follow in the wiki are an attempt to get it going.

So, by USB ID if we assume they mean the label on the USB disk partition of the device, it might be that the device will appear somewhere in gparted and you could use gparted to change the label.
If that is possible, then make sure you note what it is BEFORE you change it...just in case..

If this is not the case... then, sorry , I have no other idea other than you might need to change the Vendor ID to match that of the terratec device whose drivers you are trying to make it work.
I have no clue as to how you would do that.

---

### Post by Zimmer on 2010-08-28
[http://www.vdr-portal.de/board/thread.php?threadid=93801](http://www.vdr-portal.de/board/thread.php?threadid=93801)

Read particularly the posts that are in English referring to altering the drivers to recognise a different version of the same terratec card and maybe apply that with info from your Skystar...  just a thought ..

---

### Post by lama85 on 2010-08-28
so u think that the subject posted in that link will not go on with my skystar ?so what the think when writing u must change the usb id to make it work?

sorry but i am new on ubuntu 

really thanks

---

### Post by Zimmer on 2010-08-28
I am new to messing with drivers to TV cards, too! :)
And following the instructions you linked to is a challenge, too. I can see where errors may have crept in as well.

  idVendor           0x14f7 
Describes your card from the output of sudo lsusb ?
Ganmark wrote:
> In this case, to have the card detected you have apply a little patch to v4l sources:
in file linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h just changecode:
1:	#define USB_PID_AZUREWAVE_AZ6027           0x10a4



tocode:
1:	#define USB_PID_AZUREWAVE_AZ6027          0x10ac


Logic says you alter yours to  0x14f7 and maybe that is what they mean by 
> You have to change the usb-id to make it work.

Depending which of the instructions you used to try and get it to work (and what errors you may have had), tweaking and altering stuff may not work as expected.
It might be better to start from the beginning.

(I do not have  any TV capability on my machines and when I first read your thread I thought it was a matter of changing a label on a USB thumbdrive...)

---

### Post by limotux on 2011-05-31
hmmm... reading.. searching... ughhh

The problem is I encountered many contradicting info here and there... some said it works out of the box, others said, need to change usb id, others say need to install drivers...

I feel lost

Any success? Any advice?

---

