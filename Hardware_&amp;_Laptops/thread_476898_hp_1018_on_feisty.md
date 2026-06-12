---
title: "hp 1018 on feisty?"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by Maxster on 2007-06-17
hello
i got a laserjet 1018, im running ubuntu 7.04

wen i go throught the wizard printer install, it finds my printer (twice:
Hp laserjet 1018 (hp laserjet 1018 usb#1
and
Hp laserjet 1018 (hp laserjet 1018 kp03jadhplip )

i installed foo2zjs with the ppd file throught the wizard.

finished the wizard reboot and does not print...
wen i go to print everything looks okay from the computer side but he printer does not budge or flash a light!

thanks to anyone who helps!

---

### Post by ShagzModo on 2007-06-22
same problem here....
I picked up a new lj1018 today.
The printerdriver shipped on feisty does not print a page.
no errors, the printjobs disappear out of the queue

suggestions anyone???

---

### Post by sam123 on 2007-06-23
From [ http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018 ]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018"),

Only the firmware is missing in the distribution; to get it just enter this in a root shell (sudo bash): 
getweb 1018 ; arm2hpdl sihp1018.img > /usr/share/foo2zjs/firmware/sihp1018.dl
Then power off and on the printer and do the printer setup as usual.

---

### Post by elastigirl on 2007-10-02
Great post!

Thanks for the valueble information. Worked like a charm.

---

### Post by infol on 2007-10-14
thanks sam123 - worked perfectly.

---

