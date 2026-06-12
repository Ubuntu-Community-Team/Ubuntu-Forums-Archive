---
title: "Jaunty: Need to reinstall local printer after every reboot"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2009-05-23
HI,
I'm on a updated Kubuntu Jaunty (9.04). I have a Lexmark E232 laser printer connected to the parallel port. The problem is that after EVERY reboot, the printer isn't recognized and I've to reinstall it again. Below please find enclosed a cop of the syslog segment related to one of the printer installation sessions.
2 points which might be relevant:
a. This PC runs the Samba daemon (file sharing)
b. Kubuntu doesn't have an exact driver for that printer model. I install the "closest" Lexmark E230 which is recommended and works fine.
c. Note the last entry in the syslog saying "unregistered pardevice"


PLease Advise!
Best Regards,


Michael Badt


--------syslog  printer installation--------
May 22 12:14:42 Miki-Desk kernel: [ 2451.340363] ppdev0: registered pardevice
May 22 12:14:42 Miki-Desk kernel: [ 2451.353289] ppdev0: unregistered pardevice
May 22 12:14:42 Miki-Desk kernel: [ 2451.405592] ppdev0: registered pardevice
May 22 12:14:42 Miki-Desk kernel: [ 2451.414743] ppdev0: unregistered pardevice
May 22 12:14:42 Miki-Desk kernel: [ 2451.461166] ppdev0: registered pardevice
May 22 12:14:42 Miki-Desk kernel: [ 2451.476316] ppdev0: negotiated back to compatibility mode because user-space
May 22 12:14:42 Miki-Desk kernel: [ 2451.476324] ppdev0: unregistered pardevice
--------------------------

---

