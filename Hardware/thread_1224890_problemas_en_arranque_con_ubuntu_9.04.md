---
title: "problemas en arranque con ubuntu 9.04"
date: 2009-07-27
forum: Hardware
---

### Post by cafdez on 2009-07-27
Hola a todos. Este es mi primer mensaje, gracias por este espacio. 
Mi equipo: CPU  AMD Athlon 64 x 2 5000+
                  Mother asus M2N-MX SE plus 
                  Video NVIDIA Ge force 6100 on board
                  Ram 4 Gb
                  Disco SATA  260 Gb
Les cuento que que estoy en Ubuntu desde hace 10 meses, tuve instalado el 8.04, luego 8.10 sin problemas. Hace un mes instalé el 9.04 y empezaron los problemas de buteo. Problemas que se presentan en cualquier momento del proceso de arranque, se puede colgar tanto al comienzo despues de la pantalla de Asus, como quedar la pantalla negra con el guión parapadeando en el extremo, o reiniciarse sola y volverse a colgar cuando corre la barra de ubuntu, o después de poner el usuario, en fin no se repite ningun patrón a veces tengo que resetear 4 o 5 veces hasat que engancha.
Se muy poco de ésto, lo que fuí aprendiendo con los foros, tutos,etc. Les dejo parte de lo que me parece es importante al correr el dmesg, supongo que hay cosas que me perdí del listado ya que encima no manejo el inglés.


  	 	 	 	 	 	     0.004000] please try cgroup_disable=memory option if you don't want
 

 [    0.004000] Scanning for low memory corruption every 60 seconds
 

 [    0.004000] Checking aperture...
 

 [    0.004000] No AGP bridge found
 

 [    0.004000] Node 0: aperture @ 20000000 size 32 MB
 

 [    0.004000] Aperture pointing to e820 RAM. Ignoring.
 

 [    0.004000] Your BIOS doesn't leave a aperture memory hole
 

 [    0.004000] Please enable the IOMMU option in the BIOS setup
 

 [    0.004000] This costs you 64 MB of RAM
 

 [    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000
 

 [    0.004000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
 

 [    0.004000] Memory: 3848992k/5242880k available (4743k kernel code, 1180420k absent, 212548k reserved, 2525k data, 532k init)
 

 [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
 

 [    0.004000] hpet clockevent registered
 

 

 

     0.225158] Setting APIC routing to flat
 

 [    0.225664] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
 

 [    0.232001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
 

 [    0.232001] ...trying to set up timer (IRQ0) through the 8259A ...
 

 [    0.232001] ..... (found apic 0 pin 0) ...
 

 [    0.273106] ....... works.
 

 

 

 [    0.407750] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - C4, should be B7 [20080926]
 

 [    0.407772] ACPI: WMI: Mapper loaded
 

 

   2.350035] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
 

 [    2.350119] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
 
Estos son algunos fragmentos que me parecen importantes. Les agradezco cualquier ayuda, y perdón por lo extenso.

---

