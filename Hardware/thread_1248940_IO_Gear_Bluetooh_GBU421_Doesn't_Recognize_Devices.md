---
title: "IO Gear Bluetooh GBU421 Doesn't Recognize Devices"
date: 2009-08-24
forum: Hardware
---

### Post by user2037 on 2009-08-24
IO Gear's Bluetooth adapter appears as a mountable disk with the installation software on it. It appears Ubuntu recognizes it as a Bluetooth adapter, but all attempts to recognize other devices fail.

Lsusb with "-v" produced:
```

idVendor 0x0a5c Broadcom Corp.
idProduct 0x2148
iProduct BCM92046DG-CL1ROM

```

---

### Post by black_rob on 2009-08-28
I just bought a BT dongle for my netbook, an Asus usb-bt21, it has the same chip and lsusb gives the same output as it did for you.  

I tried to get it to work on a crunchbang install and had the same problem you had, but then I booted into my other partition where I'm testing out moblin, and it works great.  Moblin is pre-beta quality right now, and I didn't see any gui app for setting up bluetooth devices installed, but from the command line:

"hcitool dev" correctly identified my bluetooth dongle
"hcitool scan" found my bluetooth mouse
and "hidd --connect" followed by the mouse's address started it right up

I don't have time to look into it right now, but I do want to get it working in crunchbang, so I'm going to look into it.  Moblin uses a newer kernel, so perhaps something changed in the driver, or maybe it has a newer version of some utility.  

But take heart, your device does work under Linux!

---

### Post by ConanTheBarbarian on 2009-08-31
I suffer the same issue with the GBU421.  I did a little poking around on launchpad, looks like if you manually reset hciconfig it brings the adapter to life.  I was able to pair my MS Noetbook 5000 mouse and my Samsung SCH-i760 with it on 9.04.  Give this a shot ```
sudo hciconfig hci0 reset
```  You may have to restart bluetooth as well, but I was able to get it going just fine with this one command.  Check out the bug page for more info. 

 [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/133690](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/133690)

---

### Post by narnie on 2009-09-07
This solved the problem for me on my Toshiba Satellite A505-S6965 laptop and IO Gear dongle that uses the same chipset.

Thanks so much for posting the fix.

Yours,
Narnie

---

### Post by HeresJohnny on 2009-09-08
Thanks, Conan, I am happy to report this worked for me right off the bat.  I've followed the discussion on the Launchpad site, and I'll wait a bit before adding any lines to my bluetooth file.  For now, I'm happy to use this one line.  Awesome work!

---

### Post by user2037 on 2009-09-11
```

sudo hciconfig hci0 down
sudo hciconfig hci0 up

```

Down and up worked. Perhaps adding it to "/etc/init.d/bluetooth" before "exit 0" will help.

---

### Post by deerelk4x4 on 2010-10-05
I am having problems getting my GBU421 not being recognized.  I am using Kubuntu 10.04.  lsusb identifies the device but hciconfig will not return any recognition of the device.  I have tried uninstalling kbluetooth and reinstalling it, and gnome-bluetooth doesn't recognize it device either.  Any help would be greatly appreciated.

---

