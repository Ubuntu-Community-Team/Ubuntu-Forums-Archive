---
title: "Acer extensa 5220 irda not working"
date: 2008-08-11
forum: Hardware
---

### Post by twinkel1961 on 2008-08-11
Hi

I can not get irda to work.
lsmod shows the nsc_ircc alright.
I stopped /etc/init.d/irda-setup and irda-utils
now when i start irda-setup: i get:
 /etc/init.d/irda-setup: line 76: echo: write error: Device or resource busy
 /etc/init.d/irda-setup: line 77: echo: write error: Device or resource busy
 /etc/init.d/irda-setup: line 83: setserial: command not found
 /etc/init.d/irda-setup: line 84: setserial: command not found[/FONT]

and syslog shows:
   nsc-ircc 00:0a: in use; can't configure

irda-utils shows:
  Starting IrDA service: irattach.
and in syslog:
 irattach: executing: '/sbin/modprobe irda0'
 irattach: + FATAL: Module irda0 not found.
 irattach: Trying to load module irda0 exited with status 1
 irattach: executing: 'echo twinkel-5220 > /proc/sys/net/irda/devname'
 irattach: executing: 'echo 1 > /proc/sys/net/irda/discovery'
 irattach: Starting device irda0
 irlap_change_speed(), setting speed to 9600

in /etc/default/irda-utils I have:
 DEVICE=/dev/ttyS1
 dongle="none"

Can anyone help me to get this working please?

---

### Post by twinkel1961 on 2008-08-22
**bump**


anybody please?

---

### Post by _teevee_ on 2008-09-13
Hi
I had acer extensa 5220 with xubuntu 8.04. I had problem with hardware. I reinstalled the system to ubuntu 8.04.1 and it works well now. IrDa to.
Regards
Tomas

---

