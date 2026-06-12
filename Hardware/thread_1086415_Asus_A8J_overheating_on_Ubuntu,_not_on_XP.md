---
title: "Asus A8J overheating on Ubuntu, not on XP"
date: 2009-03-04
forum: Hardware
---

### Post by jackn on 2009-03-04
My Asus A8J was working fine for two years or more.
I now run Hardy 8.04.
It was overheating, I now think, but I didn't realize this.

Now, it is overheating so much, that it will turn off suddenly, without properly shutting down.
The laptop regularly reaches 90-100C within minutes after starting up. 

When I start up XP on the same laptop, this doesn't happen.

In the forums, the only viable advice I've been able to find was to use kpowersave.
I installed it, but, probably because I run Gnome, while it installed, it didn't give me a graphic interface to modify the settings.

Help?
Thanks,
Jackn

---

### Post by Fir3chi3f on 2009-03-04
kpowersave should still work under gnome, i don't know if it has a graphical interface though.

have you tried 8.10? 
does it overheat with just the liveCD?
output of dmesg?

---

### Post by jackn on 2009-03-04
> **Fir3chi3f said:**
> kpowersave should still work under gnome, i don't know if it has a graphical interface though.

have you tried 8.10? 
does it overheat with just the liveCD?
output of dmesg?

No, I haven't tried 8.10.
Should I? with a live CD?
As far as live CD goes, I have tried with the Kubuntu 8.04 live CD, and it was overheating.

I can't tell from what point in time the dmesg output comes from, but here is the latest stuff from the /var/log/dmesg file as it is now:
```
[   41.675419] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 23
[   41.675440] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   41.847173] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   41.847558] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   42.370204] lp: driver loaded but no devices found
[   42.622752] Adding 2931820k swap on /dev/sda7.  Priority:-1 extents:1 across:2931820k
[   43.400948] NET: Registered protocol family 10
[   43.401207] lo: Disabled Privacy Extensions
[   43.402130] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.428786] NET: Registered protocol family 17
[   43.466227] EXT3 FS on sda5, internal journal
[   44.751138] wlan0: Initial auth_alg=0
[   44.751145] wlan0: authenticate with AP da:2d:b6:75:da:21
[   44.760948] wlan0: RX authentication from da:2d:b6:75:da:21 (alg=0 transaction=2 status=0)
[   44.760952] wlan0: authenticated
[   44.760956] wlan0: associate with AP da:2d:b6:75:da:21
[   44.961665] wlan0: associate with AP da:2d:b6:75:da:21
[   45.157529] wlan0: associate with AP da:2d:b6:75:da:21
[   45.357415] wlan0: association with AP da:2d:b6:75:da:21 timed out
[   46.378407] kjournald starting.  Commit interval 5 seconds
[   46.378571] EXT3 FS on sda8, internal journal
[   46.378578] EXT3-fs: mounted filesystem with ordered data mode.
[   46.422471] kjournald starting.  Commit interval 5 seconds
[   46.422637] EXT3 FS on sda6, internal journal
[   46.422643] EXT3-fs: mounted filesystem with ordered data mode.
[   47.979143] RPC: Registered udp transport module.
[   47.979146] RPC: Registered tcp transport module.
```

Here's the latest from /var/log/syslog:
```
Mar  4 12:38:16 itamar dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Mar  4 12:38:24 itamar dhclient: No DHCPOFFERS received.
Mar  4 12:38:24 itamar dhclient: No working leases in persistent database - sleeping.
Mar  4 12:38:40 itamar kernel: [  518.381211] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:39:11 itamar kernel: [  549.431811] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:39:42 itamar kernel: [  580.478075] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:40:13 itamar kernel: [  611.529594] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:40:44 itamar kernel: [  642.571917] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:41:15 itamar kernel: [  673.617446] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:41:46 itamar kernel: [  704.667787] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:42:17 itamar kernel: [  735.727320] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:42:44 itamar dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Mar  4 12:42:48 itamar kernel: [  766.777723] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:42:53 itamar dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Mar  4 12:43:02 itamar dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Mar  4 12:43:16 itamar dhclient: No DHCPOFFERS received.
Mar  4 12:43:16 itamar dhclient: No working leases in persistent database - sleeping.
Mar  4 12:43:19 itamar kernel: [  797.847255] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:43:50 itamar kernel: [  827.894113] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 
Mar  4 12:44:21 itamar kernel: [  858.940696] Unknown OutputIN= OUT=wlan0 SRC=169.254.9.85 DST=169.254.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=185 

```
I can't read this.
I did notice acpi, namely power management, at the beginning of the dmesg output, for what it's worth, but can't make heads or tails out of it.
I'm now at 90C.

Help?
Jackn

---

