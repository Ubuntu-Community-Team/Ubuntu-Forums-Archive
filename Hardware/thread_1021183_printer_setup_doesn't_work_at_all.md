---
title: "printer setup doesn't work at all"
date: 2008-12-25
forum: Hardware
---

### Post by hapsis on 2008-12-25
Hi!

I have had quite a lot problems with printing lately, here's the case:

1) my printer (epson 880 on usb) wont be recognized on my laptops Ubuntu (8.10), it used to work but not anymore - somekind of update has done something, it recognizes and works on other computer with same version of ubuntu and also with the latest updates

2) when I try to open Gnome tool "default printers" it freezes for long time and I can see from top of the util that it tryes to connect to ip address wich belong to my other computer

I've tryed to remove and re-install all kinds of printing packets with Synaptics but no help. I do know that cups is up and running.

Anyone has any idea what to look for? I'm really considering to install whole ubuntu all over again - like using Windows... :)

- Hapsis Ipex

---

### Post by namdung on 2008-12-25
Connect the printer and type in terminal
```
lsusb
```

Is the Printer showing in the list?

---

### Post by hapsis on 2008-12-25
I've got it working eventually - I found out that I cannot use USB hub between my laptop and the Epson 880 printer -> probaply because lack of power on the USB... But there was something other wrong earlier because I didn't use USB hub all the time. 

What I did (if someone else googles these) I installed SAMBA server utility via Gnomes ADD / REMOVE programs before this. It might also had some effect. Now I try to take second try to get the network printing to work...


> hapsis@hapsis-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 014: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 001 Device 013: ID 059f:0651 LaCie, Ltd 
Bus 001 Device 012: ID 03eb:0902 Atmel Corp. 
Bus 001 Device 011: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 001 Device 005: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
hapsis@hapsis-laptop:~$ 


---

