---
title: "[SOLVED] Turning Off Verbose"
date: 2008-10-25
forum: General Help
---

### Post by indytim on 2008-10-25
I just included another disto into my lineup of boot options (GRUB).  For reasons unknown to me, Ubuntu has now triggered to 100% verbose at bootup.  Functionally no biggee.  Any suggestions on how to reset the flag for non-verbose bootup?

TIA,

IndyTim

---

### Post by dcstar on 2008-10-25
> **indytim said:**
> I just included another disto into my lineup of boot options (GRUB).  For reasons unknown to me, Ubuntu has now triggered to 100% verbose at bootup.  Functionally no biggee.  Any suggestions on how to reset the flag for non-verbose bootup?

TIA,

IndyTim

The flag is "quiet", eg:

```
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=34a084d1-8db0-4fa6-9454-ddc72dd4c59c ro **quiet** splash
```

---

### Post by indytim on 2008-10-26
Thanks,

I'll check the dedicated GRUB partition menu.lst as I did have to manually add the GRUB boot for the other distro (couldn't get the linked image working near-term).

IndyTim

---

