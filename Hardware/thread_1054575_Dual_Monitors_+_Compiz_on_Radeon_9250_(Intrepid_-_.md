---
title: "Dual Monitors + Compiz on Radeon 9250 (Intrepid - 8.10)"
date: 2009-01-29
forum: Hardware
---

### Post by Jenacis on 2009-01-29
Howdy!

I realize how busy everyone is and hope not to waste anyone's time, so I'm goin' to cut straight to what I'm trying to achieve:

**Dual Monitors, on an ATI Radeon 9250, running Ubuntu 8.10, w/ Compiz enabled.**

I've tried many, many instructions online, and none of them have worked out for me. Some of the solutions I've tried include:

1.) Installing the drivers for Linux from ATI's website; no such luck - their check.sh file doesn't work, and when I try installing the catalyst drivers, there's some a "Can't find X Server"-esque error.

2.) Numerous reconfigurations of xorg.conf, including some utilizing MergedFB.

3.) Playing with xrandr.

4.) Trying to install the fglrx drivers and go w/ BigDesktop. I remember reading somewhere that the newest fglrx doesn't support the Radeon 9250.

Basically, what I'm looking for (and I realize this is a one-in-a-million shot) is someone who has successfully achieved the above - and the way you achieved it. I've really tried many, many different things, all of which fail for some reason or another. 

I really appreciate any help or points in the right direction that anyone is willing to give. I will gladly do whatever I can to provide anyone with any information they request. Thank you!

---

### Post by Hendrixski on 2009-02-09
Hey, you don't need to do any of that stuff anymore.  Those are instructions from like a year ago or more.  Ancient if you consider the speed Ubuntu moves at.


I just plugged in a second monitor to my laptop and went to System->Preferences->Screen-Resolution  and there I can drag and drop the monitors into different positions and change their resolutions.  I remember trying it before by editing xorg and installing drivers.  Those days are gone.

---

### Post by kcole on 2009-04-04
This link was helpful for me getting the proprietary drivers installed properly for Ubun8.10.

[http://www.logicalinsanity.net/?p=196](http://www.logicalinsanity.net/?p=196)

I have a Radeon 9600, once you get the drivers just basically cut and paste the code into a terminal (with one or two edits depending on the driver).  Once installed properly and rebooted big desktop worked without any tinkering.

I am now having trouble with compiz working with Big desktop, so if any one has any suggestions about that it would be appreciated.  When I enable compiz I get either a 2" bar on the right side of the display that has multiple images of menus, and won't go away, or the entire screen starts having random magnified pixellation until it is finally not usable.  thankfully a simple reboot brought everything back.

I can use the compiz effects and themer when I use a single monitor but not dual monitors.  Any help would be appreciated.

---

