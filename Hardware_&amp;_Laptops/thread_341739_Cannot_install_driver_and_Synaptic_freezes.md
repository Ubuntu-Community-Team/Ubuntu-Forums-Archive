---
title: "Cannot install driver and Synaptic freezes"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by txakurra2000 on 2007-01-19
I tried to install a driver for printer Brother MCF9880 but installation failed and if I open Synaptic now I get the following message:  

E: The package mfc9880lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I of course tried to reinstall but was unsuccessful

I then tried:
apt-get clean mfc9880lpr

No reaction!

I also tried:
sudo dpkg -r --force-remove-reinstreq mfc9880lpr

The answer is:
dpkg - warning, overriding problem because --force enabled:
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
(Reading database ... 110086 files and directories currently installed.)
Removing mfc9880lpr ...
/var/lib/dpkg/info/mfc9880lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing mfc9880lpr (--remove):
subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
mfc9880lpr

I tried this too:
sudo apt-get update

No improvement.

Can someone help please ?

Thank you.
Didier.

---

