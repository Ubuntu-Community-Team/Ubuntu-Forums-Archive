---
title: "ntfs partion error"
date: 2011-09-07
forum: Hardware
---

### Post by mj125 on 2011-09-07
hello
I have a hp pavilion dv6. yesterday I try to resize my partion in windiws with paragon.
when I restart I see the grub fails. I install grub and I go to ubuntu.
ubuntu  doesn't know my ntfs partion and my flash.
know what can i do?

---

### Post by Grenage on 2011-09-07
> **mj125 said:**
> hello
I have a hp pavilion dv6. yesterday I try to resize my partion in windiws with paragon.
when I restart I see the grub fails. I install grub and I go to ubuntu.
ubuntu  doesn't know my ntfs partion and my flash.
know what can i do?

So you resized a partition; how many do you have, and which did you resize?
Grub failed, presumable because ordering or IDs changed, so you used the liveCD in reinstall grub?
Ubunto does not list your NTFS drive in Nautilus?

Does the NTFS partition show up in gparted, or is it listed when using the command:

```
sudo fdisk -l
```

Is Windows an option in Grub, an does it boot?

---

