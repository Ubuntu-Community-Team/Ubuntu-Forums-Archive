---
title: "scanModem problem modem"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by frankabel on 2007-01-21
I run "sudo ./scanModem" as a first step to get ready my modem and the following error happend:

"
FATAL: Module slamr not found.

 To enable functional diagnostics, please either briefly login as Root:
         su - root (Not for Ubuntu)
 and unload and reload the modem driver
         sudo modprobe -r slamr
         sudo modprobe slamr
 Exit Root status
         exit
 and rerun
        ./scanModem
"

but when I "sudo modprobe -r slamr" the following error appear:

"FATAL: Module slamr not found."

How can I install slamr module?

Salute
Frank Abel

---

