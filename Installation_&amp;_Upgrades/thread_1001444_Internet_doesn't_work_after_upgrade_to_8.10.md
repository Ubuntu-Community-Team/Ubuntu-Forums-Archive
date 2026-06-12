---
title: "Internet doesn't work after upgrade to 8.10"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by al3c on 2008-12-03
Sorry if this has been posted before but I've searched and searched and can't find out the solution.  Basically the internet worked fine in 8.04 and then I upgraded to 8.10 and now it doesn't work.  I'm still new with ubuntu so anyone have any suggestions?

---

### Post by DieB on 2008-12-04
ever checked the 
"HARDWARE&dRIVERS" section in system-settings ?
p.S:: the namig might be a bit different due to differnt locale ,9

---

### Post by al3c on 2008-12-08
Yeah I checked there and it was pretty much blank.  I don't really have any idea what to do, anyone have any other suggestions?

---

### Post by bl4hbl4hbl4h on 2008-12-08
Type in lshw -C network in the terminal and post what comes up.

---

### Post by al3c on 2008-12-11
This is what came up 


```







WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:13:20:7d:e3:c4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:6c:ac:87:85:ca
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes





```

---

### Post by al3c on 2008-12-15
Bump

---

### Post by al3c on 2008-12-19
Anyone?

---

### Post by Sum Guy on 2008-12-19
it might be one of the glitches in the network manager. i've got the one where it won't connect to a d-link g604t router. incidentally, how can we get the updates when they come out that fix it without internet?

---

### Post by DieB on 2008-12-21
computer/linux magazines often provide dvds with updates from the repositories. or simply use a different computer and download that needed package.

---

