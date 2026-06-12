---
title: "Win tv  1250 Tuner Card"
date: 2010-12-18
forum: Hardware
---

### Post by David52 on 2010-12-18
I have done some research thru the forum and thru linux.org and they say that this tv turner card should work under Ubuntu 10.10. When I go into the terminal it shows me that it is there
> david@ubuntu:~$ lspci -vvnn++
lspci: invalid option -- '+'
Usage: lspci [<switches>]

Basic display modes:
-mm Produce machine-readable output (single -m for an obsolete format)
-t Show bus tree

Display options:
-v Be verbose (-vv for very verbose)
-k Show kernel drivers handling each device
-x Show hex-dump of the standard part of the config space
-xxx Show hex-dump of the whole config space (dangerous; root only)
-xxxx Show hex-dump of the 4096-byte extended config space (root only)
-b Bus-centric view (addresses and IRQ's as seen by the bus)
-D Always show domain numbers

Resolving of device ID's to names:
-n Show numeric ID's
-nn Show both textual and numeric ID's (names & numbers)
-q Query the PCI ID database for unknown ID's via DNS
-qq As above, but re-query locally cached entries
-Q Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]] Show only devices in selected slots
-d [<vendor>]:[<device>] Show only devices with specified ID's

Other options:
-i <file> Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file> Look up kernel modules in a given file instead of default modules.pcimap
-M Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method> Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val> Set PCI access parameter (see `-O help' for a list)
-G Enable PCI access debugging
-H <mode> Use direct hardware access (<mode> = 1 or 2)
-F <file> Read PCI configuration dump from a given file
david@ubuntu:~$ 
david@ubuntu:~$ 
david@ubuntu:~$ 
david@ubuntu:~$ 

this is what I get, now can someone give me some advice on this one. I have installed my tv and then tried tv time, but tv time will not load. My tv will load but tells me no device found. I am bound to make the turner card work. Wiki says it will. Let me know if anyone has some advice please.
david

---

### Post by IcarusR on 2010-12-18
That terminal out put does not show anything but the lspci help.
Try running either

```
lspci
```

or

```
lspci -vv
```

Is there anything about TV card in the logs ??

This page should help you....

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200")

---

### Post by David52 on 2010-12-18
lspci, yes I have run that in the terminal and it does show the turner card. I will check out your pages of info tonite and if you would keep a eye on me if u know what ur doing on this issue. only been active in ubuntu for a few months so guess I am still green.
david

---

