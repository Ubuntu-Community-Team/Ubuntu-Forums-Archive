---
title: "Wireless network connected but no IP"
date: 2004-10-19
forum: Hardware &amp; Laptops
---

### Post by kazpox on 2004-10-19
I have some problems with my wireless network card (Topcom Skyr@cer 3011 = Realtek 8180) on my Packard Bell E1245 laptop.

It seems to work allright with ndiswrapper though:

```

  # ndiswrapper -l
  &#40;...&#41;
  Installed ndis drivers&#58;
  netr8180        hardware present

```

Also it is able to find the hotspot with "iwlist wlan0 scan" and according to "iwconfig", it seems to be able to connect to it as well. I thought this would indicate that everything works fine, however my laptop doesn't get an IP, so it cannot connect to the Internet.

When I boot in Aquamorph 0.2 (Morphix/Knoppix derivative) it works just fine and I get an IP.

Using Ubuntu I get some error on boot. Maybe they are related to this problem. (?) (Error messages etc. are listed at the end of this meassage.) I really think it's strange that wireless works in Aquamorph but not in Ubuntu.

Any ideas on what to do? Some hints to get me started? Do I need to post additional outputs?

Thanks in advance,
Kasper

PS. Sorry for the long post, but I didn't want to leave out anything important :-)

-------------------------------------
DIFFERENT OUTPUTS AND ERROR MESSAGES:
-------------------------------------
[some values are substitued with "X"]

***********************
Output from "iwconfig":
***********************

```

lo        no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID&#58;&quot;hotspot&quot;
          Mode&#58;Managed  Frequency&#58;2.412GHz  Access Point&#58; 00&#58;0D&#58;9D&#58;XX&#58;XX&#58;XX
          Bit Rate&#58;11Mb/s   Tx-Power&#58;20 dBm   Sensitivity=0/3
          RTS thr&#58;2432 B   Fragment thr&#58;2432 B
          Encryption key&#58;off
          Power Management&#58;off
          Link Quality&#58;100/100  Signal level&#58;-64 dBm  Noise level&#58;-256 dBm
          Rx invalid nwid&#58;0  Rx invalid crypt&#58;0  Rx invalid frag&#58;0
          Tx excessive retries&#58;0  Invalid misc&#58;0   Missed beacon&#58;0

```

***********************
Output from "ifconfig":
***********************

```

lo        Link encap&#58;Local Loopback
          inet addr&#58;127.0.0.1  Mask&#58;255.0.0.0
          inet6 addr&#58; &#58;&#58;1/128 Scope&#58;Host
          UP LOOPBACK RUNNING  MTU&#58;16436  Metric&#58;1
          RX packets&#58;8832 errors&#58;0 dropped&#58;0 overruns&#58;0 frame&#58;0
          TX packets&#58;8832 errors&#58;0 dropped&#58;0 overruns&#58;0 carrier&#58;0
          collisions&#58;0 txqueuelen&#58;0
          RX bytes&#58;657337 &#40;641.9 KiB&#41;  TX bytes&#58;657337 &#40;641.9 KiB&#41;

wlan0     Link encap&#58;Ethernet  HWaddr 00&#58;E0&#58;98&#58;XX&#58;XX&#58;XX
          inet6 addr&#58; fe80&#58;&#58;2e0&#58;98ff&#58;XXXX&#58;XXXX/64 Scope&#58;Link
          UP BROADCAST RUNNING MULTICAST  MTU&#58;1500  Metric&#58;1
          RX packets&#58;77 errors&#58;0 dropped&#58;0 overruns&#58;0 frame&#58;0
          TX packets&#58;16 errors&#58;0 dropped&#58;0 overruns&#58;0 carrier&#58;0
          collisions&#58;0 txqueuelen&#58;1000
          RX bytes&#58;9705 &#40;9.4 KiB&#41;  TX bytes&#58;4140 &#40;4.0 KiB&#41;
          Interrupt&#58;7 Memory&#58;10800000-10800024

```

*************
From "dmesg":
*************

```

PnPBIOS&#58; Scanning system for PnP BIOS support...
PnPBIOS&#58; Found PnP BIOS installation structure at 0xc00ff020
PnPBIOS&#58; PnP BIOS version 1.0, entry 0xea000&#58;0x382a, dseg 0xea000
PNPBIOS fault.. attempting recovery.
PnPBIOS&#58; Warning! Your PnP BIOS caused a fatal error. Attempting to continue
PnPBIOS&#58; You may need to reboot with the &quot;nobiospnp&quot; option to operate stably
PnPBIOS&#58; Check with your vendor for an updated BIOS
PnPBIOS&#58; dev_node_info&#58; unexpected status 0x28
PnPBIOS&#58; Unable to get node info.  Aborting.

```

(...I tried to boot with "nobiospnp" but it didn't work.)

(...)

```

vesafb&#58; probe of vesafb0 failed with error -6

```

(...)

 I get some modprobe errors (that is not in the dmesg output)
 on pciehp and shpchp when booting. The modules can't be loaded. In the
 dmesg output, they reappears as:

```

pciehp&#58; acpi_pciehprm&#58;\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp&#58; acpi_pciehprm&#58;get_device PCI ROOT HID fail=0x5
shpchp&#58; acpi_shpchprm&#58;\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp&#58; acpi_shpchprm&#58;get_device PCI ROOT HID fail=0x5

```

(...)

```

ndiswrapper version 0.10 loaded &#40;preempt=yes,smp=no&#41;
PCI&#58; Enabling device 0000&#58;02&#58;00.0 &#40;0000 -&gt; 0003&#41;
ACPI&#58; PCI interrupt 0000&#58;02&#58;00.0&#91;A&#93; -&gt; GSI 7 &#40;level, low&#41; -&gt; IRQ 7
PCI&#58; Setting latency timer of device 0000&#58;02&#58;00.0 to 64
ndiswrapper&#58; using irq 7
wlan0&#58; ndiswrapper ethernet device 00&#58;e0&#58;98&#58;XX&#58;XX&#58;XX using driver rtl8180.sys
ndiswrapper&#58; driver rtl8180.sys &#40;CardBus,03/13/2003,5.130.0313.2003&#41; added
wlan0&#58; no IPv6 routers present

```

*******************************
Output from "iwlist wlan0 scan"
*******************************

```

wlan0     Scan completed &#58;
          Cell 01 - Address&#58; 00&#58;0D&#58;9D&#58;XX&#58;XX&#58;XX
                    ESSID&#58;&quot;hotspot&quot;
                    Protocol&#58;IEEE 802.11b
                    Mode&#58;Managed
                    Frequency&#58;2.412GHz &#40;channel 1&#41;
                    Quality&#58;0/100  Signal level&#58;-53 dBm  Noise level&#58;-256 dBm
                    Encryption key&#58;off
                    Bit Rate&#58;1Mb/s
                    Bit Rate&#58;2Mb/s
                    Bit Rate&#58;5.5Mb/s
                    Bit Rate&#58;11Mb/s
                    Bit Rate&#58;6Mb/s
                    Bit Rate&#58;12Mb/s
                    Bit Rate&#58;24Mb/s
                    Bit Rate&#58;36Mb/s
                    Bit Rate&#58;14.5Mb/s
                    Bit Rate&#58;20.5Mb/s
                    Bit Rate&#58;10Mb/s
                    Bit Rate&#58;1.5Mb/s
                    Bit Rate&#58;1.5Mb/s
                    Bit Rate&#58;1.5Mb/s
                    Bit Rate&#58;1.5Mb/s
                    Bit Rate&#58;1.5Mb/s
                    Extra&#58;bcn_int=100

```

*************************
"ifup wlan0" doesn't help
*************************

```

Internet Systems Consortium DHCP Client V3.0.1rc140&quot;
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http&#58;//www.isc.org/products/DHCP

sit0&#58; unknown hardware address type 776
sit0&#58; unknown hardware address type 776
Listening on LPF/wlan0/00&#58;e0&#58;98&#58;XX&#58;XX&#58;XX
Sending on   LPF/wlan0/00&#58;e0&#58;98&#58;XX&#58;XX&#58;XX
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9

```

(... then times out)
(... And what is "sit0"? It's not mentioned in /etc/network/interfaces.)

***********************
/etc/network/interfaces
***********************

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

```

******
Other:
******

After booting into X, the standard X mouse cursor remains in the middle of the screen for a long time.

---

### Post by xy77 on 2005-04-26
similar problem as here: [http://www.ubuntuforums.org/showthread.php?t=22363](http://www.ubuntuforums.org/showthread.php?t=22363)

I have this problem as well, not being able to figure out the solution yet, so please post something, if you know a solution or a hint, thanks.

- David (xy77)

---

