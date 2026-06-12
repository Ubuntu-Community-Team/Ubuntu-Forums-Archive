---
title: "Problems about adding routes"
date: 2005-11-18
forum: General Help
---

### Post by c_coolguy on 2005-11-18
I have to add several routes to have the access to the LAN. So I wrote a script like that:
```

route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.85.52.254 metric 1
route add -net 10.85.52.0 netmask 255.255.255.0 gw 10.85.52.222 metric 20
route add -net 10.255.255.255 netmask 255.255.255.255 gw 10.85.52.222 metric 20
route add -net 61.129.42.0 netmask 255.255.255.0 gw 10.85.52.254 metric 1
route add -net 127.0.0.0 netmask 255.0.0.0 gw 127.0.0.1 metric 1
route add -net 202.120.64.0 netmask 255.255.240.0 gw 10.85.52.254 metric 1
route add -net 202.120.224.0 netmask 255.255.224.0 gw 10.85.52.254 metric 1
route add -net 218.78.236.0 netmask 255.255.252.0 gw 10.85.52.254 metric 1
route add -net 224.0.0.0 netmask 240.0.0.0 gw 10.85.52.222 metric 20
route add -net 192.168.0.0 netmask 255.255.0.0 gw 10.85.52.254 metric 1


```

I wonder how can I make this script run when I log in. Thanks.
:(

---

### Post by ebrowne on 2005-11-18
Add the script to the end of your .bash_profile

---

### Post by adwait on 2005-11-18
Alternatively add it in Sytem>Preferences>Session

---

### Post by c_coolguy on 2005-11-18
[QUOTE=ebrowne]Add the script to the end of your .bash_profile[/QUOTE]
Sorry, I have tried it, but nothing happened...

---

### Post by c_coolguy on 2005-11-18
[QUOTE=adwait]Alternatively add it in Sytem>Preferences>Session[/QUOTE]
But where can i find System>Preferences>sessions?
thanks

---

### Post by N6546R on 2005-11-18
If you'd like it to run when the machine boots, place it in the /etc/rc.? directories.

Perry

---

### Post by c_coolguy on 2005-11-18
[QUOTE=N6546R]If you'd like it to run when the machine boots, place it in the /etc/rc.? directories.

Perry[/QUOTE]
I have rc1.d, rc2.d, ... , rc6.d and rcS.d in /etc/

---

### Post by metoo on 2005-11-18
There must be a wiki guide somewhere...

/etc/inittab tells you into what run level you boot at default.

Put the script into /etc/init.d/your-script
Make it executable

Put a sym-link into /etc/rcX.d
where X is your runlevel from /etc/inittab

If I remember correctly
Kxxx kill is for leaving the run level,
Sxxx is for starting the run level.
Numbers are processed from low to higher.
S99 will be at the end of the start sequence (last to start) of the run level in which you have defined the sym-link.

---

### Post by c_coolguy on 2005-11-18
Thanks a lot It works. :) [QUOTE=metoo]There must be a wiki guide somewhere... /etc/inittab tells you into what run level you boot at default. Put the script into /etc/init.d/your-script Make it executable Put a sym-link into /etc/rcX.d where X is your runlevel from /etc/inittab If I remember correctly Kxxx kill is for leaving the run level, Sxxx is for starting the run level. Numbers are processed from low to higher. S99 will be at the end of the start sequence (last to start) of the run level in which you have defined the sym-link.[/QUOTE] :KS :KS :KS :KS :KS

---

