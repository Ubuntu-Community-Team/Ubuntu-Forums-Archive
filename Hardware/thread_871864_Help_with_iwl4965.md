---
title: "Help with iwl4965"
date: 2008-07-27
forum: Hardware
---

### Post by Mars Thrax on 2008-07-27
I have a Toshiba M700 with an intel 4965 wireless card. I read [here]("http://tinyshell.be/aircrackng/forum/index.php?topic=3775.0") that it was possible to build a driver for this card that has packet injection for wireless pen testing.

The driver compiles properly, however when I run "make load", I try to load the iwl4965 modeul, I get the following error:
```

WARNING: Error inserting iwlwifi_mac80211 (/lib/modules/2.6.24-19-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl4965 (/lib/modules/2.6.24-19-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

When I run "tail /var/log/dmesg", there appear to be no errors printed (the last entry deals with iptables).

Anyone have any ideas on what I can do to either
1) Finish loading this driver
or
2) Get back to my previous configuration using the old driver.

Thanks for the input.

---

### Post by bear24rw on 2008-09-19
I am having the EXACT same problem, same computer everything..
Anyone know how to install the original drivers?
I tried to

 modprobe iwl4965

but it fails saying

WARNING: Error inserting iwlwifi_mac80211 (/lib/modules/2.6.24-19-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl4965 (/lib/modules/2.6.24-19-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

