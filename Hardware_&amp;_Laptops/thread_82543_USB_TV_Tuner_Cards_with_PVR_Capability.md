---
title: "USB TV Tuner Cards with PVR Capability"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2005-10-26
Hello,

 I am looking to get a USB TV Tuner Card and was wondering if anyone knew of one that worked well under linux and could be used to pause/unpause live tv and record shows. I'm currently looking at the the Hauppage WinTV-PVR-USB2 ([http://www.hauppauge.com/pages/products/data_pvrusb2.html](http://www.hauppauge.com/pages/products/data_pvrusb2.html)) but I'm unsure about how well it would work with Breezy. Are there any other ones I should be looking at?

Also, can MythTV be used under Gnome (so you can watch/record television while using your computer) or does it have to be installed into its own partition?

---

### Post by mlomker on 2005-10-26
Happauge is the best card out there, afaik, but that's for internal cards.  Peculiar USB devices are rarely supported in linux, so you'll need to check around on that.  I think there are mailing lists just for Myth and some active people on [www.avsforum.com](www.avsforum.com) that you could follow-up with.

I talked to a guy that had trouble getting Myth to work under Hoary because newer libraries were needed, but that should be fixed with Breezy.  I'll be curious to hear if someone has it running already.

---

### Post by audax321 on 2005-10-28
I checked out the MythTV documentation and the  Hauppage WinTV-PVR-USB2 doesn't work with it. Although there are apparantly drivers available for it. I want a USB TV Tuner so I can use it with my laptop. If anyone knows of any that work, let me know. I'll check out that website you gave. Thanks.

---

### Post by Evele on 2005-11-15
If I could get my ATI tv wonder usb 2.0 to work in breezy I'd abandon windows altogether.

---

### Post by emperor on 2005-11-15
[quote=audax321]I checked out the MythTV documentation and the Hauppage WinTV-PVR-USB2 doesn't work with it. Although there are apparantly drivers available for it. I want a USB TV Tuner so I can use it with my laptop. If anyone knows of any that work, let me know. I'll check out that website you gave. Thanks.[/quote] 
The MythTV site says that this driver and the listed USB turners will work!

[http://oss.wischip.com/]("http://oss.wischip.com/")

The [FONT=arial][COLOR=#484747]**Pinnacle PCTV USB2 is reported to work in the latest CVS V4L drivers. This device requires the **[/COLOR][/FONT]"em28xx driver".
Audio is mono only, which seems to be a limitation due to bandwidth for USB2 TV cards. It might require that you upgrade the kernel to version 2.6.15.

[http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Analog+PVR+%28cable_antenna%29/PCTV+100e.htm]("http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Analog+PVR+%28cable_antenna%29/PCTV+100e.htm")

Here is the offical list of USB tuners that are working in linux:

[http://www.linuxtv.org/v4lwiki/index.php/USBVideo]("http://www.linuxtv.org/v4lwiki/index.php/USBVideo")

I bought an "AverMedia AverTV Cardbus" adapter for my Dell i9300 laptop. The tuner does not work yet but I do have a picture on the composite and s-video inputs. There are one or two people working on getting this card to fully work.

[http://www.aver.com/2005home/product/tvtuner/cardbus/cardbus/cardbus.shtml]("http://www.aver.com/2005home/product/tvtuner/cardbus/cardbus/cardbus.shtml")

ADS also makes a card that might work, as there is listed in the latest driver. However the vendor changed the chipset and id of the card 3 months after it was released in the market. This is really the main problem with the drivers for both cards, the vendors keep changing chipsets to save a buck! 

[http://www.adstech.com/products/PTV-370/intro/PTV-370_intro.asp?pid=PTV-370]("http://www.adstech.com/products/PTV-370/intro/PTV-370_intro.asp?pid=PTV-370")

This site is useful for choosing and debuging a TV card.

[http://www.linuxtv.org/]("http://www.linuxtv.org/")

---

### Post by dragonrider on 2006-06-30
i try to to make work my external tv card , i think i am really near thanks to this page : 

[http://justiceforall.free.fr/pvrusb2.html](http://justiceforall.free.fr/pvrusb2.html)

if comebody succeed please tell me 

i need to install xawtv 4 for moment to test if it really work but here is some sign encouraging : 

lsusb -->
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 003: ID 2040:2900 Hauppauge
Bus 004 Device 001: ID 0000:0000

---

### Post by emperor on 2006-06-30
[quote=dragonrider]i try to to make work my external tv card , i think i am really near thanks to this page : 

[http://justiceforall.free.fr/pvrusb2.html]("http://justiceforall.free.fr/pvrusb2.html")

if comebody succeed please tell me 

i need to install xawtv 4 for moment to test if it really work but here is some sign encouraging : 

lsusb -->
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 003: ID 2040:2900 Hauppauge
Bus 004 Device 001: ID 0000:0000[/quote]

Check this thread for latest info on the driver:
<http://marc.theaimsgroup.com/?l=linux-video&m=114191919718542&w=2>

---

