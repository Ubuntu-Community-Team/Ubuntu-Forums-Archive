---
title: "Acer TravelMate 4670: TM4674WLMi (LX.TAJ06.057)"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by ubiqquitous on 2006-05-17
:) 

So, every year I evaluate Linux distributions on various platforms.
Last year, I was quite impressed with Ubuntu. I had ranked Ubuntu second to Fedora only in terms of hardware support.

This year, I have great expectations and I hope to see Ubuntu reign supreme. :D 

Notebooks have always been a damning weakness of Linux. Traditionally, hardware support has been so erratic and inconsistent.

I strongly believe projects such as Ubuntu should define a range of reference platforms that would showcase the true effectiveness of their distribution.

Anyway, for this round of tests, I just ordered this notebook:

Acer TravelMate 4670: TM4674WLMi (LX.TAJ06.057)

It's a great power/value ratio:

- Intel Core Duo Processor T2500 (2MB L2 cache, 2.0GHz, 667MHz FSB)
- 2GB (1/1) DDR2 533 SDRAM
- 120GB SATA hard drive, 5400RPM
- Modular Super-Multi drive (DVD+R, DVD-R, DVD-RAM)
- 5-in-1 card reader
- 15.4" WXGA (1280 x 800) TFT display
- ATI MOBILITY RADEON X1400 graphics, 128MB DDR2
- 802.11a/b/g WLAN
- Gigabit LAN
- V.92 modem

I won't receive this hardware platform until tomorrow...but I am starting to gather information on what to expect.

This year, I will make a complete tutorial of my experience and hopefully establish one reference platform for Ubuntu enthusiasts.

So, let's get this ball rolling...what hurdles should I expect?

---

### Post by zhoux on 2006-05-17
[QUOTE=ubiqquitous]:) 


- ATI MOBILITY RADEON X1400 graphics, 128MB DDR2
[/QUOTE]

I don't know if this will be a problem, but i've read somewhere in this forum that ATI drivers aren't as well compiled as other drivers. But I maybe wrong.;)

---

### Post by ubiqquitous on 2006-05-17
[QUOTE=zhoux]I don't know if this will be a problem, but i've read somewhere in this forum that ATI drivers aren't as well compiled as other drivers. But I maybe wrong.;)[/QUOTE]

Thanks for offering your help!

I am not sure what that would mean. Compiled code is compiled code.
Maybe it's not optimized or it's buggy.

I found the following details:
- The touchpad device is made by Synaptics.
- The chipset is made by Intel, obviously.
- The video card is also obviously made by ATI.
- The Fast Infrared Port is either made by SMSC or NEC.
- The Ethernet adapter is made by Broadcom.
- The Wireless Network Adapter is either made by Atheros Communications or Intel.
- The audio device is made by Realtek.

I will know more after I receive the hardware.

---

### Post by nolongerlivecd on 2006-05-18
But hey, if you need to know how to do your drivers, I did it this way:

sudo apt-get install linux-686
sudo apt-get install xorg-driver-fglrx

Then, I downloaded the ATi drivers and followed a guide which said:

cd (folder containing fglrx)
sudo module-assistant prepare
sudo chmod a-i fglrx
[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#overview](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#overview) (not my webby, another guy's, and i find it very useful)

---

### Post by ubiqquitous on 2006-05-18
[QUOTE=nolongerlivecd]But hey, if you need to know how to do your drivers, I did it this way:

sudo apt-get install linux-686
sudo apt-get install xorg-driver-fglrx

Then, I downloaded the ATi drivers and followed a guide which said:

cd (folder containing fglrx)
sudo module-assistant prepare
sudo chmod a-i fglrx
[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#overview](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#overview) (not my webby, another guy's, and i find it very useful)[/QUOTE]

Thanks for the tips!

It's kind of odd you need fglrx if ATI provides a driver.

Anyway, I will receive the notebook today and proceed with BIOS updating and hardware inventory. I don't think this notebook is going to be too much different from the 5672, so I am hopeful.

---

### Post by Dralt on 2006-05-19
I received the hardware today...

Complete hardware inventory:

[http://axiom7.com/TM4672WLMi/SI.xml](http://axiom7.com/TM4672WLMi/SI.xml)

---

### Post by jdong on 2006-05-19
Congrats on your purchase!

[http://ubuntuforums.org/showthread.php?t=121125](http://ubuntuforums.org/showthread.php?t=121125)

The above thread discusses running Ubuntu on the Acer Aspire 5672, a very close relative to your travelmate (in fact, both use the same BIOS flashes).

It should prove to be a very informative read for your journey with this laptop. Bottom line is that:

(1) Ubuntu's developers were lightning fast at supporting the new hardware. Quite literally each day brings better support

(2) This laptop works great out-of-the-box already, just a video card driver install (via APT, no compiling) and you're off to the little tweaks.

(3) I have no life, and I've been doing quite a bit of tweaking on the laptop. You'll enjoy my /etc/acpi work: fully functioning suspend/resume.


On my Aspire, everything works great except:

(1) No webcam drivers. When we do get support, it'll be by the spca5xx driver (author acknowledges chipset, saying he'll look into it)
(2) Little tweaks here and there (i.e. high-pitched squeal fix)

Do read through that thread... it's long, but will be helpful in setting this thing up.

---

### Post by Dralt on 2006-05-20
[QUOTE=jdong]Congrats on your purchase!

[http://ubuntuforums.org/showthread.php?t=121125](http://ubuntuforums.org/showthread.php?t=121125)

The above thread discusses running Ubuntu on the Acer Aspire 5672, a very close relative to your travelmate (in fact, both use the same BIOS flashes).

It should prove to be a very informative read for your journey with this laptop. Bottom line is that:

(1) Ubuntu's developers were lightning fast at supporting the new hardware. Quite literally each day brings better support

(2) This laptop works great out-of-the-box already, just a video card driver install (via APT, no compiling) and you're off to the little tweaks.

(3) I have no life, and I've been doing quite a bit of tweaking on the laptop. You'll enjoy my /etc/acpi work: fully functioning suspend/resume.


On my Aspire, everything works great except:

(1) No webcam drivers. When we do get support, it'll be by the spca5xx driver (author acknowledges chipset, saying he'll look into it)
(2) Little tweaks here and there (i.e. high-pitched squeal fix)

Do read through that thread... it's long, but will be helpful in setting this thing up.[/QUOTE]

Hey jdong, you are driving this community like a true champion! :-D 
I have read your other thread daily. You can be sure I am going to make the most of it.

Yes, the TravelMate 4670 series is the same hardware as the Aspire 5670 series, without Bluetooth, without the Web cam, but with the 2.0 GHz version of the Core Duo, 2 GB of RAM, and a 120 GB HDD. I also believe the build quality of the TravelMate series is somewhat superior to the build quality of the Aspire series. (at a higher price, clearly)

Yesterday, I flashed the new BIOS and I re-partioned everything. Got rid of the pesky hidden partition (after burning a recovery DVD--just in case).
I created 2 partitions. 1 of them now hosts an optimized version of XP Pro (33% performance improvement over factory image). The other partition is unformatted and ready to welcome Ubuntu. :-D 

Today is Ubuntu day!

---

