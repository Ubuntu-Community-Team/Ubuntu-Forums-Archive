---
title: "Trying to install WiFi Drivers, got weird error."
date: 2019-11-15
forum: Hardware
---

### Post by bsykes3487 on 2019-11-15
[SIZE=6]EDIT: [SIZE=4]Just realized this isn't much of an issue as I just realized this is a bit overkill so I stuck with the out-of-the-box drivers.[/SIZE][/SIZE]

I am trying to install more compatible drivers for my WiFi, which worked OK out of the box, but not as good as it could have. Ubuntu recommended I installed backport-iwlwifi-dkms so I did via apt. While installing, it seemed to error out in the [console log]("https://pastebin.com/NXd7qMs5") and referenced [this log file]("https://pastebin.com/pQ5MdTGe").

The only error I see in the log file is:
```
/var/lib/dkms/backport-iwlwifi/7906/build/drivers/net/wireless/intel/iwlwifi/mvm/utils.c: In function &#8216;iwl_mvm_get_sync_time&#8217;:

 /var/lib/dkms/backport-iwlwifi/7906/build/drivers/net/wireless/intel/iwlwifi/mvm/utils.c:1468:14:  error: implicit declaration of function &#8216;ktime_get_boot_ns&#8217;; did you  mean &#8216;ktime_get_raw_ns&#8217;? [-Werror=implicit-function-declaration]

  1468 |  *boottime = ktime_get_boot_ns();
       |              ^~~~~~~~~~~~~~~~~
       |              ktime_get_raw_ns
   CC [M]  /var/lib/dkms/backport-iwlwifi/7906/build/net/mac80211/scan.o
 cc1: some warnings being treated as errors
 make[9]: *** [scripts/Makefile.build:290:  /var/lib/dkms/backport-iwlwifi/7906/build/drivers/net/wireless/intel/iwlwifi/mvm/utils.o]  Error 1
```

I don't exactly know what this means, but with my minor C experience it seems more like a warning than an error, and I don't know if this prevented it from fully compiling or not. Am I safe to reboot my system and use this driver/module?

---

