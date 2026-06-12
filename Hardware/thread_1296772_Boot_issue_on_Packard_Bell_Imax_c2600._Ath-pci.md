---
title: "Boot issue on Packard Bell Imax c2600. Ath-pci"
date: 2009-10-21
forum: Hardware
---

### Post by jijiz31 on 2009-10-21
Hello,

I installed **ubuntu 9.04 « Jaunty Jackalope » **on ION IMAX c2600 packard Bell. Installed the latest nvidia driver, it works fine, then make the full security update et activate atheros wifi driver. Now, the pc doesn't boot, the text boot show that the pc stop ont that line :

```
[12.726830] ath-pci 0000:05:00.0: PCI INT A -> LINK [LN4D] -> GSI 19 (llevel, low) -> IRQ 19.
```

Do I have to remove the driver, and how to do that?

Thanks for your help and sorry for my weak english.

---

### Post by jijiz31 on 2009-10-21
Up

---

### Post by jijiz31 on 2009-10-21
that's ok, I removed the /etc/modprobe.d/blacklist-ath_pci and it worked. 

But, I do not understand why ubuntu does'nt remove that file itself when I asked to use that driver.

---

