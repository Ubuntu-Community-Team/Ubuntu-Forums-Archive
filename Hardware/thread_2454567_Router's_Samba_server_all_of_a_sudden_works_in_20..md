---
title: "Router's Samba server all of a sudden works in 20.04; what happened?"
date: 2020-12-02
forum: Hardware
---

### Post by ping-wu on 2020-12-02
In 20.04 (and subsequent releases including daily updates), I was never able to connect to the USB3 HD storage attached to my router (LP-Link) via samba (had to resort to using ftp).  But after a recent upgrade, I was able to connect to the samba server in the router/NAS.  Not that I am complaining but does anyone know what happened? 

Same observation after a recent Bullseye update.

---

### Post by CelticWarrior on 2020-12-02
After an Ubuntu update or a router's firmware update?

---

### Post by SeijiSensei on 2020-12-02
SMB/CIFS can use a variety of protocols. Perhaps the router is now using one compatible with the Samba client.

---

### Post by ping-wu on 2020-12-02
> **CelticWarrior said:**
> After an Ubuntu update or a router's firmware update?

Only did Ubuntu update.  Did nothing with the router.

Again, not that I am complaining, but just wanted to know what happened in the recent Ubuntu/Debian updates.

---

### Post by rsteinmetz70112 on 2020-12-03
Most likely a recent update to samba resolved some issue. Samba negotiates the protocol to use with the server or client.

---

### Post by ping-wu on 2020-12-08
I think what happened is that I accidentally did a cold reboot of my router (powered it off for more than 30 sec).  Running diff shows that there does not appear to be any change in the smb config files before and after Ubuntu updates.  I think cold rebooting the router did the job.

---

### Post by rsteinmetz70112 on 2020-12-08
I haven't changed my smb.conf file in years but I routinely get updates to samba.

---

### Post by TheFu on 2020-12-08
Please be very careful trusting the storage features on any router. There is much history around failed security with storage connected to routers. Some features are bad ideas.  WAN routers need to be dedicated WAN routers, not 20 other convenience things too.
imho.

---

### Post by ping-wu on 2020-12-08
> **TheFu said:**
> Please be very careful trusting the storage features on any router.

Very good advice!  I am using a USB3 stick plugged into the router port.  Never store important files there.  Also I unplug it when not in active use.  Very convenient but untrustworthy.

---

