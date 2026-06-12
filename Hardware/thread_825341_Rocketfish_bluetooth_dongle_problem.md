---
title: "Rocketfish bluetooth dongle problem"
date: 2008-06-10
forum: Hardware
---

### Post by ectospasm on 2008-06-10
I've got a problem with my Rocketfish Bluetooth dongle.  It sorta works... the keyboard works, and the mouse (mostly) works.  But for some reason, the dongle does not show up as a Bluetooth device.  This dongle and keyboard/mouse combo worked well on my laptop, when following instructions from this thread:  [http://ubuntuforums.org/showthread.php?t=355695](http://ubuntuforums.org/showthread.php?t=355695)

I'm having the same problem on this new machine (the scroll wheel on the mouse doesn't work), but "sudo hciconfig hci0 reset" doesn't work because the device hci0 doesn't exist.  Both the laptop and this new machine are running Hardy Heron, so I wouldn't think it's the OS.  

I've tried turning on and off legacy USB support in this machine's BIOS, but that hasn't worked.  Any ideas?

---

### Post by slayr007 on 2009-04-19
buy a new dongle.

---

### Post by foxmajik on 2009-05-28
> **ectospasm said:**
> I've got a problem with my Rocketfish Bluetooth dongle.  It sorta works... the keyboard works, and the mouse (mostly) works.  But for some reason, the dongle does not show up as a Bluetooth device.  This dongle and keyboard/mouse combo worked well on my laptop, when following instructions from this thread:  [http://ubuntuforums.org/showthread.php?t=355695](http://ubuntuforums.org/showthread.php?t=355695)

I'm having the same problem on this new machine (the scroll wheel on the mouse doesn't work), but "sudo hciconfig hci0 reset" doesn't work because the device hci0 doesn't exist.  Both the laptop and this new machine are running Hardy Heron, so I wouldn't think it's the OS.  

I've tried turning on and off legacy USB support in this machine's BIOS, but that hasn't worked.  Any ideas?


Here is how to fix the problem:

1. Download and install Blueman.  When you install the package it will automatically replace bluez-gnome.

*[https://launchpad.net/blueman](https://launchpad.net/blueman)*

2. Download and install the bluez-broadcom firmware.

*[http://www.t2-project.org/packages/bluez-firmware.html](http://www.t2-project.org/packages/bluez-firmware.html)*

The instructions on how to install the firmware are included in the INSTALL file inside the archive.

3. Kill any running instances of Blueman daemon:

```
sudo killall blueman-manager
```

4. Restart Blueman daemon:

```
sudo blueman-manager
```

Like magic, Bluetooth now works.

**More information:**
The Bluefish bluetooth dongle uses a Broadcomm chipset whose firmware must be loaded every time the device is plugged in because it doesn't have its own firmware onboard.

With these instructions you are copying the firmware files into /lib/firmware so that Blueman can find them and load them onto the dongle.

I hope this helps.

---

### Post by Mr. Frog on 2009-06-26
Thanks for your help!
I am now able to tether my iPhone (no AT&T over here!) with the usb Rocketfish bluetooth adapter I bought for my work laptop (that has no builtin bluetooth).

But, hmm, wouldn't be usefull to have blueman-manager and the bluez-firmware included in Ubuntu base tree without having to do all this? blueman-manager seems to be working better than the original bluetooth manager included with gnome/ubuntu.

Cedric

---

### Post by ectospasm on 2009-07-05
> **foxmajik said:**
> Here is how to fix the problem:

1. Download and install Blueman.  When you install the package it will automatically replace bluez-gnome.

*[https://launchpad.net/blueman](https://launchpad.net/blueman)*

2. Download and install the bluez-broadcom firmware.

*[http://www.t2-project.org/packages/bluez-firmware.html](http://www.t2-project.org/packages/bluez-firmware.html)*

The instructions on how to install the firmware are included in the INSTALL file inside the archive.

3. Kill any running instances of Blueman daemon:

```
sudo killall blueman-manager
```

4. Restart Blueman daemon:

```
sudo blueman-manager
```

Like magic, Bluetooth now works.

**More information:**
The Bluefish bluetooth dongle uses a Broadcomm chipset whose firmware must be loaded every time the device is plugged in because it doesn't have its own firmware onboard.

With these instructions you are copying the firmware files into /lib/firmware so that Blueman can find them and load them onto the dongle.

I hope this helps.

This does not work in Jaunty.  I followed the steps, and it's still not loading the firmware for this crappy Bluetooth dongle.  Besides, blueman-manager is a GUI program, and only tangentially affects the underlying firmware.  It does not work unless the firmware is loaded already, as far as I can tell.  Got any other ideas?

---

### Post by DaJL on 2009-07-06
Same problem here in jaunty. I also tried with the bluez and bluez-utils from karmic and its still no go for the scrollwheel and multimedia buttons.

---

### Post by sgilbert on 2009-08-03
I've got the wheel working in Jaunty with latest kernel (2.6.30.4).  I've used KernelCheck to update to latest kernel.  But, I don't know about multimedia key.

My current problem is that my keyboard seems to disconnect after a while and I have to register it again and enter the PIN.  Maybe I'll have a try with Blueman.

---

### Post by jstalnak on 2009-08-29
For reference (my own) and the edification of other folks who may have little luck with the various other remedies proffered, this link fixed my reluctant Jaunty/rocketfish dongle:

[http://www.shotmentality.com/content/bgoines78/rocketfishbroadcom_bluetooth_adapter_linuxubuntu](http://www.shotmentality.com/content/bgoines78/rocketfishbroadcom_bluetooth_adapter_linuxubuntu)

---

### Post by akshunj on 2009-08-30
> **jstalnak said:**
> For reference (my own) and the edification of other folks who may have little luck with the various other remedies proffered, this link fixed my reluctant Jaunty/rocketfish dongle:

[http://www.shotmentality.com/content/bgoines78/rocketfishbroadcom_bluetooth_adapter_linuxubuntu](http://www.shotmentality.com/content/bgoines78/rocketfishbroadcom_bluetooth_adapter_linuxubuntu)

This guide works flawlessly. I turned the commands and utility into a script that runs after boot.  But like a previous poster says, the keyboard seems to disconnect after a certain amount of time idle...

--Akshun J

---

