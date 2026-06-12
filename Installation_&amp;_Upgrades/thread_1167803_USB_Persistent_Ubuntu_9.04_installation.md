---
title: "USB Persistent Ubuntu 9.04 installation"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by stSpringer2003 on 2009-05-23
I followed instructions on this link

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

My System:

OS:Windows XP Pro 32 bit, SP 3
Motherboard: Intel  D975XBX2
CPU: Intel Core 2 Quad Q6600 Processor 2.40GHz OEM 
GPU: 512MB GDDR3, PCI Express, EVGA GeForce 9600 GTS 
Ram: 2 gigs BL 2KIT 12864AL663 2GB kit (1GBx2), Ballistix Tracer 240-pin DIMM 
Power Supply:PC Power & Cooling Silencer 750 Quad (Crossfire Edition) EPS12V 750W Power Supply 

I set my bios to boot off the USB first then my internal Hard drive and I get this message 

**_boot error_**

and pc stops, when I hit enter it boots into win XP ok

Please advise. I am new to Ubuntu

Thanks

---

### Post by shel-hall on 2009-05-23
> **stSpringer2003 said:**
> I followed instructions on this link

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)
{snip}
I set my bios to boot off the USB first then my internal Hard drive and I get this message 

**_boot error_**

and pc stops....
I had that problem.  I reformatted the USB key using Sandisk's U3 removal program, which cleaned up the "autostart" or "smartstart" or whatever crapola Sandisk installed on the USB key.  I believe the program I used is at [http://www.sandisk.com/Assets/u3/launchpadremoval.exe](http://www.sandisk.com/Assets/u3/launchpadremoval.exe) ... it's a Windows program, natch.  I've used that program on other USB keys to reformat them, too; it doesn't seem tied to either Sandisk or U3.

After I reformatted the USB key and re-installed Ubuntu on it, I got no more "boot error" and it worked swimmingly.

-Shel

---

### Post by stSpringer2003 on 2009-05-24
> **shel-hall said:**
> I had that problem.  I reformatted the USB key using Sandisk's U3 removal program, which cleaned up the "autostart" or "smartstart" or whatever crapola Sandisk installed on the USB key.  I believe the program I used is at [http://www.sandisk.com/Assets/u3/launchpadremoval.exe](http://www.sandisk.com/Assets/u3/launchpadremoval.exe) ... it's a Windows program, natch.  I've used that program on other USB keys to reformat them, too; it doesn't seem tied to either Sandisk or U3.

After I reformatted the USB key and re-installed Ubuntu on it, I got no more "boot error" and it worked swimmingly.

-Shel


I'll give it a try, Thanks

---

### Post by stSpringer2003 on 2009-05-24
Sandisk's U3 removal program didn't like my USB. So I formatted my USB in Windows and reinstalled running the .bat file and no go
I get Boot Error msg same as before.Nuts!

---

### Post by TheShabz on 2009-08-26
did you download the iso yourself? it could be as simple as having a bad iso. (re)download the iso and try again. 

also, the directions on pendrivelinux need the usb stick to be formatted with FAT32. there is an option of FAT16. make sure its FAT32 as well.

---

