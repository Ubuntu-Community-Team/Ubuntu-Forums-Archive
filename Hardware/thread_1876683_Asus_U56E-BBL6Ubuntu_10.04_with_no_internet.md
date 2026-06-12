---
title: "Asus U56E-BBL6/Ubuntu 10.04 with no internet"
date: 2011-11-06
forum: Hardware
---

### Post by lam@uff on 2011-11-06
I am fairly new to Linux and completely new to Ubuntu.
I bought a laptop and installed 10.04 as a dual-boot.  The connection was fine but the laptop bricked up.  I had to return it and get a replacement.
New laptop, same model - the Win7 connects fine but the Ubuntu never has on this machine.

I've tried the 'Network Connections' tab, etc.  I've followed the posts and tried the commands in terminal and as near as I can figure out the system doesn't 'see' the Atheros hardware.

Hardware should be an Atheros AR8151 PCI-E Gigabit Ethernet Controller (NDIS 6.20) but I had to check another machine to get that.

Is there a simple way to correct this?  I really need to get this online or change distros.


[LEFT]sudo lshw -C network  

[/LEFT]
    *-network UNCLAIMED      
        description: Network controller  
        product: Intel Corporation  
        vendor: Intel Corporation  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        version: 67  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: latency=0  
        resources: memory:de800000-de801fff  
   *-network UNCLAIMED  
        description: Ethernet controller 
        product: Atheros Communications  
        vendor: Atheros Communications  
        physical id: 0  
        bus info: pci@0000:04:00.0  
        version: c0  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress vpd bus_master cap_list  
        configuration: latency=0  
        resources: memory:dd400000-dd43ffff ioport:a000(size=128



ifconfig  

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:264 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:264 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:20564 (20.5 KB)  TX bytes:20564 (20.5 KB)

---

### Post by diasf on 2011-11-06
For starters, don't consider the machine as the same as the previous one. The chips can be quite different. Yes, with the same model number for the computer.

How about lspci? dmesg?

---

### Post by lam@uff on 2011-11-06
Thank you for such a fast response.

I only said 'should be.  I think I wasn't clear, I bought two on the first day.  They were the same maker and model, bought in the same store on the same day but that only means so much.  It was one of those that had to be returned for exchange.

dmesg | grep -i eth0 yields nothing but a new prompt

and

                                                     lspci gets 


  
 00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)  
 00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)  
 00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)  
 00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)  
 00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)  
 00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)  
 00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)  
 00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)  
 00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)  
 00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)  
 00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 05)  
 00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)  
 00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)  
 02:00.0 Network controller: Intel Corporation Device 0885 (rev 67)  
 03:00.0 USB Controller: Device 1b21:1042  
 04:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)

---

