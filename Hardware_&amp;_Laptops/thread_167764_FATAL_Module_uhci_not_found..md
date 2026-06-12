---
title: "FATAL: Module uhci not found."
date: 2006-04-29
forum: Hardware &amp; Laptops
---

### Post by opera on 2006-04-29
I am trying to get my webcam working and in doing so i am advised to enter via terminal "lsmod | grep uhci" and "sudo modprobe uhci".

This is what I get: 

@ubuntu:~$ lsmod | grep uhci
uhci_hcd               33680  0
usbcore               129668  5 pegasus,usblp,ehci_hcd,uhci_hcd

@ubuntu:~$ sudo modprobe uhci
FATAL: Module uhci not found.

This is where I got the commands:
[http://wiki.ubuntu-fr.org/materiel/webcam_logitech_msn?s=amsn](http://wiki.ubuntu-fr.org/materiel/webcam_logitech_msn?s=amsn)

Help very much appreciated.

---

### Post by Sutekh on 2006-04-29
The first command
```
lsmod | grep uhci
```checks that you have the needed modules installed.  

They are typically there by default, and the repsonse you got confirms that you already have the neccessary modules.  Indeed the instructions state that the modprobe command is only needed if the modules are not present.

I think you can skip the 'modprobe' command and continue.

---

