---
title: "Problems with new ubuntu install not detecting mouse or LAN."
date: 2013-07-19
forum: Hardware
---

### Post by tven on 2013-07-19
I'm very new to Linux. I tried installing Linux via USB but couldn't get the 'try Ubuntu' to load correctly so I ended up downloading 12.04.2 LTS (AMD64) and burned it to CD and used it to install Ubuntu, which worked correctly but I had to just use the keyboard the whole time which took me ages. The problem I'm still having is that once I log into Ubuntu my USB-mouse is not being detected (at no point during the installation was the mouse working). If i boot into the bios the mouse works which makes me think that the Linux version I tried using is missing either support for my 3-4 year old mouse (unlikely) or that it is missing support for the motherboard and/or usb parts of it. It also doesn't seem able to use the LAN connection either. 

My computer:
GA-970A-UD3 Rev 3
4GB Gskill ram
8320 AMD CPU
8800GTX Nvidia

Any and all support would be greatly appreciated.

---

### Post by TheFu on 2013-07-19
Reviewing the dmesg and log files will be where I started. [http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) explains more.

---

### Post by Cheesehead on 2013-07-19
> **tven said:**
> I tried installing Linux via USB but couldn't get the 'try Ubuntu' to load correctly 

If your hardware will not run the 'Try Ubuntu' environment, then you really should not install.
Instead, tell us about the problems with the test environment. Too slow? Hardware not recognized? Some error?

---

### Post by Bucky Ball on 2013-07-19
Welcome to the forums. 

Some friendly advice. You'll make things easier for all if you concentrate on the mouse issue on this thread and post a new thread with a descriptive title about your LAN issue in the ***Wireless & Networking*** sub-forum. The two issues aren't related and the LAN one doesn't belong here so a new thread will avoid confusion and help you get better help. Cheers. ;)

12.04 LTS is the ideal place to start. Plug in your USB mouse, open a terminal (don't use Unity myself but Applications>Accessories>Terminal or you can type it in the dash?) and paste this in and hit enter:

```
lsusb

```

You'll see something like mine:

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 001 Device 004: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 192f:0416 Avago Technologies, Pte.
```

Can you see your mouse listed? If so, that's a good start. This is not an incompatible mouse (or I will eat my shoe). I'm betting on something else. My mouse is I think the last in my list, but as it has no name brand on it anywhere I couldn't say for certain. Is it specific to this mouse? Any USB device? Have you tried a dongle in the same slot? Perhaps to do with why you couldn't install from USB dongle. :-k

PS: Just to confirm: You now have 12.04 LTS installed and running from hard drive, not from CD/DVD/USB?
PPS: For the new LAN thread, provide the output of these commands (one after the other) to get things started (the first command will ask for your password when you hit enter - it will be invisible when you type it - just hit enter when done):

```
sudo lshw -C network
iwconfig
```

... and whatever info you think can help. Describe exactly what's happening and any errors you might be getting. Good luck. ;)

---

### Post by tven on 2013-07-19
Hi,

Thank you for all your suggestions BucKy Ball. I wasn't very clear with the title, it wasn't that I couldn't connect to the Local area network is was that I couldn't connect to the router. I has assumed the USB and LAN ports not working was a linked hardware problem and it appears I was right. I found this post while at work today [http://ubuntuforums.org/showthread.php?t=2111223](http://ubuntuforums.org/showthread.php?t=2111223) which exactly matches the problems I /was/ having. Reading though the posts lots of people where having success with editing the bios so that IOMMU was set to ENABLED. Once I did this and booted Linux all the USB and Net work ports began functioning correctly. 

Thanks again for the quick responses and help.

---

