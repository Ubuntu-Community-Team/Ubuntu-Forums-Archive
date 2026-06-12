---
title: "ipw2200: Firmware error detected."
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by eraclito on 2005-11-13
hi,

in my laptop (centrino with ipw2200 card) sometimes the wireless network stops and comes back shortly.

when it appens in var/log/syslog i can read:

```

ubuntu kernel [4296345.251000] ipw2200: Firmware error detected.  Restarting.
ubuntu kernel [4296345.251000] ipw2200: Sysfs 'error' log already exists.
ubuntu kernel [4296350.627000] ipw2200: Firmware error detected.  Restarting.
ubuntu kernel [4296350.627000] ipw2200: Sysfs 'error' log already exists.
ubuntu kernel [4296353.825000] ipw2200: Firmware error detected.  Restarting.
ubuntu kernel [4296353.825000] ipw2200: Sysfs 'error' log already exists.
ubuntu kernel [4296357.696000] ipw2200: Firmware error detected.  Restarting.
ubuntu kernel [4296357.696000] ipw2200: Sysfs 'error' log already exists.
ubuntu kernel [4296362.110000] ipw2200: Firmware error detected.  Restarting.
ubuntu kernel [4296362.110000] ipw2200: Sysfs 'error' log already exists.

```

it appens both with ubuntu standard kernel and whit my compiled kernel.
i use ipw2200_1.0.8 ieee80211-1.1.6 and ipw2200-fw-2.4 firmware copied in /usr/lib/hotplug/firmware

any idea?

eraclito

---

### Post by jliedeka on 2005-11-13
Try adding a file for ipw2200 in /etc/modprobe.d.  The file should say this:

options ipw2200 hwcrypto=0

That helped me anyway.

     Jim

---

### Post by eraclito on 2005-11-14
[QUOTE=jliedeka]Try adding a file for ipw2200 in /etc/modprobe.d.  The file should say this:

options ipw2200 hwcrypto=0

That helped me anyway.

     Jim[/QUOTE]


it seems to work (but it is a ramdom problem so i'm not sure...)

but can you explain me how it works?

thk

---

### Post by ruffneck on 2005-11-16
I have the same issue albiet I don't notice any drops in wifi connection just a little "blip" maybe.

---

### Post by jliedeka on 2005-11-16
I'm just guessing but I think the driver doesn't support the crypto in hardware but doesn't actually realize it.  Turning off hwcrypto when you load the driver keeps it from trying to use it.

---

