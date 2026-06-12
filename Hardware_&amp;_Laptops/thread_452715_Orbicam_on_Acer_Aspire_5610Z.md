---
title: "Orbicam on Acer Aspire 5610Z"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by dejan847 on 2007-05-23
I have installed Ubuntu 7.04 on Acer Aspire 5610Z but I cannot make Orbicam to work.  
Has anybody had any luck with Orbicam on this specific laptop?
Thanks.

P.S.  I have read post "(some) ACER Orbicam integrated webcams now supported by GSPCA" but had no luck with Orbicam.  In fact, when I did "lsusb" I get only this "Bus 001 Device 002: ID 5986:0100".  Any suggestions?

---

### Post by misconfiguration on 2007-06-18
Sadly I think this 'orbicam' is a piece of crap, I have the same laptop, it came bundled with Vista. This webcam worked for a few days with Vista drivers and it was gone, couldn't get it to work again. I then put Ubuntu on the laptop (I wanted to try Vista) I have no driver support for that either. I know of a driver project out there, I have it bookmarked, this is dedicated strickly for generic webcams, let me find it and get back to you!

---

### Post by corq on 2007-07-01
> **dejan847 said:**
> I have installed Ubuntu 7.04 on Acer Aspire 5610Z but I cannot make Orbicam to work.  
Has anybody had any luck with Orbicam on this specific laptop?
Thanks.

P.S.  I have read post "(some) ACER Orbicam integrated webcams now supported by GSPCA" but had no luck with Orbicam.  In fact, when I did "lsusb" I get only this "Bus 001 Device 002: ID 5986:0100".  Any suggestions?

I actually had had no issues with the Orbicam making it work - in fact it worked TOO well when  I was trying to get some DVR programs to work, instead of it pulling from the DVR hardware it pulled video from the webcam, more tweaking ensued. 

Presently I am reinstalling ubuntu for partitioning purposes, and I will attempt to see what "magic" I can recreate, and document it here.

From memory (Flawed memory often enough) it seems like I had extra repos enabled and just DL'd anything in synaptic that looked like it pertained to a logitech camera. I DON'T RECOMMEND this approach unless you are a tinkerer like myself. 

In fact the purpose of repartitioning today is to have a partition full of saved configs so that I may experiment and  "break" ubuntu without a lot of recovery time. 

That said - the Aspire 5610z has been remarkably stable, the Atheros (unsupported) driver even behaved well for me.

I will post with my results on getting the webcam up.

---

### Post by reya276 on 2007-07-03
I don't know how you got it to work, but I got the same Acer type/model laptop and it does not work for me. If you got any tips on how you did please post it. Thanks

---

### Post by corq on 2007-07-04
> **reya276 said:**
> I don't know how you got it to work, but I got the same Acer type/model laptop and it does not work for me. If you got any tips on how you did please post it. Thanks

This may or may not be helpful...I chose to install "camorama" from synaptic - whatever dependencies installed along with it did the job.

HOWEVER, i am still awaiting the much anticipated brightness/color adjustment fix. Presently I just use the monochrome filter in camorama to avoid the green/blue rgb oddness. (The posted modprobe options did not work for me.)

---

### Post by capiscuas on 2007-07-24
Here is a link about how to set the webcam (PCI vendor 5986:0100) and make it work with kopete.

[http://ivangarcia.org/blog/?p=13]("http://ivangarcia.org/blog/?p=13")
:popcorn:

---

### Post by dejan847 on 2007-07-27
I tried to follow the instructions from the posted link, but I managed to do something wrong.
The only application that works with orbicam is kdetv.  I tried luvcview, kopete, camorama, amsn, ekiga and all of them report some sort of error.  For example, ekiga reports error while opening video device USB2.0 Camera, and I get the green or black screen in kopete.  Camorama could not connect to video device (/dev/video0).  The following link states that the orbicam works out-of-the-box in Feisty ([https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5610]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5610")).  However, that is not the case with me.  Could you please advise on what am I doing wrong, and why is that the orbicam works only with kdetv.  
Thanks.

---

### Post by NetWizKid on 2007-10-27
I've had the same problem with the orbicam, according to Acer, if you go to the Vista folder "C:\Windows\BisonC07", there should be several files there, they told me "LiveCam.exe" but it was actually LiveCa07.exe on my laptop.  I double clicked on it and the camera starting working again.  There is much more in at Acer.com on how to really fix the issue, I simply created a new icon.  

Now, what I need to know is there a way to get the camera to come on if it senses movement - sort of a spy camera so I can check on my roommates...  They just like my room better - cable and laptop and stuff.  Hope to hear back from you soon...

---

### Post by trash on 2007-10-31
> **NetWizKid said:**
> I've had the same problem with the orbicam, according to Acer, if you go to the Vista folder "C:\Windows\BisonC07", there should be several files there, they told me "LiveCam.exe" but it was actually LiveCa07.exe on my laptop.  I double clicked on it and the camera starting working again.  There is much more in at Acer.com on how to really fix the issue, I simply created a new icon.  

Now, what I need to know is there a way to get the camera to come on if it senses movement - sort of a spy camera so I can check on my roommates...  They just like my room better - cable and laptop and stuff.  Hope to hear back from you soon...

Hmmm, I can't find a folder or file named BisonC07 nor anything on the Acer website:(.... anybody made any progress with this??

---

### Post by trash on 2007-11-09
Hmmmm, testing the new skype and guess what!?!.... the orbicam works great!
I didn't configure anything so I can't help with any advice at all except that i'm running Gutsy. The Orbicam also works in Amsn and i'm assuming Gyache but havn't tried it yet.

lsusb tells me it's a ...
Bus 005 Device 002: ID 046d:09b0 Logitech, Inc.

and in skype and amsn it shows up as...
UVC Camera (046d:09b0) (/dev/video0)

Hope this helps.

---

### Post by Evagrios on 2007-11-10
I have the same cam on my Acer.

[This page]("http://linux-uvc.berlios.de/") claims to have a driver that support the  5986:0100 device, but I don't know enough linux to make sense of it... Is this something that is worth exploring?

---

### Post by Karmafarmer on 2007-12-21
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
```

Can anyone see my camera in this mess?  I'm on an 5610Z and I can't find my cam.

---

### Post by libertas on 2007-12-23
I too was having problems, i couldn't find anything to run it. I tried camorama and it didn't recognize the orbicam so i tried cheese, which worked. 

cheese can be installed from Applications>Add/Remove 
type in "cheese", once added it worked great for me

---

### Post by Evagrios on 2008-01-17
Thanks, cheese works for me too.

---

### Post by buried on 2008-04-09
Cheese doesn't work for me, Ubuntu doesn't detect my webcam at all I think :(

---

