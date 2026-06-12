---
title: "4965 agn and Gutsy issues."
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by Braveheart1980 on 2007-11-09
I've bought some days ago a laptop with the 4965 agn wifi from intel

Gutsy detected automatically my card,no problem @ all

BUT I am experiencing some little probs....

(1) I am connecting to my WiFi router as long as it hasn't hidden ssid . If I hide the ssid I can't connect to my router.I haven't used the network manager.What I did was to manually edit the interfaces file based on [this]("http://ubuntuforums.org/showthread.php?t=202834&highlight=wifi") GREAT tutorial. 

(2) I am having problems with kismet as you can see [here]("http://ubuntuforums.org/showthread.php?t=604663&highlight=4965+kismet")

(3) Doing an lsmod gave me this


```
george@george-laptop:/etc/kismet$ lsmod | grep iwl
iwl4965               101480  0 
iwlwifi_mac80211      175112  1 iwl4965
cfg80211                7304  1 iwlwifi_mac80211

```

Does the 0 (zero) there mean that iwl4965 (which is my wifi's card driver)  isn't loaded?

Anyone else experiencing any of those?
Any help?

---

### Post by CrzySdrs on 2007-11-18
I see problems where I can't seem to connect to some wireless networks despite others with laptops around being able to. I use Network-Manager.

My lsmod also looks the same
```
lsmod | grep iwl
iwl4965               113512  0
iwlwifi_mac80211      200456  1 iwl4965
cfg80211                8720  1 iwlwifi_mac80211
```

---

