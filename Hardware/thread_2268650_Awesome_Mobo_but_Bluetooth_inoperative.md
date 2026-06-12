---
title: "Awesome Mobo but Bluetooth inoperative"
date: 2015-03-10
forum: Hardware
---

### Post by jcllings on 2015-03-10
So I have this awesome ASUS Z87 Delux Mobo and everything works on it except the Bluetooth. lspci shows no references to bluetooth but I get:
```

dmesg | grep blue
[    9.255443] init: bluetooth-touch main process (738) terminated with status 127

```

The above seems likley the result of my fiddling around. I don't know if it's related but probably not. 
Perhaps I'm just missing a package? I have: 

```
dpkg --get-selections | grep -v deinstall | grep blue
bluez                        install
bluez-alsa:amd64                install
bluez-cups                    install
bluez-gstreamer                    install
gir1.2-gnomebluetooth-1.0            install
gnome-bluetooth                    install
indicator-bluetooth                install
libbluetooth3:amd64                install
libgnome-bluetooth11                install
pulseaudio-module-bluetooth            install

```

Also: 

```
 rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Any ideas or futher investigative steps I can do? I've verified that it is enabled in the BIOS.

---

### Post by jcllings on 2015-03-10
OK reading that I've been doing suggests that I might have to wait for the next kernel release.  The ASUS Z87 Pro seems to have an identical problem.

---

### Post by weatherman2 on 2015-03-10
While you are waiting for a fix, if you really need bluetooth of some sort, you can buy cheap USB mini-dongles (very small) on eBay or Amazon, sometimes for $1 USD shipped.  I have a few of these.  They work automatically in Ubuntu.  Range may not be great but they have worked for me for years.

---

### Post by jeremy31 on 2015-03-11
A lot of bluetooth devices are listed in ```
lsusb
``` even when you have a wifi/bt card in a pci slot

---

