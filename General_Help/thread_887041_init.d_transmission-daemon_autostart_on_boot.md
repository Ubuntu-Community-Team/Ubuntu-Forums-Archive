---
title: "init.d transmission-daemon autostart on boot"
date: 2008-08-11
forum: General Help
---

### Post by Dannyboyni on 2008-08-11
Hi does anyone know of a script i could use to allow me to auto start transmission-daemon, upon boot, i dont want it to start on session logon, but upon boot.

I am using ubuntu 8.04 desktop (Hardy Heron)
I have installed transmission-daemon version 1.32

thanks for your help.

---

### Post by micro77 on 2008-09-08
hi
try this ;
in file 
 nano /etc/rc.local   

```

#exit=0  
#add this ;
transmission-daemon
```

every boot time your bt daemon will be starting .
:KS

---

### Post by lmandrake on 2008-09-10
Just starting transmission-daemon in rc.local isn't a good idea IMHO. It runs as root and uses some default configuration.

A sudo -u WHATEVER_GUY transmission-daemon should be better but doesn't find the cusotom configuration in .config/transmission-daemon :/

---

### Post by hyper_ch on 2008-09-10
with an init script you can make it run under any user.

---

### Post by mugenryuaikido on 2008-11-29
> **lmandrake said:**
> A sudo -u WHATEVER_GUY transmission-daemon should be better but doesn't find the cusotom configuration in .config/transmission-daemon :/
transmission-daemon has this covered: try -g<config-dir>.

---

