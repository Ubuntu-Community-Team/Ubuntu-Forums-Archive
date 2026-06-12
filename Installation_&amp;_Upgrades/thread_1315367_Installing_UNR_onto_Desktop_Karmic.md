---
title: "Installing UNR onto Desktop Karmic"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Dr_Bobby on 2009-11-05
Hi,

I have tried to install the UNR onto my Samsung N140 from a flash image on a pen drive.  No luck with the usb-creator or with UNetBootin.  The installer would simply crash with "Can not mount /dev/loop1 to /dev/cow" or similar.

Anyway, I tried with the Karmic Desktop .iso and it worked fine.  My question is - can I install the extra UNR packages from within Karmic and if so, what are they?

Thanks!

---

### Post by Thibaud74 on 2009-11-05
I have the same error... search with google, we must configure a file a the root of the usb. We get in touch !

---

### Post by raymondh on 2009-11-05
> **Dr_Bobby said:**
> Hi,

I have tried to install the UNR onto my Samsung N140 from a flash image on a pen drive.  No luck with the usb-creator or with UNetBootin.  The installer would simply crash with "Can not mount /dev/loop1 to /dev/cow" or similar.

Anyway, I tried with the Karmic Desktop .iso and it worked fine.  My question is - can I install the extra UNR packages from within Karmic and if so, what are they?

Thanks!

Dr. Bob,

Used to be able to do that in 9.04 and on a DELL.  I have not tried it yet on Karmic.  Here's the DELL link

[http://www.ubuntumini.com/2009/03/installing-ubuntu-netbook-remix-in.html](http://www.ubuntumini.com/2009/03/installing-ubuntu-netbook-remix-in.html)

Also, I have noticed that I get better USB burn results (using the USB creator) if I choose "non-persistent".  That's the option where you do NOT create space to save files and settings..... rather, all files/setting will be discarded.

YMMV.

---

### Post by Thibaud74 on 2009-11-05
Mhh... When I test md5sum, the original file is 
268b2ecada999fbe2e298c56a9aa1f50
So the test gets :
ed6e77587b87fe0d92a2f21855869f00

Hard to success to download it... Or is a bad file ?

---

### Post by Dr_Bobby on 2009-11-06
Raymond, thanks for link.  Trying it out now.

Thibaud - if your MD5s don't match you should download again...

Cheers

---

### Post by raymondh on 2009-11-06
@ thibaud74 .... use the 'torrent' to download.

@ Dr. Bob,

Am having problems with 9.10 UNR on an MSIWind netbook relating to X (graphics).  Hope all's well your end.

Regards,

---

### Post by wojox on 2009-11-06
@ Dr. Bob

Just open synaptic and search ubuntu netbook remix. You can download and install on top of karmic.

---

### Post by jthirt on 2009-11-07
wojox,

I did exactly that and I'm now trying to find out where I can activate the netbook desktop. 

The only sign of change is that windows are now automatically maximized (I understand maximus does that) and title bars are gone, but I have no sign of the new desktop and the desktop-switcher doesn't exist in synaptic. 

Is there a distinct source for it?

I have an old laptop with a fairly low resolution (1024x768) so it would be nice I guess!

thanks for your help!
JT

---

### Post by jthirt on 2009-11-13
I gave up and re-installed from scratch. But now it is another ball game with the launcher not working as expected!

See [here]("http://ubuntuforums.org/showthread.php?t=1325096") for details!

---

### Post by Thibaud74 on 2009-11-16
Hi,
I downloaded the daily version, not the link corrected. I verified the md5sum, it's good now. So, I installed UNR with a bootable usb disk (my first key was not recognize in the setup). Now, UNR is installed and work ! The only problem is with the resolution, 1024x768 is not recognize (only 1024x600 or 800x600), so I will try to find a best driver because clone mode is usefull for presentations.
Thanks,
Thibaud.

---

