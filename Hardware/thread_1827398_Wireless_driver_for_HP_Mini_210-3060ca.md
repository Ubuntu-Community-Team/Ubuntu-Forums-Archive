---
title: "Wireless driver for HP Mini 210-3060ca"
date: 2011-08-17
forum: Hardware
---

### Post by iconoclastic on 2011-08-17
I've got an HP mini 210-3060ca running Ubuntu 11.04.

As I've read in numerous other posts here, there's a problem with the Wireless network adapter.

Unfortunately, the solution that seems to work for most other people won't work for me.

In most other posts, it is suggested that the user runs the 'Additional Drivers' process from System->Administration. From there, one is supposed to choose one of the wireless drivers listed there.

Unfortunately, when I run 'Additional Drivers', I see nothing but the message "no proprietary drivers are in use on this system".

I do have "restricted-extras" repository active. I currently have the machine on a wired connection to the internet and I've updated all the package sources.

I also tried using the package manager to install the "bcmwl-kernel-source" package. This hasn't helped.

Any suggestions would be really appreciated.

---

### Post by iconoclastic on 2011-08-18
Bump with new info:

ubuntu@ubuntu:/$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 2c:27:d7:ec:04:8e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.142 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:50004000-50004fff memory:50000000-50003fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:52000000-5200ffff

The second network device looks really lame. I assume that's my wireless card. Can any one confirm that?

I still see nothing in the 'Additional Drivers' window. I'm trying the instructions here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by iconoclastic on 2011-08-18
ubuntu@ubuntu:/$ sudo lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Ralink corp. Device 5390

So, looks like I don't have the usual "Broadcom" wireless adapter. Might have to go the ndiswrapper route.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by iconoclastic on 2011-08-18
Tried to determine if ndiswrapper would even work. Determined that the PCI-ID for this device is 1814:5390.

By searching around for more information about that device, I found a couple of other people trying to solve the same problem.

[http://forums.linuxmint.com/viewtopic.php?f=53&t=70576&start=0](http://forums.linuxmint.com/viewtopic.php?f=53&t=70576&start=0)
This one mentions trying some kernal modules:

> First, see if we can get it going manually by:
```
sudo modprobe -r rt2860sta rt3390
```
Ignore any errors it may return because rt3390 is not loaded.
```
sudo modprobe rt3390
```
and see if wireless works (give it about 1-2 min delay before writing it off as not working)

Gonna try that.

---

### Post by iconoclastic on 2011-08-18
Modprobe didn't work.

Planned on grabbing the Windows driver and trying ndiswrapper.

Found, lucky, the Ralink website. 
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
And found, double lucky, that they have linux drivers for their 539x class drivers. Mine is a 5390.

Downloaded the driver package. It looks like pretty standard source with a make file in it. I'm running the make right now.

---

### Post by iconoclastic on 2011-08-19
As I mentioned above, the driver package from the Ralink website contained source code and a make file. It also contained some pretty great instructions.

I'll copy them here for convenience:
> 1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.
Looks like these instructions are a bit old. The make file is already configured correctly
> 3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d
I only had to change the HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT values. I did not have to run the extra script.
Do the next step as root
> 4> $make			
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    
6> load driver
    #[kernel 2.4]
    #    $/sbin/insmod rt5390sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt5390sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2860sta

My wireless device now works! Unfortunately I have to manually load the rt5390sta.ko code each time I boot the computer. However, there are instructions in the same README about setting that up at boot time. I'll try that out and report back.

---

### Post by iconoclastic on 2011-08-21
I have not yet tried the instructions in the Ralink README for loading the rt5390sta.ko module at boot time.

However, one of the items updated recently by the Update Manager broke this fix. I re-compiled the code and it works again. I'm really hoping that I won't have to re-compile each time there's an update. I'll try to figure out what specific package broke things when it was updated.

---

