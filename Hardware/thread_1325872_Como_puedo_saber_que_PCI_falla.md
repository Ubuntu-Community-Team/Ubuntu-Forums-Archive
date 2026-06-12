---
title: "Como puedo saber que PCI falla"
date: 2009-11-13
forum: Hardware
---

### Post by Brath-ga on 2009-11-13
El lector de sucesos me reporta un fallo que no se a que se refiere.

Nov 14 03:06:31 pinki-fixo kernel: [  463.831641] +------ PCI-Express Device Error ------+
Nov 14 03:06:31 pinki-fixo kernel: [  463.831651] Error Severity		: Uncorrected (Non-Fatal)
Nov 14 03:06:31 pinki-fixo kernel: [  463.831657] PCIE Bus Error type	: Transaction Layer
Nov 14 03:06:31 pinki-fixo kernel: [  463.831661] Flow Control Protocol 	: First
Nov 14 03:06:31 pinki-fixo kernel: [  463.831666] Receiver ID		: 0010
Nov 14 03:06:31 pinki-fixo kernel: [  463.831672] VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
Nov 14 03:06:31 pinki-fixo kernel: [  463.831679] pcieport-driver 0000:00:02.0: broadcast error_detected message
Nov 14 03:06:31 pinki-fixo kernel: [  463.831686] pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
Nov 14 03:06:31 pinki-fixo kernel: [  463.831692] pcieport-driver 0000:00:02.0: broadcast resume message
Nov 14 03:06:31 pinki-fixo kernel: [  463.831702] pcieport-driver 0000:00:02.0: AER driver successfully recovered
Nov 14 03:06:31 pinki-fixo kernel: [  463.831724] pcieport-driver 0000:00:02.0: can't find device of ID0010
Nov 14 03:06:31 pinki-fixo kernel: [  463.831744] pcieport-driver 0000:00:02.0: can't find device of ID0010
Nov 14 03:06:32 pinki-fixo kernel: [  464.442136] +------ PCI-Express Device Error ------+
Nov 14 03:06:32 pinki-fixo kernel: [  464.442148] Error Severity		: Uncorrected (Non-Fatal)
Nov 14 03:06:32 pinki-fixo kernel: [  464.442153] PCIE Bus Error type	: Transaction Layer
Nov 14 03:06:32 pinki-fixo kernel: [  464.442158] Flow Control Protocol 	: First
Nov 14 03:06:32 pinki-fixo kernel: [  464.442163] Receiver ID		: 0010
Nov 14 03:06:32 pinki-fixo kernel: [  464.442169] VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
Nov 14 03:06:32 pinki-fixo kernel: [  464.442176] pcieport-driver 0000:00:02.0: broadcast error_detected message
Nov 14 03:06:32 pinki-fixo kernel: [  464.442182] pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
Nov 14 03:06:32 pinki-fixo kernel: [  464.442188] pcieport-driver 0000:00:02.0: broadcast resume message
Nov 14 03:06:32 pinki-fixo kernel: [  464.442198] pcieport-driver 0000:00:02.0: AER driver successfully recovered
Nov 14 03:06:32 pinki-fixo kernel: [  464.442219] pcieport-driver 0000:00:02.0: can't find device of ID0010
Nov 14 03:06:32 pinki-fixo kernel: [  464.442240] pcieport-driver 0000:00:02.0: can't find device of ID0010
Nov 14 03:06:38 pinki-fixo rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="836" x-info="http://www.rsyslog.com"] 

Alguien sabe que falla ?

---

### Post by Mauro22 on 2009-11-14
Pci express debe haber uno solo. Igual fijate a lo ultimo hay una web.. Por ahí da una pista

---

### Post by sebastianabate on 2009-11-14
En Launchpad hay un bug abierto que viene desde Jaunty

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/321412](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/321412)

Fijate que uno de los últimos posts pone una opción de arranque que aparentemente soluciona el tema.

---

### Post by faktorqm on 2009-11-15
postea la salida de lspci

---

### Post by z37a on 2009-11-16
> **Mauro22 said:**
> Pci express debe haber uno solo. Igual fijate a lo ultimo hay una web.. Por ahí da una pista

Guarda, zocalo PCIx puede que uno solo, pero en la mayoría de los casos los dispositivos onboard suelen ser PCIx también, como por ejemplo la placa de vídeo onboard y las placas de red gigalan!!!!

---

### Post by Mauro22 on 2009-11-17
Encontré esto:

> 
+------ PCI-Express Device Error ------+ 
Error Severity      : Uncorrected (Non-Fatal) 
PCIE Bus Error type   : Transaction Layer 
Flow Control Protocol    : First 
Receiver ID      : 0010 
VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h 


El encabezado es igual.

Si los vendorid, deviceid etc no cambian; tendrias que tener esta placa:

> 02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)


El post es este: [http://www.espaciolinux.com/foros-tema-p207687.html](http://www.espaciolinux.com/foros-tema-p207687.html) (debian lenny)

---

