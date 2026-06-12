---
title: "USB Wifi dongle disconnects periodically with kernel 3.0.0.16.19"
date: 2012-02-29
forum: Hardware
---

### Post by Destruct0r on 2012-02-29
Hi guys
I have upgraded my kernel on Ubuntu 11.10 from 3.0.0.12.14 to 3.0.0.16.19. Now my USB Wifi dongle (loads module r8712u with firmware rtl8712u.bin) disconnects periodically.  About every 4th time the connection establishes, and it works, but rarely for more than 30 min.

I tried booting into the old kernel, but the problem persisted.  Did the firmware get upgraded as well?  Or does the new module get loaded with the old kernel?

I doubt that the signal strenght is the problem as all my other devices (including this PC when it actually connects) gets 5/5 signal.

What I have discovered after Googleing is that changing my security settings from WPA-PSK+WPA2-PSK to WPA2-PSK actually solves this problem.  Is this a bug in the firmware/kernel module?

Anyone else experiencing this problem?  Shall I log it in launchpad?

Some info that might be useful, this with the connection being stable.

```
uname -a
Linux htpc 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 athlon i386 GNU/Linux

# lsusb
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN
Adapter

#iwconfig
wlan1     IEEE 802.11bg  ESSID:"YOURDOGPOOPSONMYLAWN"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1B:2F:97:B5:86
          Bit Rate:54 Mb/s   Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=86/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

