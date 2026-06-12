---
title: "Canon Powershot SD Cameras...compatible with Ubuntu?"
date: 2009-08-24
forum: Hardware
---

### Post by pbateman on 2009-08-24
Hey guys
I have a Canon Powershot SD 790IS and a SD600. None work when I plug them into the PC to retrieve pictures (Ubuntu 9.04). They do not get recognized, as soon as I plug either one trough the USB port the screen goes black and activity light on the camera blinks for a second then goes off. Both work fine in Windows. Are they just incompatible with Ubuntu? 
Thanks!

---

### Post by tgalati4 on 2009-08-24
I have a Powershot A70.  I use the procedure:  turn off the camera.  Plug in USB, turn mode switch on camera to "Playback", turn on camera.  Wait a few seconds.

Windows drivers somehow detect and initiate the USB connection without any defined procedure.

This is one area where, sadly, windows outshines ubuntu.

If you are still having problems, open a terminal, plug in the camera with USB and post the output of:

dmesg | tail -30

---

### Post by tubasoldier on 2009-08-24
I've always just pulled my memory card out and plugged it into my media card reader. It seems to work faster for me that way.

---

### Post by oldfred on 2009-08-25
I do the same as tubasoldier even in windows. I can then browse the card on the computer and manually copy photos over to my photo save file structure which is not the as the default in either windows or ubuntu. Data is on a FAT partition so I can share but now primarily use ubuntu.

---

### Post by gordintoronto on 2009-08-25
> **pbateman said:**
> Hey guys
I have a Canon Powershot SD 790IS and a SD600. None work when I plug them into the PC to retrieve pictures (Ubuntu 9.04)....
Thanks!

I always turn off my Canon Rebel XT, connect it to the computer, then turn it on.  I don't like adding wear and tear to my memory cards.

Do you have F-Spot installed?  (I forget whether it's part of the default installation.)  That's the program which is suggested after I turn on the camera.  I always go into its preferences to specify a new folder for today's pictures.

---

### Post by tubasoldier on 2009-08-25
You may want to look into digikam. It has a very slick interface for importing pictures and organizes them in a very logical manner.

---

### Post by pbateman on 2009-08-25
Thanks for the tips! I will try that tonight once I get home. I usually use the card reader too in my laptop.My desktop is really old and does not have one.
I will try using Gimp after plugging the camera to see if it picks it up, the weird thing it's almost as if it was the camera that acts up (although both of them do it) it just shuts down once I put it in playback....we'll see...
Thanks again!

---

### Post by tgalati4 on 2009-08-25
Make sure your batteries are fresh.  I think only battery power is used to initiate the transfer.  If your camera doesn't boot completely, then there's no way to start the USB discovery process.

---

### Post by pbateman on 2009-09-11
Just wanted to update this thread in case others have the same issue. I got it to work by plugging the camera while the pc is off and then turning the PC on with the camera plugged in. A bit of a hassle but since I don't upload pics that often i can live with it.
Thanks all for the help

---

### Post by Marti68 on 2009-10-12
This looks like it may solve my issue with 9.04 and a Canon G3.  Do I simply need a dedicated card reader rather than work through the Canon on camera connected to the USB port?

Thanks for your help guys.

---

### Post by dabl on 2009-10-12
Just get one of these:

[http://www.sandisk.com/products/readers-accessories/sandisk-imagemate-all-in-one-usb-20-reader.aspx](http://www.sandisk.com/products/readers-accessories/sandisk-imagemate-all-in-one-usb-20-reader.aspx)

There are other models and OEMs -- but that's the idea.

---

### Post by Cycron on 2009-12-11
Thanks for helping me solve my problem. :)

---

### Post by Gene Rodgers on 2009-12-11
Have you tried DIGIKAM. It will auto detect your camera and it works better than any Windows program, especially with multiple digital cameras. I lost the Windows software for 2 of mine and was able to detect and download photos, whereas Windows don't recognize and camera being attached. Go figure.

---

