---
title: "ath0 disappeared"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by PsTJsT on 2006-02-17
My wireless device (ath0) has disappeared.  The device (a D-Link DWL-G520 PCI adapter w/ an Atheros chipset) has been working fine with the standard madwifi drivers ever since I installed Breezy several weeks ago, and I'm pretty sure it's not a hardware issue because it's identified and works when I boot with a Breezy live cd.  I've tried "lspci" and "iwconfig -a" and it doesn't show up with either command, and "ifup ath0" states the device isn't found/valid.  

An unrelated thread indicated the fix might be "apt-get install linux-restricted-modules-$(uname -r)" but that doesn't seem to be an option for me since I can't get online (with that computer).

Thanks in advance for any suggestions.

Edit:  I didn't realize the restricted modules were available outside the repositories.  Once I learned that bit of information, I booted w/ a LiveCD and downloaded the restricted modules from [http://mirrors.dotsrc.org/ubuntu/pool/restricted/l/](http://mirrors.dotsrc.org/ubuntu/pool/restricted/l/), then rebooted into Breezy and installed the restricted modules.  All is well again...

---

