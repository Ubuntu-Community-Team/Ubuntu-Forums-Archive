---
title: "No USB at all! (I think)"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by JesCed on 2006-09-19
Hello, all.

For some months I have been using Ubuntu 5.10 on one of the two identical Siragon Canaima 305 laptops we have at the office, and results have been great. Recently I decided to install on the second laptop, and given that I had recently received my 6.06 CDs, I decided to install the newer version on the second laptop, and later on upgrade the first one.

Installation went smoothly enough, but after booting Ubuntu I noticed that the built-in webcam and card reader (for SD and Memory Stick) weren't working (the webcam isn't a mejor loss, but the issue with the card reader is a moderate pain). Afther that, I noticed that no device plugged into the USB ports (pendrives, cell phones or digital cameras) was mounted, so this is a VERY serious problem for me.

Since the laptops are configured to dual boot under Ubuntu/WinXP, I booted into XP and found out that both the cam and the card reader are detected as USB devices, so I believe my problem is that I have no USB suppport at all in Ubuntu.

Does anyone know how I can be sure that this is the problem, and the way to get this stuff working? I'd really appreciate the help.

Thanks,

Jesús

---

### Post by JesCed on 2006-10-10
Hello. I'm posting this follow-up because I suppose that this problem is so out of the ordinary that no one has been able to understand what is going on or give me a solution.

First of all, I made a mistake on the original post (sorry about that) when I said it was a model 305. The actual model is a Siragon Canaima 2050s.

Second, I wrote the Siragon Support team, and they replied saying that the problem was caused by the OS, and that Linux was not able to give USB support to these laptops (THAT sounded pretty strange to me!)

So, I booted the Ubuntu Breezy Live CD, and found perfectly working USB support. Because I had to have support for USB drives, I had to get rid of Dapper, and go back to Breezy (cam and cardreader still don't work, but that doesn't really matter). I thought that updating to Dapper, instead of doing a fresh install might solve the issue, but wasn't able to upgrade from the Internet due to an "unsolvable error", so I'm going to have to upgrade from the CD. However, before I do so, I'd really like to have your thoughts on this mess.

---

### Post by krisbowen on 2006-10-10
Jesced,

I have only just begun to use Ubuntu 6.06, but I got some really good advice from a Debian user.

When I installed ubuntu he advised to have everything plugged into my laptop. USb, Camera, tablet, printer..etc

I have since noticed that if I boot the machine without my usb memory stick plugged in, it is not found, but if I boot with it already plugged into the usb port it is found fine and able to be accessed..hope this might give you a short term solution....I am searching for a way to be able to add usb devices while running and will keep you posted!!

---

### Post by JesCed on 2006-10-15
Hello.

Since my las post, quite a few things have been going on. After reading krisbowen's reply, I decided to see what would happen if I used the kubuntu desktop CD whith my USB drive plugged in during boot. After the desktop finished loading, I saw that my drive was working fine. I later booted from the CD without the drive plugged in, pluggin it in only after the desktop finished loading. Stii everything seemed fine. So, I did a fresh kubuntu install, formatting my whole root partition (I know it sounds a bit drastic, but since I was not to lose any data, I thought I'd do it just to see what happened). After installing, my USB drives work perfectly. Now the only issues are that the cam and card reader still don't work (but I belive the card reader is malfunctioning in any case) and one quirk with my digital camera. I own a Sony DSC-H2, which is capable of three different kinds of USB connection: Mass Storage, PictBridge and PTP. kubuntu only manages to recognize the camera in PTP mode. Any idea as to why I can't get it to work in Mass Storage? The camera uses MS Pro Duo cards, so I don't know if this is the source of the problem.

---

