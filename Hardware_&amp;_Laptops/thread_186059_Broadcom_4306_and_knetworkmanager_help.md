---
title: "Broadcom 4306 and knetworkmanager help"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by sal on 2006-06-01
i was using the dapper RC and betas with no problem with the broadcom 4306 and ndiswrapper and now i upgraded to the official release with a fresh install and installed ndiswrapper and knetworkmanager and it keeps going threw a loop of asking me for the passphrase over and over and never connecting.

can anyone help me with this issue?

thanks in advance.

---

### Post by snowpalmer on 2006-06-01
Dapper comes with drivers for that chipset.. although I don't think they are as stable as the ones you get with ndiswrapper.  Your system is probably setup with those drivers and thus conflicting with ndiswrapper.  Check whether you have it running with this command.

```
lsmod | grep bcm43xx
```

If you get a line that starts with bcm43xx then the (wrong) drivers are loaded.  You can unload them by doing this.

```
sudo rmmod bcm43xx
```

You will also want to add it to the blacklist so that it doesn't load again and reboot.

Open up /etc/modprobe.d/blacklist and add the line

```
blacklist bcm43xx
```

Let me know if that works.

---

### Post by sal on 2006-06-02
thanks i wound up getting it going with the bcm43xx drivers and not using ndis.

---

