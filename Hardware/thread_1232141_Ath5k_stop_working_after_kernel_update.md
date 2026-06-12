---
title: "Ath5k stop working after kernel update"
date: 2009-08-05
forum: Hardware
---

### Post by hbbb on 2009-08-05
Dear all

Using Jaunty UNR on AspireOne A150 successfully since few month, i couldn't load ath5k module anymore right after having updated kernel from 2.6.28-13-generic to 2.6.28-14-generic. For the moment, i'm still running release 13 which works. Regular, restricted and backport modules are installed too as well as tuxonice-ui package. 

Would somebody give me hand in order to get arround this issue or refine diagnostic ?

Many thanks in advance for your help.
Kind regards

Other informations
```

1. Output of `uname -a´
----------------------
Linux toto 2.6.28-14-generic #47+tuxonice1-Ubuntu SMP Wed Jul 29 14:50:42 UTC 2009 i686 GNU/Linux

2. Output of `modprobe ath5k´
-----------------------------
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-14-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath5k (/lib/modules/2.6.28-14-generic/updates/ath5k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

3. output of `dmesg´ (last lines)
---------------------------------
...
[  127.731439] lbm_cw_cfg80211: disagrees about version of symbol dev_set_name
[  127.731455] lbm_cw_cfg80211: Unknown symbol dev_set_name
[  127.732332] lbm_cw_cfg80211: disagrees about version of symbol device_initialize
[  127.732344] lbm_cw_cfg80211: Unknown symbol device_initialize
[  127.733160] lbm_cw_cfg80211: disagrees about version of symbol device_rename
[  127.733171] lbm_cw_cfg80211: Unknown symbol device_rename
[  127.733929] lbm_cw_cfg80211: disagrees about version of symbol put_device
[  127.733938] lbm_cw_cfg80211: Unknown symbol put_device
[  127.734725] lbm_cw_cfg80211: disagrees about version of symbol sysfs_create_link
[  127.734735] lbm_cw_cfg80211: Unknown symbol sysfs_create_link
[  127.735697] lbm_cw_cfg80211: disagrees about version of symbol __class_register
[  127.735706] lbm_cw_cfg80211: Unknown symbol __class_register
[  127.736262] lbm_cw_cfg80211: disagrees about version of symbol device_add
[  127.736272] lbm_cw_cfg80211: Unknown symbol device_add
[  127.736583] lbm_cw_cfg80211: disagrees about version of symbol sysfs_remove_link
[  127.736593] lbm_cw_cfg80211: Unknown symbol sysfs_remove_link
[  127.739368] lbm_cw_cfg80211: disagrees about version of symbol class_unregister
[  127.739384] lbm_cw_cfg80211: Unknown symbol class_unregister
[  127.740186] lbm_cw_cfg80211: disagrees about version of symbol device_del
[  127.740200] lbm_cw_cfg80211: Unknown symbol device_del

Please notice from last listing: no log sent by ath5k module.

```

---

### Post by hbbb on 2009-11-05
I used following packages in Jaunty on a Aspire One aoa150: 
- kernel-image-generic, 
- restricted-modules-generic, 
- backports-modules, as well as
- tuxonice-userui

The above problem had to do with backports-modules' package.

Removing backports modules resolved the issue. Now ath5k is working as expected for WPA encrypted wireless with all kernel image updates. The Led doesn't shows wireless traffic anymore, but i can live without ;-)

Please notice also:
I've no idee if this issue is solved for Karmic.
I didn't tested the above list with tuxonice-userui removed and backports-modules left installed.

Regards

---

