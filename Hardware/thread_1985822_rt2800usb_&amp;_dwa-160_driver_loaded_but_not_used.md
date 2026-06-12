---
title: "rt2800usb &amp; dwa-160: driver loaded but not used"
date: 2012-05-23
forum: Hardware
---

### Post by jaysscholar on 2012-05-23
My ultimate goal is get a D-Link DWA-160 (Rev B2) dual band wifi adapter working with Ubuntu Precise. According to [wikidevi]("http://wikidevi.com/wiki/D-Link_DWA-160_rev_B2") , I need the rt2800usb driver from compat-wireless. I have loaded that driver on my machine.

Now, I have two issues. First, the rt2800usb doesn't seem to load up at startup. Second, and more importantly, when the adapter is plugged in (and after I've manually loaded the driver with modprobe), it doesn't seem to do anything or talk to the driver. There's no blinking lights and dmesg says there was a usb plugged in, but there is no response.

Here's on startup:
```
# lsmod | grep rt
parport_pc             32866  0
parport                46562  3 parport_pc,ppdev,lp
```Then I load up rt2800usb manually:
```
# sudo modprobe rt2800usb
# lsmod | grep rt
rt2800usb              22615  0
rt2800lib              58586  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20618  1 rt2800usb
rt2x00lib              54769  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              543880  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              210370  2 rt2x00lib,mac80211
compat                 13447  6 rt2800usb,mac80211,cfg80211,rfcomm,bnep,bluetooth
parport_pc             32866  0
parport                46562  3 parport_pc,ppdev,lp
```This is what dmesg says in response to the rt2800usb driver being loaded:
```
[  386.224143] cfg80211: Calling CRDA to update world regulatory domain
[  386.273841] usbcore: registered new interface driver rt2800usb
[  386.325853] cfg80211: World regulatory domain updated:
[  386.325856] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  386.325857] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  386.325859] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  386.325861] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  386.325862] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  386.325863] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```Afterward, I unplug and plug back in the adapter, and I get this from dmesg:
```
[  489.974815] usb 2-1.4: USB disconnect, device number 4
[  494.005911] usb 2-1.4: new high-speed USB device number 6 using ehci_hcd
```It sees it got plugged in, but didn't start using a driver. It just goes silent. 

In debugging this, I've also noticed that my usb.ids file does not have the id of the DWA-160. Here's the relevant part of lsusb:
```
# lsusb
Bus 002 Device 006: ID 2001:3c1a D-Link Corp.
```That 3c1a is not in my usb.ids file. The update-usbs command doesn't fix that. Interestingly, 3c10, the same adapter but with a Atheros chip, is in the file. It also has 3c11, which is the same adapter, similar Ralink chip, but different revision (B1 as opposed to B2).
```
# cat /var/lib/usbutils/usb.ids | grep 3c1a
# cat /var/lib/usbutils/usb.ids | grep 3c10
    3c10  DWA-160 802.11abgn Xtreme N Dual Band Adapter(rev.A1) [Atheros AR9170+AR9104]
# cat /var/lib/usbutils/usb.ids | grep 3c11
    3c11  PSC 1358
    3c11  DWA-160 Xtreme N Dual Band USB Adapter(rev.B) [Ralink RT2870]
```I'm not sure if that's an issue. I'm not too familiar with the usb.ids file. 

I have another single band usb adapter (AirLink 101) that I can plug in just fine. (It's how I'm able to post this.) When I plug it in, I get chatter on the dmesg as the r8712u driver seems to be talking to the adapter:
```
[ 1350.817700] usb 1-1.4: new high-speed USB device number 4 using ehci_hcd
[ 1350.977318] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[ 1350.978419] r8712u: DriverVersion: v7_0.20100831
[ 1350.978427] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1350.978429] r8712u: USB_SPEED_HIGH with 4 endpoints
[ 1350.978970] r8712u: Boot from EFUSE: Autoload OK
[ 1351.656388] r8712u: CustomerID = 0x0000
[ 1351.656393] r8712u: MAC Address from efuse = 00:21:2f:39:e9:ec
[ 1351.656395] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1351.656535] usbcore: registered new interface driver r8712u
[ 1351.792439] udevd[2654]: renamed network interface wlan0 to wlan1
[ 1352.503817] r8712u: 1 RCR=0x153f00e
[ 1352.504687] r8712u: 2 RCR=0x553f00e
[ 1352.612020] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1352.612272] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1352.959462] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1363.539924] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1363.544880] r8712u: [r8712_got_addbareq_event_callback] mac = 14:d6:4d:c5:e6:4e, seq = 32, tid = 0
[ 1374.409688] wlan1: no IPv6 routers present

```I'm assuming the DWA-160 and rt2800usb should be doing something similar.

Any ideas as to why the the adapter isn't doing anything when plugged in? Do I need to blacklist something else in order for rt2800usb to take over? 

Assuming I can get that solved, I'd next like to get it loading on startup, though that's of secondary importance at this stage. Any ideas are appreciated. 

Here's some info about my system if it helps:
```
$ uname -a
Linux nickelnine 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
``````
$ modinfo rt2800usb 
filename:       /lib/modules/3.2.0-24-generic/updates/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D8D7FBCA519895159356605
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2800lib,rt2x00usb,compat
vermagic:       3.2.0-24-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

---

