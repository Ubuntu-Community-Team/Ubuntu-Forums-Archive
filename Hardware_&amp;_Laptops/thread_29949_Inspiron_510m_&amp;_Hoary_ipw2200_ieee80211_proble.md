---
title: "Inspiron 510m &amp; Hoary: ipw2200 ieee80211 problems"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by balderman on 2005-04-26
Hi everybody!

I'm running Ubuntu Hoary on my new Inspiron 510m and after hours and hours I haven't managed yet how to install properly the Intel Pro Wireless 2200 b/g drivers.

I followed several forum threats, I have installed linux-headers, installed ipw2200 drivers and firmware, load firmware_class modules and and I can't use mi WiFi  ](*,) 

Here are my dmesg:
```
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: Unknown symbol free_ieee80211
ipw2200: Unknown symbol alloc_ieee80211
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: Unknown symbol free_ieee80211
ipw2200: Unknown symbol alloc_ieee80211
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: Unknown symbol free_ieee80211
ipw2200: Unknown symbol alloc_ieee80211
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: Unknown symbol free_ieee80211
ipw2200: Unknown symbol alloc_ieee80211
```

When I tried to execute modprobe ipw2200 i got the following message:
```
FATAL: Error inserting ipw2200 (/lib/modules/2.6.8.1-3-386/drivers/net/wireless/ipw2200.ko):
Unknown symbol in module, or unknown parameter (see dmesg)
```

I have boot options
```
/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda6 ro quiet splash
acpi_irq_isa=7
```
to make my soundcard work

I hope someone can help me fix my wireless card!!!!

Thanks a lot

---

