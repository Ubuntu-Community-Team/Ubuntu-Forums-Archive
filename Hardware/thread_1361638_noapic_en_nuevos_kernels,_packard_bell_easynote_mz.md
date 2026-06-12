---
title: "noapic en nuevos kernels, packard bell easynote mz355"
date: 2009-12-22
forum: Hardware
---

### Post by totolinux on 2009-12-22
Hola a todos. Tengo una notebook (packard bell easynote mz355)
viejita 1g ram y celeron 1.4 la 
salida lspci
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
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

Con ubuntu 9.04 anda todo, pero con 9.10 no arranca. Solo con la opción (noapic) y esto me pone loco, porque significa que si me paso a la proxima 9.10 pierdo algunas funciones como la del apagado y la hibernacion.
Aclaro que pasa con muchas otras distros y coincide con el kernel 2.6.30
ahora estoy con 2.6.28-17-generic y todo perfecto pero algun dia voy a tener que actualizar. poede haber alguna solución? Gracias de antemano.

---

### Post by guillermolisi on 2009-12-22
> **totolinux said:**
> Hola a todos. Tengo una notebook (packard bell easynote mz355)
viejita 1g ram y celeron 1.4 la 
salida lspci
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
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

Con ubuntu 9.04 anda todo, pero con 9.10 no arranca. Solo con la opción (noapic) y esto me pone loco, porque significa que si me paso a la proxima 9.10 pierdo algunas funciones como la del apagado y la hibernacion.
Aclaro que pasa con muchas otras distros y coincide con el kernel 2.6.30
ahora estoy con 2.6.28-17-generic y todo perfecto pero algun dia voy a tener que actualizar. poede haber alguna solución? Gracias de antemano.
Actualmente KK usa kernel 2.6.31 y LL parece que saldra con el 2.6.33.
Con los kernels de JJ tuve un problema similar, acpi=off, para que las maquinas con motherboard Asus y chipset VIA que uso funcionen y cuando pase a KK se soluciono el tema (ingrese un bug en bugzilla oportunamente junto a varias personas mas).

---

### Post by totolinux on 2009-12-22
otra consulta. si actualizo y uso los kernels antiguos? esto es posible ? sino tendré que ser  paciente y ver que pasa. gracias.

---

### Post by guillermolisi on 2009-12-22
> **totolinux said:**
> otra consulta. si actualizo y uso los kernels antiguos? esto es posible ? sino tendré que ser  paciente y ver que pasa. gracias.
Si, podes seguir usando otras versiones anteriores de kernel (cosa que yo tambien hice en su momento) y como el resultado de toda la gestion generada a partir de publicar el bug dio que lo considerarian en nuevas versiones, solo me resto esperar, haciendo seguimiento para ver como evolucionaba (hasta que llego KK con el kernel y su solucion).

---

### Post by totolinux on 2009-12-22
Gracias, entonces esperaré la evolución y luego actualizaré. mientras funcione todo me quedaré con JJ. saludos

---

