---
title: "Brother MFC won't scan"
date: 2012-12-26
forum: Hardware
---

### Post by jtheb on 2012-12-26
Just purchased a Brother MFC7460DN fax-scan-copy machine
All functions have been working (install went fine)
Today the scan function didn't work
Message was "check connection"
Machine is plugged in and am able to ping it on the network.
Brother "help" said they don't service Linux systems.
That surprised me.

Any thoughts on "check connection" when trying to scan?

Thanks

---

### Post by ajgreeny on 2012-12-26
There is no indication of which version of Ubuntu you're running, and this is now old info, but I pass it on just in case it is any help to you, which it was for me running 10.04 Lucid.

BROTHER SCANNER- Ubuntu 9.10, 10.04
Install libsane-extras, then
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
    The lines to be added:-

```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```
    3. Restart the OS.

---

### Post by jtheb on 2012-12-26
Version Ubuntu 12.04.1




> **ajgreeny said:**
> There is no indication of which version of Ubuntu you're running, and this is now old info, but I pass it on just in case it is any help to you, which it was for me running 10.04 Lucid.

BROTHER SCANNER- Ubuntu 9.10, 10.04
Install libsane-extras, then
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
    The lines to be added:-

```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```
    3. Restart the OS.

---

