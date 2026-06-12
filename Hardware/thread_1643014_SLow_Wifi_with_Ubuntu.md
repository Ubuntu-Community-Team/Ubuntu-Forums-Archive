---
title: "SLow Wifi with Ubuntu"
date: 2010-12-11
forum: Hardware
---

### Post by linuxuser2424 on 2010-12-11
Hello Everybody,I have Problem with MY wifi PCi RT61,it is very slow even in Windows but when i use my wireless Usb Linksys WUSB54GC ,it's fast in windows but not in ubuntu.i was thinking that my wireless Pci is conflict with my Gpu ( see Pic ) 

thank you every body

---

### Post by WinRiddance on 2010-12-11
No, your wireless PCI has nothing at all to do with that. Sometimes WiFi is an issue on some Ubuntu systems. Often it's helpful to either upgrade your version of Ubuntu if you're using 9.04 or below, or perhaps downgrade to 10.04 if you're running the latest 10.10 version of Ubuntu.

Another thing that you can do is to go to SYSTEM then ADMINISTRATION, followed by clicking on HARDWARE DRIVERS to see if more upated WiFi or Graphics drivers are available for your system.

Finally, another easy thing to do, is to install the WICD Network Manager (available from the Ubuntu Software Center), _followed by_ **disabling** the standard network manager in your startup items (not to be confused with actually removing the network manager). If you install WICD or any of the hardware driver upgrades you should restart your system afterwards. **Good luck!** ;)

---

### Post by linuxuser2424 on 2010-12-11
thank you for the fast reply ,btw i am using ubuntu 10.10 64 bit and 10.4 is somehow buggy.i installed WICD and it's very good Gui Network manager but still slow with Pci :(,also i was trying to install usb wireless driver by ndiswrapper but it's showing me installed and present but nothing at network manager

anyway thanks :D

---

### Post by WinRiddance on 2010-12-11
Well, if you've been playing around with different network or WiFi managers there's always a possibility that you're experiencing some kind of a conflict which is exactly why it is so important to have only one network manager running at a time. In the past I've experienced exactly the problems that you're describing with Ubuntu and that was my problem at that time ... conflicting settings between the network adapters. Another weird thing that I've experienced in the past, several times actually, is a very sluggish network performance after installing or upgrading Ubuntu, apparently due to the fact that Ubuntu had problems detecting all of the correct settings for my particular WiFi adapter. Hard wiring the connection by switching to an ethernet cable solved this instantly. Another solution that I've seen more than once was to plug in a USB network adapter which was recognized properly almost immediately. Then, within hours, I'd be able to disconnect the USB network adapter followed by using my regular WiFi adapter thereafter ... and the speed issues were resolved.
Yeah, I know, it's weird, what can I say ... :o

The first thing to do IMO is to always check for the latest hardware drivers after a clean installation or an Ubuntu upgrade. Also, you posted this problem under Laptops & Hardware, but you might actually be better off taking a look and/or starting another thread [here, in the Networking & Wireless section]("http://ubuntuforums.org/forumdisplay.php?f=336") of the Ubuntu forums. I think messing around with ndiswrapper is only as a last resort. I don't know enough about network adapters but perhaps someone else can provide some additional helpful insight ... ???

---

