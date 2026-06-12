---
title: "Yo de nuevo, ahora con el bluetooth interno"
date: 2009-06-14
forum: Hardware
---

### Post by sartrejp on 2009-06-14
Después de googlear durante 3 horas y de leer las 10 paginas de resultados en ubuntu forums, no logro hacer andar el bluetooth interno de la notebook. Si le enchufo esos dongle (creo que se llaman), los usb, lo reconoce y anda bien, pero el de la note, no hay caso.

si pongo dmesg | grep tooth el resultado es (no tengo enchufado el otro)
[    1.000018] Bluetooth: Core ver 2.13
[    1.000022] Bluetooth: HCI device and connection manager initialized
[    1.000022] Bluetooth: HCI socket layer initialized
[   11.702050] Bluetooth: L2CAP ver 2.11
[   11.702051] Bluetooth: L2CAP socket layer initialized
[   11.702054] Bluetooth: SCO (Voice Link) ver 0.6
[   11.702056] Bluetooth: SCO socket layer initialized
[   11.702106] Bluetooth: RFCOMM socket layer initialized
[   11.702114] Bluetooth: RFCOMM TTY layer initialized
[   11.702116] Bluetooth: RFCOMM ver 1.10
[   22.147752] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.147755] Bluetooth: BNEP filters: protocol multicast
[ 7581.494179] Bluetooth: Generic Bluetooth USB driver ver 0.3

lsusb me da
Bus 002 Device 004: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 002: ID 0db0:6877 Micro Star International RT2573
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 22b8:4810 Motorola PCS Triplet GSM Phone (storage)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ahora si pongo hcitool dev me devuelve
devices:
y nada más, así vacío, por lo que si pongo
hcitool scan la respuesta es 
Device is not available: No such device

Alguien sabe como puedo hacer para que funcione?

---

