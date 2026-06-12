---
title: "Enable bcm43xx driver installation when compiling 2.6.23.17 kernel"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by kereish on 2009-01-31
Hello,

I'm trying to compile a 2.6.23.17 kernel for Intrepid. Before compilation I want to add the BCM43xx wifi driver to the kernel in menuconfig. But... I cannot find it in the tree of menuconfig.

It's supposed to be here:

Location:
- Device Drivers  
  -- Network device support (NETDEVICES [=y])
    --- Wireless LAN
      ---- Broadcom BCM43xx wireless support (BCM43XX [=n])

However, the last node of this tree is not visible even when Wireless LAN (IEEE 802.11) is checked.

Could anyone tell me what else should be marked to make the BCM43xx nodes visible (and how to find these options in menuconfig)?

Thank you
Ola

---

### Post by kereish on 2009-02-01
OK, I know the answer to my question :)

The following options need to be checked:

Loadable Module Support --->
	Enable loadable Module Support		
		Module Unloading
			Forced Module Unloading
		Automatic Kernel Module Loading
		
Networking --->
	Networking Support
		Generic IEEE 802.11 Networking Stack
			IEEE 802.11 WEP Encryption

Kernel Hacking --->
	Kernel debugging
		Debug Filesystem


Then BCM43xx options will appear and your new kernel will have this driver built-in.

Cheerio,
Ola

---

