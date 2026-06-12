---
title: "Samsung ATI headache"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by zoomcookieuk on 2007-09-14
Hi Everyone,

I hope someone can help me. On my old laptop (a Toshiba Satellite M30) I dual booted Win XP and Ubuntu. For me this was an ideal setup. My Linux command line experience and knowledge is  virtually zero. I was enjoying using Gnome with Ubuntu. It was such a breath of fresh air after Windows, especially not having to worry about viruses etc and getting loads of new software for free. 

Unfortunately my Toshiba died so I bought a new Samsung R20 which came with Vista. I immediately partitioned the disk and tried to set up a dual boot configuration. This is where my plan fell apart. None of my Linux discs worked, including live cd's. This seems to be due to the ATI Radeon Xpress 1250 graphics chip in the laptop. After Ubuntu wouldn't work I tried Fedora. I managed to get it installed but X would not start. Following some online help I managed to get Gnome running but before long Fedora started behaving strangely. It would take forever to boot, requiring lots of key presses to get it to eventually finish booting. 

I decided to have another go at Ubuntu having read about using the alternate CD and text install. After all the above waffling here is my question:

Could someone please provide a step by step guide to install a working graphics driver etc from the command line. The trouble is many guides say download driver, then do this etc, or they might say update kernel to a new version before you start but I don't know how to download or do anything from the command line. I don't know where to start.

I know there are many posts on this subject but I am yet to find a very clear, step by step, hand holding guide for complete noobs like me. 

I am on the verge of giving up on Linux on this laptop. I don't want to as Vista is so slow at times, expecially when copying or deleting files. I suppose I could use linux in Vista using VirtualBox or similar.

Thank you in advance for any help received.

Cheers
Rich

---

### Post by eggdeng on 2007-09-14
Try [http://ubuntuforums.org/showthread.php?t=321766]("http://ubuntuforums.org/showthread.php?t=321766") For now, you don't need to understand what you are doing, just copy and paste.

---

### Post by zoomcookieuk on 2007-09-14
Thanks for the reply but unless I am mistaken this is exactly the sort of post I don't know how to make use of.

I cannot get to any desktop at all. I am stuck at the command line. I don't know how to do the following from there:

"Right now just activate all options in the repositories, do a update in System -> Administration -> Update Manager, go to System -> Administration ->Restricted Drivers Manager and activate ATI driver"

and also I do not know how to download the driver while at the command line. I could download it in vista and copy to memory stick but then I don't know how to access the stick from the command line in Linux. 

I apologise if this seems so easy to you all and I am being a bit slow. 

Thanks anyway.

---

### Post by eggdeng on 2007-09-14
> I am stuck at the command line
OK, this is a good place to start. You need to edit a configuration file called xorg.conf but first,  back it up just in case. The commands are sensitive to things like whitespace and case.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
```
Now open the file in a command-line text editor called nano
```
sudo nano /etc/X11/xorg.conf
```
Find a line which reads 
```
Driver   "fglrx" 
```or 
```
Driver "ati" 
```or 
```
Driver "Radeon"
```
Replace it with 
```
Driver   "vesa"
```
Press Ctrl+x to exit
Press Shift+Y to save
Press Intro.
What we are doing is telling the graphics system to use a generic driver (vesa) rather than ati-specific Drivers.
Now type ```
startx
```
If everything is going well, you will be able to log on. If not, post again.

---

### Post by zoomcookieuk on 2007-09-14
Hi eggdeng, I could not backup the conf file as it said "missing destination" This would be simple enough but I don't know how to specify a destination.

I looked in the xorg.conf file and it already says "vesa".

When I try to startx it shows:

(EE) VESA(0): No matching modes
(EE) Screen(s) found but none have a usable configuration.

Fatal server error:
no screens found


Does that help at all? 

Thanks again.

---

### Post by eggdeng on 2007-09-15
I've been looking at threads dealing with the Samsung R20 and the X1250 & the record is a bit chequered alright. People seem to have got different drivers working on different versions. Which ubuntu version have you got installed? If you don't know, either
```
cat /etc/issue
``` or
```
lsb_release -a
```
should tell you.
Also post the output of ```
uname -a
``` This will tell us your kernel version.
Is ubuntu recognising your card? Can you see it in the output of
```
lspci
```
Check xorg.conf again. You may have two entries of the type ```
Driver  " xyz"
``` If so, edit the second one. If not, try replacing ```
Driver   "vesa"
``` with ```
Driver "ati"
``` This is the open source driver for ati cards which comes bundled with ubuntu as distinct from fglrx, the closed-source proprietary driver distributed by ATI.

---

### Post by zoomcookieuk on 2007-09-15
The details requested are as follows:

Ubuntu 7.04

Linux Ubuntu 2.6.20-15-generic #2 SMP


lspci gives lots of lines referring to ATI such as:

00:00., Host bridge: ATI Technologies Inc Unknown Device 7930

USB Controller: ATI Technologies Inc SB600 USB

the VGA line is:

VGA Compatible Controller: ATI Technologies Inc Unknown Device 7942


I check the conf file and changed vesa to ati but still doesn't work

Does the above help?

Thanks for your time and effort on this.

---

### Post by eggdeng on 2007-09-15
The card is not being detected correctly. ```
lspci
``` should identify the model. Can you run ```
update_pciids
``` & then run ```
lspci
``` again. I suppose you have not been able to get to a gui booting in recovery mode.

---

### Post by eggdeng on 2007-09-15
If none of the above work, you will have to go for a reinstall. From the posts I have read, it sems to be important that you install in text mode (so that the installer doesn't try to configure your graphics), which means downloading the alternate install CD. 
Hopefully, you will then be able to boot to a GUI in recovery mode and download the latest ATI drivers (fglrx) from [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) If you can't get to a  GUI, you can download them on another machine, copy them over using a pen drive and install in text mode.
There are detailed installation instructions at [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.40.4-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.40.4-inst.html)
and you will always find help on the forums You could also post on this thread [http://ubuntuforums.org/showthread.php?t=396751](http://ubuntuforums.org/showthread.php?t=396751) as a lot of these guys are using the same card / same computer as you.

---

### Post by fodder on 2007-09-19
I assume you have a working internet connection on this machine? If so then do the following:

```
sudo aptitude install xorg-driver-fglrx
```
Then
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nano /etc/X11/xorg.conf
```
Find a section which looks like
```
Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "vesa"
EndSection
```
and change the driver line to "Driver  "fglrx"". Ctrl+X, y, enter to save and quit. Now 
```
sudo startx
```
should work.

---

### Post by Nikos.Alexandris on 2007-10-07
[https://wiki.ubuntu.com/LaptopTestingTeam/SamsungR20?highlight=%28samsung%29](https://wiki.ubuntu.com/LaptopTestingTeam/SamsungR20?highlight=%28samsung%29)

---

