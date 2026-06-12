---
title: "how to fix RAID 1 degraded"
date: 2009-10-04
forum: Hardware
---

### Post by catman711 on 2009-10-04
I just did a new install of Jaunty using "alt. x64 desktop" disk as RAID 1. All went fine and works great, except it boots in degraded mode. I used this [https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html) and followed to the letter.

I am a noob to Linux, but not computers. I did the normal diagnostics. I checked drives and cables. I can boot to desktop with ether drive connected to any port on MB. If both drives are connected it boots fine, but still shows degraded. 

If I run "sudo mdadm -D /dev/md1" with single drive (ether one) this is what get[ATTACH]130777[/ATTACH]

If I run "sudo mdadm -D /dev/md1" with both drives this is what I get
[ATTACH]130778[/ATTACH]

If I run "cat /proc/mdstat" with both drives this is what I get
[ATTACH]130780[/ATTACH]

I don't know how to find out which drive it is not recognizing or why.

Any help would be great

Please, if you give me code to run, give me a disc. of what it dose. I would like to LEARN what I am doing, not just "do this" That way I will know to do next time, or be able to help someone else.

AMD Athlon x2 500+
Gigiabyte GA-MA69VM-S2 AMD 690V/SB600
4GB ram

Thanks, Mike

---

