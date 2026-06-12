---
title: "Ignoring Hardware WIFI Button"
date: 2011-01-10
forum: Hardware
---

### Post by Joshua on 2011-01-10
I have a laptop, Averatec 3280, that I'd like to use remotely via a WIFI connection.  It has a button that can be used to enable/disable WIFI, and as far as I can tell, it works properly under any circumstances I've seen.  Unfortunately, WIFI seems to be turned off if there is a power interruption or hard restart.  When this happens, I have to go, physically, to the laptop to press the WIFI button to turn it back on.  Normal shutdowns and restarts return the WIFI setting to it's previous state.  This is inconvenient if I only want to use it remotely.

Does anyone know if there is a way to control that button via software?  Or how I can even start to determine if it's possible?

I have some hope because I believe there were reports years ago that Ubuntu actually ignored that button in the past, but that it was fixed in Karmic:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/435441]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/435441")

Some info about my WIFI:

```
$ sudo lshw
....
        *-network:0
             description: Wireless interface
             product: RT2500 802.11g
             vendor: RaLink
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 01
             serial: 00:11:09:f8:14:37
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt2500pci driverversion=2.6.35-24-generic firmware=N/A ip=192.168.108.30 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
             resources: irq:16 memory:febfe000-febfffff
....
```

rfkill reports the state accurately:

```
$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

But the "Hard blocked" line changes based on using the button and I have not found a way to change that state via Ubuntu software.

Also, I should clarify that, as far as I can tell, the button is not an electrical switch.  It doesn't feel like there is an on or off position - like it stays down when on and up when off.  It just feels like a button that sends a signal somewhere.  Though I haven't taken the motherboard out yet to look at it.

---

### Post by Joshua on 2011-01-11
I read a little about udev.  I don't really know much about it, but maybe this will help solve my problem:

```
$ udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1294783738.161613] change   /devices/pci0000:00/0000:00:09.0/ieee80211/phy0/rfkill0 (rfkill)
UDEV  [1294783738.167524] change   /devices/pci0000:00/0000:00:09.0/ieee80211/phy0/rfkill0 (rfkill)
KERNEL[1294783738.168651] change   /devices/platform/regulatory.0 (platform)
UDEV  [1294783738.185560] change   /devices/platform/regulatory.0 (platform)
KERNEL[1294783763.168145] change   /devices/pci0000:00/0000:00:09.0/ieee80211/phy0/rfkill0 (rfkill)
UDEV  [1294783763.171692] change   /devices/pci0000:00/0000:00:09.0/ieee80211/phy0/rfkill0 (rfkill)
```

The first 4 lines pop up when I turn WIFI off and the last 2 pop up when I turn WIFI on.

Is there any way to use this information to:
1) stop udev from performing those actions
2) write a script to ensure that WIFI is always on after bootup

---

### Post by mc4man on 2011-01-11
On my laptop there is a bios setting where one can set what gets turned on/off with the button on the case (here's it's a slider button

Have you checked?

---

### Post by Joshua on 2011-01-11
I did check the BIOS.  At first I assumed that all laptop WIFI buttons worked at a lower level than the OS, which upset me because there are so few options in the Averatec's BIOS.  It actually shocks me how basic they are - clock, fan and battery calibration, legacy USB... I think that might be all.  I'll post the full list and the version next time I'm in front of it.

Anyway, BIOS won't help, but from the bug report I linked, it looks like Ubuntu didn't always care how that button was set.  If that's the case, there must be a way to control WIFI availability through the OS, right?

EDIT: The BIOS say
Version: E12KA R1.03
VGA BIOS: 40N1008

---

### Post by Joshua on 2011-01-22
I haven't completely tested this yet, but I may have found a solution.  I recompiled the kernel without support for rfkill.

In menuconfig it's under Networking Support -> RF switch subsystem support.

I think that changes several things in the actual .config file, but after I recompile without that option, it looks like the computer basically ignores the WIFI button and led.  As long as I have the network set up in /etc/network/interfaces everything seems to work after booting.

Recompiling the kernel seems like overkill, but I'll use it this way until I figure something else out.

---

