---
title: "Wireless disappeared on eMachine M5310"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by PhragMunkee on 2006-02-23
I have an eMachine M5310.  I was able to get Ubuntu 5.10 installed beautifully.  I used the Windows driver supplied with the laptop to get the wireless working.  The wireless is a Broadcom BCM4306 802.11b/g Wireless LAN.  The System -> Administration -> Windows Wireless Drivers utility lists a 'bcmwl5' driver as installed and Hardware present is yes.

The wireless was working just a couple of hours ago.  I plugged in the onboard ethernet to copy some large files faster.  When I unplugged the ethernet and tried to use the wireless again, it wouldn't work.  I tried bringing the interface up and down with ifconfig.  I also tried activating and deactivating it with the network utility.  I even tried deactivating and reactivating the onboard LAN.  According to the network utility, it could see my AP's SSID (the AP is a Linksys WAP54G).  I tried renewing the DCHP lease with dhclient and it just timed out.  I tried removing the driver with 'ndiswrapper -e' and re-installed the driver with no problems, but it still doesn't work.  The last few lines of dmesg are:

```
[4296281.289000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4296281.394000] ndiswrapper: driver bcmwl5 (Broadcom,03/19/2003, 3.10.53.0) loaded
[4296281.395000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[4296281.403000] ndiswrapper: using irq 10
[4296281.904000] wlan0: ndiswrapper ethernet device 00:90:96:61:b9:2c using driver bcmwl5, configuration file 14E4:4320:144F:7050.5.conf
[4296281.904000] ndiswrapper (set_auth_mode:517): setting auth mode failed (C0010015)
[4296281.904000] wlan0: encryption modes supported: WEP
```

The results of ifconfig wlan0 are:
```
wlan0     Link encap:Ethernet  HWaddr 00:90:96:61:B9:2C
          inet6 addr: fe80::290:96ff:fe61:b92c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:d0004000-d0005fff
```

The results of iwconfig wlan0 are:
```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I'm don't know what to try next.  Rebooting only makes the interface disappear again.  I'm not sure what to try next.

If anyone can help, it would be greatly appreciated.  Let me know if you need any more information to troubleshoot further.

---

