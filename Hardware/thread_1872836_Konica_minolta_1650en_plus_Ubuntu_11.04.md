---
title: "Konica minolta 1650en plus Ubuntu 11.04"
date: 2011-10-31
forum: Hardware
---

### Post by dugii on 2011-10-31
Hi,

Recently I've bought KM 1650en laser printer, it has LAN port, so just connected to my wifi router. In windows everything works fine, but got problem in Ubuntu with printing. I can see the printer, also I can install drivers (from KM website), but can't print. No matter what option I'll choose, there's always the same fail: 

"/usr/lib/cups/backend/dnssd failed"

and basicly, dont know where to start looking for solution.

---

### Post by mwijz on 2011-11-07
I have about the same problem: with 11.04 installing and printing with my KonicaMinolta 1650en went without problems, but now, woth 11.10, I have the same problem: instllation without problem, but no printing. The web-address of the printer is also given as `localhost', but the printer has an independant connection to my lan.

---

### Post by dugii on 2011-11-08
Hi,

I have manage with that problem, what you should do is click:

add printer -> find printer in network (U need to write in a fix IP for your printer in network)

then Ubuntu will find printer, show it manualy drivers and print :)

---

