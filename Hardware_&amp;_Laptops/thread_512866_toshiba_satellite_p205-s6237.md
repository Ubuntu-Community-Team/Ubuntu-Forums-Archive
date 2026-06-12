---
title: "toshiba satellite p205-s6237"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by devron6 on 2007-07-29
Hi I am having trouble getting the sound, wireless and video resolution higher on my laptop. I got 7.04 installed.  I have read the other threads about getting sound to work and non have worked so far I have also tried a suggestion of added resolution915 did not work on getting my resolution bigger. Any help would be deeply appreciated:confused: Id hate to go back to xp.

---

### Post by devron6 on 2007-07-30
bump... anyone help?

---

### Post by misfitpierce on 2007-07-30
What are specs? Wireless card name, Gpu name (intel xtreme, ATI x200 so on...) and whats the sound device/card?

lscpi can show this stuff and list it.

---

### Post by donkihote on 2007-07-30
I got the same problem:

Someone please help me to choose with package of Ubuntu 7.04 32bit that can be installed on my laptop, I did try to use live CD 7.04 Feisty but it could not start X-server with error &#8220;can not attach hardware&#8221; & "MP-bios bug: 8254 timer not connected to IO-APIC". That happened because of &#8230;???

Toshiba Satellite_A215-S4817
AMD Turion&#8482; 64 X2 Dual-Core Mobile Technology TL58
Chipset AMD M690V
2048MB DDR2 SDRAM
160GB (5400RPM); Serial ATA
ATI Radeon® X1200 128MB-319MB

---

### Post by devron6 on 2007-07-30
> **misfitpierce said:**
> What are specs? Wireless card name, Gpu name (intel xtreme, ATI x200 so on...) and whats the sound device/card?

lscpi can show this stuff and list it.

Here is my video card and monitor information


Intel@Graphics Accelerator 950, Monitor is a 17 inch TFT Widescreen. 

Sound is driver_audio_realtek_25937A

---

### Post by devron6 on 2007-07-30
I have found a way to get the sound working now, and I have got my display to 1280x800 but I can not seem to get it to 1440x900 any help would be greatly apprcaited, also i do have a monitor output id like to get that to work as well.

---

### Post by devron6 on 2007-07-31
anyone :) where are all the gurus at

---

### Post by firstc624 on 2007-09-02
how has this laptop been for you now running fiesty?

---

### Post by Danthonyt on 2007-09-02
How did you get the sound to work?  I have been having the same problem with my sound since I bought my toshiba satellite a205 and am frustrated beyond description.  it's only been a few days but since I am somewhat ocd about these things i am going nuts.

i am relatively new to linux.....my new laptop is awesome for the price i paid for it, but it came with vista.....i have dabbled with linux in the past but this is the first time i am using it as my primary os, so i really don't know what i am doing.  the sound worked fine when i first booted into vista but running ubuntu, nothing.  everything else works fine, just no sound at all.  any help would be greatly appreciated.

Thanks,
-David-

---

### Post by humator on 2007-09-07
I have 1440x900 resolution under Debian 4.0 on the same laptop, I installed 915resolution and modified /etc/default/915resolution:
MODE=4d
XRESO=1440
YRESO=900
BIT=24

---

### Post by Rockman4140 on 2007-09-19
In order to get sound working on my laptop, I plugged my laptop straight into my router and updated. It works fine from there, and although I do not yet know how to adjust hw much my scroll wheel adjusts the sound, it still works.

Wifi should be handled with ndiswrapper and wicd, that's how I got it working on my A215-S4817. I was going to attempt to see if my card can handle compiz-fuzion, but probably not. Until then, if anyone knows how to force 1440x900 resolution, or if anyone could post the specs for the A215-S4817 TFT screen, that would be nice.

---

### Post by hideo_10 on 2007-10-04
devron6

how did you get that sound working on your computer 
i have the same computer that i run feisty on

and another thing that isnt working is the wireless 
do you know any thing about that

---

### Post by rivera151 on 2007-11-26
Did you upgrade to Gutsy?  The ath_hal driver should be working automatically, through the Restricted Drivers Manager (make sure to enable the restricted repo's for apt).  Actually, I got mine in Feisty, so you shouldn't even have to upgrade.  Also, don't forget to check out my post on how I got my other stuff working.

[http://ubuntuforums.org/showthread.php?t=622098](http://ubuntuforums.org/showthread.php?t=622098)

Cheers.

---

