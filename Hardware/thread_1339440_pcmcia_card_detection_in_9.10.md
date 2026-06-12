---
title: "pcmcia card detection in 9.10"
date: 2009-11-27
forum: Hardware
---

### Post by mhstn on 2009-11-27
I've just installed ubuntu 9.10 on an older Toshiba 2250CDT laptop and I can't get the system to recognize any of my pcmcia cards so I can connect to my home network and then to the internet via the home network
 
I have a hard wire ethernet pcmcia card connected to the router, and a linksys wireless pcmcia card. Neither one is recognized or detected as far as I can tell

---

### Post by mhstn on 2009-11-27
anyone?  bueller?  anyone?

---

### Post by mhstn on 2009-12-02
additional information:
 
When I run "lspci" on the root terminal, I get the following
 
00:00.0 Host bridge: Intel corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev02)
00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev01)
00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev01)
00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev03)
00:07.0 Communication controller: Agere Systems 56k WinModem (rev01)
00:0b.0 CardBus bridge: Toshia America Info Systems ToPIC100 PCI to Cardbus bridge with ZV support (rev20)
00:0c.0 Multimedia audio controller: ESS technology ES1978 Maestro 2E (rev10)
01:00.0 VGA compatible controller: Trident microsystems Cyber 9525 (rev 49)
02:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
 
Running "lspcmcia" gives the following:
 
Socket 0 Bridge:     [yenta cardbus]   (bus ID: 0000:00:0b.0)
   CardBus card -- see "lspci" for more information
 
 "pccadrctl pcmciautils" gives these results:
 
Supported commands are 
ls
insert
eject
suspend
resume
reset
info
status
config 
ident
 
the "pccardctl info" command shows
PRODID_1= " "
PRODID_2= " "
PRODID_3= " "
PRODID_4= " "
MANFID= 0000,0000
FUNCID=255
 
"pccardctl status" shows
 
Socket 0:
  3.3v 32 bit PC Card
 
"pccardctl config" results in
socket 0:
command 'config' not yet handled by pccardctl
 
and finally "pccardctl ident" results in
Socket 0:
no product info available
 
Apparently the system is recognizing when there is a PCMCIA card inserted, but isn't recognizing what kind of card it is
 
Additionally, I've tried connecting directly to my cable modem with a USB cable, and can't get an internet connection that way either

---

### Post by mhstn on 2009-12-03
any other suggestions?

---

### Post by benprescott on 2009-12-12
thanks for the leads!

My fix, to get a 3com PCMCIA NIC working, was to install pcmciautils and then reboot. 

It adds a script  - /etc/init.d/pcmciautils - which led me to think this is an applicable step.

```
$ uname -a
Linux thunderchild 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux
$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1211
00:05.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro (rev dc)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 09)
00:09.1 Serial controller: Agere Systems LT WinModem
$ sudo apt-get install pcmciautils
$ sudo lspcmcia
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:04.0)
$ pccardctl status
Socket 0:
  5.0V 16-bit PC Card
$ pccardctl ident
Socket 0:
  no product info available
$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
```After rebooting, I have eth1 and
```

$ pccardctl status
Socket 0:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "3c574_cs"
$ pccardctl ident
Socket 0:
  product info: "3Com", "Megahertz 574B", "B", "001"
  manfid: 0x0101, 0x0574
  function: 6 (network)
$ pccardctl info
PRODID_1="3Com"
PRODID_2="Megahertz 574B"
PRODID_3="B"
PRODID_4="001"
MANFID=0101,0574
FUNCID=6

```hope this helps someone else!

---

