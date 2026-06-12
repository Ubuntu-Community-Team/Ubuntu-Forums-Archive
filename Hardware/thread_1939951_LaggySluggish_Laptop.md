---
title: "Laggy/Sluggish Laptop?"
date: 2012-03-12
forum: Hardware
---

### Post by Dimmizer on 2012-03-12
Good Day,

I am creating this thread due to a laptop I have which is currently running Ubuntu 11.10. According to the Installation/System Requirements I meet them all.

**Ubuntu Desktop Edition**
 
[LIST]
[*]1 GHz CPU (x86 processor (Pentium 4 or better)
[*]1 GiB RAM (system memory)
[*]15 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
[*]800 by 600 screen resolution
[/LIST]
**Laptop Specifications**
   
[LIST]
[*]AMD Athlon Processor TF-20 (1.6 GHz CPU) 64bit Processor
[*]2 GiB RAM (system memory)
[*]160GB HDD
[*]Easily passes the 800x600 resolution.
[/LIST]


 The problem I am having with it is when I try to open say Firefox or the Ubuntu Software Center it feels like it's lagging or really slow. It doesn't open right away like boom done. It feels like its taking 2-3 secs to really open and come up. I've noticed YouTube videos are choppy and slow as well. If I'm watching say RayWilliamJohnson or PhillyD it's like there done saying an entire sentence but there mouths are still moving so I'm guessing that's a video driver error but when I installed the distro and got it all good I restarted and a popup was at the top right of my screen asking me to install newer video drivers.


I'm running a new install so maybe I forgot something? anyone have any ideas? No I'm not a newb with linux but I am new with Ubuntu. I used Back Track for 2 years and never had anything like this happen. I think something got screwed when I installed the new video drivers but the question is what? any ideas?


Thanks for your time and help in advanced, always a pleasure to be work with like minded people ;D.

---

### Post by ahallubuntu on 2012-03-12
So what are the specs of your actual laptop?

I've installed Ubuntu on some very old machines, and it works - but it can be quite slow.

---

### Post by Dimmizer on 2012-03-12
> **ahallubuntu said:**
> So what are the specs of your actual laptop?

I've installed Ubuntu on some very old machines, and it works - but it can be quite slow.


**Laptop Specifications**
   
[LIST]
[*]AMD Athlon Processor TF-20 (1.6 GHz CPU) 64bit Processor
[*]2 GiB RAM (system memory)
[*]160GB HDD
[*]Easily passes the 800x600 resolution.
[/LIST]
That's my laptop specs lol, what else do ya need to know? or were you just confused a bit there?

---

### Post by lowbudgetlaptops on 2012-03-12
try installing ubuntu restricted extras from terminal sudo apt-get install  ubuntu restricted extras

---

### Post by Dimmizer on 2012-03-13
> **lowbudgetlaptops said:**
> try installing ubuntu restricted extras from terminal sudo apt-get install  ubuntu restricted extras

Anyone else got ideas or tips maybe? restricted extras didn't work

---

### Post by ahallubuntu on 2012-03-13
I still don't have the specs of your laptop, so I can't really offer you much more specific help.  The CPU and RAM isn't quite enough.  What make/model laptop?  What kind of graphics does it have?  I don't care about the resolution.

I guess I'm not sure if what you're seeing is normal or not for a laptop of that vintage.  Why is it a problem for you to wait 2-3 seconds for an application to open?  My laptop is faster than yours and it takes about that time or longer to open a new program either in Ubuntu or in Windows.  If I want faster performance I'll upgrade to an SSD.

Choppy web videos (youtube) usually mean the CPU is overloaded or the flash player is not performing correctly.  Sometimes having the correct video driver installed will help that issue, but I don't have any idea what kind of video card your laptop has.

If you open System Monitor (or "top" in a terminal), what processes are consuming the most CPU when you are watching a YouTube video?  What % of the CPU do they use?

I have seen cases where a failing hard drive or an overheating CPU could cause performance issues.  Or just poor driver support in the Linux kernel for your hardware.  There are a lot of possibilities.

---

### Post by lovinglinux on 2012-03-13
Two or three seconds to open Firefox looks normal to me.

The issue with flash movies is probably due to excessive CPU usage.

See [http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)

---

### Post by Dimmizer on 2012-03-13
> **lovinglinux said:**
> Two or three seconds to open Firefox looks normal to me.

The issue with flash movies is probably due to excessive CPU usage.

See [http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)


Thanks lovinglinux :D

---

### Post by Dimmizer on 2012-03-13
> **ahallubuntu said:**
> I still don't have the specs of your laptop, so I can't really offer you much more specific help.  The CPU and RAM isn't quite enough.  What make/model laptop?  What kind of graphics does it have?  I don't care about the resolution.

I guess I'm not sure if what you're seeing is normal or not for a laptop of that vintage.  Why is it a problem for you to wait 2-3 seconds for an application to open?  My laptop is faster than yours and it takes about that time or longer to open a new program either in Ubuntu or in Windows.  If I want faster performance I'll upgrade to an SSD.

Choppy web videos (youtube) usually mean the CPU is overloaded or the flash player is not performing correctly.  Sometimes having the correct video driver installed will help that issue, but I don't have any idea what kind of video card your laptop has.

If you open System Monitor (or "top" in a terminal), what processes are consuming the most CPU when you are watching a YouTube video?  What % of the CPU do they use?

I have seen cases where a failing hard drive or an overheating CPU could cause performance issues.  Or just poor driver support in the Linux kernel for your hardware.  There are a lot of possibilities.

```
**Processor / Chipset**

 
[LIST]
[*] **Processor**  AMD Athlon 64 TF-20 / 1.6 GHz
[*] **Cache**  L2 cache - 512.0 KB
[*] **64-bit Computing**  Yes
[*] **Chipset**  AMD M780G
[/LIST]
 **Memory**

 
[LIST]
[*] **RAM**  2.0 GB ( 2 x 1 GB )
[*] **Max RAM Supported**  4.0 GB
[*] **Technology**  DDR2 SDRAM
[*] **Speed**  667.0 MHz
[*] **Form Factor**  SO DIMM 200-pin
[*] **Slots Qty**  2
[*] **Empty Slots**  0.0
[/LIST]
 **Storage**

 
[LIST]
[*] **Floppy Drive**  None
[*] **Hard Drive**  160.0 GB HDD / 5400.0 rpm
[*] **Storage Removable**  None
[*] **Optical Drive**  DVD±RW / DVD-RAM
[*] **Optical Drive (2nd)**  None
[*] **Hard drive type**  Portable
[/LIST]
 **Environmental Parameters**

 
[LIST]
[*] **Environmental standards**  RoHS
[/LIST]
 **Display**

 
[LIST]
[*] **Type**  15.6 in
[*] **Max Resolution**  1366 x 768 ( HD )
[*] **Widescreen**  Yes
[/LIST]
 **Audio & Video**

 
[LIST]
[*] **Graphics Processor**  ATI Radeon HD 3200
[*] **Memory Allocation Technology**  HyperMemory up to 1919MB
[*] **Camera**  Yes
[*] **Sound**  Microphone
[/LIST]
 **Input**

 
[LIST]
[*] **Type**  Touchpad,
 Keyboard
[/LIST]
 **Communications**

 
[LIST]
[*] **Wireless**  802.11b/g
[*] **Network Interface**  10/100 Ethernet
[*] **Compliant Standards**  Wi-Fi CERTIFIED
[/LIST]
 **Battery**

 
[LIST]
[*] **Technology**  6-cell Lithium ion
[*] **Capacity**  4400.0 mAh
[*] **Run Time**  3.0 hour(s)
[/LIST]
 **AC Adapter**

 
[LIST]
[*] **Voltage Required**  AC 120/230 V ( 50/60 Hz )
[/LIST]
 **Connections & Expansion**

 
[LIST]
[*] **Expansion Bays**  None
[*] **Interfaces**  2 x VGA,
 USB 2.0,
 Microphone input,
 LAN,
 Headphone output
[*] **Memory Card Reader**  Card reader ( Memory Stick ),
 ( MultiMediaCard ),
 ( Memory Stick PRO ),
 ( SD Memory Card ),
 ( xD-Picture Card )
[/LIST]

```My Laptop Specs, that better? lol


[COLOR=Red][SIZE=3][FONT=Verdana]Thanks again everyone for the help and the time :)[/FONT][/SIZE][/COLOR]

---

