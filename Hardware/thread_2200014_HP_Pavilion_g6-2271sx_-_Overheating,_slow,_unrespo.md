---
title: "HP Pavilion g6-2271sx - Overheating, slow, unresponsive, wireless issues"
date: 2014-01-17
forum: Hardware
---

### Post by kaushik2 on 2014-01-17
Hey all,

So, I have this model of the HP pavilion g6 Notebook series: [http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c03506055](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c03506055)

These are the specs:

[TABLE]
[TR="bgcolor: #E7E7E7"]
[TD]**Microprocessor**[/TD]
[TD="class: columnReducedMargin"]2.5 GHz Intel Core i5-3210M[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]**Chipset**[/TD]
[TD="class: columnReducedMargin"]Intel HM76 Express[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]**Microprocessor Cache**[/TD]
[TD="class: columnReducedMargin"]3 MB L3 cache[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]**Memory**[/TD]
[TD="class: columnReducedMargin"]4 GB DDR3[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]**Memory Max**[/TD]
[TD="class: columnReducedMargin"]Upgradeable to 8 GB DDR3 (2 DIMM)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]**Video Graphics**[/TD]
[TD="class: columnReducedMargin"]AMD Radeon HD 7670M (2 GB DDR3 dedicated)[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]**Hard Drive**[/TD]
[TD="class: columnReducedMargin"]500 GB SATA (5400 rpm)
Up to 24 GB partition for system recovery[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]**Multimedia Drive**[/TD]
[TD="class: columnReducedMargin"]SuperMulti DVD±R/RW with double layer support[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]**Display**[/TD]
[TD="class: columnReducedMargin"]39.6 cm (15.6") HD BrightView LED-backlit (1366 x 768)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]**Network Card**[/TD]
[TD="class: columnReducedMargin"]Integrated 10/100 BASE-T Ethernet LAN[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]**Wireless Connectivity**[/TD]
[TD="class: columnReducedMargin"]802.11b/g/n
 Bluetooth[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]**Sound**[/TD]
[TD="class: columnReducedMargin"]Altec Lansing speakers with Dolby Advanced Audio[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]**Keyboard**[/TD]
[TD="class: columnReducedMargin"]Full size textured island-style with numeric keypad[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]**Pointing Device**[/TD]
[TD="class: columnReducedMargin"]TouchPad supporting multi-touch gestures and on/off button[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]**External Ports**[/TD]
[TD="class: columnReducedMargin"]Digital media card reader
1 VGA
 1 HDMI
 1 headphone-out
 1 microphone-in
 1 USB 2.0
 2 USB 3.0
 1 RJ45[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]**Dimensions**[/TD]
[TD="class: columnReducedMargin"]37.6 x 24.4 x 3.63 cm[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]**Weight**[/TD]
[TD="class: columnReducedMargin"]Starting at 2.48 kg[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]**Power**[/TD]
[TD="class: columnReducedMargin"]90W AC power adapter
6-cell Li-Ion[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]**Camera**[/TD]
[TD="class: columnReducedMargin"]HP TrueVision HD Webcam with integrated digital microphone[/TD]
[/TR]
[/TABLE]

I've been running Ubuntu 12.04 on this machine for about 6 months now, but I've always faced the issue of the laptop getting overheated. I also start to hear loud noises (Fan being extremely loud) when the laptop overheats. The laptop also slows down massively when I try to run multiple processes, especially when I'm running multiple browsers - Chromium and Firefox for example. The system sometimes just hangs or becomes extremely slow, that I'll be forced to hard boot (Soft boot if I'm lucky enough to move the mouse to the power button). The battery also doesn't stay for too long without the power cable. The UI would show me something like 2 hours of battery left - but the battery would last hardly for a little more than an hour.

Could this be a driver issue? Something to do with the graphic card? Or is it an issue with the battery?

I also faced issues with the wireless driver - RT3290. I got really annoyed with this, cause whenever I used wifi, the system ended up in a kernel panic. So I decided to buy a ThinkPenguin wireless adapter and that worked right out of the box with no issues what so ever.

Now the only problem is the speed, overheating, the really loud fan noise and frequent hang-ups.

Has anyone else faced issues with their pavilion g6? Are there driver alternatives for the hardware components? What is it exactly that is causing this issue?

Should I maybe be looking at other linux distros?

Thanks in advance.

Kaushik

---

### Post by Bucky Ball on 2014-01-17
Welcome. Are you doing regular updates?

Open a terminal and paste these three commands, one after the other and hitting return in between. Report any errors:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
This will NOT upgrade you to a newer release, just update/upgrade any packages you already have installed in 12.04 LTS.

---

