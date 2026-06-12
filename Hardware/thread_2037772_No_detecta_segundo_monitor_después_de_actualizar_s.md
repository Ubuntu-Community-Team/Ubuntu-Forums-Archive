---
title: "No detecta segundo monitor después de actualizar sistema"
date: 2012-08-05
forum: Hardware
---

### Post by edu4d on 2012-08-05
Buenas a todos,
Trabajo con Ubuntu 12.04 64 bits, siempre me ha ido bien (eso si, sin acceleración 3d) porque no hay manera de que me funcione bien la tarjeta INTEL que lleva incorporado mi portatil HP G61.
Pero lo peor de todo es que no me va ahora el segundo monitor (el grande..) y me es dificil trabajar así.

Podrian darme alguna pista? ya no se que mas probar de verdad.
Os adjunto algunas salidas de terminal que he hecho para tratar de arreglarlo..


**lspci | grep VGA**
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

**sudo lshw -C video**
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d2400000-d24fffff

[B]lspci -nn
[/B]00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)


Os da alguna pista? no se de verdad, siempre he tenido problemas con los drivers de Intel de la grafica, jamas he tenido acceleración pero lo acepto, pero no disponer de segundo monitor me mata...
Gracias comunidad.

---

