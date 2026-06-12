---
title: "after restoring backup, cannot enable wifi"
date: 2009-02-20
forum: Hardware
---

### Post by johnnyhostile on 2009-02-20
I made a huge error and formatted my Ubuntu partition by mistake, but was able to restore it from a backup that I made.

The ONLY thing that is not working is my wifi, for example when I right click the network connections there is no options to enable wireless, it's like it doesn't even recognize my hardware. I have a switch to turn the wireless of on the machine, but I never had to use that before - and it still doesn't work.

I am using a Lenovo Thinkpad T60 with Hardy (8.04.2), and I am still trying to figure out exactly which wifi card I have.

Any thoughts?

---

### Post by johnnyhostile on 2009-02-20
I guess my second noob question is, how do I tell which wifi card I have?

---

### Post by johnnyhostile on 2009-02-20
> **johnnyhostile said:**
> I guess my second noob question is, how do I tell which wifi card I have?

larry@larry-laptop:~$ lspci

03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

Thank you Google ;)

---

### Post by johnnyhostile on 2009-02-20
larry@larry-laptop:~$ sudo lshw

*-network UNCLAIMED
                description: Ethernet controller
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list
                configuration: latency=0

---

### Post by sharathpaps on 2009-02-20
Hey,   
          Try issuing the following commands and see if it works for you. 

Check if the pci device is enabled by using : ```
lspci
```

Then, if you can see the device (You'll find a reference to the Ethernet Controller on your system in the output of the above command)

Then, ```
sudo lshw -C network
```

Then, ```
sudo ifconfig wlan0 down
```

and finally, ```
sudo ifconfig wlan0 up
```

I have managed to enable wireless on my friends laptop with this. Hope it works for you. Please do let me know.

---

### Post by johnnyhostile on 2009-02-20
Thanks for the reply!!

larry@larry-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

larry@larry-laptop:~$ sudo lshw -C network
Password or swipe finger:
*-network UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

larry@larry-laptop:~$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device

larry@larry-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device


I have been trying to figure out what '*-network UNCLAIMED' means... I think that is the key...

---

### Post by sharathpaps on 2009-02-20
> **johnnyhostile said:**
> 
I have been trying to figure out what '*-network UNCLAIMED' means... I think that is the key...

I think so too... Try going through this [Wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") to see if it will help you.

---

### Post by johnnyhostile on 2009-02-21
I will have to read through that... I am at work now though so later I guess...

Thanks for the input!

---

### Post by johnnyhostile on 2009-02-24
Hey just thought you might be interested to know, after I got home and fired up my machine... the wifi was just working.

*shrugs

Anyways, thanks for your help!!

---

