---
title: "Intel 82G33"
date: 2010-10-29
forum: Hardware
---

### Post by kracken9 on 2010-10-29
Buenas, sucede que en mi trabajo usamos unas maquinas prearmadas de marca Bangho, la verdad que son bastantes malas...
 Aun asi, la pc cumple con lo que le pido, pero en las cuestiones graficas deja mucho que desear.
 Sucede que cada tanto, la pantalla se vuelve inestable, aparecen rayas por todos lados haciendo imposible trabajar.


> root@franco:~# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
> root@franco:~# lshw -c display
  *-display
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:a0200000-a027ffff ioport:c140(size=8)  memory:80000000-9fffffff(prefetchable) memory:a0100000-a01fffff


En mi caso desactive Compiz y cualquier otro tipo de efectos, desde mi punto de vista lo bonito pocas veces es util :)




Asi se ve en muchas ocasiones, aclaro que ese es un caso leve...



[IMG]http://i51.tinypic.com/1234c1z.jpg[/IMG]


La imagen en cuestion, fue tomada teniendo instalado maverick, pero tambien sucede con el 9.10 y 10.04, ni siquiera debian se salvo de ese problema.


Como dije la pc es de pesima calidad, pero cuando instale windows (no soy de la idea de booteo dual, aunque ultimamente lo estoy pensando), no tengo ningun tipo de problemas con los graficos, asi que dudo que sea la maquina la que anda mal.

---

