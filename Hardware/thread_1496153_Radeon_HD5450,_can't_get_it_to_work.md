---
title: "Radeon HD5450, can't get it to work"
date: 2010-05-28
forum: Hardware
---

### Post by Ethan_bennett on 2010-05-28
So, I've been trawling the threads and can't seem to find anyone with my issue. I've got a HIS 512mb Radeon HD 5450. I'm on a fresh install of Lucid 10.04 LTS, and whenever I try to install FGLRX, it says it needs dependancies, and then fails to install. I can't get the "Desktop effects" to work, because it doesn't have a legit driver, nor can I get my dual monitor or it to work because whenever I plug a monitor into the HDMI port, it freaks out. I tried --buildpkg on the ATI driver downloaded directly from their site and running the individual .deb's and it won't install any of them, either, with the same "broken dependancies" complaint. Anyone else with an HD5450 experiencing similar issues or anyone know a fix for this?

---

### Post by Ethan_bennett on 2010-06-03
bump. does anyone have any ideas? It's really kind of annoying to not be able to use desktop effects, dual screen, etc...

---

### Post by andrew frank on 2010-06-20
i had problems with a HD5450 dual head system. after installing ATI (not clear how this got done) ATI catalyst control center appeared on my system->preferences menu. it asked for initialization.
in the instruction there i found the line
sudo aticonfig --initial=dual-head --screen-layout=right
then i restarted and bingo! it works!

---

### Post by artemka373 on 2010-06-20
I have little more rare graphic card: ATI Mobility Radeon HD 5470 512MB. fglrx from Ubuntu repositories is little old. A few days ago ATI Cataylst 10.6 was released (a lot of perfomances): [http://www.phoronix.com/scan.php?page=news_item&px=ODM0Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODM0Mg) .
You can download new version here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)
I am using this driver at now (before I used fglrx from Ubuntu repos).
P.S. I can have 2 workspaces with monitor connected over HDMI.
P.P.S. Sorry for errors with English language.

---

### Post by electricgolem on 2010-06-21
I finally got my Radeon HIS HD5450 1GB PCIe card going on one monitor via the DVI port - however the VGA output for my second monitor has a terrible gamma problem and everything has a strong blue cast. 
Is there anything I can do to fix this?
Could I get a cheap HDMI to VGA adaptor and see if that helps?

Many thanks for all and any help.

---

### Post by dq476 on 2011-04-12
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

I got mine there. It works great. When you download it, go to where you downloaded it, right click, properties, permissions, and check "allow executing file as program" then open it, then press run in terminal, a few seconds later it will start installing. :)

---

### Post by Yellow Pasque on 2011-04-12
> **dq476 said:**
> [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

I got mine there. It works great. When you download it, go to where you downloaded it, right click, properties, permissions, and check "allow executing file as program" then open it, then press run in terminal, a few seconds later it will start installing. :)

Not the recommended way of installing Catalyst at all. Follow this to install: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

