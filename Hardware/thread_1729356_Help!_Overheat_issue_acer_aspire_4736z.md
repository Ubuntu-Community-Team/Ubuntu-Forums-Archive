---
title: "Help! Overheat issue acer aspire 4736z"
date: 2011-04-14
forum: Hardware
---

### Post by unloki9 on 2011-04-14
help me please I think my laptop fan isn't working very well. Yes, it's running but I think in it's minimum speed my cpu temp is always 46-50 degrees after 5mins. And my video card is a built in intel pentium.  I have ubuntu 10.04 os intalled.


thanks!

---

### Post by pqwoerituytrueiwoq on 2011-04-14
[http://ubuntuforums.org/showthread.php?t=1725595](http://ubuntuforums.org/showthread.php?t=1725595)
maybe something there will help

---

### Post by Hedgehog1 on 2011-04-15
To improve the function of the laptop fan using 'current' grub options:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by unloki9 on 2011-04-15
@hedgehog..

Thanks that really helped.. thanks for the replies everyone

---

