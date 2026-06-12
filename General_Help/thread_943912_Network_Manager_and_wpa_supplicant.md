---
title: "Network Manager and wpa_supplicant"
date: 2008-10-10
forum: General Help
---

### Post by mentarm on 2008-10-10
Dear all,

I'm able to connect to a wireless secure network using the following command:

```
/sbin/wpa_supplicant -Dwext -iwlan0 -c ./wpa_supplicant.conf
```

and my wpa_supplicant file looks like this:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
update_config=0
fast_reauth=1
ap_scan=2
eapol_version=1

network={
        ssid="ssid"
        scan_ssid=1
        key_mgmt=IEEE8021X
        eap=PEAP
        identity="username"
        password="password"
        phase2="auth=MSCHAPV2"
}

```

However, whenever I try to use the network manager, no matter, which options I choose, I fail to connect.

Hence, I would appreciate if somebody could help me and tell me whether the network manager is capable of performing the same tasks as wpa_supplicant and if that's the case, could anybody please help me make it work.

Thank you!

---

