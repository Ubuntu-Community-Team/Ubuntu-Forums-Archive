---
title: "Ubuntu on EP121 Touch screen problem"
date: 2011-02-16
forum: Hardware
---

### Post by eugenet on 2011-02-16
Hi there,

I just got myself an Asus EP121 tablet PC ([http://promos.asus.com/US/ASUS_EeeSlate/index.htm](http://promos.asus.com/US/ASUS_EeeSlate/index.htm)) and put Ubuntu 10.10 on it :)
All works quite well out of the box, except for the touch screen :/
The wacom digitizer works perfectly there, but the eGalax finger touch does not, no matter what I do.
So far I followed every single tutorial I could find on the web with eGalax in it's name, but no luck anywhere. The most I achieved is I managed to make the touch screen work like a mousepad, meaning that the touch coordinates are not absolute, but relative :/ and I have no touch click (not to mention multitouch).
The xinput list call the device like so:
eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller id=15

lsusb shows this:
oeef:a001 D-WAV Scientific Co., Ltd

so far I tried to get eGalax driver from the website and installed it, but once activated the driver does nothing as it can not find the device :?

I tried simple evdev, then it works as regular touchpade with relative coordinates. Xorg log says that it finds it (event8) to have absolute axes, and registers as absolute touchpad, but it still behaves as a relative one :/
xorg also finds it as a mouse8, but initializing svdev on it resilts in an error, so I disabled it.

Also, I had to disable the synaptics detection because using synaptics driver with this device results in it registering mouse wheel scroll at all times :O making the desktop unusable :/

Does anyone have one experience with eGalax, and behavior like that.

---

