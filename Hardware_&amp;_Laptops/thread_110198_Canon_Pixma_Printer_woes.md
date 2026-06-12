---
title: "Canon Pixma Printer woes"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by drewbie on 2005-12-30
Hi, I have a Canon PIXMA IP2200 and was wondering if anyone else has managed to get one working? 

It recognises the printer, but for every driver I have tried including the BJC-7000, [Turboprint]("http://www.turboprint.de/english.html") and the [IP1500 installer script]("http://www.ubuntuforums.org/showthread.php?t=93265") drivers;  the light just flashes a few times but nothing else happens. (also searched the [linux printing forums for canon ]("http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general") )

[B]In the meantime I advise everyone with a canon printer to ask canon to release linux drivers
[http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225#1](http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225#1)
[/B]

Also if you have got the PIXMA IP1600 or IP1200 working, it might be a similar method since it is a shared quick start guide???

Many thanks,
Drew

---

### Post by HLS on 2005-12-30
If TurboPrint has named that printer in its latest package I would contact them first.  I know that unless you purchase the TurboPrint license, you will get a logo across the screen, understandable; since they have to make a living; and working backwards to generate the right drivers, rather than get OEM support is a headache.  :(

---

### Post by HLS on 2005-12-30
Sorry for repetition.  Ignore this entry.  (edited)  :roll:

---

### Post by rx78gp03 on 2006-04-11
I got source driver from canon japan (version 2.60), it's support newer pixma printer including iP2200, iP4200, iP6600d, iP7500, and MP500. I haven't compiled it yet, tough. [http://cweb.canon.jp/drv-upd/bj/bjlinux260.html]("http://cweb.canon.jp/drv-upd/bj/bjlinux260.html")

---

### Post by drewbie on 2006-04-21
[QUOTE=rx78gp03]I got source driver from canon japan (version 2.60), it's support newer pixma printer including iP2200, iP4200, iP6600d, iP7500, and MP500. I haven't compiled it yet, tough. [http://cweb.canon.jp/drv-upd/bj/bjlinux260.html]("http://cweb.canon.jp/drv-upd/bj/bjlinux260.html")[/QUOTE]

Although the website is in japanese, I can't see the ip2200 mentioned there. Has anyone installed the driver and got it working with the ip2200?

However the latest turboprint does support the ip2200, (although for me it kept crashing, so I had to use the ip1600 turboprint driver instead).

---

### Post by mr_niceguy on 2006-04-26
[QUOTE=HLS]unless you purchase the TurboPrint license, you will get a logo across the screen[/QUOTE]

I thought so too but found out you can also set up the printer quality to "Draft" (300 dpi) in which case it will allow you to print for free with no banners. The license allows you to print higher resolutions.

---

### Post by enslam on 2006-05-03
This thread has really been helpful.
I managed to get my Canon PIXMA IP1200 working with the TurboPrint IP1600 drivers.
Think its just a matter of matching up the cartridge codes.
Hope this helps someone else out as well.

---

### Post by Linux bear on 2006-05-04
I have a Pixma ip 3000, and have been wanting it to work with Linux Ubuntu but in trying to configure this printer for use in Linux, I could find no drivers for this device. A friend who put my Linux computer together advised me that the BJC7000 was reported to work ok with, presumably Ubuntu so I used it and all seemed to flow together smoothly until I tried to print something.  Nothing happened.  The printer took such time 'preparing' itself to print that after a while I turned it off.

Wonder if anyone else in this forum has such a printer and if so were you  able to get it to work with some kind of driver, would you please tell me how you did it?  Please note that I'm a Linux newbie so please be as detailed as you can.

Thank you

---

### Post by mschievano on 2006-05-04
my pixma ip4200 wont work with the japan driver.
In vmware-player the printer print veryyyy good.

---

### Post by mg620 on 2006-10-15
> **rx78gp03 said:**
> I got source driver from canon japan (version 2.60), it's support newer pixma printer including iP2200, iP4200, iP6600d, iP7500, and MP500. I haven't compiled it yet, tough. [http://cweb.canon.jp/drv-upd/bj/bjlinux260.html]("http://cweb.canon.jp/drv-upd/bj/bjlinux260.html")
Hi,
I know you posted this a long time ago, but did you have any success?  I downloaded some stuff from the japan website for my ip6600D, but since all the docs are in Japanese, as they should be, I have no clue what I'm doing.  I also have no clue because I've been using ubuntu for about 2 weeks.
I'd appreciate hearing your experience.
Thanks

---

### Post by clownius on 2006-10-16
I had similar problems with a pixma ip4200.  if you can find the thread laying around it has some info im shure can be used toward fixing this.  i found canon europe also keeps linux drivers available for most printers and its in english so well worth a look there.  As for canon Australia it was hopeless.  Feel free to pm me as i might be able to walk you through.  only issue i have is my printers prints really slowly with this driver but it works and thats enough to make me jump for joy.

I found Pixma drivers for linux here.
[Canon Europe Pixma  Linux Driver downloads/]("http://www.canon-europe.com/Support/software/linux/")

For more info on how to install them see this [Wiki Page]("https://wiki.ubuntu.com/CanonPixmaIP4200").
Page is for a ip4200 but change some link names and it should work

Clownius

---

### Post by anoopjohn on 2006-12-18
TurboPrint just recently announced their latest version with support for more printers. I tried with Canon Pixma iP1200 and it didnt work. If somebody is able to set it up please let me know.

---

