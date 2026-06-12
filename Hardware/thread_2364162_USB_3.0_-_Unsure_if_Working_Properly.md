---
title: "USB 3.0 - Unsure if Working Properly"
date: 2017-06-19
forum: Hardware
---

### Post by clalian on 2017-06-19
Hello everyone,
I have a Dell XPS 14Z (at the bottom it shows Model: P24G).
The machine works awesome: I have an ssd installed and 16gb.
Running Xubuntu 16.04
Everything good with it.

Recently, I bought a Magewell USB Capture HDMI Plus card.
It takes an HDMI input, and provides it as a video stream.
Magewell provides [linux drivers download at their page]("http://www.magewell.com/downloads").

I couldn't get it to work on this laptop, so I installed the drivers on a workstation I have, running Xubuntu 16.04.
Once the drivers were installed, I ran the qv4l2 utility, and it is able to capture the video stream from the Magewell.

Yet over on the laptop, the qv4l2 utility only sees the laptop's integrated camera (the one on top of the screen).
I made sure to connect the Magewell unit to the USB port that has the "SS" logo (SuperSpeed), which should be usb3.0.
I also looked at it physically, and that port does have the additional contact pins of USB 3.0

I am at a loss as to why the laptop does not recognize the Magewell.

Any ideas what I could try?
The output of lsusb, with everything unplugged, is:
```
Bus 001 Device 004: ID 8086:0189 Intel Corp. 
Bus 001 Device 003: ID 174f:143f Syntek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The output of lsusb, with the Magewell only plugged in is:
```
Bus 001 Device 004: ID 8086:0189 Intel Corp. 
Bus 001 Device 003: ID 174f:143f Syntek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 2935:0004  
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

What else could I check?
I found some threads that might be relevant, yet I can't see them helping in my situation.
[URL="http://www.linuxquestions.org/questions/slackware-14/usb-3-0-port-not-working-925355/"]USB 3.0 port not working
[/URL][URL="https://unix.stackexchange.com/questions/72625/why-is-usb-not-working-in-linux-when-it-works-in-uefi-bios"]Why is USB not working in Linux when it works in UEFI/BIOS?
[/URL][USB and networking broken in 64-bit ubuntu for new motherboard ]("https://ubuntuforums.org/showthread.php?t=2114055")

Any help is greatly appreciated!

---

### Post by clalian on 2017-06-19
Another interesting point is that if I check the contents of /dev/

I have in there
/dev/video0

And if I plug in the Magewell, I have in there:
/dev/video0
/dev/video1

---

### Post by clalian on 2017-06-20
I performed a test:
I took a different laptop, a Lenovo X1Carbon.
I installed Xubuntu 16.04, downloaded today.
I then installed the Magewell linux driver.
Then installed qv4l2...
Yet the same result happened.

The qv4l2 utility only sees the laptop lid's webcam.
I made sure to plugin the Magewell into the usb port that has the "SS" logo, for USB3.0

Could it be that the laptops don't have enough power for the Magewell?
Yet that doesn't make sense.

---

### Post by clalian on 2017-06-21
I ordered a USB 3.0 powered hub, to eliminate the possibility of low-power from the laptop.
Will update once it arrives.

---

### Post by gordintoronto on 2017-06-21
Have you tried running Cheese, and selecting each video device?

---

### Post by clalian on 2017-06-21
> **gordintoronto said:**
> Have you tried running Cheese, and selecting each video device?

[This Cheese]("https://wiki.gnome.org/Apps/Cheese")?
I didn't know that existed! 
Going to test it out shortly in the laptop and report back.
Thank you gordintoronto!

---

### Post by clalian on 2017-06-24
> **gordintoronto said:**
> Have you tried running Cheese, and selecting each video device?

Hello.
I tested with Cheese in the laptop (Xubuntu 16.04), and the image comes up perfectly.

Yet in QV4L2, it's not showing.

What could I check?
Any and all help is greatly appreciated!

EDIT: I correct my self... QV4L2 in the laptop *IS* in fact working.
I will post shortly what I am seeing, so others can benefit.

Yet loading from the command line qv4l2, it brings up the gui V4L2 Test Bench.
In there, the Card is "USB Capture HDMI+".

I do believe I needed a powered USB 3.0 hub in order for this to work... even though I was pluggin the Magewell into a "SS" power on the laptop.

---

