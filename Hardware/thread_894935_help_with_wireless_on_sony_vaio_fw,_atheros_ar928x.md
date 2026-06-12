---
title: "help with wireless on sony vaio fw, atheros ar928x chipset"
date: 2008-08-19
forum: Hardware
---

### Post by BitJ on 2008-08-19
I have been trying to put my wireless to work, on a sony vaio fw, ubuntu hardy heron, wireless atheros ar928x chipset

I think my problem begins with this

@BITJ:~$ lspci 
06:00.0 Network controller: Atheros Communications Inc.Unknown device 002a (rev 01) 
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)

First I tried with madwifi, my chipset driver is not listed yet, even tough I tried

sudo modprobe ath_pci 
wlanconfig ath0 create wlandev wifi0 wlanmode sta 
sudo modprobe ath_pci wlanconfig ath0 create wlandev wifi0 wlanmode sta

It returned "wlanconfig: ioctl: No such device", I think this is because of the Unknown device that I recieve with the lspci command. It's weird, because with the device manager, I can see the network controller, but there is not any "networking interface", but the wired controller has an interface.

Then I tried with ndiswrapper, using the GUI and the command line, both of then showed me that it was ok, I use the drivers that I download from [http://www.atheros.cz/](http://www.atheros.cz/), after that I thought that maybe I was using the wrong drivers, so I took them from the DRIVERS folder on my windows vista, but I had the same result. I used the xp and vista drivers, and this is the response that I had

XP drivers install
@BITJ:~$ sudo ndiswrapper -i /media/disk/Users/BitJ/Downloads/xp32-7.6.0.239-whql/netathw.inf  
@BITJ:~$ ndiswrapper -l netathw : driver installed 
    device (168C:002A) present 
@BITJ:~$ sudo depmod -a 
@BITJ:~$ sudo modprobe ndiswrapper

...after restart

@BITJ:~$ dmesg  
[   35.432010] ndiswrapper (link_pe_images:604): DLL initialize failed for athw.sys 
[   35.432037] ndiswrapper: driver netathw (,06/27/2008,7.6.0.239) loaded 
[   35.432244] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 18 
[   35.432256] ndiswrapper (mp_init:207): assuming WDM (non-NDIS) driver 
[   35.454544] ACPI: PCI Interrupt 0000:01:00.1<span style='font-weight: bold;'> -> GSI 17 (level, low) -> IRQ 17 
[   35.454565] PCI: Setting latency timer of device 0000:01:00.1 to 64 
[   35.456749] usbcore: registered new interface driver ndiswrapper 
[   35.504429] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 16 (level, low) -> IRQ 16 
[   35.504459] PCI: Setting latency timer of device 0000:08:00.0 to 64 
[   35.504587] sky2 0000:08:00.0: v1.20 addr 0xd0120000 irq 16 Yukon-EC Ultra (0xb4) rev 3 
[   35.505919] sky2 eth0: addr 00:1d:ba:18:d7:b6 
[   35.979614] lp: driver loaded but no devices found 

Vista Drivers
After installing, I got this

@BITJ:~$ tail /var/log/messages 
Aug 18 19:09:49 BITJ kernel: [ 2453.370983] usbcore: deregistering interface driver ndiswrapper 
Aug 18 19:09:49 BITJ kernel: [ 2453.382368] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
Aug 18 19:09:49 BITJ loadndisdriver:loadndisdriver:load_driver(358): couldn't load driver netathr  
Aug 18 19:09:49 BITJ kernel: [ 2453.394460] usbcore: registered new interface driver ndiswrapper

Some information

@BITJ:~$ uname -a 
Linux BITJ 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux 
@BITJ:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:18:d7:b6   
          inet addr:192.168.1.100  Bcast:192.168.1.255 Mask:255.255.255.0 
          inet6 addr: fe80::21d:baff:fe18:d7b6/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:6630 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:6176 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:6446998 (6.1 MB)  TX bytes:1028481 (1004.3 KB) 
          Interrupt:16  
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2044 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2044 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:102200 (99.8 KB)  TX bytes:102200 (99.8 KB)  

@BITJ:~$ iwconfig 
lo        no wireless extensions. 
eth0      no wireless extensions. 


@BITJ:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Network controller 
       product: Atheros Communications Inc. 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper 
  *-network 
       description: Ethernet interface 
       product: 88E8055 PCI-E Gigabit Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: eth0 
       version: 13 
       serial: 00:1d:ba:18:d7:b6 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.100 latency=0 module=sky2 multicast=yes 


thanks in advance...

---

### Post by Libertine on 2008-08-20
I have this same laptop and problem! Any help would be appreciated :)

---

### Post by BitJ on 2008-08-21
Well, it's working now, as Libertine told me, here in this post you can find how to install the new atheros drivers, after that you just have to configure your wireless settings 

[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)

---

