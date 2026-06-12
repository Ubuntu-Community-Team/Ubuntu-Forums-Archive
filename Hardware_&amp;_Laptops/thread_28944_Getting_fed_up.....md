---
title: "Getting fed up...."
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by HainjeDAF on 2005-04-22
Well, I'm new to Ubuntu but longtime user of Debian.
I got Ubuntu on DVD with Linux Magazine

Hardware:
Asus P2B + PII-400
IBM 40Gb Harddrive /dev/hda
Lite-on DVD /dev/hdd
3ware 7506-4LP P-ATA raid array /dev/sda (500Gb)
             4x 250 Gb Seagate P-ATA-133 ->

Now I really in trouble: Mij 3Ware 7500-4LP 4-port parallel ATA raid is not accessed.
In insall, It was identified, formated and mountend as /target/srv
Butr after reboot it refuses to be seen. The 3w-xxxx module is loaded. and LSPCI reconginzes it.
But when I mount, it says 'special device /dev/sda1 missing'.

I've
-edited the initrd modules file and made a new initrd.
-copied 3w-xxxx to /lib/modules/2.6.10-2-686/initrd and made new initrd
-edited /etc/modules

several reboots later I'm still stuck and inclined towards getting Debian/Sarge back... But probably I'm missing a key point. It seems that the kernel ought to make /dev/sda and /dev/sda1 by itself but it doesn't....

Help?!?

Regards,
marout Borms

---

