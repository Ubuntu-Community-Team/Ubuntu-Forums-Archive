---
title: "Fingerprint reader in Fossa"
date: 2020-04-23
forum: Hardware
---

### Post by volkerbradley on 2020-04-23
Evidently fingerprint gui will not be available for Fossa. I tried clicking on Settings -> Users -> Fingerprint Login and then moving the slider to enable it.  A message appeared: "Could not start finger capture on 'UPEK TouchStrip Sensor-Only" device. GDBus. Error: orgfreedesktop. DBus.Error. No reply. Message recipient disconnected from message bus without replying.
What is going on here?  Is there any hope of being able to use the UPEK device for fingerprint login?
Thanks

---

### Post by dino99 on 2020-04-24
Libfprint seems dealing with such a device.

 Found some (old) threads about Upek:
[https://menelkir.itroll.org/2010/05/upek-biometric-touchchiptouchstrip.html](https://menelkir.itroll.org/2010/05/upek-biometric-touchchiptouchstrip.html)
[https://trainingslist.info/other/linux-upek-driver-download-49/](https://trainingslist.info/other/linux-upek-driver-download-49/)

Report (old): [https://bugzilla.redhat.com/show_bug.cgi?id=504399](https://bugzilla.redhat.com/show_bug.cgi?id=504399)

Debian has a more recent version : [https://packages.debian.org/experimental/libfprint-2-2](https://packages.debian.org/experimental/libfprint-2-2)

Upstream: [https://fprint.freedesktop.org/](https://fprint.freedesktop.org/)
Your device should work, as it is listed as supported: [https://fprint.freedesktop.org/supported-devices.html](https://fprint.freedesktop.org/supported-devices.html)

You might need reporting against libfprint-2-2 upstream :
[https://gitlab.freedesktop.org/libfprint/fprintd/-/issues](https://gitlab.freedesktop.org/libfprint/fprintd/-/issues)
 [https://gitlab.freedesktop.org/libfprint/fprintd](https://gitlab.freedesktop.org/libfprint/fprintd)

---

### Post by DuckHook on 2020-04-24
It's supposed to be available, but probably a bug. I successfully used my fingerprint reader in Eoan, but it no longer works in Focal. According to [this link]("https://fprint.freedesktop.org/supported-devices.html"), my device, 0483:2016 is supported. This is also confirmed by the fact that it worked in Eoan.

---

### Post by slickymaster on 2020-04-24
Thread moved to the **Hardware** forum since 20.04 has been released

---

### Post by Welly Wu on 2020-07-09
I got the same problem too so I am affected. Is there a Launchpad Bug report for this that I can subscribe to?

---

