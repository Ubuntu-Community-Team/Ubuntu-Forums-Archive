---
title: "sound,wifi and HD problem on Dell Latitude D830"
date: 2008-08-12
forum: Hardware
---

### Post by Shiroku on 2008-08-12
I installed Kubuntu 8.04 on my new Dell Latitute D830, and there are some problems:
1- sound doesn't work.
I installed the new alsa driver (1.0.17) and when the installation was finished, I get this message:
> 
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

What can I do?
If I run sudo lshw -C sound, this is the output:
> 

  *-multimedia
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel



2- wireless connection doesn't work.
knetworkmanager find the wireless connection, let me put the WPA, then the computer try to get the ip address configuration, but an error pop up.
If I use a konsole, I get this error:
> 
eth1      no private ioctls.

(eth1 is my wireless interface)


3- How can I check if my computer is afflicted be this bug: [https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD830]("https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD830") ('Serious HD Problem') ?

---

### Post by pytheas22 on 2008-08-12
I can't help with sound, as I don't know much about it, but I will help with the wireless.  Please post the output of these commands so that I can figure out what to do to fix it:
```

lshw -C Network
lspci -nn
lsusb
iwlist scan
dmesg | grep ndis
```

> 
3- How can I check if my computer is afflicted be this bug: [https://wiki.ubuntu.com/LaptopTestin...llLatitudeD830](https://wiki.ubuntu.com/LaptopTestin...llLatitudeD830) ('Serious HD Problem') ?

I think this issue has been fixed for a long time, so you don't need to worry about it.  That happened a couple of years ago.

---

### Post by Shiroku on 2008-08-13
Thank's for the help.

```

daniela@ubuntu:~$ sudo lshw -C Network
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:c6:b6:4f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:6d:8e:3f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5755m-v3.29 ip=192.168.1.143 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
daniela@ubuntu:~$

```

```

daniela@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro NVS 135M [10de:042b] (rev a1)
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
daniela@ubuntu:~$

```


```

daniela@ubuntu:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 003: ID 0b97:7772 O2 Micro, Inc.
Bus 005 Device 002: ID 0b97:7761 O2 Micro, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
daniela@ubuntu:~$

```


```

daniela@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

daniela@ubuntu:~$

```



```

daniela@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated

daniela@ubuntu:~$

```



```

daniela@ubuntu:~$ dmesg | grep ndis
daniela@ubuntu:~$

```





> 
[QUOTE]
3- How can I check if my computer is afflicted be this bug: [https://wiki.ubuntu.com/LaptopTestin...llLatitudeD830](https://wiki.ubuntu.com/LaptopTestin...llLatitudeD830) ('Serious HD Problem') ?

I think this issue has been fixed for a long time, so you don't need to worry about it.  That happened a couple of years ago.
[/QUOTE]
mmmhh.. I'm not sure, for many reasons:
1- last update of the wiki page is '2008-08-06'
2- on launchpad bug section, bug ( [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) ) is fixed only on Suse and Debian, but not in Ubuntu
3- there are some recently posts on [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) about the bug

---

### Post by pytheas22 on 2008-08-13
Thanks for the information.

To fix the wireless, please try this (make sure you are connected via the ethernet first):
```

sudo -s
apt-get install ndiswrapper*
wget http://myspamb8.googlepages.com/R174291-pruned.zip
unzip R174291-pruned.zip
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
echo 'blacklist wl' >> /etc/modprobe.d/blacklist
```

Then reboot and see if the wireless works better.  If not, please tell me the output of:
```

ndiswrapper -l
cat /etc/modprobe.d/blacklist
dmesg | grep -e ndis -e wlan
lshw -C Network
```

As for the hard-drive bug, I will look into that more...maybe you're right that it's not really fixed.

---

### Post by Shiroku on 2008-08-15
> **pytheas22 said:**
> 
To fix the wireless, please try this (make sure you are connected via the ethernet first):
```

sudo -s
apt-get install ndiswrapper*
wget http://myspamb8.googlepages.com/R174291-pruned.zip
unzip R174291-pruned.zip
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
echo 'blacklist wl' >> /etc/modprobe.d/blacklist
```

Then reboot and see if the wireless works better. 


Yes! Thank's!! It works!


About the sound: I tried Kubuntu 8.10 alpha4 livecd, and the sound works out of box... :confused:

---

### Post by pytheas22 on 2008-08-15
I'm glad the wireless is straightened out.

As I say, I don't know really anything about sound in Ubuntu, but you might want to take a look [here]("http://ubuntuforums.org/showthread.php?t=205449") and [here]("https://help.ubuntu.com/community/SoundTroubleshooting") if you haven't already.  If the sound works in 8.10 alpha but not 8.04, it's probably a matter of upgrading to the latest stable version of alsa, which probably will require compiling it. Those guides that I linked to should cover that stuff, though.

If you still can't figure the sound out, you may want to start a new thread about it so that you'll get more attention from people who can help you.

---

### Post by Shiroku on 2008-08-16
ok, the sound now works: I installed a new version of alsamixer and then I raised all mixers.


	
The last remaining problem is the 'HD problem' 	;)

---

### Post by pytheas22 on 2008-08-16
I found the main [bug report]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695") for the hard disk problem.  It says that you can check whether it's affecting you:

> Please see for yourself how often your drive is load cycling:
```
smartctl -d ata -a /dev/sda
```
(This command is for an SATA drive; you'll need to install the smartmontools package first ["sudo apt-get install smartmontools"].)

You can get the average per hour by the following division:
Load_Cycle_Count / Power_On_Hours

About 15 cycles per hour and lower is apparently what you want to see, unless your laptop is being used heavily during the testing period.

If you think you're affected, please look through that bug report, as there are a number of solutions suggested.

---

### Post by Shiroku on 2008-10-11
wireless doesn't work....

I run pppoeconf and when I reboot the pc, the wireless doesn't work...

if I run 'sudo iwlist wlan0 scan', I can see my wireless connection...
If I use Knetworkmanager, I can't see the wireless connection...

---

### Post by pytheas22 on 2008-10-12
Can you see your network or connect using [wicd]("http://wicd.sourceforge.net")?

Also, did you apply any updates before the wireless broke?

---

### Post by Shiroku on 2008-10-12
I installed wicd and the wireless connection works!

Thank's!!

---

