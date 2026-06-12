---
title: "bluetooth annoyance"
date: 2009-11-27
forum: Hardware
---

### Post by Frank Golden on 2009-11-27
Hi folks, been experimenting with Karmic the last few days an I have encountered an annoying problem common to both Karmic and Jaunty.

 First some background I have an Acer Aspire WLMi notebook (see my sig for indepth specs). 
It has a manual switch to shut off the bluetooth module on the front edge of the computer with a wi-fi disconnect switch next to it.
 
Both switches are slide switches of the momentary type. By that I mean to toggle between states you slide the spring loaded switch to the right and release.
A blue LED in the middle of the switch indicates on.
 
I multi boot this machine with Win 7 RC and XP-SP3 as well as Ubuntu intrepid 64 and Hardy Ultimate 64. I have not experienced this problem with these two earlier versions of Ubuntu.

 I have a large external USB drive that has 6 different versions
of Ubuntu installed on it (all the upgradable versions from Dapper to Karmic).
 
I can boot to these individual releases using my menu.lst from my Intrepid install on my main drive.
This menu.lst is a custom file that lets me boot everything on my main drive (Win 7 and XP as well) and my external drive as long as it's plugged in and running when I boot the machine.
 
Ok enough background. Both Karmic and Jaunty have a "feature" that turn on the bluetooth and wi-fi hardware, regardless of whether the switches are positioned off in Windows.
 
I don't use either bluetooth or wi-fi in Windows or any of the other OS's.
 
The truly annoying thing about this is if I forget to use the hardware switch to shut off bluetooth before shutting down  Karmic/Jaunty it causes a problem with Win 7.

 If the bluetooth activation light is lit when I boot Win 7
it breaks the "safely remove hardware" app that has an icon in the system tray when I plug in a USB storage device.
 
By "breaking" I mean that clicking on the tray icon to safely remove a USB storage device does absolutly nothing.
 
The only way to safely remove such a device is to shutdown the computer.
 
 The only way to restore the utility's function is to reboot and use the front panel switch to shut off bluetooth before rebooting. 
 
 I've googled extensively for a way to prevent Karmic from turning on bluetooth at startup and tried several methods suggested to no avail. I've even uninstalled "bluez" with no effect. The blue light is on after every Karmic reboot.
I need to stop this behavior in  Karmic\Jaunty. 
Very annoying behavior indeed. 

 This was not a problem in Intrepid and earlier. Any help or suggestions will be appreciated.

Thanks.

---

### Post by Frank Golden on 2009-11-27
bump

---

