---
title: "notebook deja de funcionar si desconecto el cargador"
date: 2011-08-01
forum: Hardware
---

### Post by totolinux on 2011-08-01
Hola a todos el problema es el siguiente:
mi notebook packarbell easynote mz355 deja de funcionar (se cae el sistema grafico y pasa a una salida de comandos) cuando desconecto el cargador de la corriente, pero solo sucede cuando estoy conectado a la red wifi.
De otro modo funciona normalmente
tengo instalado ubuntu 11.04

shiduk@shiduk-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: Ralink corp. RT2561/RT61 rev B 802.11g


Desde ya se agradece cualquier ayuda...

---

### Post by totolinux on 2011-08-26
Bueno luego de tanto luchar e logrado al menos esquivar el problema. El tema esta en el kernel que usa ubuntu y otras distros. No me quedó mas remedio que instalar (arch linux) que siempre tiene los kernels mas recientes (noté una mejora en la duración de la batería, puedo suspender la notebook que antes no podía y descargar las fotos de mi vieja kodak c300 de esta forma problema resuelto. Otra solución sería actualizar el kernel de ubuntu pero escapa a mis conocimientos. Gracias a todos...

---

### Post by guillermolisi on 2011-08-26
Actualmente Arch esta utilizando la version 3.x del kernel, FYI.

---

