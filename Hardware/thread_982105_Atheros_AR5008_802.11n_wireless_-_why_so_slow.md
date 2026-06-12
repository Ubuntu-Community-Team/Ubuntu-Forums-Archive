---
title: "Atheros AR5008 802.11n wireless - why so slow?"
date: 2008-11-14
forum: Hardware
---

### Post by Aaron44126 on 2008-11-14
I have a laptop with a wireless card with the Atheros AR5008 802.11n chipset.

When I'm connected to an 802.11b or g network, the speed seems reasonable.  However, when I am connected to an 802.11n network, the speed seems unreasonably slow.  I checked iwconfig and got this info:

```
wlan0     IEEE 802.11abgn  ESSID:"Vanguard Airport Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:63:2C:C5:54   
          Bit Rate=1 Mb/s   Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=73/100  Signal level:-48 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
...Huh?  1 Mb/s?  Under Windows, I connect to this access point at 130 Mb/s.

If it matters, the access point is one of those Apple Airport Extreme base stations.  We have a few of them set up as access points only.  This is the only 802.11n hardware I have to test with.

Anyone seen something like this before, or have any ideas of how to kick my wireless card into gear?

Thanks.

---

### Post by Gizmonty on 2008-11-16
I also have this issue with an Atheros AR5008 PCIe card (D-Link DWA-556). My iwconfig is essentially identical. There doesn't seem to be a solution posted anywhere. Can anyone shed some light?

---

### Post by Aaron44126 on 2008-11-16
I messed with this some yesterday and figured out how to load the latest version of the wireless drivers from here: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

I haven't had a chance to test it yet to see if there is any difference.  I'm going to be trying it out tomorrow.

If it works better, I will post directions here on getting those drivers compiled and loaded.  If it doesn't work, I'll file a bug report against ath9k at wireless.kernel.org, where the development seems to be going on.

---

### Post by Aaron44126 on 2008-11-17
Sorry for double posting but I wanted to report my results.

The ath9k driver dated November 10, 2008 performs much better.  But I got a kernel panic after a short while of using it so I went back to the original, slow driver.  :-P

Some numbers:

Transferring from an FTP server on my LAN.
With the stock Ubuntu driver I get about 220 KB/sec.
With the newer driver I get a little over 3 MB/sec.

Hopefully they'll fix it up and it'll make its way into the kernel eventually.

I've noted all of this in my Ubuntu bug:
[https://bugs.launchpad.net/ubuntu/+bug/298192](https://bugs.launchpad.net/ubuntu/+bug/298192)

---

### Post by Aaron44126 on 2008-11-17
[Edit]
This was an accidental double post that I did not intend!

---

