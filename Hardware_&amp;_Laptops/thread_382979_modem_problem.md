---
title: "modem problem"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by john1911 on 2007-03-12
I have problem with eksternal usb modem. 
I used Ubunu 6.10 for a couple of days, can somebody help me to install it.
I scan with scanmodem, here is a modem dat file:

Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List
Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org)
.
 Local Linux experts can be found through:
[http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2
20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26
UTC 2006 (Ubuntu 2.6.17-10.34-generic)
 scanModem update of:  2007_Jan_22


Bus 002 Device 003: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem
  idVendor           0x0483 SGS Thomson Microelectronics
  idProduct          0x7554 56k SoftModem
  idVendor           0x0458 KYE Systems Corp. (Mouse Systems)
  idProduct          0x005c 

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:02.6	1039:7013	1584:4003	Modem: Silicon Integrated Systems [SiS] AC'97
Modem Controller 

 Modem interrupt assignment and sharing: 
 10:        516          XT-PIC  ohci_hcd:usb1, ohci_hcd:usb2, SiS SI7012

 --- Bootup diagnositcs for card in PCI slot 00:02.6 ----
[17179574.816000] ACPI: PCI Interrupt 0000:00:02.6[C] -> Link [LNKC] -> GSI
10 (level, low) -> IRQ 10
[17179574.816000] ACPI: PCI interrupt for device 0000:00:02.6 disabled

 The PCI slot 00:02.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

ALSAversion 1.0.11

---

### Post by corax on 2007-03-13
Hi !

I tried to install as far as i remember exactly the same chip (AC'97 from SIS ) and it is almost working, it dials but the ppp daemon dies before i get my IP ... :-(   I was playing with it for just half an hour, so i think with more tweaking it will work ... :-) 

That is what i did :

```
sudo modprobe snd-intel8x0m
```
(after you hit enter a message will appear on screen that says something like that : " ... a new sound device was found ..." )
```
sudo aptitude install sl-modem-daemon
```

After that read the "Configuring the dial-up connection for your Internet Service Provider(ISP)" section here: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

good luck :)

---

### Post by john1911 on 2007-03-13
Thx, i would try it.

---

