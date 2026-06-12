---
title: "Wireless problem - changing kernel modules"
date: 2008-08-12
forum: Hardware
---

### Post by krastanov on 2008-08-12
Hi,

I am quite new to Linux, but I have what I believe is a bit advanced problem. In the campus of the school we have free wifi spot but I am unable to connect from ubuntu - it detects the network but after attempting for few minutes to connect it fails. Or worse - it says it's connected but still I can't browse anything (and reports zero signal). Iwlist scan detects the network and reports good quality(sometimes fails with "resource temporally unavailable").

The strange thing is that under Fedora 9 I connect with no problems(and it needs only 5-10 seconds). I suspected it has to do with some kernel modules - so I checked the differences between fedora's and ubuntu's modules and loaded all of fedora's modules in ubuntu. I don't know what to search for so I loaded all of them but it did not work. Here is the script - it loaded with no errors.

#!/bin/bash

modprobe -v bridge
modprobe -v bnep
modprobe -v ipt_REJECT
modprobe -v xt_state
modprobe -v i2c_i801
modprobe -v squashfs
modprobe -v loop
modprobe -v nf_conntrack_ipv4
modprobe -v nf_conntrack_ipv6
modprobe -v nf_conntrack
modprobe -v dm_mirror
modprobe -v dm_multipath
modprobe -v dm_snapshot
modprobe -v dm_mod
modprobe -v ip6t_REJECT
modprobe -v ip6table_filter
modprobe -v ip6_tables

#fuse 41116 3 - Live 0xf8c52000            -it told me it's already loaded

#wmi 9640 0 - Live 0xf8b07000              - NOT FOUND - no idea if it's important
#firewire_ohci 21636 0 - Live 0xf88a0000   - NOT FOUND - I believe it's not important
#firewire_core 34208 1 firewire_ohci, Live 0xf8896000
#crc_itu_t 5760 1 firewire_core, Live 0xf883f000

#mac80211 185184 1 iwl3945, Live 0xf8b7d000 - some ubuntu version is already loaded



I believe that the problem is with the mac80211 module - in ubuntu it's called iwlwifi_mac80211 and I was unable to load the original unmodified version or fedora's version of the module.

My laptop is FujitsuSiemens Amilo xi,
ubuntu version hardy with kernel 2.6.24-19-generic with networkmanager (nm-applet) 0.6.6
fedora 9 with kernel 2.6.25-14.fc9.i686 with networkmanager (nm-applet) 0.7.0

Any ideas, any help will be welcomed.
Should I try to load different kernel module?
Should I install newer version of nm-applet?

I believe it's important problem because wireless connection is important part of desktop computing and usually ubuntu is the best in this field - but last month I was unable to use my laptop under ubuntu without this connection. I connect to other networks without problems. Some windows laptops had also problems connecting but usually after few tries they succeed(not in my case with ubuntu).

Should I file a bug report about this?
Is it possible to be a mistake I have done during installation? I have not checked if I can connect with Ubuntu LiveCD - I do not have one at the moment. Should I check this?

---

