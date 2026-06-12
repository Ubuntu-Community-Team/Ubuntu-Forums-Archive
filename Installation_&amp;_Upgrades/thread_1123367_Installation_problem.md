---
title: "Installation problem"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by Krepanilo on 2009-04-12
hi. i'm trying to install ubuntu from a bootable dvd-rw. when i get to the boot menu and choose install only a black screen shows with a cursor blinking. i've tried all the other options with the same result. my configuration: 
MB Asus P4C800
P4 3.0 with HT
1 GB DDR
ATI Radeon 9200
HDD Seagate 120 GB SATA.

what may be the problem?? thx

---

### Post by jcm1107 on 2009-04-12
> **Krepanilo said:**
> hi. i'm trying to install ubuntu from a bootable dvd-rw. when i get to the boot menu and choose install only a black screen shows with a cursor blinking. i've tried all the other options with the same result. my configuration: 
MB Asus P4C800
P4 3.0 with HT
1 GB DDR
ATI Radeon 9200
HDD Seagate 120 GB SATA.

what may be the problem?? thx

First what version are you installing?there is 8.1,8.04,7.1. I had the same problem and to get Ubuntu installed I had to install Ubuntu 7.1 once it installed I let it do all its updates and then it had an option to upgrade to 8.04 hardy and once you install that I could help you get 8.1 but I upgraded to that and it wasn't any different really so I went back to 8.04 because it is Long term support, this means there are updates for 18 months.

---

### Post by Krepanilo on 2009-04-12
i've tried installing 8.04 and 8.10 with the same result. i will try to download 7.1 and see if that helps. thx

---

### Post by jcm1107 on 2009-04-12
That is the only way I could get Ubuntu I tried all sorts of fixes and still havent found any. The 7.1 worked for me and then I could upgrade. Let me know if it works for you. Good luck.

---

### Post by dE_logics on 2009-04-12
Most probably the problem with with the ATI drivers (as usual).

Disable your graphs card and enable your on board through the bios, then connect your monitor to the on board display jack...THEN boot.

---

### Post by jcm1107 on 2009-04-12
> **dE_logics said:**
> Most probably the problem with with the ATI drivers (as usual).

Disable your graphs card and enable your on board through the bios, then connect your monitor to the on board display jack...THEN boot.

I don't have a graphics card installed just the onboard graphics, and I had the same problem. I know my problem is because of my hard drive but I still can not figure out a fix for it I have tried the all_generic_ide but that didn't work. My motherboard is xfxforce nvidia 630i with 7150 on board graphics. I would like to know how to get 8.04 installed on my system with the cd instead of having to install 7.1.

---

### Post by Krepanilo on 2009-04-12
ok, so i've tried versions 8.04, 8.10, 9.04 beta and finally 7.10 and the same result over and over. also, i don't have an onboard graphic card but i have tried to put radeon 9700 and radeon 9800 in my pc and no success. i know, you said that this is maybe an ATI issue, but on my brother's PC (from which i took the 9800) instalation worked just fine. that eliminates the graphic card and also the medium (dvd-rw) and burning procedures.

any other ideas i could try? maybe some command for a workaround?
thx for your effort.

---

### Post by jcm1107 on 2009-04-12
> **Krepanilo said:**
> ok, so i've tried versions 8.04, 8.10, 9.04 beta and finally 7.10 and the same result over and over. also, i don't have an onboard graphic card but i have tried to put radeon 9700 and radeon 9800 in my pc and no success. i know, you said that this is maybe an ATI issue, but on my brother's PC (from which i took the 9800) instalation worked just fine. that eliminates the graphic card and also the medium (dvd-rw) and burning procedures.

any other ideas i could try? maybe some command for a workaround?
thx for your effort.

try installing the 8.04 again but this time after you select language go to the installation you are trying to use (by this I mean either, install with no changes to windows, or install) and hit F6 on the boot line remove quiet splash and then hit enter and let me know what your screen says. This will tell us what error you are getting.

---

### Post by dE_logics on 2009-04-12
> **jcm1107 said:**
> I don't have a graphics card installed just the onboard graphics, and I had the same problem. I know my problem is because of my hard drive but I still can not figure out a fix for it I have tried the all_generic_ide but that didn't work. My motherboard is xfxforce nvidia 630i with 7150 on board graphics. I would like to know how to get 8.04 installed on my system with the cd instead of having to install 7.1.

You said that you have an ATI graphs card...then you said you have Geforce 7150 onboard.

That means you have an ATI graphs in your PCI or AGP.

Nvidia chipsets will never have an ATI chip...both hate each other!

---

### Post by dE_logics on 2009-04-12
[quote=Krepanilo]but i have tried to put radeon 9700 and radeon 9800 in my pc and no success.[/quote]

ATI has drivers for all cards except x1270 (which I have :mad:)

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I see your card here.

---

### Post by upchucky on 2009-04-12
if the machine boots from the dvd and you get a graphical display then it will work when actually installed.

you can check the display settings it uses when booted from the dvd before you actually install.

use these settings to manually edit the xorg.conf after the install drops you to a command prompt.

---

### Post by jcm1107 on 2009-04-12
> **dE_logics said:**
> You said that you have an ATI graphs card...then you said you have Geforce 7150 onboard.

That means you have an ATI graphs in your PCI or AGP.

Nvidia chipsets will never have an ATI chip...both hate each other!

No I don't have an ATI grahics card. I only am using what the board has on it, and the box says geforce 7150 is what it has.

---

### Post by dE_logics on 2009-04-12
Oh...I mixed it up with the thread starter.

Check your CD for defects.

---

### Post by jcm1107 on 2009-04-12
> **dE_logics said:**
> Oh...I mixed it up with the thread starter.

Check your CD for defects.

I have tried two different cds for Ubuntu 8.1 and one cd for 8.04 and then one for 7.1 and 7.1 is the only one that will install and then I can upgrade from there. I do have a question, is there anyplace that I can see the boot line so I know what to change to get the other ones to work? I would like to figure out this problem so I can help the many others that have this issue. Ok I now tried my Ubuntu cd in my brothers computer and it booted with no problem. First I went on the check cd line and it didn't find any errors, then I went on the install without any changes to windows and the orange bar moved back and forth for a little bit then the desktop came up. With either one of those options and also on my computer when I try a full install I get a "busy box" I am sure it is a problem with my hard drive setup. I have an IDE hard drive with an adapter to connect to sata because there are not enuff ide connectors on my board. I have tried using raid after using ide in the bios didn't work neither helped.

---

### Post by dE_logics on 2009-04-13
IF there would have  been any problems with the HDD windows would have crashed first...I mean that OS needs an excuse to crash.

Yeah you can change the boot option...in the first interface that comes up, you'll see certain option which'll activate when using the F keys...its in one of them.


You can recover a broken installation that way too.

---

### Post by t0p on 2009-04-13
**jcm1107:** There is not an Ubuntu 7.1 or 8.1 release.  It's **7.10** and **8.10**.

---

