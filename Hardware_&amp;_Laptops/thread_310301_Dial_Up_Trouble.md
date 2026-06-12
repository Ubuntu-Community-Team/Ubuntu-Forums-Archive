---
title: "Dial Up Trouble"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by shubox357 on 2006-12-01
I downloaded scanModem and ran it on my fresh install of ubuntu 6.10 (i think, i know its 6.something) and got this for ModemData:

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 0000:03:03.0	14f1:2f20	14f1:200f	Communication controller: Conexant HSF 56k Data/Fax Modem

 Modem interrupt assignment and sharing: 
225:       3858   IO-APIC-level  uhci_hcd:usb4

 --- Bootup diagnositcs for card in PCI slot 0000:03:03.0 ----

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 0000:00:1b.0	8086:27d8	1028:01d2	0403: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
169:        761   IO-APIC-level  HDA Intel

 --- Bootup diagnositcs for card in PCI slot 0000:00:1b.0 ----
[17179588.096000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179588.096000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===





then I read "Conexant" so i went to the part of the "DialupModemHowto" labelled as "Modems supported by the Conexant drivers" then went to their site and ran tehir device scanner and got this:

=====================================================================
=              SYSTEM INFORMATION                                   =
=====================================================================
Date         : 12/1/2006
ListMdm Ver  : 1.6
Windows OS   : Microsoft Windows XP 
Build Number : 2600 

=====================================================================
=              RESULT OF MODEM QUERY                                =
=====================================================================
NUMBER OF MODEMS FOUND = 1

MODEM #1:
  PCI CONFIGURATION INFORMATION READ:
     VENDOR ID              : 14F1
     DEVICE ID              : 2F20
     SUBVENDOR ID           : 14F1
     SUBDEVICE ID           : 200F
     REVISION ID            : 00

  DEDUCED INFORMATION:
     VENDOR NAME            : CONEXANT
     DEVICE NAME            : UNKNOWN
     SUBVENDOR NAME         : ACTIONTEC                   -- [HTTP://WWW.ACTIONTEC.COM/](HTTP://WWW.ACTIONTEC.COM/)
     MODEM TYPE             : HSF
     WINXP INBUILD SUPPORT  : N=====================================================================
=              SYSTEM INFORMATION                                   =
=====================================================================
Date         : 12/1/2006
ListMdm Ver  : 1.6
Windows OS   : Microsoft Windows XP 
Build Number : 2600 

=====================================================================
=              RESULT OF MODEM QUERY                                =
=====================================================================
NUMBER OF MODEMS FOUND = 1

MODEM #1:
  PCI CONFIGURATION INFORMATION READ:
     VENDOR ID              : 14F1
     DEVICE ID              : 2F20
     SUBVENDOR ID           : 14F1
     SUBDEVICE ID           : 200F
     REVISION ID            : 00

  DEDUCED INFORMATION:
     VENDOR NAME            : CONEXANT
     DEVICE NAME            : UNKNOWN
     SUBVENDOR NAME         : ACTIONTEC                   -- [HTTP://WWW.ACTIONTEC.COM/](HTTP://WWW.ACTIONTEC.COM/)
     MODEM TYPE             : HSF
     WINXP INBUILD SUPPORT  : N







now what do i do with all this info? thanks a lot! the sooner i get dial up working the sooner i stopusing windows as much. hopefully i can get to the point that i dont even dual boot anymore....

---

### Post by kvonb on 2006-12-01
Hello :)

Firstly, have you looked in: Menu -> System -> Administration -> Network(ing) and enabled the modem in there?  If you highlight (click on :)) the modem and then properties, select the modem from the drop down list if it is listed.

If that doesn't work then you might be in for a rough ride.  The problem is that most modems these days are made only for MS Windows, the reason being that they are cheap.  Unfortunately hardware manufacturers usually will only make drivers available for Windows and most refuse to co-operate with Linux developers so we are stuck with what the developers can work out for themselves!

All I can suggest is to use the search tool an look for your modem in the forums here, you might get lucky.

Regards, KEv :)

---

### Post by shubox357 on 2006-12-01
i tried that but it didnt detect my modem. any suggestions?

---

### Post by shubox357 on 2006-12-01
is there a list of ubuntu supported modems that do not require any configuration?

---

### Post by kvonb on 2006-12-01
This is the list, but I couldn't see modems :-k.  But I'll give to to you anyway:

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

All I can suggest is an external modem which will be the easiest and simplest to work with.  You might pick one up cheap at a garage/yard sale or something.

---

### Post by towsonu2003 on 2006-12-01
After running the scanModem tool, you were supposed to go back to the main wiki page and check out which section is for your winmodem. 
> **shubox357 said:**
> 
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 0000:03:03.0	14f1:2f20	14f1:200f	Communication controller: **Conexant** HSF 56k Data/Fax Modem


in your case, check out this link:
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

after you manage to install the drivers and everything, you will have to set up your dialer: [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

hope this helps

ps. edited modem howto to make sure the user have to check what link s/he should check after running scanmodem

---

