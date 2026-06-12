---
title: "takes longer to boot each time"
date: 2008-09-18
forum: General Help
---

### Post by chrismcb on 2008-09-18
Ubuntu progressively takes longer to boot up each time, and firefox is running slower as the days go on.  does anyone know why? or how to fix it?

---

### Post by oilchangeguy on 2008-09-18
> **chrismcb said:**
> Ubuntu progressively takes longer to boot up each time, and firefox is running slower as the days go on.  does anyone know why? or how to fix it?

computer specs, version of ubuntu, and what you've done to it recently would be very helpful.

---

### Post by chrismcb on 2008-09-18
right, sorry bout that.  i have ubuntu 8.4 i believe, about 512 ram, 2.0 ghz processor. 20 g hd.  recently i have installed audacity, a few games, python, open jdk, and other similar items.  however, the boot after i installed them was not noticeably different that a boot before.

---

### Post by spiderbatdad on 2008-09-18
```
dmesg > ~/Desktop/dmesg.txt
```will write a diagnostic message file to your desktop. From that you may pick up some clues...or upload the  file here as an archive, by right clicking and selecting "create an archive." Use the manage attachment tool below.

---

### Post by chrismcb on 2008-09-18
ok, i did it, but it doesnt mean anything to me

---

### Post by spiderbatdad on 2008-09-18
There are several suggestions from the kernel message. First you might remove "quiet splash" to see where the boot may be slow. To do this edit the file /boot/grub/menu.lst :
```
gksu gedit /boot/grub/menu.lst
```

Scroll to this section:
```
# savedefault=true

## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.27-3-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-3-server root=UUID=#'s ro **lapic hpet=force **
initrd		/boot/initrd.img-2.6.27-3-server
quiet
savedefault
``` You see where I have highlighted the end of the line that begins with the word kernel, above. You will see "quiet splash." Delete quiet splash, save, reboot.

Watch the verbose boot for hanging. Your dmesg makes these suggestions:
```
 intel_rng: Firmware space is locked read-only. If you can't or
[   28.679959] intel_rng: don't want to disable this in firmware setup, and if
[   28.679961] intel_rng: you are certain that your system has a functional
[   28.679962] intel_rng: RNG, try using the 'no_fwh_detect' option.


PCI: Using ACPI for IRQ routing
[   10.743297] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report


 ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.726854] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   10.726858] * this clock source is slow. If you are sure your timer does not have
[   10.726859] * this bug, please use "acpi_pm_good" to disable the workaround
```

You can try any, or all three suggestions. To do so add the option to the end of the kernel line after "ro." so one option might look like:

```
kernel		/boot/vmlinuz-2.6.27-3-server root=UUID=#'s ro **no_fwh_detect **
```


OR:

```
kernel		/boot/vmlinuz-2.6.27-3-server root=UUID=#'s ro **lapic no_fwh_detect **
```

OR
```
kernel		/boot/vmlinuz-2.6.27-3-server root=UUID=#'s ro **lapic no_fwh_detect acpi_pm_good **
```

---

### Post by chrismcb on 2008-09-18
ok, i did all that and it seems to be running faster now.  thank you so much.  just one last question, i have seen that with windows and macintosh computers, over time they run slower.  if this happens with ubuntu, would you have any suggestions on how to speed things up in general without re-installing the OS?

---

