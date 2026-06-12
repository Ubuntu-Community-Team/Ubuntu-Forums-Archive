---
title: "Acer TravelMate 2480-xxxx Laptop Easy Fix Guide"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by Espionage724 on 2007-04-28
This guide will help you set up your Acer TravelMate 2480-xxxx Laptop for use with Ubuntu, and Kubuntu 7.04. I'm pretty sure it will work for Xubuntu also but I didn't test. This guide assumes that you did a clean install of Ubuntu or Kubuntu 7.04 (probally doesn't matter as long as you didn't mess with that much settings. Still wouldn't hurt to try).

First we shall deal with the sound. Intel HDA
In Ubuntu or Kubuntu the sound drivers are already installed with the Intel HD Audio drivers. To enable them go to your mixer settings and just turn all of your audio settings on and max their volume. Then your sound should work.

Next we shall deal with the Video Card. Intel 945 Graphics Media Accelerator
The only compatible video driver is the i810 driver. It works quite well. To set it up (Kubuntu) just go to K Menu > System Settings > Monitor and Display > Hardware Tab. You should see Graphic Card and Driver in the first box. Your Graphic card should be i915 (or i810 mines locked at that for some reason it doesn't matter which though) and your Driver should be i810. For your monitor I choose Plug n Play (widescreen). To enable the 1280x800 resolution I went to Adept Manager and went down the list till I saw 915resolution. (6th choice for me). I installed it and restared my laptop and it works just fine.

Next is the Wireless Card. Broadcom 4318
This wifi card it probally the most difficult thing to setup (It doesn't take too long to install though). First you should probally have Broadcom 4813 Wiress Card on your laptop (I heard that some Acer 2480 laptops come with another card but i'm not sure) (Atheros I Believe. Next go to Adept Manager and search for "Ndiswrapper" (without quotes). Install ndisgtk, ndiswrapper-common, and ndiswraper-utils-1.9 (if there isn't a newer one select 1.9). If they don't show up push Fetch Updates button and then search again. Then install them and exit Adept Manager. Next I download the drivers (go to the acer site and find wireless drivers for your laptop and download them) then unzip them into a folder in your home directory. Next i went to terminal and typed```
sudo ndiswrapper -i /home/(inf location)
``` and pushed enter. Then my drivers were installed. (If this doesn't work just search the fourms for a solution.

Other problems with this laptop are:
Bluetooth
5 in 1 Card Reader (On WIndows Vista/XP its called 6 in 1 for some reason) (I didnt test it, Problem reported by jih68)
4 Keyboard Buttons (Top Left of Keyboard) (2nd Key Works [Email]) (Probelm reported by jih68)

Not tested:
S-Video Port
Modem

-This laptop works fine with Beryl so I recommend that you try it. It is quite nice.
- Untested with Compiz.
- If you use the script that installs your wireless drivers (Somewhere on the fourms) the laptop cannot be far from the router or you will get a bad signal or none at all.
- OpenGL works ok.
- Touchpad drivers can be installed under your package manager (Synaptics)
- Ethernet Port works

Well that is all for now.

---

### Post by jlh68 on 2007-04-28
I also have a Travelmate 2480 and I can not get the 5-in-1 media card reader to work.  I use SD cards so that would be what I would like to get working.  Also my wifi card is an Atheros, I had a little trouble getting it to work but I finally did get it operational.  I also have some problems with the scroll button between the two buttons on the touch pad.  When I press it to go down if opens a menu, press the left side it pastes the last copy,  Another area is the four spcial buttons on the upper left side.  Only the e-mail one works.  So help in any or all of the areas woud help.  I am running ubuntu 6.06lts.  I am going to upgrade to 6.10 then to 7.04 with the hope that these new versions will help me.

---

### Post by Espionage724 on 2007-06-07
In Feisty Fawn the 4 buttons at the top right of my keyboard aren't working correctly either. Only the email works. Also it would be nice to have this page sticky.

---

### Post by March20 on 2007-06-10
My problems are wth the Fn key, sound is fine. evrything else is fine... just the Fn key....

---

### Post by jlh68 on 2007-06-10
I broke my installation of Ubuntu 7.04. I could not boot.  I changed the BIOS so it would boot from CD-ROM, then I did a clean install (again).  This time my _wireless worked out of the box,_ my _SD card reader worked out of the box_.  Of the four special keys in the upper left,  only the email and the internet keys work, they will pull up the respective application.  

What doesn't work yet is the scroll button on the touch pad.  The Fn+F7 will turn the touch pad on and off.  The left button works as it is supposed to, the right button brings up a menu 

When I plugged in my printer (USB), Ubuntu recognized it and installed it quickly and easily.  

I I took the original HD out of my laptop which has WinXP on it and replaced it with a new HD, which is what I have Ubuntu installed on.   The old HD is in an aluminum case with an IDE to USB interface.  When I plug it into my laptop Ubuntu 'sees' all three partitions (one is a hidden one, one is the WinXP OS, and one is the data partition).  The strange part is that my WinXP PC will only 'see' the OS (C) partition and not the D or hidden partition.  I was thinking of using the old HD  for dual booting with WinXP if needed.  I haven't gotten that to work out yet.  I may just give up on Windoze for my laptop.  The more I use Ubuntu the less I think I need Windoze.  In fact even with my PC, the only two reasons to ever use Windoze is to use my analog audio converter, or my analog video converter to make either digital Cd's or DVD's.

By the way I have a new 320 GiB HD for my PC and I will leave the 120 GIB HD in it with the new one being the Maser and the Old being the slave.  I will install Ubuntu on the 320 HD and I will then have a dual boot PC.

Bottom line is that I was encourage to have most everything work right after an install.

---

### Post by the_master on 2007-06-13
You said you can install the touchpad drivers via synaptic package manager,  but when i look i can't find anything that is what i'm looking for.  There is gsnaptics but the touchpad on the 2480 is wacom not synaptics.  What is the name of the driver to install?

Another this is fn + up/down doesn't control the volume does anyone know how to set that?

---

### Post by ludavicious on 2007-06-18
> **the_master said:**
> Another this is fn + up/down doesn't control the volume does anyone know how to set that?

Hi.  I had same problem on Acer Aspire 2000. Fn + up/down (or Fn + F8 for mute) worked without problems in Edgy, but these combinations weren't working in Feisty.  Finally I've worked it out.

Try:  System -> Preferences ->Sound , then Devices tab , there's a Default mixer tracks  section on the bottom, choose your mixing device and select at least **one of the mixer tracks** (I chose master). The Fn + up/down combination works fine for me now.

I hope this will help you too.

---

### Post by slimjim83 on 2007-06-19
> **the_master said:**
> You said you can install the touchpad drivers via synaptic package manager,  but when i look i can't find anything that is what i'm looking for.  There is gsnaptics but the touchpad on the 2480 is wacom not synaptics.  What is the name of the driver to install?


My touchpad was mis-detected as a wacom device.  I followed these directions [_https://help.ubuntu.com/community/SynapticsTouchpad_]("https://help.ubuntu.com/community/SynapticsTouchpad") and everything is working like it is supposed to.  I also added the gsynaptics package to configure the touchpad, but really the only thing I changed in it was I allowed horizontal scrolling.  Hope this helps you.

slim

---

### Post by Toontwnca on 2007-06-26
> **slimjim83 said:**
> My touchpad was mis-detected as a wacom device.  I followed these directions [_https://help.ubuntu.com/community/SynapticsTouchpad_]("https://help.ubuntu.com/community/SynapticsTouchpad") and everything is working like it is supposed to.  I also added the gsynaptics package to configure the touchpad, but really the only thing I changed in it was I allowed horizontal scrolling.  Hope this helps you.

slim

I have a Acer Aspire 5050.
I now have scrolling in my touchpad thanks to the link above.
Thanks for posting it.

---

### Post by hacienda_irrevocably on 2007-10-03
> **jlh68 said:**
>  Also my wifi card is an Atheros, I had a little trouble getting it to work but I finally did get it operational. .
any recollection on just HOW you got it to work?

---

