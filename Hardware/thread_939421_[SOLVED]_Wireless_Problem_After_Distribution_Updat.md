---
title: "[SOLVED] Wireless Problem After Distribution Update"
date: 2008-10-05
forum: Hardware
---

### Post by jubu8 on 2008-10-05
Hello, I recently updated my Ubuntu 7.10 installation to 8.04 and for some reason I cannot get my wireless card (Linksys WMP54GS) to work. I had it working flawlessly with 7.10. I don't know if this is related or not, but whenever I enable my integrated ethernet card I cannot open administrative tasks, so I cannot use the Hardware Drivers app to install the drivers for the card. So I have to install the wireless card manually, which appears to work, but I am unable to see any wireless networks. Any help is greatly appreciated.

---

### Post by pytheas22 on 2008-10-05
Did you have to do anything special in Ubuntu 7.10 to get your wireless card working, or did it "just work" out-of-the-box?

Please also post the output of the following commands:
```

lspci -nn
lsusb
lshw -C Network
sudo iwlist scan
```

---

### Post by jubu8 on 2008-10-06
> Did you have to do anything special in Ubuntu 7.10 to get your wireless card working, or did it "just work" out-of-the-box?

In Ubuntu 7.10 I used the Restricted Drivers Manager to enable the driver and it worked.

Below are the outputs from the commands.

> lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02) 
00:02.0 Display controller [0380]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
01:01.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)
```

> lsusb

```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 059b:0034 Iomega Corp.
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 047d:105e Kensington
Bus 001 Device 001: ID 0000:0000
```

> lshw -C Network

```
 *-network
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
```

> sudo iwlist scan

```
lo        Interface doesn't support scanning.
```

---

### Post by pytheas22 on 2008-10-06
Please try running these commands.  They should get your card working using the driver that it had in Gutsy (Hardy uses a different driver by default for your card, which is probably why it's not working now):
```

echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist
sudo sed 's/blacklist bcm43xx/#blacklist bcm43xx/' /etc/modprobe.d/blacklist
```

Then download [this file]("http://burnthesorbonne.com/files/bcm43xx-firmware.tar.gz") on a computer that has Internet access, and transfer it to your Ubuntu machine (using a USB stick, CD or whatever you have available).  Save it to your desktop on Ubuntu, and then finish by running these commands:
```

cd ~/Desktop
sudo cp bcm43xx-firmware /lib/firmware
cd /lib/firmware
sudo tar -xzvf bcm43xx-firmware
```

Then reboot.  After the reboot, your wireless card should work.  If it still doesn't, please post the output of the following:
```

dmesg | grep -e eth -e bcm
cat /etc/modprobe.d/blacklist
ls /lib/firmware
lshw -C Network
sudo iwlist scan
```

Also, this computer doesn't have an ethernet card, right?  The wireless is its only means of getting online?

---

### Post by jubu8 on 2008-10-06
The blacklist commands worked without a problem, however, when I try dealing with the bcm43xx-firmware file it doesn't want to cooperate. Below are the commands in terminal.

```
<username>@<computer name>:~$ cd ~/Desktop
<username>@<computer name>:~/Desktop$ sudo cp bcm43xx-firmware.tar.gz /lib/firmware
sudo: unable to resolve host <computer name>
<username>@<computer name>:~/Desktop$ cd /lib/firmware
<username>@<computer name>:/lib/firmware$ sudo tar -xzvf bcm43xx-firmware
sudo: unable to resolve host <computer name>
tar: bcm43xx-firmware: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

Since it was not working after a reboot, I entered the commands you listed, below are the results.

> dmesg | grep -e eth -e bcm

```
[   21.367312] Driver 'sd' needs updating - please use bus_type methods

[   21.378042]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
```

> cat /etc/modprobe.d/blacklist

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
# evbug is a debug tool that should be loaded explicitly blacklist evbug
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
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
blacklist b43
blacklist b43legacy
blacklist ssb
```

> ls /lib/firmware

```
2.6.22-14-generic  b43                      bcm43xx_microcode11.fw

2.6.22-15-generic  b43legacy
2.6.24-19-generic  bcm43xx-firmware.tar.gz
```

> lshw -C Network

```
  *-network               
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: 02
width: 32 bits
lock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
```

> sudo iwlist scan

```
lo        Interface doesn't support scanning.
```

> Also, this computer doesn't have an ethernet card, right? The wireless is its only means of getting online?

It does, it's an integrated card, but I have it disabled in the BIOS because after updating to 8.04 I am unable to open Administrative task with it enabled. This card was also working perfectly before the update.

Also, not sure if this is related, but anytime I use a command in terminal with sudo it always says "sudo: unable to resolve host <computer name>".

Thank you for all of your help so far.

---

### Post by pytheas22 on 2008-10-06
Sorry, my fault...there was a typo in the instructions I gave you (I should have written bcm43xx-firmware.**tar.gz**).  Please try running these:
```

cd /lib/firmware
sudo tar -xzvf bcm43xx-firmware.tar.gz
```

That should work, and after a reboot your wireless should be up.  If not, please type these commands and post the output:
```

sudo modprobe -r b43 b43legacy b44 ssb bcm43xx
sudo modprobe bcm43xx
dmesg | grep -e bcm -e eth
sudo iwlist scan
```

---

### Post by jubu8 on 2008-10-06
After fixing the typos Ubuntu successfully copied the files. The only way to get the card to work after a restart is to enter the commands you listed.

> sudo modprobe -r b43 b43legacy b44 ssb bcm43xx
sudo modprobe bcm43xx
dmesg | grep -e bcm -e eth
sudo iwlist scan

After I run those commands, the card starts working (I'm typing this in Ubuntu). However, I have to enter those commands at each restart for the card to work.

The "sudo modprobe -r b43 b43legacy b44 ssb bcm43xx" and "sudo modprobe bcm43xx" commands give no output. The "sudo iwlist scan" command list wireless networks around the computer. Below is the output from "dmesg | grep -e bcm -e eth".


```
[   16.702629] Driver 'sd' needs updating - please use bus_type methods
[   16.702904]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  221.865424] bcm43xx driver
[  222.077827] bcm43xx: Radio enabled by hardware
[  222.260629] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  223.250780] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

---

### Post by pytheas22 on 2008-10-06
Good to hear that you got the wireless working--that was the hard part.  The issue with having to type those commands manually is to be expected (I was hoping to avoid it by using the blacklist, but apparently it's not working).  However, you can write a simple boot script to run those commands automatically each time Ubuntu boots, which will work around the problem.  To do so, first type:

```
sudo gedit /etc/init.d/wifi-fix.sh
```

A blank text file will open.  Add to it these lines:
```

#!/bin/bash

modprobe -r b43 b43legacy b44 ssb bcm43xx
modprobe bcm43xx
ifconfig eth1 up
```

Then save and close the file, and run these commands so that Ubuntu will run the script at each boot:

```
cd /etc/init.d
sudo chmod +x wifi-fix.sh
sudo update-rc.d wifi-fix.sh defaults
```

Then reboot.  After rebooting, your wireless should "just work" without any manual commands required.  If it doesn't, please tell me the output of:
```

lshw -C Network
dmesg | grep -e bcm -e eth1
iwconfig
```

---

### Post by jubu8 on 2008-10-07
Well, all of the commands completed successfully, but after a restart, it still doesn't load automatically. As you requested, the output to your commands are listed below.

> lshw -C Network

```
  *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
```

> "dmesg | grep -e bcm -e eth1" has no output

> iwconfig

```
lo        no wireless extensions.
```

---

### Post by pytheas22 on 2008-10-07
I made a mistake in one of the commands I gave you to run--sorry.  Please run these commands; they should do the trick:
```

cd /etc/init.d
sudo -s
update-rc.d wifi-fix.sh defaults
```

Do things work now after a reboot?  If not, please post the output of:

```
cat /etc/init.d/wifi-fix.sh
ls -l cat /etc/init.d/wifi-fix.sh
sudo modprobe -r ssb
```

---

### Post by jubu8 on 2008-10-08
It's working after restarts now. Thank you so much for all of your help.

---

