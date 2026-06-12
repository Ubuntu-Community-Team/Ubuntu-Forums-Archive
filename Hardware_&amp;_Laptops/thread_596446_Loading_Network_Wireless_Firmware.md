---
title: "Loading Network Wireless Firmware"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by jd3010 on 2007-10-29
Hello,
Just downladed the driver for Atmel NIC wireless card " atmel-firmware-1.3-1fc3.noarch.rpm" for Comapq TC1000 and it says that :

the driver for these chips in Linux 2.6 do not include the firmware : this firmware need to be leoaded by the host ... firmware should be automatically loaded by the hotplug system. Il also provided a loader utility which cabn be uses tohe same thing when hotplug is not enabled "

Can anyone explane or translate, what do I have to do ??

the NIC is listed with lshw command 

thanks

---

### Post by tturrisi on 2007-10-29
post result of:
lspci

---

### Post by jd3010 on 2007-10-30
> **tturrisi said:**
> post result of:
lspci
00:00.0 Host bridge: Transmeta Corporation LongRun Northbridge (rev 03)

00:00.1 RAM memory: Transmeta Corporation SDRAM controller

00:00.2 RAM memory: Transmeta Corporation BIOS scratchpad

00:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)

00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)

00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)

00:08.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)

00:0a.0 Ethernet controller: Atmel Corporation at76c506 802.11b Wireless Network Adaptor (rev 11)

00:0b.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)

00:0b.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)

00:0c.0 USB Controller: NEC Corporation USB (rev 41)

00:0c.1 USB Controller: NEC Corporation USB (rev 41)

00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

---

### Post by tturrisi on 2007-10-30
Go here and download the atmel-firmware-1.3.tar.gz  and see the readme.
[http://www.thekelleys.org.uk/atmel/](http://www.thekelleys.org.uk/atmel/)

Try just extracting all the firmware files to /lib/firmware.
The atmel frivers are already installed/built into the kernel.

---

### Post by jd3010 on 2007-10-30
> **tturrisi said:**
> Go here and download the atmel-firmware-1.3.tar.gz  and see the readme.
[http://www.thekelleys.org.uk/atmel/](http://www.thekelleys.org.uk/atmel/)

Try just extracting all the firmware files to /lib/firmware.
The atmel frivers are already installed/built into the kernel.

I read through the readme but ....
I just did and I not sure what exactly I have to do ... the firmware *.bin files are in /lib/firmware directory.

But the /etc/Hotplug is empty, except for a USB directory.  Whcih file do I nee dto copy over ?

thanks for your time

Some omands :

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



eth1      Link encap:Ethernet  HWaddr 00

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:1 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:15 Base address:0x1c00 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



lshw

 *-network:0             

       description: Ethernet interface

       product: 82551QM Ethernet Controller

       vendor: Intel Corporation

       physical id: 8

       bus info: pci@0000:00:08.0

       logical name: eth0

       version: 10

       serial: 00

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

  *-network:1

       description: Wireless interface

       product: at76c506 802.11b Wireless Network Adaptor

       vendor: Atmel Corporation

       physical id: a

       bus info: pci@0000:00:0a.0

       logical name: eth1

       version: 11

       serial: 00

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=atmel latency=99 maxlatency=60 mingnt=12 module=atmel_pci multicast=yes wireless=IEEE 802.11-DS

---

### Post by jd3010 on 2007-10-30
The read me says also something about NOT using Hotplug (I am not sure if Hotplug works by default on 7.10, too new to know)

If you do not wish to use the hotplug system, this package includes 
a "push" firmware loader, atmel_fwl. You should arrange to run this  
as root from a network-startup script or PCMCIA script _before_ the  
interface is brought up. The command is simply 
 
atmel_fwl <interface> /path/to/firmware 
 
for instance 
 
/sbin/atmel_fwl eth0 /usr/lib/hotplug/firmware/atmel_at76c502.bin 

To which file do I copy the line over ??

thanks

---

### Post by tturrisi on 2007-10-30
[http://packages.debian.org/unstable/net/atmel-firmware](http://packages.debian.org/unstable/net/atmel-firmware)
download, install the deb, reboot and connect.

---

### Post by jd3010 on 2007-10-31
> **tturrisi said:**
> [http://packages.debian.org/unstable/net/atmel-firmware](http://packages.debian.org/unstable/net/atmel-firmware)
download, install the deb, reboot and connect.
Thka a lot for the time you take for me to solve this prob ....

Downloaded the file.

Do I nee also Udev or Hotplug package ?

thanks,

---

### Post by tturrisi on 2007-10-31
udev should already be installed.

---

### Post by jd3010 on 2007-11-01
Bingo,

It works ... could connect to a open Router.!!!! Woahhhh thanks,

Just another question, when I try to connect to another Router, I have only WEB encryptioon available in the Drop down list. How can I enable WPA encryption. M router is ocnfigured fwith WPA2.


Agian thanks

---

### Post by tturrisi on 2007-11-01
apt-get install wpasupplicant

Dropdown list in what program?  If NOT using network-manager and using the gnome default net-admin network utility, then you need to also use /etc/network/interfaces file with wpasupplicant.

/etc/network/interfaces:

# WPA GENERAL
# iface ath0 inet dhcp  (athX,ethX,wlanX,etc)
# wpa-ssid thisismynetworkname
# wpa-key_mgmt WPA-PSK
# wpa-proto WPA
# wpa-pairwise TKIP
# wpa-group TKIP
# wpa-psk thisismypassword
# wpa-driver wext

---

### Post by jd3010 on 2007-11-01
Well I click onthe 2 TV Top right and then choose "Connect to Other  Wireless Network ... Then I can put in the Network Name and still no WPA in the drop down list.

Wpasupplicant is installed .

My Interfaces file looks like this now:

auto lo
iface lo inet loopback
WPA GENERAL
iface ath0 inet dhcp (athX,ethX,wlanX,etc)
wpa-ssid thisismynetworkname
wpa-key_mgmt WPA-PSK
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-psk thisismypassword
wpa-driver wext

Do I have to personalise this file to my settings.... or will it be done automatically the first time O connect to my router and give in all the data ? Would another Programm do this ?

 Wirelles card is on eth1.

I also noted if I do a Manual setup of Wireless settings in Network (2 TV). I can there choose all the settings WPA etc ... BUT Roaming Mode is disbaled, meaning that as soon as I leave the house non Wirelless anymore without enabling Roaming again....

Thanks again, you are really of great help ...

---

### Post by tturrisi on 2007-11-02
I have no clue what Network (2 TV) is, I don't use any 3rd party connection managers.  Perhaps you are using Network-Manager program.

---

### Post by jd3010 on 2007-11-02
It must be that one.It is the default one of UBUNTU, no thirdparty installed.

I smy Interfaces ok ... ?

Thanks

---

### Post by tturrisi on 2007-11-03
> **jd3010 said:**
> It must be that one.It is the default one of UBUNTU, no thirdparty installed.

I smy Interfaces ok ... ?

Thanks
The default one in ubuntu IS a third party network tool, it's called network-manager.  IMHO, more trouble than it's worth.  I don't believe it even uses the interfaces file!  Try a forum search for network-manager wpa

---

### Post by jd3010 on 2007-11-07
Thanks a lot,

Not easy to setup the WPA ... I will continue trying, again thanks alot for your help.

---

