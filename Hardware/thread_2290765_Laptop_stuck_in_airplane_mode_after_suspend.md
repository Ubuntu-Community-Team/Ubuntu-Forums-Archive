---
title: "Laptop stuck in airplane mode after suspend"
date: 2015-08-15
forum: Hardware
---

### Post by julo42 on 2015-08-15
Hii,

I've just bought an HP Pavilion 15-p158nf laptop, installed Ubuntu 15.04 on it, and I'm having trouble with suspend: each time I suspend / resume, the laptop sets itself in "airplane mode" and there's no way to turn it off, short of rebooting the laptop.

Before I suspend, here's what rfkill list all shows:

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

And after suspend, it shows this:

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Notice how the bluetooth part suddenly disappeared, and the wifi is blocked.

I tried pressing the "airplane" button, but it doesn't change a thing. I also tried running rfkill unblock all, and it failed too.

Also, I created /etc/modprobe.d/rtl8723be.conf with the following: options rtl8723be fwlps=0 swlps=0 ips=0
But it didn't help either.

Any help is very welcome!

---

### Post by NoWayWin8 on 2015-08-16
Right-click on "Nerwork Manager" icon and make sure there's a checkmark next to "Enable WiFi". The system can't override the physical wifi switch, so if it's in the wrong state the wifi can't turn on (a power cycle always fixes it).
> Also, I created /etc/modprobe.d/rtl8723be.conf with the following: options rtl8723be fwlps=0 swlps=0 ips=0
I don't now if the options are right or not, but does output of **sudo lshw -C network** list that exact driver (rtl8723be) in the wireless lan configuration?

---

### Post by julo42 on 2015-08-18
Indeed there is an "Air plane mode" item in the network-manager icon, but it's greyed out and it says: "use the hardware toggle to de-activate it". And if I try to re-activate the wifi via the network properties, it doesn't work: the toggle goes back to "inactive" immediately. Pressing the hardware button, of course, doesn't work either.

As for your question, here' the output of lshw -C network:

  *-network               
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 74:29:af:1b:61:3b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.2.0-040200rc6-generic firmware=N/A ip=192.168.1.51 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:5000(size=256) memory:b5500000-b5503fff

---

### Post by julo42 on 2015-08-19
I just reset my BIOS settings and the bug is now gone. Thanks for your help, and sorry for the noise!

---

