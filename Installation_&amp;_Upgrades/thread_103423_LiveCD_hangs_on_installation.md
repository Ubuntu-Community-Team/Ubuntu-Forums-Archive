---
title: "LiveCD hangs on installation"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by Ibizibi on 2005-12-14
Hello!

I'm trying to boot ubuntu 5.10 on my new HP Pavilion w5080 with LiveCD, but the process hangs after showing the message: "ohci_hcd 0000:00:13.1: Unlink after no-IRQ? Controller is probably using the wrong IRQ". 

I have wireless usb keyboard and mouse. Is that the problem?

Please help!

Here are specs of my computer: [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00396758&lc=en](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00396758&lc=en)

antti

---

### Post by aysiu on 2005-12-14
Your problem isn't a very common one. Your best bet is to follow some of [these 170 or so links about it](http://www.google.com/search?hl=en&q=Unlink+after+no-IRQ%3F+Controller+is+probably+using+the+wrong+IRQ&btnG=Google+Search). Hope you find the answer.

---

### Post by reiki33 on 2005-12-16
Did you find a solution?  I am having the same symptom.  It is hard to apply a patch, when you cannot first get Linux installed...

I am running a new eMachines T6520, AMD64, 1 GB memory.  My last eMachines, a T2080 which worked just fine.  

When I boot Ubuntu, with "live DEBCONF_DEBUG=5" the last two lines it emits:

running /etc/hotplug/usb.rc
4294675.980000 ohci_hcd 0000:00:13.1: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.

At this point, it requires a cold boot, for even Windows MCE to come up.

Booting "live debian-installer/probe/usb=false" seems to have no effect on this problem.


Windows Media Center Edition, MCE boots and I can see the following information about the USB ports:

Under Device Mangager, UniVersal Serial Bus controllers,

Standard Enhanced PCI to USB Host Controller
Device type: Universal Serial Bus controllers
Location: PCI bus 0, device 19, function 2
. Memory Range FE02b000 - FE02BFFF
. IRQ 19

Standard OpenHCD USB Host Controller
Device Type: Universal Serial Bus controllers
Location:  PCI bus 0, device 10, function 0
. Memory range FE02D000 - FE02DFFF
. IRQ 19

Standard OpenHCD USB Host Controller
Device Type: Universal Serial Bus controllers
Location:  PCI bus 0, device 10, function 1
. Memory range FE02C000 - FE02CFFF
. IRQ 19

USB Mass Storage Device
Device Type Universal Serial Bus controllers
Location:  Location 0 (USB Reader)

USB Root Hub
Device type:  Universal Serial Bus controllers
Loation:  Location 0
Power:
 . USB Mass Storage deivce 100 mA
 . 3 port(s) available  0mA

USB Root Hub
Device type:  Universal Serial Bus controllers
Loation:  Location 0
Power:
 . 4 port(s) available  0mA

USB Root Hub
Device type:  Universal Serial Bus controllers
Loation:  Location 0
Power:
 . 8 port(s) available  0mA

Under Device Manager, Disk drives
Generic USB CF Reader USB Device
Generic USB MS Reader USB Device
Generic USB SD Reader USB Device
Generic USB SM Reader USB Device
Maxtor 6Y080P0
ST3200021A

---

### Post by Ibizibi on 2005-12-18
I partly solve my problem by turning USB LEGACY MODE off from bios but now  I can't use my wireless keyboard and mouse. Is this kernel problem or something else? Should i try to install Debian with different kernel version than Ubuntu's kernel?

---

### Post by reiki33 on 2005-12-18
After I reread my computer description at [http://www.emachines.com/products/products.html?prod=eMachines_T6520#](http://www.emachines.com/products/products.html?prod=eMachines_T6520#) I had the crazy idea to unplug the media card reader from jumper JUSB2 on the motherboard.  Ubuntu LiveCD then booted through most of the process, and then went out to lunch on my video, as far as I can tell.  SuSE 10.0 32 and 64 bit do the same, so I suspect Ubuntu and SuSE are seeing enough of the video card and monitor to think they can do it, but do not quite get it right.  The Fedora Core 4, FC4, brings me up with an unknown video card and monitor which it used VESA generic driver.  Which only provided 800x600 and less.  But it is up.  If I correctly told FC4 that it was a Sony HS75P, it apparently tried to boot into 1280x1024 mode, which the VESA driver would not handle.  The video card is an ATI RADEON Xpress 200 (PCI-Express).  None of the FC4 open source drivers worked.  Ok.  I stopped trying the ATI RADEON ones after about 30 of them.  I went to [www.ati.com](www.ati.com) and downloaded a 56meg proprietary Linux driver.  Voile'!  My guess at this point, is that if I used this driver on Ubuntu, it would work, but that would obviate the always free and open part...  I use my USB connection for my camera, disliking extra handling on the media cards as potentially damaging through error.  I think I will leave the Media Card Reader unplugged.  
The only leaves two odd questions.  1. What is going on that power off and back on will not boot, but requires pulling the power cord.  That works fine, as does a clean reboot, and shutdown and restart.  It must leave something in a card somewhere that survives power-button shut off.  2. What is going on with the Media Card Reader that makes it think it has an incorrect IRQ.  Perhaps it just does not deal with what is obviously a USB media card reader?

---

### Post by Darkhack on 2005-12-18
[QUOTE=aysiu]Your problem isn't a very common one. Your best bet is to follow some of [these 170 or so links about it](http://www.google.com/search?hl=en&q=Unlink+after+no-IRQ%3F+Controller+is+probably+using+the+wrong+IRQ&btnG=Google+Search). Hope you find the answer.[/QUOTE]

Actually it is pretty common.  Try this at the boot prompt....

boot: linux irqpoll

See the following topic for more details: [http://www.ubuntuforums.org/showthread.php?t=81153](http://www.ubuntuforums.org/showthread.php?t=81153)

---

