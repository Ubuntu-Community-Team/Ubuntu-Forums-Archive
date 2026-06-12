---
title: "Benq 640U scanner problem"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by SilvioTO on 2005-03-05
Hi, I'm installed ubuntu 4.1 and, when xsane start (as root), give this error: 
"impossible to open device 'snapscan:libusb:006:004'; invalid argument.
if I start xsane as normal user the same error appear.

the only way is restart pc with windows xp, restart pc with ubuntu; in this case the scanner work correctly.

I have put the firmware in /dev directory and add line "firmware /dev/u96v121.bin" in snapscan.conf file.

Now I don't know to do; can you help me please? I readed the other thread of scanner problems but don't know wich way is right for me...

Thanks.
Silvio, Torino, Italy.

---

### Post by SilvioTO on 2005-03-07
I found the problem.
Windows, when turn off, "umount" the scanner and turn it off. If I make a windows session, without turn off the scanner and reboot, ubuntu recognize it and xsane work correctly.

If I turn on pc, start ubuntu, and after turn on the scanner, don't work. When turn off ubuntu the scanner remain turn on, whit green led.

If I leave scanner always on, ubuntu turn it off when pc turned off, and at reboot work correctly.

Any ideas to resolve this problem? For now I leave scanner always on.

Thanks, Silvio.

---

