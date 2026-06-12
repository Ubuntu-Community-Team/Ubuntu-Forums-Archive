---
title: "Hardware VPN/Crypto Accelerators"
date: 2017-02-09
forum: Hardware
---

### Post by m-dw on 2017-02-09
Hi All

I'm looking for a PCI crypto accelerator to go in a Ubuntu 16.04 based VPN router. There is a Soekris VPN1401 on Ebay for approx GBP40, but I can find very little technical information (manufacturer says that Linux support is under development).

Anyone got experience of using this or other similar cards in Ubuntu?
Any recommendations for alternatives, preferably ones currently in production.

---

### Post by m-dw on 2017-02-15
[COLOR=#111111][FONT=Ubuntu]OK, so I obtained the card in question, and installed it in my server system. It booted up without issues and the card was identified correctly (lspci).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]No drivers were loaded, but having the card in my possession allowed me to identify what driver would be needed. I'm apparently looking for hifn_795x.ko which doesn't exist in the current kernel. It looks like the driver is no longer maintained in the Ubuntu kernel, potentially because of an incompatibility with AMD64 code (see launchpad bug)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1085115](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1085115)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]There is evidence that the Fedora 32bit kernels still have the module available.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][https://www.rpmfind.net/linux/rpm2html/search.php?query=kmod(hifn_795x.ko)](https://www.rpmfind.net/linux/rpm2html/search.php?query=kmod(hifn_795x.ko))[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Not much good to me though. The most likely scenario is that I'll keep the card and use in a home-built pfSense router at some time in the future.[/FONT][/COLOR]

---

