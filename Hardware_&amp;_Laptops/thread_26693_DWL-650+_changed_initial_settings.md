---
title: "DWL-650+ changed initial settings"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by malmjako on 2005-04-13
I have a D-Link DWL-650+ wireless PCMCIA card. In Warty it was working all-right, but I have had some troubles in Hoary. It appears that in Hoary, the card gets different initial settings when inserted:
Hoary:```
Channel = 1
Tx Power = 18 dBm
Rate = 1 Mb/s
```Warty:```
Channel = Auto (or so it seems, anyway)
Tx Power = 20 dBm
Rate = 11 Mb/s
```
This has the effect that waproamd doesn't scan all channels, signal strength is lower, and data rate is slow. I can change these three settings using iwconfig, but only manually. What decides these initial settings? Can I change them?

The same firmware is used, according to dmesg output. The following shows the part of the output from dmesg which reports the initial settings:
Hoary:```
Updating Tx fallback to 1 retries
Updating WEP key settings
Setting WEP key 0 as default.
Updating transmit power: 18 dBm
changing radio power level to 18 dBm (23)
Updating antenna value: 0x8D
Updating Energy Detect (ED) threshold: 112
Updating Channel Clear Assessment (CCA) value: 0x0D
Updating: enable Tx
Updating: enable Rx on channel: 1
Updating short retry limit: 7, long retry limit: 4
Updating xmt MSDU lifetime: 4096
Updating regulatory domain: 0x30
setting RXconfig to 2010:0fdd
Starting radio scan
acx_set_status: Setting status = 1 (SCANNING)
```Warty:```
Updating Tx fallback to 0 retries
Updating WEP key settings
Updating transmit power: 20 dBm
changing radio power level to 20 dBm (0x00)
Updating antenna value: 0x8D
Updating Energy Detect (ED) threshold: 112
Updating Channel Clear Assessment (CCA) value: 0x0D
Updating: enable Tx
Updating: enable Rx
Updating short retry limit: 5, long retry limit: 3
Updating xmt MSDU lifetime: 4096
Updating regulatory domain: 0x30
acx100_set_status: Setting status = 1 (SCANNING)
```
The full dmesg outputs can be found at:
Hoary: [http://www.dd.chalmers.se/~malmjako/dmesg_hoary.out](http://www.dd.chalmers.se/~malmjako/dmesg_hoary.out)
Warty: [http://www.dd.chalmers.se/~malmjako/dmesg_warty.out](http://www.dd.chalmers.se/~malmjako/dmesg_warty.out)

---

### Post by FaQuid on 2005-04-27
I have the same problem so if you have found away to fix it I would aprciate if you could help me out

---

### Post by malmjako on 2005-04-28
Nope, I haven't found a solution yet. Wireless networking has not been a good experience for me on Ubuntu. I haven't tried any other distribution though since I got my laptop, so it might be the same on all of them. Maybe it's just the DWL-650+ card that isn't well supported on Linux. I haven't tried any other cards.

---

### Post by FaQuid on 2005-04-29
Okey, I have got it to work better with ndiswrapper that with the ubuntu drivers so if you what to give that a shoot here is a link[http://http://www.ndeepak.info/tech/wlansarge.php](http://http://www.ndeepak.info/tech/wlansarge.php)
But before it worked for me I hade to disable the ubuntu driver but I can't tell you how becouse a friend did that for me  :?

---

### Post by malmjako on 2005-05-12
Wonderful! It's working for me right now, using ndiswrapper, and I'm going to try it out to see if it's more stable. If so, I'll keep using it.
[QUOTE=FaQuid]But before it worked for me I hade to disable the ubuntu driver but I can't tell you how becouse a friend did that for me  :?[/QUOTE] To disable acx-pci, I added it to /etc/hotplug/blacklist. Did your friend do the same? (Check the end of the file...)

---

### Post by FaQuid on 2005-05-16
No, he just changed the name of the file.

---

