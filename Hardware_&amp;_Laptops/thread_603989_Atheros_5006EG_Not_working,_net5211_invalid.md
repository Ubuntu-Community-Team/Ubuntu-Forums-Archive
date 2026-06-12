---
title: "Atheros 5006EG Not working, net5211 invalid?"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by adam206 on 2007-11-05
Hey all, new to Ubuntu as of last night. I have a Toshiba Satellite U300 with an Atheros 5006EG wlan card. I was having the same problem: the device manager does recognize the wireless card, but wireless connection does not show up on network options. I installed ndiswrapper and ndisgtk, and got the net5211.inf driver. But when I add it to the wireless network drivers it says "invalid Driver", and upon restarting has no effect. I have disabled the restricted driver (Atheros Hardware Access Layer (HAL)), but in restricted drivers it still lists it as 'in use'.

Any suggestions on where I can go from here to get the wireless working? Im very limited in the command prompt but im learning, and desparate. Thanks All!

---

### Post by icaris13 on 2007-12-29
Hey, I'm having a similar problem and have been frantically searching around for a solution (and unfortunately haven't found one).  Have you tried blacklisting ath_pci and ath_hal?  Also, how did you add the net5211.inf driver to the wireless network drivers?

---

### Post by icaris13 on 2007-12-31
I GOT IT TO WORK!!!!   Make sure to blacklist the old drivers after you install net5211.inf This is done by typing the following code into the terminal:

sudo gedit /etc/modprobe.d/blacklist
<you'll probably be prompted for your password here>
a screen will pop up and at the very bottom add these lines:

blacklist ath_pci
blacklist ath_hal

reboot and it should work (it did for me)

This is all assuming you've already installed ndiswrapper and used it to install the windows driver.

---

### Post by Fir3chi3f on 2007-12-31
Sort of the same problem here. 

Mine does not say invalid it doesn't tell me anything

I have the same wireless card

Here is the tut i used:
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

Others that I've tried: [http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf)

Here is my /etc/modprobe.d/blacklist: 

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist ath_pci
blacklist ath_hal
```

Here is my ndiswrapper -l :

```
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.
```

Last but not lest I am running 64bit Gutsy

Any other suggestions are appreciated or methods of testing

---

