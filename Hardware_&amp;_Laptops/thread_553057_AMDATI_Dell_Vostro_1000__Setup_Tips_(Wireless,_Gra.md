---
title: "AMD/ATI Dell Vostro 1000 : Setup Tips (Wireless, Graphics, Beryl, etc)"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by Spam Banjo on 2007-09-17
I have had a few issues with my Dell Vostro 1000 under Ubuntu but have just about everything I need. I feel strangely compelled to put all of this information in one place so the next guy doesn't have the same treasure hunt I have.

I have the Vostro 1000, AMD 64 X2, 2GB Ram and the upgraded TrueLife Display.

I'm offering tips to get the following to work:
[LIST]
[*]**GRAPHICS **: ATI Radeon Xpress 1150
[*]**WIRELESS **: Dell 1390 Wireless Card
[*]**DESKTOP **: XGL for Beryl, GL Desktop, Compiz Fusion, etc
[/LIST]

There are many different model Vostros using different boards & chip-sets, but I'm fairly confident these guides will work for most of the AMD/ATI variants. Dell drivers, etc seem to be fairly generic.

**Graphics Drivers ( ATI Radeon Xpress 1150 )**
I advise using the drivers offered by the Restricted Drivers manager within Ubuntu. The ATI web site did not offer the exact drivers for the 1150 anyway, but I'm told the 200 drivers on the ATI site are the same as the ones suggested by the Restricted Drivers manager anyway. The ATI site's drivers will give you the catalyst control panel, but I have always found the recommended drivers to function better on previous machines. With the Ubuntu drivers, I can run full screen 3D games like Nexuiz and OpenArena as well, if not better than in Vista.

**Wireless ( Dell 1390 Wireless Card )**
I used an installer to detect my card and offer the correct method for getting my card to work. It was written into a guide on the Ubuntu Forums [and can be found here]("http://ubuntuforums.org/showthread.php?t=405990&highlight=dell+1390"). I was a little dubious at first, but after reading all the posts thanking the original poster, I gave it a go. It works perfectly, and makes light work of what is normally a tricky task for beginners.

**XGL & Beryl**
Again, I found [this incredible guide]("https://help.ubuntu.com/community/Beryl/ATI/Feisty") for XGL and Beryl. It's easy to follow, and does nothing unnecessary to your machine. I've followed hundreds of guides to get this working on various machines... all ATI (Nvidia normally just works... sorry guys!)... and this is by far most straight forward and successful.

I will add to this post as I find more stuff, and appreciate any feed back or links to alternative guides regarding AMD/ATI Vostros.

---

### Post by himynameiskevin on 2007-09-28
i just installed feisty fawn on my vostro 1000... having a few problems, figured maybe this would be a good place for it.

there are no screen brightness controls, in the power management or anything. fn + up/down don't do anything (but they do at the grub menu). any advice on that is appreciated..

also i can't get beryl to work. it installed just fine and everything, but when i try running it i get this:

> **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0


also in another thread somebody brought up the fact the fans are not working properly.

---

### Post by t0yman5643 on 2007-10-04
I have a vostro 1000 with the restricted drivers installed and xgl/beryl running.

ive been trying to play world of warcraft via wine, however I only have software rendering instead of hardware rendering, so i only get around 3 frames per second when i try to play.

if you can tell me what you did to get hardware rendering going it would be greatly appreciated

---

### Post by Spam Banjo on 2007-10-04
> **t0yman5643 said:**
> I have a vostro 1000 with the restricted drivers installed and xgl/beryl running.

ive been trying to play world of warcraft via wine, however I only have software rendering instead of hardware rendering, so i only get around 3 frames per second when i try to play.

if you can tell me what you did to get hardware rendering going it would be greatly appreciated

I haven't had much time to mess with games in wine to be honest.

As for direct 3d... it kinda just worked. I followed the guides above to get everything going with full 3D support.

---

### Post by jaakan on 2007-11-20
the version I just got is 
Vostro 1000, AMD 64 X2, 1GB Ram 
    * GRAPHICS : ATI Radeon Xpress 1150
    * WIRELESS : Dell 1390 Wireless Card

I used the restricted drivers for both ATI and wireless

I got it with XP. I updated the bios and then I wiped it and put on 7.10 desktop.

the only issue was have to reload the restricted driver for the wireless on ever boot but it work perfectly 


thats a win for DELL and Ubuntu

if the "reload the restricted driver" gets fixed soon DELL could have more hardware working  out of the box without jumping through hoops...

---

### Post by Spam Banjo on 2007-11-21
> **jaakan said:**
> the only issue was have to reload the restricted driver for the wireless on ever boot but it work perfectly 

Just upgraded to 7.10 myself but decided to give Xubuntu a go seen as I was formatting the Ubuntu drive anyway.

WOW!!! I am simply amazed!

As you say, a sure win for Dell, ATI and Ubuntu. Well done guys!!!

Kudos to anyone involved with XGL or Compiz too... I used to dread that inevitable "can you install that on my computer" question that came with showing someone my laptop. Now with the new XGL setup and improved Compiz front end, it's easier than I thought it ever could be.

These are proud times for linux users... Microsoft must fear the potential we have here.

---

### Post by jaakan on 2007-11-21
And FYI: I got a bug report in on that issue

[https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/164248](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/164248)

which is now marked as Confirmed!

---

### Post by alexisbellido on 2007-12-06
I've got everything working right out of the box in my new Dell Vostro 1000 with Ubuntu Gutsy Gibbon.

At first I was having strange disconnection issues with my Wi-Fi but then noticed I had to enable Wi-Fi on the laptop by pressing Fn+F2 (the key with the antenna symbol).

Great job Dell. It seems you're one of the most Linux friendly big brands around now.

---

### Post by Spam Banjo on 2007-12-11
> **alexisbellido said:**
> I've got everything working right out of the box in my new Dell Vostro 1000 with Ubuntu Gutsy Gibbon.

At first I was having strange disconnection issues with my Wi-Fi but then noticed I had to enable Wi-Fi on the laptop by pressing Fn+F2 (the key with the antenna symbol).

Great job Dell. It seems you're one of the most Linux friendly big brands around now.

Yep... Just changed from X to U myself... everything that was a problem in X, is now working. All straight out of the box or using suggested settings... Compiz, Kiba-dock, etc all running sweet!!

---

### Post by hx129 on 2007-12-22
I just tried Ubuntu Gibbon on Vostro 1000 (AMD 64x2 CPU, 2G memory, ATI Express 1150 integrated display card) and here is some update on this topic:

AIGLX mode still doesn't work.(driCreateScreen symbol not defined).  But I do see GART memory correctly allocated and interrupt is enabled for the display card. This is way better than the case 10 months ago.

THe XGL+compiz works right out of box now(after installing xgl debian package) All video effects of compiz run very smooth.

Wireless link works out of box using the restricted broadcom driver.

---

