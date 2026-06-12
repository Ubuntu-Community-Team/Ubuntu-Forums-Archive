---
title: "~$1200 Wide Aspect Ubuntu Laptop"
date: 2004-12-29
forum: Hardware &amp; Laptops
---

### Post by killerfish on 2004-12-29
Hello gang, 

I have the OK to go for a laptop which I can run linux on (I dual boot my PC and it drives my wife insane..)  Here's my wishlist:

1) Price Range <$1200 US
2) Wireless B Supported easily (don't care about g).
3) Wide aspect display (love it 12, 14 or 15.4 doesn't matter to me)
4) Battery Life: > 2.5hrs
5) DVD Burner
6) AMD or Intel is cool with me...
7) working ACPI

Any suggestions? Does such a beast exist?   I'm thinking of the Averatec 6240 (AMD64), but I don't know what kind of wi-fi card is in it.  Plus, I'm guessing battery life is so,so... Other options are Compaq v2000 or HP dv1000 (basically the same).

Thanks!
KF

---

### Post by killerfish on 2004-12-29
[QUOTE=killerfish]Hello gang, 

I have the OK to go for a laptop which I can run linux on (I dual boot my PC and it drives my wife insane..)  Here's my wishlist:

1) Price Range <$1200 US
2) Wireless B Supported easily (don't care about g).
3) Wide aspect display (love it 12, 14 or 15.4 doesn't matter to me)
4) Battery Life: > 2.5hrs
5) DVD Burner
6) AMD or Intel is cool with me...
7) working ACPI

Any suggestions? Does such a beast exist?   I'm thinking of the Averatec 6240 (AMD64), but I don't know what kind of wi-fi card is in it.  Plus, I'm guessing battery life is so,so... Other options are Compaq v2000 or HP dv1000 (basically the same).

Thanks!
KF[/QUOTE]
 Update:

The Averatec 6240 uses the PRISM A02 802.11b/g wireless nic.  Reading the .inf file of the windows drivers, it also says it's a USB bus type.  Net, I think the PRISM kernel driver should support it....  I could use ndiswrapper if it doesn't, but then I'm stuck in 32 bit mode on a 64 bit machine....(BTW, current machine is an AMD64 so I do know the gains are minimal at best)....

---

### Post by bob k on 2004-12-30
I'm going to test an Acer TM 4000, although it has an on board ATI video, I don't give much of a chance, but you never know. I did a search and some people had some luck with this, it worked but not every thing (like the batt, wlan, eth0, lights, plus some pcima stuff).

---

### Post by magicfab on 2004-12-30
[Averatec](http://www.averatec.com)'s laptops may be your best bet. Unfortunately #7 not being completely ironed out means you can forget about #4. I currently get roughly 1/2 the battery time on Ubuntu compared to WinXP - still doing some research on that :)

---

### Post by nicolas on 2004-12-30
Hi, I run Ubuntu on an Acer Travelmate 4000 WLMi. Install was the best I have seen and I tried distro's like Red Hat 8, Fedora Core 3, Debian and Suse9. 

The things I needed most were working fine. I still have some issues with getting my USB memory stick recognized and some DVD's give me problems. Wireless works like a dream.

Nico

---

### Post by killerfish on 2004-12-30
[QUOTE=nicolas]Hi, I run Ubuntu on an Acer Travelmate 4000 WLMi. Install was the best I have seen and I tried distro's like Red Hat 8, Fedora Core 3, Debian and Suse9. 

The things I needed most were working fine. I still have some issues with getting my USB memory stick recognized and some DVD's give me problems. Wireless works like a dream.

Nico[/QUOTE]
 Thanks for the replies!  Yuck about 1/2 the battery life...w/o working ACPI.  Do any laptops have a working ACPI implementation?  I'll check out the ACERs  haven't given them a good look yet.

---

### Post by jerome bettis on 2005-01-20
[QUOTE=killerfish]Thanks for the replies!  Yuck about 1/2 the battery life...w/o working ACPI.  Do any laptops have a working ACPI implementation?  I'll check out the ACERs  haven't given them a good look yet.[/QUOTE]
 [www.laclinux.com](www.laclinux.com)

check it out.  they might be slightly out of your price range, but i promise everything will work.  these guys know what they're doing.

good warranty too.  i spilled water on my keyboard, and they fixed it no questions asked.  i just had to pay shipping.

battery life is approaching 4 hours with a 7200 rpm hard drive.  acpi is flawless, hibernate works everytime.

---

### Post by jayded on 2005-03-03
Yes I agree its one of the best laptops I've ever run linux on. I got mine yesterday  :-)

To get better power management out of your averatec try running the fan and battery calibration tools in the BIOS and also make sure the powernow daemon is running.

I get about 2.5 hours out of mine on the battery but then again I never tried XP, I just wiped the hard drive as soon as I took the machine out of the box ;-)

[QUOTE=magicfab][Averatec](http://www.averatec.com)'s laptops may be your best bet. Unfortunately #7 not being completely ironed out means you can forget about #4. I currently get roughly 1/2 the battery time on Ubuntu compared to WinXP - still doing some research on that :)[/QUOTE]

---

### Post by Viper12 on 2005-03-06
[QUOTE=killerfish]Hello gang, 

I have the OK to go for a laptop which I can run linux on (I dual boot my PC and it drives my wife insane..)  Here's my wishlist:

1) Price Range <$1200 US
2) Wireless B Supported easily (don't care about g).
3) Wide aspect display (love it 12, 14 or 15.4 doesn't matter to me)
4) Battery Life: > 2.5hrs
5) DVD Burner
6) AMD or Intel is cool with me...
7) working ACPI

Any suggestions? Does such a beast exist?   I'm thinking of the Averatec 6240 (AMD64), but I don't know what kind of wi-fi card is in it.  Plus, I'm guessing battery life is so,so... Other options are Compaq v2000 or HP dv1000 (basically the same).

Thanks!
KF[/QUOTE]
 Just my 2cents here.

The compaq x1000 widescreen series of laptops is my top choice.  My current install of hoary array 6 was flawless.  usb, fglrx (for the ati9200 mobility) all installed with no issues.

I'm not sure about battery life at this point, but another reason for this series is the LCD, which after shopping and looking around has to be one of the crispest and 'eye-easy' I've ever used.   The 1280x800 wide resolution came up with no configuring.
The laptop should be selling for 900-1200 US now, and some of the newer X series widescreens are out for not much more after rebates. (they have dvd-writer, and faster processors/ 80gig drives).
-happy ubuntu laptop user here. :)

p.s. the install on the laptop gave me LESS trouble than a stock Dell desktop system with the same array series. :)

---

### Post by jliedeka on 2005-03-09
I considered the Dell D700m and Compaq V2xxx models.  Both sell for around $1200 with decent options.  I ended up buying a Sony for a bit more.  The Dell has a small keyboard, I'm not aware of any down side to the Compaq.

     Jim

---

