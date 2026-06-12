---
title: "Ubuntu 7.10 Freeze after boot up"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by deepaknr on 2008-01-26
HI All,

I have a acer aspire 5710G notebook. I installed Ubuntu 7.10 recently. I am encountering a strange problem from the day one. After boot up, Ubuntu hangs and there is no way unless I restart. This happens every day after boot up. Ones I restart and login back, it does not freeze again

I had a look at the system logs to see whats happening and I get these error messages:

```
Jan 26 22:12:50 hcid[5390]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Jan 26 22:12:50 hcid[5390]: Default authorization agent (:1.19, /org/bluez/auth) registered
Jan 26 22:12:57 NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 26 22:12:57 NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jan 26 22:16:03 syslogd 1.4.1#21ubuntu3: restart.
```

From the messages, I can understand there is something going on wireless network.

Kindly let me know if there is a solution to this problem.

---

