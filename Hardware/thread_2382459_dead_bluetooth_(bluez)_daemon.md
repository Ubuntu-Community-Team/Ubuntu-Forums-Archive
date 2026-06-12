---
title: "dead bluetooth (bluez) daemon"
date: 2018-01-13
forum: Hardware
---

### Post by Alex22 on 2018-01-13
Hello Dears, I have a problem to run my Bluetooth.

Software: Xubuntu 16.04.3 
Hardware: HP ProBook 4540s (Ralink RT3290 Bluetooth)

I cannot start Blueman, and seems that Bluez daemon is dead:
```

olek@olek-probook:~$ sudo /etc/init.d/bluetooth status
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:bluetoothd(8)
```

I tried purging and reinstalling bluez and only at the first time i could start BT via systray icon.

Could anybody help to resolve this please?

---

### Post by jeremy31 on 2018-01-13
I don't know if this will work but it could be tried
```
sudo add-apt-repository ppa:blaze/rtbth-dkms
sudo apt-get update
sudo apt-get install rtbth-dkms
```
Reboot

The big issue is that the bluetooth chipset is not really supported in the kernel because the manufacturer didn't want to release the source code

---

### Post by Alex22 on 2018-01-13
Hello Jeremy, thanks for your interest.
Unfortunately merging this module in didn't help.

I see, got the situation...

---

