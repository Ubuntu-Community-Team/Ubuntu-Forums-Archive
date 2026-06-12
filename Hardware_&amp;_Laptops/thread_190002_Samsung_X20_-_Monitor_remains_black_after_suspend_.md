---
title: "Samsung X20 - Monitor remains black after suspend to RAM"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by Wermut on 2006-06-05
Suspend to RAM worked fine in Breezy using the following script for sleepbtn.sh:

```

rmmod uhci_hcd
rmmod ehci_hcd

/sbin/hwclock --systohc
echo mem > /sys/power/state
/sbin/hwclock --hctosys

modprobe uhci_hcd
modprobe ehci_hcd

```

With Dapper, after pressing the power button the screen remains black, but the system itself is resumed, i.e. I can open konsole and reboot "in the dark". Switching virtual terminals does not have any effect.

Does anybody know what was changed?

---

### Post by woifi on 2006-08-13
> **Wermut said:**
> Suspend to RAM worked fine in Breezy using the following script for sleepbtn.sh:

```

rmmod uhci_hcd
rmmod ehci_hcd

/sbin/hwclock --systohc
echo mem > /sys/power/state
/sbin/hwclock --hctosys

modprobe uhci_hcd
modprobe ehci_hcd

```

With Dapper, after pressing the power button the screen remains black, but the system itself is resumed, i.e. I can open konsole and reboot "in the dark". Switching virtual terminals does not have any effect.

Does anybody know what was changed?

same problem here, does your x20 have an ati card or an intel?

edit:

does this work for you?
[https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/46181](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/46181)

---

### Post by woifi on 2006-09-17
any news here?

edit:
Even if i stop gdm and try to suspend in console, my book doesn't wake up (so it should not be a problem with fglrx?)!

edit2:

**Problem solved!**
Suspend to RAM works with
```
sudo /usr/sbin/pmi action sleep
```

yippie!

---

