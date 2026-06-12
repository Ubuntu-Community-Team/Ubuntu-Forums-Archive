---
title: "usb won't automount"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by ndaman on 2005-04-26
When I first installed ubuntu, whenever I insterted my usb storage device, it would automatically mount and an icon would be placed on my desktop. Now when I insert the device, it will not automount, but when I look in the device manager, everything is fine and I can manually mount it, why won't it mount automatically anymore?

---

### Post by ernestoongaro on 2005-04-26
Have you tried System > Preferences > Removable Drives and Media  ?

---

### Post by ndaman on 2005-04-26
yeah, I tried that and it still doesn't work :( I wonder if this could be a problem though, I also have the kde-desktop installed (but I still run gdm and right now I'm in gnome)

---

### Post by heimo on 2005-04-26
Does
```
 sudo /etc/init.d/hotplug restart
``` 
have any effect?

---

### Post by ndaman on 2005-04-26
I just tried restarting hotplug and that didn't work either :( any other suggestions?

---

### Post by ernestoongaro on 2005-04-27
I had sort of the same problem on my older laptop, a lot of my hardware was misbehaving when I updated to Hoary, i had forgotten to disable ACPI (new power management) which causes some major irq issues, well i gave the 'acpi=off' to grub and everything worked great. Maybe it is an irq issue you are experiencing. ??

---

