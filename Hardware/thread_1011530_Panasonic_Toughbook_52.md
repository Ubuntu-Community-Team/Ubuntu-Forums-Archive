---
title: "Panasonic Toughbook 52"
date: 2008-12-14
forum: Hardware
---

### Post by pigphish on 2008-12-14
This thread is to document and discuss setting up Ubuntu on a Panasonic Toughbook 52 or CF-52. 

The major hardware on my laptop was:
- Intel® Core&#8482; 2 Duo Processor P8400 2.26GHz
- 1024MB SDRAM (DDR2) standard, 
- 15.4" 1200x800(WXGA) TFT 
- Intel® GMA 4500MHD video controller
- Teac Optical DVD Super MULTI Drive      
- Bluetooth® v2.0+EDR (Class 1)
- Intel® Wireless WiFi Link 5100 802.11a/b/g/draft-n

Successfully tested the toughbook 52 (cf-52) with Ubuntu 10.04. A few configuration kinks are noted below. No special boot options were used.

Hibernation and Sleep also are successful.

Graphics: The default resolution (1024×768) worked but changed the resolution settings to get a higher resolution (1280×800).
  Goto System Menu&#8594;Preferences&#8594;Monitors

My device in xorg.conf is: 
sudo gedit /etc/X11/xorg.conf

Section "Device"
    Identifier    "Configured Video Device"
    Option "AccelMethod" "uxa"
    Option "Tiling" "true"
EndSection

glxgears shows fps over 2200. Keep in mind that processor stepping affects this number as well.

Sound: Sound worked. However, the hardware buttons, fn-F4,fn-f5,fn-f6 have visual queues but do not work. Oddly, have to make sure the windows side has sound enabled for it to work with ubuntu on reboot. 

The headphones did not turn off the speakers. I seem to need to change them manually in sound preferences. 

sudo gedit /etc/modprobe.d/alsa-base.conf

... added to end of file

options snd-hda-intel  model=panasonic

After reboot both speaker, microphone jack, and headphone jack correctly worked. (still no jack sensing though)

Any other changes people found useful?

Also see [http://www.linlap.com/wiki/panasonic+toughbook+52](http://www.linlap.com/wiki/panasonic+toughbook+52)

---

### Post by rwslippey on 2010-07-14
I also have the toughbook cf-52 here and can't seem to get the sound working.... I can't recall if I had it working in 9.10 or not.... Yes, back then I was a dual booter, but just whiped everything out this week and reinstalled single boot......

The volume buttons seem to work,(visualy anyway, however I can't get any sound at all out of the system.

Also I can't dimm the display with the keyboard buttons, which for the most part isn't a big issue, as long as I can find another way to dim the display...

any ideas on the sound issue?

Thanks 

Rob

---

