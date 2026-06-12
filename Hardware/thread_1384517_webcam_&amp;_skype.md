---
title: "webcam &amp; skype"
date: 2010-01-18
forum: Hardware
---

### Post by poisoneggs on 2010-01-18
So I have a crappy cam, OmniVision OV519. It works with Cheese, and Audacity can record about half a second of audio with it. However it won't work with Skype. Any ideas? Thanks.

EDIT: It uses the module gspca_ov519, if that helps.

---

### Post by poisoneggs on 2010-01-19
anyone?

---

### Post by wimduk on 2010-02-08
I have the same problems:confused:, see my details below
  	 	 	 	 	 	  **Facts**
 
[LIST=1]
[*]wim dukker, 63 years old, linux 	newbie
[*]Software: Linux Kubuntu 9.10
[*]Hardware: Packerd Bell Easy Note 	laptop
[*]Webcam: Trust 320 Spacecom webcam 	(= Omnivision OV519, see lsusb output below)
[*]Skype for linux (version 2.1.0.81) 	sees the webcam but the video test fails
[*]Camorama give the message “Unable 	to capture image”
[*]Cheese sees the camera!! and a 	initial picture is shown. If I start talking nothing happens on the 	screen but the movements and voice is recorded with a very bad 	quality (slow motion output, voice hardly to understand)
[/LIST]
 

 **lsusb gives the following output;**
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 007: ID 04d9:1400 Holtek Semiconductor, Inc.  
 Bus 001 Device 006: ID 0930:0b09 Toshiba Corp.  
 Bus 001 Device 005: ID 1267:0210 Logic3 / SpectraVideo plc  
 Bus 001 Device 004: ID 0bc2:2300 Seagate RSS LLC  
 Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 **Bus 002 Device 003: ID 05a9:8519 OmniVision Technologies, Inc. OV519 Webcam**
 Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

 **Part of dmesg output (as fas as the webcam is concerned)**
 **[   30.263724] Linux video capture interface: v2.00**
 [   30.337831] cfg80211: Calling CRDA to update world regulatory domain
 [   30.362353] cfg80211: World regulatory domain updated:
 [   30.362360] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
 [   30.362366] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
 [   30.362370] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
 [   30.362374] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
 [   30.362379] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
 [   30.362383] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
 [   30.397472] lp: driver loaded but no devices found
 **[   30.399454] gspca: main v2.6.0 registered**
 [**   30.457382] gspca: probing 05a9:8519**
 **[   30.498112] irda_init()**
 **[   30.498132] NET: Registered protocol family 23**
 **[   30.679693] ov519: I2C synced in 0 attempt(s)**
 **[   30.679701] ov519: starting OV7xx0 configuration**
 **[   30.691688] ov519: Sensor is an OV7648**
 **[   30.731797] gspca: probe ok**
 **[   30.731819] gspca: probing 05a9:8519**
 **[   30.731833] gspca: probing 05a9:8519**
 **[   30.731865] usbcore: registered new interface driver ov519**
 **[   30.731870] ov519: registered**
 

 It seems that the right driver is loaded but the webcam is not/bad working (see facts)
 

 Who can help me to get the webcam working, especially in Skype.
 

 Many thanks in advance for your grat help.
 

 Kind regards wimduk

---

### Post by sublimation on 2010-02-11
EDIT: didn't notice this was a days old thread. Perhaps now it can be marked Solved


Hi guys, I've spent the better part of this evening trying to fix my webcam with skype. The most helpful site I found was
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
By finding my webcam in the list I was able to get the exact solution. I had the exact same issue, Cheese worked fine, but no dice in Skype. This was the solution: [http://forum.skype.com/index.php?showtopic=252681&st=0&p=1512731&#entry1512731](http://forum.skype.com/index.php?showtopic=252681&st=0&p=1512731&#entry1512731)


Hope it helps!

---

### Post by wimduk on 2010-02-12
Hi Sublimation,

GREAT! :D It worked for me as well with Ubuntu 9.10.
Is Ubuntu aware of this video incompatibility so that it will be solved in the next release?

Many thanks for this help because I have searched the internet for days to get this problem solved  

Kind regards, wimduk

---

### Post by sublimation on 2010-02-12
hi wimduk,
   I'm so glad it helped you, too!
From what I understand about my particular problem, is that the issue is driver and application dependent, rather than the fault of ubuntu. The gspca driver for me had everything working with any program I threw at it except skype. Skype attempts to use a library that doesn't work properly for this particular camera with the driver configuration, so the little bit of code I had to run before opening skype tells it to fallback to another version. 

As it's part of the SkpyeWebCams page which has been developed to help people like us use this Beta version of Skype while they work out the kinks. So perhaps this is one kink that Skype will fix.

---

### Post by wimduk on 2010-02-12
Hi Sublimation,

Thanks for your fast reply. And yes reading your comment I think Skype has to fix this.
Because it is a beta version we can't blame them (can we? :) )

Regards wimduk

---

### Post by poisoneggs on 2010-03-14
Damn, wish I could have checked the thread sooner... since I hadn't found a solution I removed the cam's usb cable to power an electronics project I was working on! Thanks anyway

---

