---
title: "Ubuntu on Dell poweredge 800 SATA"
date: 2004-12-17
forum: Hardware &amp; Laptops
---

### Post by Maxobelix on 2004-12-17
Hi everybody,
  
  I have some problems with warty's installation on this server.
 The worst one is due to the clock synchronization (software-hardware). During boot, the first step is ok but i have to end the second step with CTRL+C...
 During a shutdown or a reboot the last step (saving the system clock to the hardware clock) freeze my server, i have no solution to override it, i have to make a hardware shutdown (switch off).
  
 I have read and tried some solution about chmod -x /etc/init.d/hwclock.sh or/and chmod -x /etc/init.d/hwclockfirst.sh but i still have these problems...
  
  Any suggestions ?
  
  
  Best regards from Paris.
  PS : Sorry for my bad english...

---

### Post by Maxobelix on 2004-12-22
I have solved my clock synchro's problems with this help :
 
 [http://lists.debian.org/debian-kernel/2004/12/msg00151.html](http://lists.debian.org/debian-kernel/2004/12/msg00151.html)
 
 On Ubuntu we have to add --directisa on these lines :
 
 /etc/init.d/hwclock.sh
lines 69, 98, 114

/etc/init.d/hwclockfirst.sh
lines 61, 77, 79, 84

/usr/sbin/tzsetup
line 142

All works fine now ! :lol:

---

