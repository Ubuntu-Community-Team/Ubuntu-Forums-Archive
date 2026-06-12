---
title: "Toshiba Satellite A60 S1591 Modem driver??"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by veap on 2005-10-24
Need help with modem driver - 1 Minute Ago 
victor@ubuntu:~$ sudo /usr/bin/scanModem.sh
Password:


UPDATE=2005_April_19

/usr/bin/scanModem.sh: line 224: gcc: command not found
PCIBUS=0000:00:14.6

Providing detail for device at PCI_bus 0000:00:14.6
with vendor-ID:device-ID
----:----
Class 0703: 1002:434d Modem: ATI Technologies Inc: Unknown device 434d (rev 01) (prog-if 00 [Generic])
SubSystem 1179:0001 Toshiba America Info Systems: Unknown device 0001
0000:00:14.6 0703: 1002:434d (rev 01)
Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
Memory at f0000500 (32-bit, non-prefetchable) [size=256]


-----PCI_IDs------- --CompilerVer-
Feature List: Primary Subsystem Distr KernelVer kernel default CPU
./scanModem test 1002:434d 1179:0001 debian 2.6.12-9-386 3.4.5 i686


The soft modem Subsystem operates under a controller
1002:434d ATI
capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:
AgereSystems
Conexant
Intel
find: aviso: especificou a opção -mindepth após um argumento não opção -name, mas as opções não são posicionais (-mindepth afecta os testes especificados antes, assim como os especificados após). Por favor, especifique as opções antes dos outros argumentos.

find: aviso: especificou a opção -maxdepth após um argumento não opção -name, mas as opções não são posicionais (-maxdepth afecta os testes especificados antes, assim como os especificados após). Por favor, especifique as opções antes dos outros argumentos.

The Subsystem has an Agere Systems codec SIL27
A PCMCIA modem is detected.

 Now what should I do? Can anyone help? Thanx

---

