---
title: "Network data not saveing"
date: 2008-12-01
forum: General Help
---

### Post by Oxidize on 2008-12-01
Just installed 8.10 but when ever i set my manual network data it will reset upon reboot, any idea whats causing this and how to fix it.

---

### Post by cariboo on 2008-12-01
The way I fixed the problem is to uninstall dhcp3-client. You don't need dhcp if you have a static ip address, so you might just as well get rid of it:

```
sudo apt-get purge dhcp3-client
```

Jim

---

### Post by Oxidize on 2008-12-01
Thank you for the info, tryed this but sadly the problem persists.
No matter how many times i set the manual info as soon as i reboot it resets to auto.

---

### Post by cdenley on 2008-12-01
It's a bug. You need to delete the automatically created network configuration(s), then create a new one using the correct MAC address.
```

ifconfig -a|grep HWaddr

```
When it saves the configuration correctly, you will be required to enter your password.

---

