---
title: "MS Bluetooth adapter"
date: 2008-11-18
forum: General Help
---

### Post by jcoolkatzerg on 2008-11-18
I have finally gotten Vista and Ubuntu to play nicely with each other, however, I am having issues with ubuntu and my bluetooth adapter.  It is the same one that comes with the MS wireless entertainment keyboard and mouse 8000.  Even in the live CD, the mouse works fine, but the keyboard does not (however, in vista everything is ok).  I believe that this is because Ubuntu does not recognise the MS adapter as a bluetooth device.  Here is the output from lsusb:

```
Bus 002 Device 004: ID 046e:5500 Behavior Tech. Computer Corp. (a backup usb keyboard I have to type this)
Bus 002 Device 002: ID 045e:070c Microsoft Corp. (the charging hub that came with the mouse/keyboard)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 045e:0714 Microsoft Corp. (I think these next three are all dealing with the adapter)
Bus 001 Device 004: ID 045e:0715 Microsoft Corp. 
Bus 001 Device 003: ID 045e:0707 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

And this is the output from hcitool dev
```
Devices:

```

and hcitool scan

```
Device is not available: No such device

```

Gnome-bluetooth reports that there are no bluetooth adapters present.  Some of the posts I read before this suggested moving the adapter from the hub to a port on the back, and I have tried every port, and it still doesn't work.

I also when into my bios settings and check that both PnP OS and USB keyboard were enabled and working

I am at a loss as to what to do next.  Everything works fine in Vista, and I can even pair other bluetooth devices with this adapter, such as my PDA.  But nothing in ubuntu except the mouse.  Any suggestions from the really helpful ubuntu community?

Ubuntu 8.10 x86_64

---

### Post by Crafty Kisses on 2008-11-18
Try the following:
```
sudo hciconfig hci0 reset
```
Then see if that gets you back up and running.

---

### Post by jcoolkatzerg on 2008-11-18
Here is what is returned:

```
Can't get device info: No such device
```

---

### Post by jcoolkatzerg on 2008-11-19
*bump*

---

### Post by dgaretz on 2008-12-23
I am having the exact same problem with the exact same hardware. Still searching for a solution.

---

### Post by fragos on 2008-12-23
I believe some bluetooth dongles aren't ssupported by the Linux drivers. You may find this compatibility list helpful.

[http://www.qbik.ch/usb/devices/search_res.php?pattern=bluetooth](http://www.qbik.ch/usb/devices/search_res.php?pattern=bluetooth)

I've a TRENDnet BT dongle that works well with 8.10 and previous releases. Your MS devices should wwork with an alternate dongle if your MS dongle isn't supported.

---

### Post by dgaretz on 2008-12-25
Hey, OK well this might sound odd but my keyboard and mouse work. I was trying to use it with xubuntu 8.10 on my Eee and I didnt try to see if my keyboard and mouse actually worked, I was attempting to use the dongle to connect bluetooth headphones. However I didnt try to see if either the keyboard or mouse worked, I just assumed they wouldn't. 

On my regular Ubuntu 8.10 on my desktop the keyboard and mouse work flawlessly, however the problem still exists. Ubuntu doesnt seem to recognize the device, yet the mouse and keyboard work. As I am typing this now I have been able to turn off the mouse and turn it back on successfully. I will test the keyboard after this post and report back. 

However, even though the keyboard/mouse works I would still like to be able to get the dongle recognised and working so I can connect other bluetooth devices (phone and headphones). I checked that list and from what I can tell the dongle nor the mouse/keyboard are listed so I dont know. Thanks again ahead of time if anyone can offer any insight on getting the dongle recognised it would be much appreciated. Thanks guys

Edit: Keyboard works.

---

### Post by fragos on 2008-12-26
Bluetooth headsets use a special protocol. You'll need to install bluez-btsco aand perhaps bluez-audio. Bluetooth headset works for me with these installed.

---

### Post by jcoolkatzerg on 2008-12-26
I found an interesting solution to my problem.  When I have a USB keyboard plugged in during boot, my bluetooth adapter will work fine.  However, with the keyboard unplugged during boot, it won't work after boot.  Very odd....

---

### Post by dgaretz on 2008-12-26
> **fragos said:**
> Bluetooth headsets use a special protocol. You'll need to install bluez-btsco aand perhaps bluez-audio. Bluetooth headset works for me with these installed.

Thanks for your input fragos. However neither of these packages will do me any good if I cant even get ubuntu to recognize I have a Bluetooth adaptor. I cannot get to a screen where I can pair the headphones. Besides, I think I actually have these packages installed already. Its possible that Microsoft's bluetooth adaptor just can't support audio, if anyone can confirm these please do so I don't buy another adaptor if I don't need one.

On Windows, I can pair the device but I think the MS drivers are purposely limiting its capabilities. I tried getting Bluesoleil drivers installed but that took me all day and got me nowhere. The bluesoleil drivers don't seem to recognize I have a bluetooth adaptar as well. I tried literally every combination/order to install drivers and no luck. Puts me in a pickle everytime though cuz I dont have another keyboard lol, my old one is TOAST and I had to plug in the adaptar for BIOS/GRUB/Logon (lol) but then unplug it when I actually got back into windows to attempt to install the bluesoleil drivers. My guess is Microsoft is to blame....Its more than often the case.

Anyway, my search attempts have been unsuccessful. I just need ubuntu to recognize the dongle, I can take it from there to get bluez-also and A2DP working and everything, I just need ubuntu to recognize the dongle. Thanks again everyone.

---

### Post by DaveBG on 2010-05-08
I have the exact same issue. Does someone know how to install driver or something that will recognize the blutooth device?

---

