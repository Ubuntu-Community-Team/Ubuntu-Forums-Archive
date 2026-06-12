---
title: "Negear WG111T"
date: 2009-05-20
forum: Hardware
---

### Post by Narusegawa on 2009-05-20
I've got a 32bit install of Ubuntu 9.04 Jaunty on my laptop now and figured I'd connect it online... that's where the fun began.

I've installed the ndiswrapper from the repository and also ndisgtk. FYI I used an ethernet cable to do so and get updates.

I copied the WG111T 1.2 (UK) drivers from their website, installed them using the Windows Wireless Drivers gui. Installed both sets of .inf files as others have recommended. My wireless USB WG111T finds and detects other networks fine aswell as my own.

```
iwlist scan
```

Lists me all the nearby networks too. My router is setup for "WPA Personal" and "TKIP" and this works fine for everything else of mine. Password of mypassword for example and SSID of mywifi.

I put those into the config gui and it finds my network and signal strength (I don't broadcast either, but as it found it, and the signal strength I guess my authentication is right?). The problem is, it won't actually connect, it'll wait a minute or 2 and prompt for the keys again, and then again and again. But all I see is a little twirly icon spinning around like it's trying to do something (I'd have expected a tooltip to say what its trying to do).

My router shows nothing on the wireless being connected at all.

Anyone got any idea's on what I can try? (I can't try now as I'm at work but will try later)

I've ruled out DHCP Client issues as I can plug in an ethernet cable and bang voila it's up and running (hence I've actually updated my Jaunty with all the latest updates using Update Manager).

---

### Post by Black_Wolf_92 on 2009-05-20
open a terminal and post output for the following.

> lsusb
ndiswrapper -l

---

### Post by Narusegawa on 2009-05-20
```

Bus 001 Device 003: ID 1385:4250 Netgear, Inc WG111T
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```and also

```

athfmwdl : driver installed
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netwg11t : driver installed
    device (1385:4250) present

```

oh, and from "dmesg | tail"

```

[  294.448081] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[  294.590734] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[  294.976315] usb 1-1: USB disconnect, address 2
[  295.248054] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  295.381639] usb 1-1: configuration #1 chosen from 1 choice
[  295.548084] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[  295.691609] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded
[  296.066097] wlan0: ethernet device 00:1e:2a:df:11:ec using NDIS driver: netwg11t, version: 0x10000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1385:4250.F.conf
[  296.066136] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[  300.402966] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by Black_Wolf_92 on 2009-05-22
Ok follow these instructions. I'm thinking it COULD be a blacklist interference, as it seems those are missing in your setup. If the following DOESN"T work, post back, and we'll start from scratch manually with terminal.


1. Download attached file to desktop and extract it.
2. Open terminal and run
> sudo nautilus
3. Backup the contents of
> /etc/modprobe.d/
to a different location, in case this step doesn't work, you may want to replace your original settings
4. Copy the contents of the downloaded folder attached to
> /etc/modprobe.d/ And replace all your old files (assuming you backed up).
5. Reboot your computer


If the above doesn't work please get back to me
-Black Wolf

---

### Post by Narusegawa on 2009-05-22
I'll try that this weekend thanks. I'm actually in the middle of re-installing XP onto my laptop and setting up a dual-boot.

I've already learnt the hard way (i.e. laptop nearly went out the window) last night how unreliable a "Dell Inspiron 1100" is with Ubuntu. Every other boot X doesn't start, even with changes from this forum like using a new ppa launchpad soruce to get the intel driver, modifiying the menu.lst too. So far the only advice is to install 8.04 which to me seems backwards to do.

---

