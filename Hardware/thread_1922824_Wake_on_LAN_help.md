---
title: "Wake on LAN help"
date: 2012-02-09
forum: Hardware
---

### Post by thejoester on 2012-02-09
So I am trying to setup my system for Wake on Lan (WOL). 

I ensured it is enabled in the BIOS but it will not work. 

my search found this post: [http://ubuntuforums.org/showthread.php?t=1380776](http://ubuntuforums.org/showthread.php?t=1380776)

So I editied the /etc/network/insterfaces so it reads: 

```
auto lo
iface lo inet loopback

auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
post-up /usr/sbin/ethtool -s eth0 wol g
post-down /usr/sbin/ethtool -s eth0 wol g
```

Then as per the other post I tried running **acpitool -w** and here are the results:```
   Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. PEGP         S4    *disabled  pci:0000:00:01.0
  2. P0P2         S4    *disabled  pci:0000:00:1e.0
  3. AC97         S4    *disabled
  4. USB0         S3    *disabled  pci:0000:00:1d.0
  5. USB1         S3    *disabled  pci:0000:00:1d.1
  6. USB2         S3    *disabled  pci:0000:00:1d.2
  7. USB3         S3    *disabled  pci:0000:00:1d.3
  8. USB7         S3    *disabled  pci:0000:00:1d.7
  9. UAR1         S4    *disabled  pnp:00:06
  10. PEX1        S4    *disabled  pci:0000:00:1c.0
  11. PEX2        S4    *disabled  pci:0000:00:1c.1
  12. PEX3        S4    *disabled  pci:0000:00:1c.2
  13. PEX4        S4    *disabled  pci:0000:00:1c.3
  14. AZAL        S4    *disabled  pci:0000:00:1b.0
  15. PWRB        S4    *enabled

```

I am not sure which one is my LAN card (which is built into the notherboard) so I ran **lspci -v** and the relevant part for my network card reads: ```
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
        Subsystem: Gateway 2000 Device 4037
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at ff8fe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at bc00 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: e100
        Kernel modules: e100

```

can someone please advise me which of these (from **acpitool -w** I need to enable to I can have Wake on Lan?

Many thanks!

---

### Post by ahallubuntu on 2012-02-09
WOL works by MAC (hardware) address not IP, so you don't need to set a static IP.  I didn't - I have nothing in /etc/interfaces for WOL or a static IP.  I have an Ubuntu 10.04 box I regularly wake up with WOL and I recently changed the IP address and didn't change anything with how I woke it up.

I use my DD-WRT (Linux-based) router to wake up my box, using the "wol" command (which you may not have in your /usr/sbin).  Like this:

/usr/sbin/wol  -i 192.168.1.255 xx:xx:xx:xx:xx:xx

Change "192.168.1.255" to match your subnet.
Change "xx:xx:xx:xx:xx:xx" to be the MAC ID ("HWaddr") of the ethernet card you are waking up - find it on that box with the ifconfig command.

I don't remember what else I may have done to my box to make WOL work, but as I said, I needed to put anything in the interfaces file.

Use this page to find the package you'd need on the other box to issue the wol command (My Ubuntu laptop doesn't have it installed, so apparently it's not installed by default.):

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

---

