---
title: "3G Wireless Dongle"
date: 2010-04-12
forum: Hardware
---

### Post by Ciwan on 2010-04-12
Hello Guys

I have just installed Ubuntu for a friend of mine who got fed up with Windows because of all the Viruses ..etc

Anyways, he now has no internet because his [SIZE="4"]**3G Wireless Dongle**[/size] doesn't work with Ubuntu !!

The Model is [ **[SIZE="4"]HUAWEI E122[/SIZE]** ]. What can we do to get his Wireless Internet Working ?

**We'd appreciate any help**.

Thank You.

---

### Post by 2hot6ft2 on 2010-04-12
I don't know if it will help any but I saw this post a while back that was interesting.
> **fheinsen said:**
> I have the same mobile broadband modem and use it regularly without any problems. 

The Verizon UMW190 is a so called "global ready" 3G modem, meaning that it connects to both CDMA and GSM networks.  Alas, Ubuntu 9.10's Network Manager currently identifies this modem as GSM only, so until this gets fixed, connecting over a CDMA network (such as Verizon's network in the US) requires that you use an additional application.

Install gnome-ppp -- this is the application you will use to connect, and do the following:

**Step 1.** Plug the modem in on a freshly restarted computer.
**Step 2.** Launch gnome-ppp as superuser (e.g., press Alt-F2 and type "gksu gnome-ppp"), and configure the following settings:
 
[LIST]
[*]Modem Tab
[LIST]
[*]Device: /dev/ttyACM0
[*]Type: USB Modem
[*]Speed: 460800
[*]Phone Line: Tone
[*]Volume: Off
[/LIST]
 
[/LIST]
 
[LIST]
[*]Options Tab
[LIST]
[*]Minimize: checked
[*]Dock in Notification Area: checked
[/LIST]
 
[/LIST]
 Click Close.  Fill in the fields in the main Gnome PPP window:
 
[LIST]
[*]Username: _1234567890@vzw3g.com_
[*]Password: vzw
[*]Phone Number: #777
[/LIST]
 **Step 3.** Click Connect.  That should be it.


To disconnect, click on the gnome-ppp dock notification icon.

(Hat tip: [http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/](http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/))
If nothing else it may help you figure the problem out.

---

### Post by kwatson512 on 2010-04-14
I just got a Verizon UMB190 USB modem for those occasions when wired and wifi aren't available.  I configured it under Windows and it works just fine there.  I can't get it to work under Linux (my preferred OS).

I added a Mobile Broadband connection in Network Manager, with the following entries:
  Number:  #777
  Username:  <devicephonenumber>@vzw3g.com
  Password:  vzw

The only thing that happens when I plug the device in is that it mounts the imbedded drive that has the Windows VZAccess Manager software.  NM does not recognize the modem.

I started to install gnome-ppp until I saw that it was going to also uninstall resolvconf.  I'm a little gun-shy about messing up Network Manager, which I need for all my other connections (wired, wifi).  I only need the UMW190 when nothing else is available.  I'm running Linux Mint 8 Helena (based on Ubuntu 9.10 Jaunty) and NM 0.7.998 from the PPC repository, on a Lenovo Thinkpad x200.

I had a Verizon AC595 that worked perfectly with NM on my old computer (Thinkpad X61s), but I can't get this USB modem to work under Linux.  Unfortunately it was a full PC card, and the x200 doesn't have a PC slot (just a PC Express, plus 3 USBs).

---

### Post by crlang13 on 2010-04-14
I've read various reports on huwaie modems.  Some just work when you plug them in, some are a little trickier.

The trickier ones seem to come down to the fact that they are both a modem and a USB storage device.  Ubuntu only sees them as a storage device.  I've seen a few threads in this forum on changing the default setting of the modem.  I can't find any at the moment, but I think that that is the direction you want to take.

Goodluck.

---

