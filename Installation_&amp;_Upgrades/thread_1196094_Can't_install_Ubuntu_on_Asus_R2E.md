---
title: "Can't install Ubuntu on Asus R2E"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by Sukhinov on 2009-06-24
Hello, I am a regular Windows user.

I decided to install Ubuntu in my Asus R2E. It has 800×480 screen, also I have lost CD-ROM drive for it, so I decided to download 9.04 Netbook remix, which could be installed from USB flash drive.

I downloaded ubuntu-9.04-netbook-remix-i386.img file, writed it on the flash drive using Flashnul, configured BIOS to boot from flash drive, and got an error "Operating system not found". I have another 2 laptops, so I tried them all. Only one (Toshiba) laptop could start from flash ant boot Ubuntu, other two (Asus) report an error: "Operating system not found".

Next, I decided to install Ubuntu from Windows. I run the wubi.exe, but nothing happened! Program just did not start. I tried to start it on other 2 laptops: the same result. I managed to find wubi's log in temp files. All 3 laptops have the same error there: "ACSII decoder cannot decode..." (I don't remember exactly). I tried to search Internet and found that I need newer version of wubi (btw, why the bogus version was included in the latest release of Ubuntu??). I downloaded the new wubi and placed it near the old wubi on the flash drive.

I started it. After that the window "Exception processing message... bla bla bla..." popped up. The window has 3 buttons: Abort, Retry, Ignore. I pressed Abort, but the same window popped up again. I pressed Abort some times more, and after that wubi managed to display its GUI! I selected the drive to install, installation type and pressed «install» button, the same error "Exception processing message..." appeared 10 more times, after that program started to download Ubuntu from the Internet! But I have already downloaded it! It's on the flash drive! My Internet is expensive, so I pressed «cancel».

I need an advice.

Is there any way to install Ubuntu?

---

### Post by Sukhinov on 2009-06-24
After 8 hours of experimenting I used DiskImage instead of Flashnul, and now all 3 laptops can boot Ubuntu just from the USB-flash!

I think you should put the phrase «Attention! If you use Flashnul to write image into a flash, you probably will not be able to boot from this flash!» on that page: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles) 

So, I booted Ubuntu on my R2E and tested it. Two problems:
1) Intrerface elements are too large for R2E screen. I cannot use some windows, because their bottom buttons are below the screen border. Do you have Ubuntu version for Webbooks like R2E?
2) Ubuntu just freezed after two minutes of working (it was connecting to wireless network when freeze occur).

P.S. I tested RAM and verified MD5 checksum of .img before experimenting.

---

### Post by mk1w86 on 2009-06-24
> 1) Intrerface elements are too large for R2E screen. I cannot use some windows, because their bottom buttons are below the screen border. Do you have Ubuntu version for Webbooks like R2E?

I have an Asus Eeepc 701 which runs at 800x480 and according to here

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

one of the main problems is that some windows are not designed for a resolution as low as 800x480.  A workaround for windows that go off the screen is to hold down the alt key which lets you move the window without needing the cursor on the title bar. :)

---

### Post by mk1w86 on 2009-06-24
> A workaround for windows that go off the screen is to hold down the alt key which lets you move the window without needing the cursor on the title bar. 

Just realized what an R2E is and that it probably doesn't have an alt key unless it has an onscreen keyboard. :confused:

---

### Post by Sukhinov on 2009-06-24
OK, thank you for the Alt-key tip!

Edit: I will use external keyboard for this :)

---

### Post by Sukhinov on 2009-06-24
I managed to install it!!!

But I have the same problem after the installation: Ubuntu sometimes freezes when connecting to a wireless network. The only thing I can do is power down. Please help!
[B]
WLAN[/B]
Manufacturer:	Asustek Computer Inc.
Model:		A9T wireless
Revision:	48.02
Interface:	USB

---

### Post by Sukhinov on 2009-07-04
WLAN is working now, after kernel update!!!

---

### Post by yellow99 on 2009-07-13
> **Sukhinov said:**
> WLAN is working now, after kernel update!!!

Good to hear that there is hope for my freeze problem on my ASUS! 

Which kernel have you upgraded to? Mine is 2.6.28-13. But I might be missing the point here since my wireless card is an "Intel Corporation Wireless WiFi Link 5100". 

/yellow99

---

