---
title: "Need to add acpi=off and noapic on Zepto?"
date: 2008-08-27
forum: Hardware
---

### Post by krestensb on 2008-08-27
Hi,

I have just installed linux on my new zepto. I could only do it if I added ACPI=OFF and NOAPIC to the GRUB string on install, and when I start the system I have to add it every time. 
Could something be done about it? 

Wikipedia told me that it is something about powermanagement. Could that be solved with a new driver? 


Best regards
Kresten

---

### Post by tangibleorange on 2008-08-27
> **krestensb said:**
> Hi,

I have just installed linux on my new zepto. I could only do it if I added ACPI=OFF and NOAPIC to the GRUB string on install, and when I start the system I have to add it every time. 
Could something be done about it? 

Wikipedia told me that it is something about powermanagement. Could that be solved with a new driver? 


Best regards
Kresten

i'm not sure about solving the actual problem, but I can help you add acpi=off and noapic permenantly so you don't have to add them everytime:

```
gksu gedit /boot/grub/menu.lst
```
find the entry that boots ubuntu (usually quite far down). the entry probably looks like this:
```
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=75421f84-559e-496d-ac4a-3fb544331416 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet
```

at the end of the 'kernel' line add:

```
acpi=off noapic
```

then save and reboot. you should be able to boot normally...

---

### Post by krestensb on 2008-08-28
Hi mate,

Thanks for the tip, its booting ok now.

/Kresten

---

