---
title: "Intersil Corporation Prism 2.5 Wavelan"
date: 2009-09-14
forum: Hardware
---

### Post by GGsalas on 2009-09-14
Yo tengo una Presario 2500. Wifi anda pero no con para las conexiones protegidas ¿puede ser por el driver? ¿Me cnvendrá probar esta solución? ¿Que debo hacer para volver al driver anterior si no funciona?

Saludos y gracias.

---

### Post by sergiom99 on 2009-09-14
Yo empezaria probando con Wicd en lugar de Network Manager.

---

### Post by Hei Ku on 2009-09-14
> **sergiom99 said:**
> Yo empezaria probando con Wicd en lugar de Network Manager.

Eso es porque usas Kubuntu. En Ubuntu parece que el Network Manager, y de hecho tiene mas funcionalidades que el Wicd.

Igual, en realidad, el 9.04 debería tomar esta placa sin problema, y a partir de ahi la configuracion que usando ndiswrapper. Por supuesto, si estamos hablando de la misma placa Wifi. Si no, thread aparte.

---

### Post by GGsalas on 2009-09-14
> **Hei Ku said:**
> Eso es porque usas Kubuntu. En Ubuntu parece que el Network Manager, y de hecho tiene mas funcionalidades que el Wicd.

Igual, en realidad, el 9.04 debería tomar esta placa sin problema, y a partir de ahi la configuracion que usando ndiswrapper. Por supuesto, si estamos hablando de la misma placa Wifi. Si no, thread aparte.

Si, probé con wicd. 

No, no se si es la misma placa. Adjunto el resultado de $lspci
```

00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
```

La placa la reconoce, el problema es que no puedo conectarme a conexiones protegidas.

Gracias

---

### Post by Hei Ku on 2009-09-14
No es la misma placa. Ni parecida. Abierto en un thread aparte.

---

