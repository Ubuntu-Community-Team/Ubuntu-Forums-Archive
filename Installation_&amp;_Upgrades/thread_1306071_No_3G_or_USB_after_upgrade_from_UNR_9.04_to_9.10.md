---
title: "No 3G or USB after upgrade from UNR 9.04 to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by animaniac on 2009-10-30
I made a clean install of karmic and I can't get the 3G connection working, nor can I access my external drives. All these things worked out of the box in 9.04, would be good to have a fix, info below:

I'm using a LG X110 with built in 3G module, the 3G card seems to be detected in NM as:
Wired Network (Ericsson Ericsson F3507g WMC Composite Device)
But it is constantly "disconnected". 

When I go to "Edit Connections..." In the "Wired" tab I have:
Auto eth0
Auto usb0
I never set-up any usb connection so I'm guessing it's the 3G module that's there for some weird reason.

In the "Mobile Broadband" tab when I try to "Add" a connection on the first page of the wizard there are no devices I can select, only a greyed out "Any device". Completing the wizard and adding the connection doesn't let me connect the 3G in NM.

None of the 3 USB ports or the card reader are working.

Output for lsusb is:

user@user-laptop:~$ lsusb
Bus 001 Device 003: ID 5986:0203 Acer, Inc 
Bus 001 Device 002: ID 0bdb:1902 Ericsson Business Mobile Networks BV 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
user@user-laptop:~$

Any ideas? I'm all out.

---

### Post by animaniac on 2009-10-30
I booted up from live-usb, same problems.

---

### Post by animaniac on 2009-10-30
BUMP, anyone? I'd rather not go back to 9.04, not to mention the technical difficulties of accomplishing that without USB support.

---

### Post by Sealbhach on 2009-10-30
Hi, I found some information here:

[http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module#Using_F3507g_with_NetworkManager](http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module#Using_F3507g_with_NetworkManager)

It seems you need the modemmanager packages by adding that PPA and then updating your system. However, you would need an internet connection for that.:oops:

.

---

### Post by animaniac on 2009-10-30
I added the PPA and updated, nothing happened. Checked Synaptic and all those packages are already installed. I have ethernet for now, but that's only temporary. Also I don't see how this would help the USB problem, I have a feeling that the two might be related.

---

### Post by animaniac on 2009-10-30
limited to using my phone for surfing. Found out this is actually a  reported bug (#455408 on launchpad) that has been around since beta, weird its still in the final release. Hoping for update soon.

---

### Post by animaniac on 2009-10-30
limited to using my phone for surfing. Found out this is actually a  reported bug (#455408 on launchpad) that has been around since beta, weird its still in the final release. Hoping for update soon.

Edit: after a dozen restarts i managed to get everything working like one of the commenters in the bug report, will just have to avoid powering off until it gets patched.

---

### Post by Sealbhach on 2009-10-31
> **animaniac said:**
> limited to using my phone for surfing. Found out this is actually a  reported bug (#455408 on launchpad) that has been around since beta, weird its still in the final release. Hoping for update soon.

Edit: after a dozen restarts i managed to get everything working like one of the commenters in the bug report, will just have to avoid powering off until it gets patched.

Thanks for letting people know, I'm sure there must be a lot of others affected by this.

.

---

### Post by gabitech on 2009-10-31
I'm also affected by this, running on a Samsung NC10 - just that only my 3G modem doesn't get recognized... - I'll try the bug link above maybe that would help

---

### Post by Jolaren on 2009-11-09
> **animaniac said:**
> I made a clean install of karmic and I can't get the 3G connection working, nor can I access my external drives. All these things worked out of the box in 9.04, would be good to have a fix, info below:

I'm using a LG X110 with built in 3G module, the 3G card seems to be detected in NM as:
Wired Network (Ericsson Ericsson F3507g WMC Composite Device)
But it is constantly "disconnected". 

When I go to "Edit Connections..." In the "Wired" tab I have:
Auto eth0
Auto usb0
I never set-up any usb connection so I'm guessing it's the 3G module that's there for some weird reason.

In the "Mobile Broadband" tab when I try to "Add" a connection on the first page of the wizard there are no devices I can select, only a greyed out "Any device". Completing the wizard and adding the connection doesn't let me connect the 3G in NM.

None of the 3 USB ports or the card reader are working.

Output for lsusb is:

user@user-laptop:~$ lsusb
Bus 001 Device 003: ID 5986:0203 Acer, Inc 
Bus 001 Device 002: ID 0bdb:1902 Ericsson Business Mobile Networks BV 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
user@user-laptop:~$

Any ideas? I'm all out.


Hey.
I have the same problem as you. The exact same problem. But my card reader acctually worked for last reboot. First time since 9.10. So my question to you, has this issue been resolved? I'm so tired not beeing able to use my 3G Broadband connection.

---

### Post by Bejje on 2010-01-08
I have the exact same problem too. Please some help would be greatly appreciated.

Edit: Blacklisted the camera "uvcvideo" in "/etc/modprobe.d/blacklist.conf" solved the problem. Since I don't use the camera this works for me.

---

