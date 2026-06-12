---
title: "Sony viao VGN-CR120E/R wireless, screen resolution"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by makhand on 2007-08-07
I just got a very pretty new sony viao VGN-CR120E/R. I cant wait to wipe vista off this baby. I booted the fiesty disk and am having some issues. My wireless card doesnt look like it is being detected at all. Also, the resolution is set to 800x600. Right now, wireless is priority. if anyone has had success with this one, let me know. I'm also downloading the gusty alpha and will see if that does any better at detecting the hardware.

---

### Post by kerry_s on 2007-08-07
vaio is not very well supported, to much proprietary. mines from the 1990's and it still not supported. there are workarounds for somethings, but you must specify what you have, it's all in the details.

my guess is you just need to switch to your video driver in xorg.conf, it's most likely set to vesa.

wireless is always a roll of the dice.

---

### Post by makhand on 2007-08-07
> **kerry_s said:**
> vaio is not very well supported, to much proprietary. mines from the 1990's and it still not supported. there are workarounds for somethings, but you must specify what you have, it's all in the details.

my guess is you just need to switch to your video driver in xorg.conf, it's most likely set to vesa.

wireless is always a roll of the dice.

thanks for the response. I'm a bit disappointed to hear about the lack of support for viaos. (i realize its not Ubuntu's fault).

Putting in Gusty Tribe 3 makes the screen resolution work just fine, but still no network. Logging back into vista tells me that i have an Intel Wireless WiFi Link 4965AGN. The video card is a Mobile Intel 965 Express Chipset Family card. Hopefully, by the time gusty comes out at lease the wifi will also be supported. This is quite a nice laptop.

---

### Post by 0live on 2007-08-07
There's only a fairly limited set of drivers on the CD. Wireless didn't work for me either when I booted from Feisty's CD, but now it works.
I own a VGN-FS115Z and cannot guarantee it'll work on yours as well, but it's not because it doesn't work with the CD that it won't work with the 'full' install.

---

### Post by makhand on 2007-08-07
according to [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi) , it appears that intel is actively working on this as we speak. The question then becomes, is this now integrated into gusty, and if not, when will it be. Apparently, the chipset that i have is pretty new and allows for the 802.11N protocol, so new drivers need to be developed for linux. I'm hoping that they have something that works well and soon. Also, apparently the support of the new network stack that this card requires is included in the newest linux kernel. 

I'll try to get something working soon (when i have some time) and will try to post back here.

---

### Post by makhand on 2007-08-10
Looks like the wireless issue is fixed in gusty alpha 4. I really wanted to give winVista a chance, but this is quite tempting. Dont know if its is a good idea to install an alpha, but, I'm quite happy with this and was getting pretty annoyed with the slowness and annoyingness of vista's constant confirmations. I suppose I'll keep my data backed up in case of major breakage. 

GOOD JOB UBUNTU DEVS! (And intel guys too)

---

### Post by AlbinoButt on 2007-08-10
makhand, if you don't want to install the gutsy alpha or wait until it's released you can get the 4965 working by backporting the gutsy kernel to feisty.  Things will be much more stable than running the alpha. [Here's the guide]("http://ubuntuforums.org/showthread.php?t=493095").

---

