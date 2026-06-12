---
title: "PCMCIA Ethernet stops working"
date: 2005-10-09
forum: Hardware &amp; Laptops
---

### Post by nir on 2005-10-09
Hi,

I'm running 5.04 on an R50e Thinkpad. About 3 weeks ago the laptop's built-in LAN connection stopped working, and I started using a PCMCIA card instead (Dyamode Cardbus 10/100) as eth1. This worked fine for some time, and then suddenly stopped working. Now, when I boot, the network icon shows no connection, and clicking it pops the error message "SIOCGIFFLAGS error: No such device"

A day later, everything was suddenly working well again - not thanks to anything I've done - and a few days later it stopped working again... I did not do any changes to the system, updates/installs etc (that I'm aware of) so this is all quite strange...

I tried restarting PCMCIA, networking, hotplug, but no avail.

The card's LEDs do light up when it's inserted, and the card works fine on the very same machine under Windows.

When the card is inserted, /var/log/messages shows:


PCI: Enabling device 0000:03:00.0 (0000 -> 0003)
ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 11 (level, low) -> IRQ 11
tulip1:  MII transceiver #1 config 3100 status 7849 advertising 05e1.
eth0: ADMtek Comet rev 17 at 00014000, 00:E0:98:D2:B8:C1, IRQ 11.
pci.agent[9187]:      tulip: already loaded

lsmod shows (among many others ;-)):
pcmcia_core            53568  2 pcmcia,yenta_socket

After looking at other posts here, I tried 

sudo setpci -s  0:a.0 SUBORDINATE_BUS=0x0A

I got :"setpci: Warning: No devices selected for `SUBORDINATE_BUS=0x0A'". Restarting PCMCIA and inserting the card didn't help any.

cardctl eject/reset/insert also do not help.

This is the output of lspci:
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:02:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:03:00.0 Ethernet controller: Abocom Systems Inc 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)


Does anyone has any ideas? Thanks!

---

### Post by nir on 2005-10-10
Anyone? :-)

---

