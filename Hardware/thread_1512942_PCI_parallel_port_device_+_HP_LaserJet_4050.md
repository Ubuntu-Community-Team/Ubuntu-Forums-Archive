---
title: "PCI parallel port device + HP LaserJet 4050"
date: 2010-06-18
forum: Hardware
---

### Post by niiiklas on 2010-06-18
Hey,

I've recently got my hands on an old HP LaserJet 4050 T printer. So I got myself a pci card with a parallel port to use the printer via lpt. I plugged the card in, I plugged the printer in, added the printer from the parallel port, but it's not really reacting to print jobs. Now I'm trying to figure out whether it's the printer or the pci card that's not configured/installed properly. 

I'm using Ubuntu 10.04, 64-bit. I've searched the forums for general problems with pci parallel port cards and didn't find anything at all. On the other hand, I found a couple threads about the same printer I have now. The users there experienced similar problems, but no suggested workarounds worked for me.

Could somebody point out to me how I could check whether the devices are properly installed, resp. which one isn't? The card is a Delock [89015]("http://delock.com/produkte/gruppen/IO+Karten/Delock_PCI_Card_1_x_Parallel_89015.html"). I did not install any additional drivers for the card. When trying to add a new printer under Sys->Adm->Printing, I get a listing under Parallel Port #1. When I add the printer using the HP driver, it doesn't print. One solution on the forums was to use the Generic PS driver instead. Same result. The test page never gets printed.

Maybe this is a start:
```
[nik@nik ~]$ lsmod | grep lp
lp                      9336  2 
parport                37160  3 ppdev,parport_pc,lp

```I added three printing jobs. Using the GUI, there are no printing jobs listed under View Print Queue. However, lpstat returns

```
[nik@nik ~]$ lpstat
HP-24                   nik             205824   Sat 19 Jun 2010 12:13:59 AM CEST
HP-25                   nik             205824   Sat 19 Jun 2010 12:14:12 AM CEST
HP-26                   nik             205824   Sat 19 Jun 2010 12:14:28 AM CEST

```. I realized there were quite a few more jobs in the queue so I deleted them all with cancel HP-JOBID. Still nothing. lpstat -p HP returns

```
[nik@nik ~]$ lpstat -p HP
printer HP now printing HP-0.  enabled since Sat 19 Jun 2010 12:14:10 AM CEST
    Printer busy; will retry in 30 seconds...

```

I'd really appreciate any help.

---

### Post by niiiklas on 2010-06-19
Bump. Seriously, no one? :/

---

