---
title: "acer aspire: can't connect to internet"
date: 2009-09-26
forum: Hardware
---

### Post by wakajawaqa on 2009-09-26
hi, just installed ubuntu 9.04 on an acer aspire 5517 laptop and can't connect to my wired ethernet connection

i ran "if config eth1" in the terminal and it came up as device not found

i've been checking around but can't seem to find any fixes, is there a known hardware issue with this model?

thanks

---

### Post by Jose Catre-Vandis on 2009-09-26
Was your ethernet connected when you installed? Did you see it allocate an IP address via DHCP during the installation? What is the output of **ifconfig** and **lspci -v**?

---

### Post by wakajawaqa on 2009-09-26
thanks for the reply

the results are as follows (i cut lspci -v down to what seemed to be the relevant information...):

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e016
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at d1100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

08:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
    Subsystem: Acer Incorporated [ALI] Device 028d
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d1000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>


and:

~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by wakajawaqa on 2009-09-26
and i wasn't connected when i installed

---

### Post by Jose Catre-Vandis on 2009-09-27
You answer should be here

[http://ubuntuforums.org/archive/index.php/t-1244898.html](http://ubuntuforums.org/archive/index.php/t-1244898.html)

---

### Post by wakajawaqa on 2009-09-27
Success!

thank you very much, i had been digging around for hours trying to find a fix

cheers

---

### Post by Jose Catre-Vandis on 2009-09-27
:)

Please mark as solved

---

