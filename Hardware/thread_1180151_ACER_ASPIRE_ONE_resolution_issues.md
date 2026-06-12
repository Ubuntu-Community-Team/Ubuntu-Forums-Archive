---
title: "ACER ASPIRE ONE resolution issues"
date: 2009-06-06
forum: Hardware
---

### Post by CheeseEatingBulldog on 2009-06-06
Hello all,

Just bought an acer aspire one for my gf, and it loaded ubuntu fine, but now the resolution is stuck and I can't find anywhere to change it.

I have tried to edit the xorg.conf, which is now empty as apparently HAL does that.
I have tried via "display" menu item, which gives no choice but the one filled in
I have tried to dpkg-reconfigure xserver-xorg, which only allows me to set up mous and keyboard.

All nice and well to remove xorg from the equation, but how does one edit a wrongly detected / HAL input.

Can someone point me in the right direction? There used to be another menu item called "screens & graphics" ..where is that?

Thanks in advance!

---

### Post by Ferrat on 2009-06-06
What resolution is it struck on?
do you have the right driver fo you graphic card?

---

### Post by beddy on 2009-06-06
just had this problem with dual screen resolutions on a dell laptop.  We pulled new drivers and installed them. then went to gnu to resize the resolution.. so far no complaints...:p
 
maybe this link can help a bit:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
 
they didnt solve the problem but might help pin point it:
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/resolution-issue-on-acer-aspire-one-with-rhel-5-700363/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/resolution-issue-on-acer-aspire-one-with-rhel-5-700363/)

---

### Post by CheeseEatingBulldog on 2009-06-07
It;s a Acer Aspire One Model:ZA3 ..and what graphics drivers would I need, and how do I install them?

Very annoying that I can't change resolution by hand.

I found [http://touchmods.wordpress.com/2009/05/31/acer-aspire-one-1366x768-graphics-driver-needed/]("http://touchmods.wordpress.com/2009/05/31/acer-aspire-one-1366x768-graphics-driver-needed/") which indicates that I can't set 1366x768 as a resolution? I have tried editing the xorg.conf, but the only resolution I get is 1024x768 which is stretched out and thus horrible.

Is there no one who has any ideas? Can I specify another driver? Can I manually edit the config file that feeds the display menu item? 

Very frustrating as wifi/sound etc work out of the box.

---

### Post by CheeseEatingBulldog on 2009-06-07
Can someone also explain, what [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne") means with the steps "To Fix Choppy Video Playback With Intel Video" .

I think I have added the mtrr fix to the default kernel options, but then the guide loses me. Anyone able to explain these steps in lamens terms?

---

### Post by CheeseEatingBulldog on 2009-06-08
I have managed to add a modeline to the xorg.conf which causes an error when starting gdm, which if you click through with generate new config will give you 1024x768, not ideal as it is not the native resolution ( 1366x768 ), but slightly better than 800x600. If anyone has any ideas please let me know.

---

### Post by seannon on 2009-06-09
Hey Bulldog... the ZA3 is the new AO751H correct? this sounds like exactly the same issue I am trying to get help with as well... may be a good idea to reference the AO751H in the posts as well... the acers seem to be seen as that type of number... 

Seannon

Acer Aspire One AO751h ZA3 2GB RAM 250GB HDD External class 2 Bluetooth Dongle... running 9.04 UNR in gnome desktop mode... (seems Mammoth slows the system down too much) running in 1024x768 until I find a fix...


BTW... I tried using the Xrandr posts... no luck... got a new modeline, but could not get it active...

---

### Post by #11u-max on 2009-06-09
i need some acer help, too. i'm stuck in 640x480 and i need 1024x768.

---

### Post by CheeseEatingBulldog on 2009-06-10
Yes it is the new Acer Aspire One, I have total faith that it will be resolved soon, just a pain.

---

### Post by nordak on 2009-06-10
CheeseEatingBulldog, checkout thread [http://ubuntuforums.org/showthread.php?p=6300992](http://ubuntuforums.org/showthread.php?p=6300992) (quoted below).  It allowed me to run my Aspire One 751 on 1366x768 resolution.

> 
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

and added ppa key as described in link from this page:
[https://launchpad.net/~ubuntu-mobile..._filter=jaunty](https://launchpad.net/~ubuntu-mobile..._filter=jaunty)

I then installed libdrm-poulsbo1 and xserver-xorg-video-psb through synaptic. Then reboot and now 2D works fine and with the correct resolution.

/ Anfanglir


Regards,
Nordak

---

### Post by meeples on 2009-06-10
i have the aspire one andive never had a problem with resolution always been perfect on install.

im surprised you are having problems.

---

### Post by CheeseEatingBulldog on 2009-06-11
> **nordak said:**
> CheeseEatingBulldog, checkout thread [http://ubuntuforums.org/showthread.php?p=6300992](http://ubuntuforums.org/showthread.php?p=6300992) (quoted below).  It allowed me to run my Aspire One 751 on 1366x768 resolution.



Regards,
Nordak

Is it that easy? Just add the repos, update & upgrade and reboot?

Will give it a go later thanks for this.

---

### Post by nordak on 2009-06-11
CheeseEatingBulldog, 
I should specify my Acer One (ZA3) uses the GMA500 graphics card.  
The GMA500 is not well supported for Linux but adding those 2 packages, fixed my resolution issues.

Regards,
Nordak

---

### Post by CheeseEatingBulldog on 2009-06-11
> **nordak said:**
> CheeseEatingBulldog, checkout thread [http://ubuntuforums.org/showthread.php?p=6300992](http://ubuntuforums.org/showthread.php?p=6300992) (quoted below).  It allowed me to run my Aspire One 751 on 1366x768 resolution.



Regards,
Nordak

Nordak, you are a saint! Thanks, worked like a charm. It really was 5 minutes work...and reboot. All looks great now. I know it maybe pushing my luck, but did you get visual effects to work as well? Direct rendering works, so I would assume that they work, unless the graphics card is just too tiny.

---

### Post by seannon on 2009-06-12
> **CheeseEatingBulldog said:**
> I have managed to add a modeline to the xorg.conf which causes an error when starting gdm, which if you click through with generate new config will give you 1024x768, not ideal as it is not the native resolution ( 1366x768 ), but slightly better than 800x600. If anyone has any ideas please let me know.

please check THIS post... I have the AO751H ZA3 as well... the solution has worked for me, Kudos for the poster!!!

[http://ubuntuforums.org/showpost.php?p=7441567&postcount=142](http://ubuntuforums.org/showpost.php?p=7441567&postcount=142)

Seannon

---

### Post by bris8 on 2009-06-25
Hi seannon,
on my AO751h I've just follow your solution. Resolution is 1366 but no hardware acceleration:

/var/log/Xorg.0.log 
(EE) PSB: Failed to load module "Xpsb" (module does not exist, 0)
(EE) PSB(0): the stolenBase is:0x3f800000
(EE) PSB(0): screnIndex is:0;fbPhys is:0x3f800000; fbsize is:0x007bf000
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) PSB(0): has_fbdev is true
(EE) AIGLX error: dlopen of /usr/lib/dri/(null)_dri.so failed (/usr/lib/dri/(null)_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!

Does this happens also to you?

---

