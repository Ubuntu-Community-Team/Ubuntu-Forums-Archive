---
title: "Tried to update graphics driver, now command line only!"
date: 2008-11-15
forum: Hardware
---

### Post by nlakes on 2008-11-15
Hi everyone, 

Well I am new to Kubuntu and just installed 8.10 a day ago and already I've stuffed it up - I tried to change a driver for my inbuilt intel graphics card on my laptop from i810 to the other one.. can't remember the name, and now when I try to start kubuntu I end up with a command line thing.

Could someone please tell me in baby-steps how I can fix this?

Thanks, much appreciated!

---

### Post by pytheas22 on 2008-11-16
Could you please explain exactly what you did?  Did you try to switch from the 'intel' driver (used by default since Ubuntu 8.04) to the 'i810' driver?

You can also try opening up your xorg.conf file by logging in on the command line and typing:

sudo nano /etc/X11/xorg.conf

Look for the section labeled 'device'.  It should look like this:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Make it look like this:
```

Section "Device"
	Identifier	"Configured Video Device"
        driver          "i810"
EndSection
```

Then press control-O (O the letter, not zero) to save the file, then control-X to exit.  Then type 'startx'.  Does it work?  If not, repeat the steps above, except this time change the relevant section of the xorg.conf file to look like this:
```

Section "Device"
	Identifier	"Configured Video Device"
        driver          "intel"
EndSection
```

Any luck now?  If not, try:

```

Section "Device"
	Identifier	"Configured Video Device"
        driver          "mesa"
EndSection
```

That should get you an X session in low-graphics mode.

If none of the above helps, try typing:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Then try using 'startx' again.

If none of this helps you, let us know, and again, please try to explain in detail what you did to break this.

---

### Post by nlakes on 2008-11-16
resolved :)

sudo apt-get install xserver-xorg-video-intel



On a separate issue, can someone tell me why the graphics are a bit shaky, when I minimise and maximise windows to the dock it goes black and shows these weird squiggly lines like static on a tv reception. The graphics card works fine on xp, am i using the right driver?

---

### Post by pytheas22 on 2008-11-16
> On a separate issue, can someone tell me why the graphics are a bit shaky, when I minimise and maximise windows to the dock it goes black and shows these weird squiggly lines like static on a tv reception. The graphics card works fine on xp, am i using the right driver?

The 'intel' driver is the most modern one.  You could try i810, which is older but may give you better results--although probably not.  Does the problem occur even with desktop effects turned off?  What is the output of:
```

lspci -nn
```

---

### Post by nlakes on 2008-11-16
Thanks for all the replies. 

This is what I get pytheas22:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)                      
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)            
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)               
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCIController [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-EFast Ethernet Controller [11ab:4352] (rev 14)
0a:03.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bgNIC [168c:001a] (rev 01)
0a:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0a:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

---

### Post by pytheas22 on 2008-11-16
I googled around but unfortunately I can't find anyone else with this problem on your graphics card.  There are some people who seem to be having [issues with X crashing entirely]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218334"), but it seems limited to Mac Minis--you don't have one of those, do you?

Does the problem happen even with desktop effects disabled?

---

### Post by nlakes on 2008-11-16
It doesn't happen if I turn off the effect for minimising, as often. Occasionally right-click menus appear black with that static for a second, then come good. 

I'm using it on an Acer laptop, it's only got pretty basic settings (1.6g celeron, 512 ram). But on XP I've got some add-ons to mimic expose etc, and that runs fine. Maybe I'm using the wrong driver.
Should I use another one, and how would I use it? I'm not really good at this stuff. 

I don't supose you could recommend a good website or book for an absolute noob like me to familiarise myself with how to do things on kubuntu?

---

### Post by pytheas22 on 2008-11-16
'intel' is the best video driver available for your card on Linux, and the only one besides i810.  The bug you're seeing may not actually be the driver's fault as much as that of compiz (the program that creates desktop effects) or KDE (your Kubuntu desktop environment).  But the best thing that you could do about it would be to [submit a bug report]("http://www.ubuntu.com/community/ReportProblem").

I can't really recommend a good book or website for learning Kubuntu myself, as I didn't learn it that way, plus I haven't used Kubuntu as much as Ubuntu (the difference is that Kubuntu uses KDE as its desktop environment, while Ubuntu uses Gnome; beneath the graphical interface they're identical).  But if you start a thread about it or search amazon.com for 'ubuntu' or 'kubuntu', you should get some useful information.

---

