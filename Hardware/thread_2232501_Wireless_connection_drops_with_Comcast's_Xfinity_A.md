---
title: "Wireless connection drops with Comcast's Xfinity Arris TG852 TG862 Cable Modem"
date: 2014-07-02
forum: Hardware
---

### Post by vajorie on 2014-07-02
Not a question but just to let people who might have this issue be aware that:

If you have Comcast's Arris TG852/TG862 gateway, and if your wireless connection drops again and again and again, it is not your setup but the gateway that is causing the trouble. I am not sure if this is a faulty gateway but I suspect that it is not. (I also cannot connect using an ethernet cable but I'm not sure if that's due to my laptop or the gateway.)

I'm using 12.04 on a Clover laptop using the iwlwifi driver in an intel N6300 wifi card. Confirmed by connecting the same laptop to multiple other non-comcast routers. 

A section from my logs, in case people duckduckgo and find them here: 

```

# grep wlan0 /var/log/syslog
Jul  2 08:46:42 panp7 NetworkManager[1084]: <info> (wlan0): device state change: activated -> failed (reason 'ip-config-unavailable') [100 120 5]
Jul  2 08:46:42 panp7 NetworkManager[1084]: <warn> Activation (wlan0) failed for access point (blabla)
Jul  2 08:46:42 panp7 NetworkManager[1084]: <warn> Activation (wlan0) failed.
Jul  2 08:46:42 panp7 NetworkManager[1084]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jul  2 08:46:42 panp7 NetworkManager[1084]: <info> (wlan0): deactivating device (reason 'none') [0]
Jul  2 08:46:42 panp7 NetworkManager[1084]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 26374

```

---

