---
title: "Toshiba satelite L655 wifi connection"
date: 2010-08-29
forum: Hardware
---

### Post by vampcheah on 2010-08-29
hi all, 
i just bought a new laptop (toshiba satellite L655).
but i found that the wifi and wired connection totally can't work.
i am pretty sure my router running dhcp cause there already 2 pc and 1 laptop connected to network.


cat /etc/network/interfaces 
```

auto lo
iface lo inet loopback

```

cat /etc/NetworkManager/nm-system-settings.conf 
```

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```


dmesg | grep -e eth0 -e bcm
```

[   10.878522] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   69.554158] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr c8:0a:a9:b7:8e:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36816 (36.8 KB)  TX bytes:36816 (36.8 KB)

```
lspci
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```


lsusb
```

Bus 002 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 001 Device 004: ID 0e8f:0020 GreenAsia Inc. 
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lshw -C Network
```

  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d4000000-d4003fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: c8:0a:a9:b7:8e:1e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes
       resources: irq:35 memory:d3000000-d303ffff ioport:2000(size=128)

```


sudo dhclient eth0
```

There is already a pid file /var/run/dhclient.pid with pid 1721
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/c8:0a:a9:b7:8e:1e
Sending on   LPF/eth0/c8:0a:a9:b7:8e:1e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by IcarusR on 2010-08-29
Try the suggestions in this post

[http://ubuntuforums.org/showthread.php?t=1505697]("http://ubuntuforums.org/showthread.php?t=1505697")

---

### Post by vampcheah on 2010-08-29
already tried but not working.

---

### Post by IcarusR on 2010-08-29
Did you try the drivers from the Broadcom site ??

If you have tried several different drivers & ways to get network to work I would suggest you do a fresh install then try drivers from Broadcom site.

---

### Post by pytheas22 on 2010-08-29
I'm not sure why the ethernet isn't working.  If your network is using dhcp, you should get an address assigned when you type "sudo dhclient eth0".  It's possible there's something wrong with the ethernet driver and that updating it will fix the problem.

Since you currently have no Internet connection at all, however, updating the ethernet driver will be tough.  So let's try to get the wireless working first, and deal with the ethernet once you can get online wirelessly.

If you have an Ubuntu installation, it should have the wireless driver that you need on it.  Put the CD in your drive, then go to System>Administration>Software Sources.  Under the "Ubuntu Software" tab, enable the use of your CD as a repository.  Close the window and agree to update your sources list when prompted.  Finally, run:
```

sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```

This should install the driver you need (it's the same one from Broadcom's site, but packaged for Ubuntu).  After it's installed, reboot and hopefully the wireless will work.  If it still doesn't, please post the output of these commands (some commands may have no output):
```

sudo modprobe wl
dmesg | grep -e eth1 -e wl
sudo iwlist scan
modinfo wl
```

---

### Post by vampcheah on 2010-08-30
> **pytheas22 said:**
> I'm not sure why the ethernet isn't working.  If your network is using dhcp, you should get an address assigned when you type "sudo dhclient eth0".  It's possible there's something wrong with the ethernet driver and that updating it will fix the problem.

Since you currently have no Internet connection at all, however, updating the ethernet driver will be tough.  So let's try to get the wireless working first, and deal with the ethernet once you can get online wirelessly.

If you have an Ubuntu installation, it should have the wireless driver that you need on it.  Put the CD in your drive, then go to System>Administration>Software Sources.  Under the "Ubuntu Software" tab, enable the use of your CD as a repository.  Close the window and agree to update your sources list when prompted.  Finally, run:
```

sudo apt-get install bcmwl-kernel-source bcmwl-modaliases
```

This should install the driver you need (it's the same one from Broadcom's site, but packaged for Ubuntu).  After it's installed, reboot and hopefully the wireless will work.  If it still doesn't, please post the output of these commands (some commands may have no output):
```

sudo modprobe wl
dmesg | grep -e eth1 -e wl
sudo iwlist scan
modinfo wl
```when i insert the ubuntu installation cd and change the sources as you mention, i got a "No proprietary drivers are in use on this system". so i click on the Activate button and it's prompt me with "Failed to fetch cdrom:[Ubuntu_10.04 LTS_Lucis_Lynx_amd64]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb".

---

### Post by vampcheah on 2010-08-30
i get the wifi working with the broadcom driver. just for sharing what i did.


[LIST]
[*]Do not install any proprietary drivers when prompted. Remove the bcmwl-kernel-source package if it is installed.
[*]Download the appropriate driver (for x86 or x64) from here : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
[*]Follow the instructions in README.txt.
[*]Note : In instruction 4 in README, you will need root's privilege to execute modprobe and insmod. You can issue sudo.
[*]However, you have to load the module (issue modprobe and insmod) every time you boot. You may write a shell script and set it to execute at every boot.
[/LIST]
(this is what i found in older thread)

---

### Post by pytheas22 on 2010-08-30
If you open your CD in a file browser (there should be an entry for it under the Places menu), can you navigate to the location ...pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb?  If so, double-click the file named patch_2.6-2ubuntu1_amd64.deb to install it.  Then navigate to ...pool/restricted/b and look for two files with names similar to bcmwl-kernel-source_amd64.deb and bcmwl-modaliases_amd64.deb (they may be in subfolders).  Install those as well.

This will get the driver that you need installed manually--it achieves the same result as what I suggested in my last post.  Please let me know if this works.

EDIT: sorry, I wrote this before seeing your last post.  Glad to see you got the wireless working.

As for the ethernet, I think your best option would be to reinstall the driver using the source code from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (choose the "AR81Family Linux Driver").  Let me know if this works, or if you need more specific instructions (since you were able to get the Broadcom STA driver installed from source, I'm assuming you can install the Atheros one as well, but no worries if you aren't sure what to do).

---

### Post by mike909 on 2010-08-30
> **vampcheah said:**
> when i insert the ubuntu installation cd and change the sources as you mention, i got a "No proprietary drivers are in use on this system". so i click on the Activate button and it's prompt me with "Failed to fetch cdrom:[Ubuntu_10.04 LTS_Lucis_Lynx_amd64]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb".

Vampcheach,
It looks like you have the exact hardware as I, so following the directions here: [http://ubuntuforums.org/showthread.php?t=1505697&page=9](http://ubuntuforums.org/showthread.php?t=1505697&page=9) should work. You have your wireless working, from broadcom drivers which is fine too, but how about your wired connection (the AR8152)? Be sure to follow my post, and **don't** try the modified ones (ie [http://www.at.kernel.org/pub/linux/kernel/people/mcgrof/ethernet/](http://www.at.kernel.org/pub/linux/kernel/people/mcgrof/ethernet/) ). Those drivers will appear to work, and you will get a link, but you won't actually establish a L2 connection (won't get ip address). If you "watch ifconfig", you'll see it bounce between UP RUNNING and just UP.
Curios how you got the driver version "driverversion=1.0.1.0-NAPI" on your system...that may help point out how it's broken. (sorry if you mentioned this already).

---

### Post by vampcheah on 2010-09-02
once i got my wifi working, i update Broadcom STA driver by using update manager and the wifi work fine now.

but i come out another issue that the battery power not showing. i goto power management but the tab "on battery power" disappear .... seem quite lot problems with my new laptop to ubuntu....

---

### Post by pytheas22 on 2010-09-02
The battery-icon issue seems to be fairly prevalent in Ubuntu 10.04.  If updating your system doesn't take care of it, you can try going to System>Preferences>Startup Applications and changing the command for the "Power Manager" option to be:
```

gnome-power-manager --no-daemon
```

I recall having this issue on my netbook and that solved it, so maybe it will help you, but I'm not sure--unfortunately this kind of stuff is not my strong suit.

There are also several bug reports related to the battery icon in Ubuntu 10.04 which you can find via googling, for example: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/577825](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/577825)

---

### Post by vampcheah on 2010-09-12
> **pytheas22 said:**
> The battery-icon issue seems to be fairly prevalent in Ubuntu 10.04.  If updating your system doesn't take care of it, you can try going to System>Preferences>Startup Applications and changing the command for the "Power Manager" option to be:
```

gnome-power-manager --no-daemon
```

I recall having this issue on my netbook and that solved it, so maybe it will help you, but I'm not sure--unfortunately this kind of stuff is not my strong suit.

There are also several bug reports related to the battery icon in Ubuntu 10.04 which you can find via googling, for example: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/577825](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/577825)


tried the command but still not functioning...
(gnome-power-manager:1668): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x9b9f100'

i opened Preferences > Power management. there's only On AC Power and General tabs, Batter Power was lost....

---

### Post by pytheas22 on 2010-09-12
> 
tried the command but still not functioning...
(gnome-power-manager:166: GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x9b9f100'

i opened Preferences > Power management. there's only On AC Power and General tabs, Batter Power was lost....

Sorry that didn't help.  I really don't know much about this stuff (it's probably an ACPI problem or something along those lines, which is a far cry from wireless, which I know more about), so I'm afraid I can't be of more help with that.  You'd probably have better luck if you created a new thread, where you'd hopefully get the attention of someone who is more familiar with those types of issues.

And of course, google google google if you haven't done so already--in particular, see if anyone else has this problem with your particular model of laptop.

---

### Post by RafaelBarreto on 2010-09-15
This acpi/battery issue is related to this thread
[http://ubuntuforums.org/showthread.php?t=1546463](http://ubuntuforums.org/showthread.php?t=1546463)

...and I did not find a solution to this issue yet.

I am using the latest kernel (2.6.35-21-generic), but acpi still ignores my battery information (and even if the cable is connected or not, after it get this info for the first time in boot).

---

