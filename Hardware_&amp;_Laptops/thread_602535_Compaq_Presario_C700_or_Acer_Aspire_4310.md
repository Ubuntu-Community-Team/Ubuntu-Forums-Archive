---
title: "Compaq Presario C700 or Acer Aspire 4310?"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by rolibalicas on 2007-11-04
Hi everyone,
I'm in a market for a new laptop and I now have 2 items on my shortlist:

Compaq Presario C700 (the lowest specs! I'm on a tight budget.)
[http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Brand&v1=Compaq+Presario&a2=From+price&v2=Under+%24500&series_name=C700T_series&a1=Brand&v1=Compaq+Presario&a2=From+price&v2=Under+%24500]("http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Brand&v1=Compaq+Presario&a2=From+price&v2=Under+%24500&series_name=C700T_series&a1=Brand&v1=Compaq+Presario&a2=From+price&v2=Under+%24500")

And the Acer Aspire 4310 

[http://www.acer.com.ph/notebook.php?pkey=70]("http://www.acer.com.ph/notebook.php?pkey=70")

I would appreciate it if anyone can give me an advice on which model would give me less trouble on running ubuntu 7.10. Thanks!

---

### Post by clyphox on 2007-11-07
Hi rolibalicas

as luck would have it I've just bought a C700 today, I know nothing of the other laptop but as soon as I'm finished backing up the machine I'll post my results running ubuntu. Will update u tomorrow on how it went.

---

### Post by clyphox on 2007-11-08
ok heres the breakdown:

Works out the box:
-VGA, glxgears running at 900 FPS and screen at 1280x800 (max) on default
-Audio (Fn / +- volume buttons, unsure of other compaq shortcut buttons)
-HDD, USB, onboard NIC+Modem etc...

Hickups: 
-Problems with the touchpad, can't move cursor or click. I have just plugged in a USB mouse for now and will resolve it later.
-Wifi: this 1 took 2min and 3 commands to get going, see:
     [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
-Video, for some reason I get a blank screen when switching to the console from X (CTRL+ALT+F1), all I did to fix this was add "vga=0"  to the boot.

Outstanding (will update as I work out)
-Power  management:
   System went into hibernation however it didn't resume??
   Suspend: untested
   Halt and Reboot: OK
-Beryl (I dunno if I can get it going on this yet but it would be nice)
-Off Topic but I wanna see if/how OSX86 manages


here is a copy of lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



I'm enjoying this laptop. it's quiet and way better than my last one, I've been pushing it for the last few hours and its temperature is only between 45-50 degrees
My last one lived in the high 50s haha :)

HTH -david

---

### Post by lashi on 2007-11-15
So, I've gone and bought one of these too. But I haven't opened the box. It's actually a C710TU, but it says C700 on the top right hand corner. 

It was cheap, I only run Linux. I'm not going to open it just yet - just wondering whether you've got the trackpad issue sorted out. That could be a bummer if that doesn't work...

---

### Post by dannyboy79 on 2007-11-20
Compaq Presario C717NR is being sold on Black Friday at Circuit City for $299 due to some instant saving but also a $150 rebate so it'll be $449.99 at the checkout.

The specs are as follows:
Complete C717NR Specs:
Display: 15.4&#8243; WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
Processor: Intel Core Duo T2310, (1.46 GHz, 1MB L2 Cache, 533MHz FSB)
Memory: 1GB DDR2 System Memory (2 Dimm)
Hard Drive: 80GB 5400RPM
Graphics: Intel Graphics Media Accelerator X3100
Wireless: 802.11b/g WLAN
Optical Drive: SuperMulti 8X DVD+/-R/RW with Double Layer Support
OS: Windows Vista Home Premium
Ports: 3x USB 2.0, VGA, mic-in, headphone-out, S-Video, LAN, modem
Weight: 6.3 pounds
Dimensions: 14.1 (L) x 10.11 (W) x 1.29 (min H)/1.58&#8243; (max H)


Store opens at 5am but I think I am camping out starting at 2AM with chair and plenty of clothes!

Anyone get the touchpad or power management stuff to work?

---

### Post by lashi on 2007-11-24
I bought the Compaq Presario C710TU.

I actually just installed Ubuntu-amd64 on it, and it works like a dream. The touchpad worked out of the box. I had to put vga=0 to get the graphics going properly (kernel framebuffers are unhealthy anyway).

In terms of power management, I've been hibernating perfectly okay for about the past week.

And use ndiswrapper with bcmwl5 to get the wireless. The link a few threads up didnt' work for me, I downloaded the driver from somewhere Compaq. It came with the 64-bit drivers too.

So, the whole unit works flawlessly.

I suggest buy it!

---

### Post by wtfitsRICK on 2007-11-26
I just bought the Presario C700 as well.  What exactly is the deal with getting the WiFi to work?  My trackpad seemed to work just fine, so my biggest concern is the internet.  The button on the laptop won't do anything if I press it.  Also, I'll be a new user, so anything code would be helpful if it were laid out fairly clearly.

---

### Post by dannyboy79 on 2007-11-29
> **wtfitsRICK said:**
> I just bought the Presario C700 as well.  What exactly is the deal with getting the WiFi to work?  My trackpad seemed to work just fine, so my biggest concern is the internet.  The button on the laptop won't do anything if I press it.  Also, I'll be a new user, so anything code would be helpful if it were laid out fairly clearly.

he saying that you need to use ndiswrapper along with the downloadable windows driver for the wifi chipset that in your computer. ndiswrapper is module that allows linux to use a windows driver. there are plently of guides for installing and using ndiswrapper within this forums community. As for the wifi driver, you'll have the same wifi shipset as he, so just go to compaq site and download the broadcom wifi driver and the ndiswrapper guide will tell you where to put this windows driver. here's a link to a ndiswrapper guide that is even working with the exact windows broadcom wifi driver that you need:
[http://ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper)

---

