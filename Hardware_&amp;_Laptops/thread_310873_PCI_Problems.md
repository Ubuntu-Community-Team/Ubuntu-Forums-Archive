---
title: "PCI Problems?"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by igeterrors on 2006-12-01
About a week ago I managed to install Xubuntu on an old K6-2 box I had lying around.  I say "managed" because I'd been trying for weeks, using every technique I could glean from forums, google, etc, to get some form of Ubuntu running on that thing.  But since I do all my work on my laptop, which already has Ubuntu Dapper on it, having the other PC just sitting there seemed kind of anticlimactic.  So I got the idea that I'd drop down to runlevel 3 and maybe use it as a server.  When I did so, I discovered sheer waves of the following message cascading across my monitor:

```
Dec  1 08:26:03 ubuntu kernel: [17461291.152000] uhci_hcd
0000:00:0b.0: host system error, PCI problems?
Dec  1 08:26:03 ubuntu kernel: [17461291.152000] uhci_hcd
0000:00:0b.0: host controller process error, something bad happened!
Dec  1 08:26:04 ubuntu kernel: [17461292.160000] uhci_hcd
0000:00:0b.0: host system error, PCI problems?
Dec  1 08:26:04 ubuntu kernel: [17461292.160000] uhci_hcd
0000:00:0b.0: host controller process error, something bad happened!
Dec  1 08:26:05 ubuntu kernel: [17461293.160000] uhci_hcd
0000:00:0b.0: host system error, PCI problems?

[...snip...]


```

This error message has apparently been generated twice a second for the past week!  I just didn't know about it because it was all happening underneath the desktop, if you will.  

Anyway, it seems to indicate a problem with the USB PCI card, or maybe the driver?  But since I'm a newbie, I haven't got a clue what to do about it.  Other than just shut off the computer before the error logs fill up my hard drive!  :) 

Please, any help would be appreciated.  Thanks.

-------------------------------------------------------------------------------
"To err is human, but to really foul things up requires a computer."
Farmers' Almanac, 1978

---

