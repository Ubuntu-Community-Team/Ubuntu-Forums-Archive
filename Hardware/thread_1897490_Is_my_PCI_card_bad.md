---
title: "Is my PCI card bad?"
date: 2011-12-19
forum: Hardware
---

### Post by w3rn on 2011-12-19
I upgrade from Karmic/Lucid to v11.10. And I also install a new ASUS motherboard M5A87.
All previous pci cards work fine except one. I am trying to determine if this is bad . 

Here is the info I obtain:

"lspci -v" 
     04:05.0 Network controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
    Subsystem: Device 4001:0001
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at d800 [size=256]
    Memory at fe3ff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: netjet
    Kernel modules: hisax, netjet
    Looks ok!

"sudo modprode radiomain"
     This is the "/var/log/syslog responses:
          Dec 19 10:29:40 w3rn kernel: [ 2138.017359] radioMain: Searching For Devices
          But i am also suppose to get "Found card %s, base address %#lx"
          Does not look like the probe function is working for the driver or bad pci card.

"sudo rmmod radioMain"
     This is the "/var/log/syslog responses:
         Dec 19 10:36:01 w3rn kernel: [ 2518.731485] radioMain: End All Device Searches
         This is the correct response.

Is there some new version changes or just a bad card?
is there anything else I need to check?

---

### Post by w3rn on 2011-12-19
Quick update:

I reinstall the karmic distribution on this new motherboard. This the output after running "sudo modprobe radioMain":

Dec 19 20:07:44 puredyne kernel: [ 1257.378531] radioMain 0000:04:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 19 20:07:44 puredyne kernel: [ 1257.378645] radioMain0: Found card 0000:04:05.0, base address 0xd800
Dec 19 20:07:44 puredyne kernel: [ 1257.378727] radioMain: Searching For Devices

The pci card was correctly probe, install and found. There is nothing wrong with my pci card. There seems to be some missing kernel functionality in ubuntu version 11.10.
Can someone please help!!!

---

### Post by xyzzyman on 2011-12-20
When you upgraded to 11.10 was it an apt-get dist-upgrade or was it a fresh install? Also, what is the output of "lspci -v" in karmic?

---

### Post by wolfen69 on 2011-12-20
> **w3rn said:**
> Quick update:

I reinstall the karmic distribution on this new motherboard. This the output after running "sudo modprobe radioMain":
Karmic is ubuntu 9.10. Below you say you are using 11.10. Which one are you using?

> **w3rn said:**
> The pci card was correctly probe, install and found. There is nothing wrong with my pci card. There seems to be some missing kernel functionality in ubuntu **version 11.10**.
Can someone please help!!!

---

### Post by xyzzyman on 2011-12-20
> **wolfen69 said:**
> Karmic is ubuntu 9.10. Below you say you are using 11.10. Which one are you using?

He was using Karmic/9.10. His card works, even doing a fresh install of it so he knows the card is still good. Under 11.10 the card doesn't work which is why he posted here.

---

### Post by w3rn on 2011-12-20
"lspci  -v" in karmic:

04:05.0 Network controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
    Subsystem: Device 4001:0001
    Flags: bus master, medium devsel, latency 64, IRQ 10
    I/O ports at d800 [size=256]
    Memory at fe3ff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel modules: hisax


How do I get  hisax to be the main kernel module in ubuntu v11.10?

It was a fresh install to v11.10

---

### Post by w3rn on 2011-12-20
Must remove netjet prior to issuing the "sudo modprobe" command:

     "sudo rmmod netjet"


I do not know if you should blacklist it!!!!!!

---

