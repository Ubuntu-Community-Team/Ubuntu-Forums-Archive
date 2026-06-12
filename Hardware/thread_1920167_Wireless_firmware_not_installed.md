---
title: "Wireless firmware not installed"
date: 2012-02-04
forum: Hardware
---

### Post by timobis on 2012-02-04
Hey all,

sorry for posting yet another post about wireless firmware, I have seen a lot and tried a few different things to install the firmware but my laptop just isn't downloading anything :/

I ran nm-tool and lpsci -nn and got the following:


timothy@Priscilla-Elsa:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:21:9B:CC:39:D2

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:1F:E1:C3:0D:1E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


timothy@Priscilla-Elsa:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)


does anyone have any ideas at all?? thanks :)

---

### Post by shakabra on 2012-02-04
Plug in to a wired ethernet connection and open up "Additional Drivers". That should find your BCM43 driver no problem. Or check this out [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by timobis on 2012-02-04
it worked, then I went to the additional drivers to activate the drivers and then it stopped working again ¬_¬

---

### Post by Bucky Ball on 2012-02-04
Get wired and install:

firmware-b43-installer
b43-fwcutter

... from Synaptic Package Manager or Software Centre, depending on your release. That should fix it but you might need to reboot. You should then be able to activate the driver in 'Additional Drivers' but you might not even need to do that. ;)

---

### Post by timobis on 2012-02-04
> **Bucky Ball said:**
> Get wired and install:

firmware-b43-installer
b43-fwcutter

... from Synaptic Package Manager or Software Centre, depending on your release. That should fix it but you might need to reboot. You should then be able to activate the driver in 'Additional Drivers' but you might not even need to do that. ;)

I've uninstalled and re-installed both the firmware installer and the fwcutter, I've removed them entirely via synaptics and installed it again then tried re-installing both but its just not working :/

---

### Post by Bucky Ball on 2012-02-04
Did you reboot after installing? Check additional drivers and attempt to activate? Could you provide the terminal output of:

```
lspci
```

---

### Post by TBABill on 2012-02-04
> **Bucky Ball said:**
> Get wired and install:

firmware-b43-installer
b43-fwcutter

... from Synaptic Package Manager or Software Centre, depending on your release. That should fix it but you might need to reboot. You should then be able to activate the driver in 'Additional Drivers' but you might not even need to do that. ;)

The reason the b43 did not work is because these instructions were incorrect. You have a BCM4312 LPPHY (low power) which requires a different installer file. What you should have done was plug into ethernet and ```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
``` If that finishes fine, instead of restarting just ```
sudo modprobe b43
```Wait a few moments then connect. If that works fine and you get online, then to make the driver activate with each restart, just ```
gksudo gedit /etc/modules
``` and add "b43" without quotes to the end of the list, save and restart to test if it held.

---

### Post by timobis on 2012-02-05
> **TBABill said:**
> The reason the b43 did not work is because these instructions were incorrect. You have a BCM4312 LPPHY (low power) which requires a different installer file. What you should have done was plug into ethernet and ```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
``` If that finishes fine, instead of restarting just ```
sudo modprobe b43
```Wait a few moments then connect. If that works fine and you get online, then to make the driver activate with each restart, just ```
gksudo gedit /etc/modules
``` and add "b43" without quotes to the end of the list, save and restart to test if it held.


Thanks dude things worked out perfectly in the end :D

---

### Post by Bucky Ball on 2012-02-05
Great! Please mark thread as Solved from Thread Tools to help others. ;)

---

### Post by TBABill on 2012-02-05
> **timobis said:**
> Thanks dude things worked out perfectly in the end :D

Very welcome and best of luck to you!

---

