---
title: "IP Printing in Intrepid?  (Dell 1815dn)"
date: 2008-11-02
forum: General Help
---

### Post by windfix on 2008-11-02
I have two Dell 1815dn printers that worked fine under Hardy, but I can not get them working under Intrepid.  Any ideas?

The Printer dialogue allows me to input the IP address if I use AppSocket/JetDirect (prepends "socket://" and appends ":9100", but not if I use Other. I browse to the .ppd file and the printer is successfully added.

After it's added I get a "Printer X may not be connected" error.

Help!

(obtained .ppd file per these instructions:  [http://sudan.ubuntuforums.com/showthread.php?t=768745](http://sudan.ubuntuforums.com/showthread.php?t=768745) )

---

### Post by windfix on 2008-11-02
OK - solved my own problem.  Must eliminate preceding zeros in the IP addresses.  ie, use 192.168.2.51 vs. 192.168.002.051)

Maybe this tip will help somebody else!

---

