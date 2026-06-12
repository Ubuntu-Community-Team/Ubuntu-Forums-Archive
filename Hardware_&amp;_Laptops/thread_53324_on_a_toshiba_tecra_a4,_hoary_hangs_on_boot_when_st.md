---
title: "on a toshiba tecra a4, hoary hangs on boot when starting hotplug subsystem"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by davious on 2005-07-31
did a ubuntu hoary install on an a4 terca toshiba laptop. everything is going fine until it reaches
```

* Starting hotplug subsystem...

```
where is hangs.

did some research and came up with a few links that possibly address the issue
[list]
[*][https://bugzilla.ubuntulinux.org/show_bug.cgi?id=4487#c2](https://bugzilla.ubuntulinux.org/show_bug.cgi?id=4487#c2)
[*][http://www.de-brauwer.be/wiki/wikka.php?wakka=LinuxTecraS2](http://www.de-brauwer.be/wiki/wikka.php?wakka=LinuxTecraS2)
[*][http://tuxmobil.org/toshiba_tecra_a4_linux.html](http://tuxmobil.org/toshiba_tecra_a4_linux.html)
[/list] 

each one mentions something about using a noapic or acpi=off boot option. I've tried adding them both (and once in combination) by appending it to end of the kernel command in grub at boot time.

(Newbie question) Am I correctly adding the boot options on the grub kernel command line?
Any recommendations on getting ubuntu to boot on an toshiba tecra a4 laptop?

---

### Post by a2ps on 2005-07-31
i too have a toshiba laptop that hangs on boot ("starting hotplug subsystem"), and forget acpi, it hangs because of the ethernet card (marvell i bet).

just disable LAN on the bios, download the marvell ethernet linux driver (you can download it from the last link you posted on your previous post), boot your ubuntu, install the driver, reboot and enable LAN in bios, and youre done.

good luck with that.

---

### Post by davious on 2005-08-11
Thanks!

Disabling BIOS ethernet did the trick.  Hello, ubuntu.

Now, if only the wireless card could detect my router...

---

### Post by davious on 2005-10-13
Just for closure...

in breezy
turn the ethernet in the bios on

after install, you still won't get ethernet until you modify your
/boot/grub/menu.lst
add
acpi=off
to the end of the kernel /vmlinuz-2....

you can edit the line in grub first to try it out

---

