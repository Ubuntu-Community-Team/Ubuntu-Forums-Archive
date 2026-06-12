---
title: "Fujitsu Lifebook UH552 ?"
date: 2012-09-07
forum: Hardware
---

### Post by Fujiuser on 2012-09-07
Tried installing and most things work ok with 12.04. Screen brightness adjustment are fine, wifi is a little bit flaky but it's easy to replace wifi card if necessary. Synaptics Touchpad/clickpad does not work and it would be great to know if someone has got it working? Otherwise it's a great experience to run Ubuntu on this ultrabook, maybe HD4000 graphics will get a good driver later too.

---

### Post by inasne on 2012-09-15
Yes, I also have the same laptop. Obviously with the same problem, if anyone has any ideas on what to do to get the touchpad running in ubuntu I would appreciate it.

---

### Post by jerrrys on 2012-09-15
Got a few hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Fujitsu+Lifebook+UH552&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Fujitsu+Lifebook+UH552&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

And welcome to the forums :)

---

### Post by inasne on 2012-09-15
Thank you, feels good to be here :)

Couldn't find anything there, it was mostly broken links to this site :/ But thanks anyway.

---

### Post by halfex on 2012-09-27
Fujiuser, insane: Can you post output of lsusb command?

---

### Post by inasne on 2012-09-27
Sure.

here is the output from lsusb -t:

inasne@inasne-LIFEBOOK-UH552:~$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    |__ Port 2: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 3: Dev 5, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 3: Dev 5, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
        |__ Port 3: Dev 4, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
        |__ Port 3: Dev 4, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M

and here is the lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 005: ID 04c5:1330 Fujitsu, Ltd 
Bus 001 Device 004: ID 10f1:1a44 Importek 

any ideas?

---

### Post by mbergner on 2012-10-23
Hi there,

i got the touchpad running on Fujitsu UH552. I added the parameter i8042.notimeout to the entry GRUB_CMDLINE_LINUX_DEFAULT of /etc/default/grub, did a "sudo update-grub" and rebooted. For left click, tap with one finger, for right click, tap with two fingers.

---

### Post by Fujiuser on 2012-11-09
> **mbergner said:**
> Hi there,

i got the touchpad running on Fujitsu UH552. I added the parameter i8042.notimeout to the entry GRUB_CMDLINE_LINUX_DEFAULT of /etc/default/grub, did a "sudo update-grub" and rebooted. For left click, tap with one finger, for right click, tap with two fingers.


Fantastic, works well! are there any side effects possible by this hack? less batterytime?

---

### Post by cdiem on 2013-02-11
I'm considering this laptop for Ubuntu. 
Im curious about the battery life/fan noise/temperature. Do you have any positive or negative experiences with the above after using it for some time? Thanks you in advance for any opinions.

---

### Post by rvibek on 2013-05-25
> **cdiem said:**
> I'm considering this laptop for Ubuntu. 
Im curious about the battery life/fan noise/temperature. Do you have any positive or negative experiences with the above after using it for some time? Thanks you in advance for any opinions.

i am considering it as well. anybody, your thoughts?

---

