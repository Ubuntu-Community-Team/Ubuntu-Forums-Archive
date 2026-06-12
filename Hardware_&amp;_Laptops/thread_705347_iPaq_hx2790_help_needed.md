---
title: "iPaq hx2790 help needed"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by zikace on 2008-02-23
Hello,
could you please help me with connecting my iPaq? I have installed all the needed packages, but I think the problem is elsewhere .First I need to load the iPaq driver manually and second, the system doesnt recognize the iPaq at all. It does recognize that there is a device connected to the usb and that it is HP, but there is no information about the ttyUSBx as I saw in all the tutorials. W/o that I am completely lost. I saw in some tutorials that it perfectly worked for hx4150, that should be similar devices. 

dmesg |tail output: 
```
petr@pjc:~$ sudo modprobe ipaq
[sudo] password for petr:
petr@pjc:~$ dmesg |tail
[  264.012000] usbcore: registered new interface driver usbserial_generic
[  264.012000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  264.056000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
[  264.056000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
[  264.060000] usbcore: registered new interface driver ipaq
[  272.792000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  272.976000] usb 3-1: configuration #1 chosen from 1 choice
[  273.300000] usbcore: registered new interface driver cdc_ether
[  273.664000] eth2: register 'rndis_host' at usb-0000:00:1d.2-1, RNDIS device, 80:00:60:0f:e8:00
[  273.668000] usbcore: registered new interface driver rndis_host

```

lsusb output:
```
petr@pjc:~$ lsusb
Bus 004 Device 001: ID 0000:0000  petr@pjc:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:0301 Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 0000:0000  
petr@pjc:~$  
```

---

### Post by oldsoundguy on 2008-02-23
what operating system is on your iPaq?  If you have not changed that to Familiar Linux or some other of the new PDA Linux builds, you will have NO access to the iPaq from a Linux machine.  Liinux can't work with the file system since it is WINDOWS.

---

### Post by zikace on 2008-02-23
There is a Windows Mobile 5, but I just want to synchronise with Evolution. And every tutorial is for synchronizing Windows Mobile with Ubuntu ([here]("https://help.ubuntu.com/community/PortableDevices/WindowsMobile?action=show&redirect=PocketPCHowto")), so I think It should work

---

### Post by oldsoundguy on 2008-02-23
I have found several references on various iPaq sites for other issues and mostly they say "If a device is not listed as working in a program, it will not work!"

I am trying to PUT Linux on a 4155 and on a 5455 and have hit a brick wall with the flash utility! (and the forum sites are sparsely populated.)

But I now see what you are attempting.  Somehow trying to run a Linux program on a Windows machine seems a real task.  I wish you luck (I know how bad it can be to have to use OutHOUSE!)

Did you cut and paste the commands from that page? (a typo can upscrew you if not careful!)

---

### Post by zikace on 2008-02-23
I am not trying to run anything on the iPaq. I am just trying to get to work the MultiSync ot synchronise the PIM in the iPaq with Evolution. But first of all, I need Ubuntu to recognize the iPaq and to connect it to ttyUSBx and I dont know why it is not working.
Sry if I expressed myself unclearly, English is not my native language.

---

### Post by zikace on 2008-02-28
Please. Don't tell me that there is noone who synchronise iPaq with Evolution :(

---

### Post by Yellow Pasque on 2008-02-28
Try this:
```
sudo update-usbids
lsusb
```

---

### Post by zikace on 2008-03-01
Thank you for your reply, but unfortunately, it doesnt solve anything. It still doesnt show which ttyUSB the pda is connected to.

---

