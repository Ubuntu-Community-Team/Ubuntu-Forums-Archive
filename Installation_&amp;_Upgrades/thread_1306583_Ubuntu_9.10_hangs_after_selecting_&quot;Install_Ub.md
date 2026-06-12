---
title: "Ubuntu 9.10 hangs after selecting &quot;Install Ubuntu&quot;"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by chrisdevries on 2009-10-30
Hello, 

Can anyone help me install Ubuntu 9.10? I realy want to try it out!
I am trying to install Ubuntu on my pc but when I choose "Install Ubuntu" it hangs after a while showing only a white Ubuntu logo.

What I have tryed:
Use the option "Check disc for defects" boot menu.
No errors were detected.

Use the acpi=off option F6

Can anyone tell me what to try next?

My computer is a Pentium 4 3 Ghz with 2 gb memory.

I have used Knoppix to get information about the hardware:
lspci

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
02:01.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

---

### Post by XDevHald on 2009-10-30
Welcome to Ubuntu and the Forums!

First off, are you sure you picked the right CD to install Ubuntu? For example: Your system is Intel which runs the i386 unix files. IF this is the case then you can burn the ISO (Desktop Edition) to your CD and will work just fine. Be sure to select the i386 ISO file to download if the website of Ubuntu does not automatically recognize your processor.

This report does not give enough information to diagnose the issue. Keep us up to date on the issue and if this did resolve it with what I provided above.

---

### Post by chrisdevries on 2009-10-30
Hello 
Thank you for your help.
I have downloaded and burned ubuntu-9.10-desktop-i386.iso
I allso tryed Ubuntu 8.04 witch is running without any problems.

How can I get more information for you? (I can start Ubuntu 8.04 from CD.)

With kind regards,

Chris

---

### Post by XDevHald on 2009-10-30
What it looks to me is that the CD did not burn properly to let you install it. Try again if you can. I know that this seems crazy and a waste of time but this is a troubleshooting test.

Keep us posted and thank you for replying back.

---

### Post by chrisdevries on 2009-10-30
I'll try and burn the CD again. The problem is. I have only two rewritable disks.
Tomorrow I will buy more CD-R's (stores are now closed at my local)
It just may be that my disk drives have problems reading CD-RW. But what I don&#8217;t understand is why the CD check option did not detect errors. 
my computer has two cd trays and I have tried them both.


Are there any more things I can try tonight?

---

### Post by MG37221 on 2009-10-30
Mine does exactly the same thing.  After several attempts, I finally booted to the Live CD.  That did come up.  I perused the 9.10 desktop and selected the "Install Ubuntu 9.10" icon on the desktop.  Install is now at 80% (Configuring APT.. and holding) but it *seems* to be running successfully.  This is the X86_64 version on an AMD Phenom II with 4GB of RAM.  Please note that 9.4 was running quite nicely but I am moving to 9.10 in the hopes that newer drivers will better support my newer hardware.

---

### Post by chrisdevries on 2009-10-30
What did you do to get it working?
Just try it a couple of times or did you do something spesific?

---

### Post by chrisdevries on 2009-10-30
Ah it is working now!
I removed my Sweex Model LW057V2 wireless card and my Hauppauge WinTV PAL-B/G-I-D/K-SECAM 23559 Rev D591.
Wait I will re insert one of the cards to see witch one was the problem.

Chris

---

### Post by Jazzy_Jeff on 2009-10-30
If you are having problems installing from the live cd, you can download the Alternate Install CD. It is text based but easy to use. I always have problems with the live cd's myself. Here is the link for the alternate cd [http://ubuntu-releases.eecs.wsu.edu/karmic/](http://ubuntu-releases.eecs.wsu.edu/karmic/)

---

### Post by chrisdevries on 2009-10-30
> **chrisdevries said:**
> Ah it is working now!
I removed my Sweex Model LW057V2 wireless card and my Hauppauge WinTV PAL-B/G-I-D/K-SECAM 23559 Rev D591.
Wait I will re insert one of the cards to see witch one was the problem.

Chris

             Aha.  I reinserted my Wireless adapter and it booted correctly.
Then I inserted my TV card and the same problem recured. White ubuntu logo and freezes up. It might be a kernel bug or something. As a developer I have done some C++ projects but I realy don't know anything about Linux yet.

Thank you all for helping me out!
 
Chris.

---

