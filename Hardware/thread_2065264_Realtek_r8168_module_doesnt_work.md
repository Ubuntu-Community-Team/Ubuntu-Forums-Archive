---
title: "Realtek r8168 module doesnt work"
date: 2012-10-01
forum: Hardware
---

### Post by de0xyrib0se on 2012-10-01
Seems that in kernel 3.x after compiling the module and updating the initfs the following message comes up when booting;

[HTML][    1.848180] r8168: disagrees about version of symbol module_layout
[   10.572586] r8168: disagrees about version of symbol module_layout[/HTML]

If I manually load the same module it works fine;

[HTML]insmod r8168[/HTML]

All of the above are when manually compiling the module.

Furthermore if using the automatic script to compile the module;

[HTML]WARNING: All config files need .conf: /etc/modprobe.d/blacklist-network, it will be ignored in a future release.
FATAL: Error inserting r8168 (/lib/modules/3.2.0-24-generic-pae/updates/dkms/r8168.ko): Invalid module format[/HTML]

---

### Post by nothingspecial on 2012-10-18
Duplicate thread.

Closed.

---

