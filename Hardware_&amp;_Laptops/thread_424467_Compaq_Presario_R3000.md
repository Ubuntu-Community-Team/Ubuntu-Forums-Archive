---
title: "Compaq Presario R3000"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by TheBuzzSaw on 2007-04-26
My wife is using a Compaq Presario R3000 laptop, and we are having difficulty enabling the wireless in Ubuntu 7.04. I've done some research around the web and discovered Broadcom's disinterest in supporting the Linux world, so this is obviously going to be trickier than I originally hoped.

I am somewhat familiar with ndiswrapper which runs wireless Windows drivers, but all documentation I read refers to Ubuntu 6.10. So, my question is this: does ndiswrapper work in 7.04? I noticed that the help file instructed me to install ndiswrapper from the CD using Synaptic Package Manager, but I had to dig out my 6.10 CD in order to do that. The 7.04 CD did not have it (I couldn't find it, anyway). What is the best way to go about enabling wireless for this laptop? We also noticed that the blue light indicating that the wireless device is on/off does not turn on at all in Ubuntu. In Windows, we can freely toggle it back and forth, but it's not too Ubuntu friendly at the moment.

---

### Post by karpluk on 2007-04-29
I have the same hardware (and the same setup - it's my wife's computer) and am wondering if you have had success? Please post with any information that might assist me. We've installed the 64 bit version of 7.04.

Thanks.

---

### Post by kberkopesies on 2007-05-01
I have the same problem with Feisty Fawn on my Compaq R3000.  I installed ndiswrapper, and the driver is working ok, but the card is disabled.  Running iwlist tells me the card is disabled, and the blue light next to the activation button is off.  All the documentation I've found says that a solution might be brand-specific.   Can anyone please help?

Thanks,

Kyle

---

### Post by zhfm622 on 2007-05-01
i don't know if this works for you, at least i have had wireless problem before and solved it via the following :

there are packages you need:
alsa-firmware-loaders
atmel-firmware
bcm43xx-fwcutter

just install them by Synaptic Package Manager, then reboot. 
and don't forget start your wireless ;-)

Good luck!

---

### Post by TheBuzzSaw on 2007-05-19
> **zhfm622 said:**
> i don't know if this works for you, at least i have had wireless problem before and solved it via the following :

there are packages you need:
alsa-firmware-loaders
atmel-firmware
bcm43xx-fwcutter

just install them by Synaptic Package Manager, then reboot. 
and don't forget start your wireless ;-)

Good luck!
Are these available on the CD? Or are they only online? If they're online, is there a way I can download them using my computer and then move them over using my USB drive or something? Please enlighten me further! Thanx in advance!

---

### Post by Escipion on 2007-12-03
I was looking for an answer and bumped with this thread, I'm wondering if any of you got desktop effects working under gutsy??

I even tryed with envy and I keep getting the "Desktop effects could not be enabled" message when I try to activate them.

Thanx

JR

Sorry I forgot to mention that i'm using a R3000 right now

---

### Post by chadeusmaximus on 2008-03-03
I have a compaq r3000 (AMD Athlon XP-M 3000+)  Depending where I look on the net, It's either a R3000, or a R3200.  I have tried every version of Ubuntu from 6.06 on up, and until  7.10, I couldn't get my graphics or my wireless to work. However everything else did work immediately after a fresh install, including my DVD/CDRW & ethernet.

Last fall, when 7.10 came out, I tried it on a whim, not expecting much, but I was pleseantly surprised at how easy it was to get them working by using the Restricted Drivers control panel.  (ADMINISTRATION->RESTRICTED DRIVERS)

It recognized my nvidia nforce 3 AGP card (integrated graphics,) my dial up modem, and broadcom wireless card.  All I had to do was check the boxes, and then it would go on the net and get the drivers.  A couple restarts later, and everything works. 

One thing I noticed though, is that it helps to have ethernet hooked up to the internet during the install process. If I don't, I sometimes (although not always-maybe 25%) have to manually edit the repos.  I'm not sure why this is.  Maybe it checks the repos from the server during installation if there is an active internet connection.

Anyway, the point of the story is to get your wireless working, the easiest way is to go to  ADMINISTRATION->RESTRICTED DRIVERS and click on wireless, follow the EASY instructions, and then restart if it asks you too.  you will then have to chose your wireless network from the network drop down menu on the top right by the clock.  

as for the graphics, It works, mostly. it defaults to 1024X768 (the native resolution for this laptop and while it does give me the option to chose either 800X600 or 640X480, 800X600 works correctly while  640X480 doesn't.  When I select  640X480, it gives me what appears to be top left of 1024X768 and all my windows are extended beyond the visable screen area.  not sure why this is,   Also, I am unable to activate desktop effects, even though i should be able to.  

Also, you may want to keep a copy of the wireless firmware on a CD or flash drive.  That way you can install it locally if you don't have an active internet connection.  It's available at:   [http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)  (This is the address that you download it from in the Restricted Driver control panel)

Update:  I was able to fix part the resolution problem by going to SCREENS AND GRAPHICS ->GRAPHICS CARD tab -> click on NVIDIA-> Choose driver by model -> select NVIDIA ->select LEGACY.    Restarted, and checked all my resolutions.  all 3 work OK.  However, I am still unable to enable desktop effects...

Update 2:  I finally got desktop effects enabled.  First I had to go to SCREENS AND GRAPHICS-> and select LCD 1024X768.  Before it was autodetected, but apparently you need to manually select it.  Then I followed the instructions on this thread:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?page=2&t=632199](http://ubuntu-ky.ubuntuforums.org/showthread.php?page=2&t=632199)

I needed to install x-servcer by doing:   sudo apt-get install xserver-xgl
Then, after a couple of restarts everything worked.  Yay!

Chad

---

### Post by b5baxter on 2008-06-16
I also have a R3000. Using restricted drivers everything works except the multi-card reader.  Has anyone had success getting that to work?

---

