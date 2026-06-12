---
title: "Need help setting up wireless on an Acer Aspire 3009WLCi"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by Tiede on 2005-12-31
Here's the streamed version of the story.
*Bought an Acer last week (12-26th-05) and put Ubuntu on it as quickly as I could say "I am back home from the store"
*Installed automatix, with the ndisgtk package, for wireless access... (thru  a DSL lan, for I haven't tried wlan yet)
*Open ndisgtk. oops! no device shown. My wireless seems not to be set up.

So, I came here to try to get some help from you guys, so I can better juggle with the different outputs I have gotten from the command line.
Here  are the relevant stuff that were in it. I tried to help with arrows and comments, but there is no denying that it is a bit long...

```
marc@Tuxed:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:e8:73:8a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.08 Jan. 22 2005 duplex=half ip=10.1.18.100 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:1800-18ff iomemory:e2005000-e2005fff irq:19
  *-network:1 UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       resources: iomemory:e2000000-e2001fff irq:4
##############################################################################################
marc@Tuxed:~$ lspci -v | grep Network
0000:00:0b.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
				####################
##and to show the whole thing associated with that...
marc@Tuxed:~$ lspci -v
0000:00:0b.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
        Subsystem: AMBIT Microsystem Corp.: Unknown device 0312
        Flags: fast devsel, IRQ 4
        Memory at e2000000 (32-bit, non-prefetchable) [size=8K]
###############################################################################################
marc@Tuxed:~$ lspci -n
0000:00:00.0 0600: 1039:0760 (rev 03)
0000:00:01.0 0604: 1039:0002
0000:00:02.0 0601: 1039:0963 (rev 25)
0000:00:02.1 0c05: 1039:0016
0000:00:02.5 0101: 1039:5513
0000:00:02.6 0703: 1039:7013 (rev a0)
0000:00:02.7 0401: 1039:7012 (rev a0)
0000:00:03.0 0c03: 1039:7001 (rev 0f)
0000:00:03.1 0c03: 1039:7001 (rev 0f)
0000:00:03.2 0c03: 1039:7002
0000:00:04.0 0200: 1039:0900 (rev 91)
0000:00:06.0 0607: 104c:ac50 (rev 02)
0000:00:0b.0 0280: 14e4:4318 (rev 02)		<-----------
0000:00:18.0 0600: 1022:1100
0000:00:18.1 0600: 1022:1101
0000:00:18.2 0600: 1022:1102
0000:00:18.3 0600: 1022:1103
0000:01:00.0 0300: 1039:6330
#################################################################################################
marc@Tuxed:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
#################################################################################################
marc@Tuxed:~$ ifconfig
eth0      Lien encap:Ethernet  HWaddr 00:C0:9F:E8:73:8A
          inet adr:10.1.18.100  Bcast:10.1.18.255  Masque:255.255.255.0
          adr inet6: fe80::2c0:9fff:fee8:738a/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:1125355 (1.0 MiB)  TX bytes:154585 (150.9 KiB)
          Interruption:19 Adresse de base:0x1800

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:3932401 (3.7 MiB)  TX bytes:3932401 (3.7 MiB)
###################################################################################################
marc@Tuxed:~$ ndiswrapper -l
No drivers installed
					###############################
##Note: ndisgtk is installed.
```

Again sorry for the length...
Can anyone help? 

Just to be on the safe side, the output of lshw -businfo:
```
marc@Tuxed:~$ sudo lshw -businfo
Password:
Bus info     Device    Class          Description
=================================================
                       system         Aspire 3000
                       bus            Lugano M
                       memory         BIOS
cpu@0                  processor      Mobile AMD Sempron(tm) Processor 3000+
                       memory         L1 cache
                       memory         L2 cache
                       memory         System Memory
                       memory
                       memory         DIMM DDR Synchronous
                       memory
                       memory         DIMM DDR Synchronous
                       memory
                       memory
pci@00:00.0            bridge         760/M760 Host
pci@00:01.0            bridge         SG86C202
pci@01:00.0            display        661/741/760 PCI/AGP VGA Display Adapter
pci@00:02.0            bridge         SiS963 [MuTIOL Media IO]
pci@00:02.1            bus            SiS961/2 SMBus Controller
pci@00:02.5            storage        5513 [IDE]
ide@0        ide0      bus            IDE Channel 0
ide@0.0      /dev/hda  disk           WDC WD600UE-22HCT0
ide@1        ide1      bus            IDE Channel 1
ide@1.0      /dev/hdc  disk           HL-DT-STCD-RW/DVD DRIVE GCC-4244N
pci@00:02.6            communication  AC'97 Modem Controller
pci@00:02.7            multimedia     Sound Controller
pci@00:03.0            bus            USB 1.0 Controller
usb@1        usb1      bus            Silicon Integrated Systems [SiS] USB 1.0 Controller
pci@00:03.1            bus            USB 1.0 Controller
usb@2        usb2      bus            Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
pci@00:03.2            bus            USB 2.0 Controller
usb@3        usb3      bus            Silicon Integrated Systems [SiS] USB 2.0 Controller
pci@00:04.0  eth0      network        SiS900 PCI Fast Ethernet
pci@00:06.0            bridge         PCI1410 PC card Cardbus Controller
pci@00:0b.0            network        Broadcom Corporation
pci@00:18.0            bridge         K8 [Athlon64/Opteron] HyperTransport Technology Configuration
pci@00:18.1            bridge         K8 [Athlon64/Opteron] Address Map
pci@00:18.2            bridge         K8 [Athlon64/Opteron] DRAM Controller
pci@00:18.3            bridge         K8 [Athlon64/Opteron] Miscellaneous Control

```


Also, what do you guys think of this piece of info?
##From this page -->[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#A)

*

# Notebook: Acer Aspire 3023WLMi

    * Kernel 2.6.12 vanilla RPM for Fedora Core 4
    * Chipset: Broadcom Corporation BCM4318 802.11/g Wireless LAN
    * pciid: 14e4:4318
    * Driver: ndiswrapper v1.3rc1 with bcmwl5a.inf or bcmwl5.inf (either works) [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/) (Broadcom, 12/22/2004, v3.100.46.0)
    * Other: acerhk v0.5.27 compiled and loaded with /sbin/modprobe acerhk autowlan=1 poll=0 force_series=5020 verbose=3 usedritek=1. wlan0 can be activated with ifup or the Network Configuration GUI tool. The LED button blinks very dimly when the card is searching for APs. 
-----------

thanks in advance for any help.

---

### Post by redsmoke on 2006-01-02
You need a neweer version of ndiswrapper....get the one from the ndiswrapper homepage and compile and install I did a quick guide on it here: [http://ubuntuforums.org/showthread.php?t=110749](http://ubuntuforums.org/showthread.php?t=110749)

It has to do with 64-bit but instructions should be the same for getting compiled in 32-bit

---

### Post by Tiede on 2006-01-03
Thanks a lot for your help, redsmoke, it was just what I needed.
One question though... Is it safe to delete these folders, remnants of the installation, that are trashing up my home directory?

---

### Post by redsmoke on 2006-01-03
Yes after you installed it it is safe to delete the files from the home directory.

---

