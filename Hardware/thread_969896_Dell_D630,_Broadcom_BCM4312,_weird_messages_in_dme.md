---
title: "Dell D630, Broadcom BCM4312, weird messages in dmesg"
date: 2008-11-03
forum: Hardware
---

### Post by sagyvolkov on 2008-11-03
I've noticed this in 8.04 and now also in 8.10
my syslog is full of:
[125820.894453] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=f5150b40
[125821.201591] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=f5150b40
[125821.202645] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=f5150b40
[125821.203960] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=f5150b40
[125821.816096] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=f5150b40
[125822.124604] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=f5150b40
[125822.737518] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=f5150b40

Wireless is working perfectly (much better in 8.10), yet this is annoying.
Anyone have this problem or knows how to disable this?

Thanks.

---

### Post by effenberg0x0 on 2008-11-29
Same thing here for DELL Vostro 1310. I have no clue.

[12751.589630] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12752.706557] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12771.558240] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12791.629200] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12808.106755] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12808.107634] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12811.597864] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12818.756705] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12827.768202] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12831.668647] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12851.637180] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12871.708215] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12891.676826] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12893.818107] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12902.727174] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12911.748094] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12931.716558] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0
[12951.787531] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ee7a8cc0

Regards,
Effenberg

---

### Post by kratib on 2008-12-01
Same thing happening on my MacBook Pro with Broadcom BCM4328 802.11a/b/g/n. 
```

TKIP: RX tkey->key_idx=2 frame keyidx=1 priv=f2275780

```
over and over again.

---

### Post by effenberg0x0 on 2008-12-03
Are you guys seeing any effects of this behavior in the overall functioning of your network connection?

Since this problem started, I noticed my wireless router is more overloaded, to a point in which it drops other machine's connections. I still haven't found a way to debug this.

---

### Post by effenberg0x0 on 2008-12-10
Disabling TKIP in my wireless router (Linksys WRT54G running DD-WRT) fixed it. No more weird mesgs.

---

### Post by mocho on 2009-01-17
I also have this error in my hp laptop with braodcom 4321 a-b-g-n 

first when i turn my computer on wireless works great but after some minutes i start getting this messages and wirreless crawls very slowly

I also noticed that this driver also displays some strange results concerning tx power, much higher than it should (can this be why i've read that ubuntu kills broadcom wireless cards ?)

#sudo iwlist txpower

eth1 2 available transmit-powers :
   0 dBm (1 mW)
   25 dBm (255 mW)
          Current Tx-Power:32 dBm (1496 mW)

also i can not set this driver to activate the European extra channels 12 & 13 with adding

options cfg80211 ieee80211_regdom=EU

to /etc/modprobe.d/options

---

### Post by swajime on 2010-01-16
almost 1 year later ...
Thousands of "TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=eceb5180" in the logs

eth1      2 available transmit-powers :
	  0 dBm  	(1 mW)
	  25 dBm  	(255 mW)
          Current Tx-Power:32 dBm  	(1496 mW)

/var/log# grep -c 'TKIP: RX tkey->key_idx' *|grep -v ':0$'
debug:76679
kern.log:76658
syslog:11549
syslog.1:40668

---

### Post by nrune on 2010-01-18
This bug continues...

 TKIP: RX tkey->key_idx=1 frame keyidx=2

Over and over,

I disabled tkip and sticking with AES and my speeds on the system realy increased, and loads really dropped off.

---

