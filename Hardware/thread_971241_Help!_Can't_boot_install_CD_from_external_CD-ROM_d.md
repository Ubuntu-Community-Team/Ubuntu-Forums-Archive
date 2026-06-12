---
title: "Help! Can't boot install CD from external CD-ROM drive. Internal drive disappeared!"
date: 2008-11-04
forum: Hardware
---

### Post by MrCloudHands on 2008-11-04
I need help badly! My Ubuntu is beyond repair and I want to do a fresh install, wiping out everything on my hard drive. The main problem is that my internal CD/DVD drive magically disappeared and isn't recognized by my computer. When I put a CD into an external USB CD-ROM, Ubuntu detects it fine, but I need BIOS to detect it. I've tried entering PhoenixBIOS (on my Toshiba Satellite A215) and setting the boot order to run CD/DVD drive first, so I can boot from CD, but it doesn't respond.  Please help me so I'm not stuck without a working OS! 

Thanks

---

### Post by caljohnsmith on 2008-11-04
First off, does your BIOS support booting from a USB device? If it doesn't, I think you're not going to have any luck with your external USB CD drive. Have you set your BIOS to boot the USB device (CD drive) first? Or are you maybe setting your BIOS to just boot the internal CD drive? 

If you happen to have a floppy drive, you can install "Smart Boot Manager" to a floppy, boot from that, and it will give you the option to boot a CD drive. I haven't tried it with USB devices though. If you have a floppy drive and want to try it, let me know and I can give you directions of how to install Smart Boot Manager.

---

### Post by Djalmahal on 2008-11-07
Hi,

I have a Toshiba Satellite, now 2 years old and the CD-Drive is broken, it still reads original DVD's but no other CD's.

So, go to another Computer and boot Ubuntu 8.10 from your Live-CD. In the Live Session go into System>Administration>Create a USB Startup disk and create a Live-USB (you'll need a USB-Stick with 1GB or more). Next when you boot your own Computer press F12 or whatever it says at the BIOS Screen (the first screen that shows up when you start your computer) and select USB it will then boot up using the USB Stick. Once your Live-Session is up you can install it on your hard rive and you should be good.

This worked for me with exactly the same problem.

Good Luck
Andreas

---

