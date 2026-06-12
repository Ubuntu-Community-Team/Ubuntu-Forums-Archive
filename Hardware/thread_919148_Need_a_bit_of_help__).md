---
title: "Need a bit of help  :)"
date: 2008-09-13
forum: Hardware
---

### Post by ZQ8 on 2008-09-13
Ok so one of my friends in college introduced me to Ubuntu and I am a VERY FIRST TIME USER lol. 

Here is my thing.....I am somewhat computer inclined but am havin issues with Ubuntu 8.04 on my Dell XPS M1210 laptop.  I have a tri-boot with XP, Vista, and Ubuntu. I have evrything working in Ubuntu EXCEPT for my ISP. I have an AT&T air card and I can't figure out how to get it to work!! I hate having to go to xp or vista just for internet surfing as I LOVE how fast Ubuntu is.

I have a Option GT MAX 3.6 Express card. and the lights flash when I plug it into the PCI port but i don''t have anything to click "connect" so i can surf the net. This air card is the source of internet that I use the most. 

Any help would be grate!!! :biggrin:

---

### Post by NoReflex on 2008-09-13
Hello!

I have a Huawei E220 3G modem from Vodafone and it works very well on Ubuntu Hardy (in fact I'm using it right now).
If your card is anything like my modem then you should find some interface like /dev/ttyUSB0 for it. In Gnome I use Gnome PPP and in KDE I use KPPP (both work with my modem).
First you can check if your system recognizes the card. I don't know how you connect your card (PCI, PCMCIA, USB) so try **lspci** or **lsusb** to find it.
Also, could you post the result of **tail /var/log/messages**? 

Best wishes,
NoReflex

---

### Post by ZQ8 on 2008-09-13
i think that this is what you want right??

jose@jose-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
jose@jose-laptop:~$

---

### Post by ZQ8 on 2008-09-13
I also ran the lsusb and it did recongnize the card!!!!

jose@jose-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0af0:6701 Option 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
jose@jose-laptop:~$

---

### Post by NoReflex on 2008-09-14
Ok! So the system recognizes your card. Could you post the result of **tail /var/log/messages**. You should run this command about thirty seconds after you plugin your card.

Best wishes,
NoReflex

---

### Post by rrrlc on 2008-09-16
ZQ8-

I noticed that your audio device was the Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller rev 01.  Are you having sound troubles as well?

---

### Post by ZQ8 on 2008-09-16
> **rrrlc said:**
> ZQ8-

I noticed that your audio device was the Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller rev 01.  Are you having sound troubles as well?


none so far....and I have watched a complete movie with VLC player yesterday. the only thing is that the sound is a lil on the soft side but I can deal with it :D



here are the results for you NoReflex

jose@jose-laptop:~$ tail /var/log/messages
Sep 16 09:29:13 jose-laptop kernel: [   42.178414] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Sep 16 09:29:13 jose-laptop kernel: [   42.184696] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
Sep 16 09:29:13 jose-laptop kernel: [   42.184743] option 2-2:1.0: GSM modem (1-port) converter detected
Sep 16 09:29:13 jose-laptop kernel: [   42.184908] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
Sep 16 09:29:13 jose-laptop kernel: [   42.184923] option 2-2:1.1: GSM modem (1-port) converter detected
Sep 16 09:29:13 jose-laptop kernel: [   42.185027] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
Sep 16 09:29:13 jose-laptop kernel: [   42.185041] option 2-2:1.2: GSM modem (1-port) converter detected
Sep 16 09:29:13 jose-laptop kernel: [   42.185144] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
Sep 16 09:29:13 jose-laptop kernel: [   42.185160] usbcore: registered new interface driver option
Sep 16 09:29:13 jose-laptop kernel: [   42.185164] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
jose@jose-laptop:~$

---

### Post by NoReflex on 2008-09-16
Apparently everything is fine. Try to start Gnome PPP (it should be under the Internet menu; if it's not install it : sudo apt-get install gnome-ppp).
Now go to Setup, hit Detect, under the Modem section and it should detect your modem as /dev/ttyUSB0. After that click Close, enter the phone number (in my case it's *99# - Vodafone) and click Connect.
If your modem isn't detected try the following : 
```
rmmod airprime
rmmod usbserial
```
then unplug your device, wait a few seconds and then plug it back in and it should be detected.
Good luck!

Best wishes,
NoReflex

---

### Post by ZQ8 on 2008-09-17
ok it almost worked!! it connected for like 1 second and then asks if I wanna connect again. i did a screne shot of the connection log so you can see :D

---

### Post by NoReflex on 2008-09-19
Are you sure that *99# is the number you have to dial. It seems a little odd that it would match the number i use...

---

### Post by ZQ8 on 2008-09-19
> **NoReflex said:**
> Are you sure that *99# is the number you have to dial. It seems a little odd that it would match the number i use...

hmmm.....maybe. Mine uses a SIM card from a cell phone and it has a full (888)888-8888 number a 10-digit number bot a 4 digit one.:)

---

