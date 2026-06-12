---
title: "Loaded module &quot;X&quot; is called &quot;Y&quot; in modules directory--why not the same?"
date: 2008-08-01
forum: General Help
---

### Post by caljohnsmith on 2008-08-01
While helping tijmz solve his ndiswrapper problem, he found something that I was totally unaware of up until this point: he was having problems with the module [COLOR="Blue"]prism54pci[/COLOR] being used for his wireless card instead of his Windows driver via ndiswrapper. So he blacklisted prism54pci, but still it was being loaded. He searched through his [COLOR="Blue"]/lib/modules/`uname -r[/COLOR]` directory tree, and couldn't even find a module with that exact name (prism54pci.ko). But then he noticed a similarly named module [COLOR="Blue"]p54pci.ko[/COLOR], which he then blacklisted, and finally no longer was [COLOR="Blue"]prism54pci[/COLOR] being loaded.

To figure out what was going on, I did:
```
john@TECH5321:~$ modinfo p54pci
filename:       /lib/modules/2.6.24-20-rt/kernel/drivers/net/wireless/p54pci.ko
[COLOR="Red"]alias:          prism54pci[/COLOR]
license:        GPL
description:    Prism54 PCI wireless driver
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     6DB895A8682C1EC6D253199
alias:          pci:v00001260d00003886sv*sd*bc*sc*i*
alias:          pci:v00001260d00003877sv*sd*bc*sc*i*
alias:          pci:v000010B7d00006001sv*sd*bc*sc*i*
alias:          pci:v00001260d00003890sv*sd*bc*sc*i*
depends:        p54common,mac80211
vermagic:       2.6.24-20-rt SMP preempt mod_unload 586 
```
Lo and behold, the prism54pci module being loaded was actually the p54pci module.

So now comes the question, if I want to blacklist a module, how am I going to know its real name? If it is aliased like above, I won't know the correct module to blacklist. I suppose I could write a bash script that takes every module in the /lib/modules/`uname -r` directory tree and passes it to modinfo, and then I could grep it to find the aliased name of the module actually being loaded.

Any ideas or thoughts about this? Thanks in advance.

---

