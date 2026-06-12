---
title: "Eee PC 701 4G w/ XP, want to install Ubuntu"
date: 2008-12-11
forum: Hardware
---

### Post by Rubicon421 on 2008-12-11
So I want to put Ubuntu on an Eee PC with XP installed on the 4GB SSD. I have plenty of 2GB jumpdrives and one 4GB SD card. I also have an external DVD drive. 

So what is the best method to add Ubuntu in this case?
Live CD from external drive or as iso on SD or jump drive?
Wubi without separate partition?
partition first in Windows?


I would prefer to install Ubuntu on the SSD so I don't have to constantly take up one of the USB ports or SD card slot to run it from. 

Please indicate if you have successfully done any of these methods.

Thanks!

---

### Post by Rubicon421 on 2008-12-11
I just saw on the eeebuntu.org forums that eeebuntu 8.10 releases tomorrow. Should I wait and try that first? If there is a fairly easy method to install 8.10 on and Eee PC 4G with XP I would like to try it first incase the new release still has some bugs to work out.

---

### Post by snowpine on 2008-12-11
Hi Kill Vista, a 4gb is TINY for both Ubuntu and Windows. I would suggest either replacing XP entirely or installing Ubuntu to an SD card (but it will be very slow). 

When I installed Ubuntu to my eee, I used an application called Unetbootin (easy to find on google) to copy the Ubuntu .iso file to a 1gb thumb drive. Then, boot the eee from the thumb drive, and it's just like installing from a live CD.

Hope that helps, please ask if you have questions!

---

### Post by Rubicon421 on 2008-12-11
I used unetbootin to put eeebuntu 8.04 on a usb drive but it only gives me options to 'try' it or install it on the eee pc. How can I make the usb drive be the install itself so that any changes are made on it and I can add programs to the usb drive instead of the hard drive?

---

### Post by snowpine on 2008-12-11
> **Kill Vista said:**
> I used unetbootin to put eeebuntu 8.04 on a usb drive but it only gives me options to 'try' it or install it on the eee pc. How can I make the usb drive be the install itself so that any changes are made on it and I can add programs to the usb drive instead of the hard drive?

Boot from the USB and choose Install. But rather than install it to your eee, install it to a different USB drive. When you get to Step 7 of the installer, click Advanced Options and make sure you install the Grub bootloader to the correct device, your 2nd USB drive, not your internal drive.

If you don't have two USB drives, but you have a computer with a CD drive, you can burn a Live CD, boot from the live CD, and then install to the USB device. Again, make sure you install Grub in the right place.

This will do a full install to the USB drive, meaning you can save your documents, install new applications, even do kernel upgrades. However, it will be slower and take up more space than a live USB type of install; I would recommend 4gb minimum.

Good luck, let me know if you have questions!

---

### Post by Rubicon421 on 2008-12-11
I just did that and finished the install then restarted. I got the following error on start up

grub loading, please wait...
error 21


I'm trying to make a nlite install now. Got any tips or know of a good tutorial?

---

### Post by MonkeyPaw on 2008-12-11
nLite should explain things fairly well as you go. Each feature is described in some detail. It might take a few trial and error runs, but eventually you get what you want. A word of caution, when I tried to integrate SP3 into my SP2 ISO, it caused a problem with accepting CD keys, so I recommend against integrating SP3 into the nlite ISO. I also recommend keeping IE, as it's needed for windows update. Otherwise, you can really trim down XP to install under 1GB.

---

### Post by Rubicon421 on 2008-12-12
cool, thanks. I found this tutorial for nLite, 
[http://www.eeeguides.com/2007/12/this-tutorial-will-show-you-how-to-slim.html](http://www.eeeguides.com/2007/12/this-tutorial-will-show-you-how-to-slim.html)
If anyone has time, could you skim through it and see if you agree with the settings they recommend? Also, does anyone know what areas or options in XP take up the most space? I would like to leave anything that is not going to save a significant amount. Just seems kind of stupid to loose a bunch of features that only took up a few MB. I know extra languages are not needed, but the tutorial recommends leaving out the drivers since they are all on the Eee PC recovery disc. So what will happen when I plug in some device that needs those drivers and I can't get on line?

---

### Post by MonkeyPaw on 2008-12-13
Well, if there is specific hardware that you know you'll plug in, then make sure you don't remove them with nLite. I found that I didn't plug that many other devices into my Eee, mainly just thumb drives and other external drives. Also, as the tutorial said, you will have all your other drivers for the Eee hardware (I made sure I had them all on a thumb drive for quicker/faster installation). As long as you can get your network working (or internet available on another PC), you can typically recover from any major problems.

---

### Post by BlackGlance on 2008-12-21
Hello everybody.
I'm new here.

Isn't it possible to install ubuntu on Asus Eee PC with 2 GB?
I've added 8 GB SD card and tried to install ubuntu 8.04 and then ubuntu eee on it, but didn't work?
One of them (can't remember which one exactly, but I think ubuntu 8.04) was installed on SD, but computer couldn't boot from SD card.
and the other OS simply couldn't install on that card.

please help me. I don't like xandros, which is installed on my pc.

---

