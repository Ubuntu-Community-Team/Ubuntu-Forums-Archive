---
title: "ipw2200 + wpa-psk"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by AndersAA on 2005-04-13
My /etc/wpa_supplicant.conf is set up correctly (works perfectly on other systems), and ipw2200 driver loaded, but when I run wpa_supplicant I get this:


```

/usr/sbin/wpa_supplicant -i eth1 -D ipw -w -c /etc/wpa_supplicant.conf -dd

wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.

```

will I have to compile ipw2200 driver manually?  I'd much rather do this in the "as easy as possible way", I dont mind getting my hands dirty personally, but I want to set this laptop up with gui tools/easy steps to follow only.  Recompiling kernel modules hardly counts as easy steps ;)

---

### Post by luca_linux on 2005-04-13
I've written a howto, look here: [http://www.ubuntuforums.org/showthread.php?p=130227#post130227](http://www.ubuntuforums.org/showthread.php?p=130227#post130227)

---

### Post by AndersAA on 2005-04-13
thanks :)

---

