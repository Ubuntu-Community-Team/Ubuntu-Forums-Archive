---
title: "Ubuntu 10.04 arranque con problemas con power management"
date: 2010-04-30
forum: Hardware
---

### Post by diego8787 on 2010-04-30
Hola, este es mi primer post.

Hoy decidí instalar el ubuntu 10.04, la instalación salio todo bien (use Ext4 como formato de archivos, y el Swap para memoria), al arrancar salio un cartel que nunca llegue a leer, y cargo la interfaz pero no aparecia el famoso log-in donde pide usuario y password, el mouse no andaba, después de esperar aproximadamente un minuto me pidio el usuario y pass, (sin andar todavia el mouse) lo ingrese y me salta un cartel (Power management no responde, desea cerrarlo?) a lo que pongo cerrar y despues anda el mouse y carga el resto de los programas.

El problema que tengo es que me tarda 1 minuto en cargar y siempre me sale ese tema del power management. Estoy usando la versión de 64 bits, y uso una computadora de escritorio.

Alguien tiene idea de como solucionar el tema ese así arranca rapido?? 

P.d.: tengo un quad core Amd, 4 gb ram ddr 2 y una nvidia gtx 260

Gracias ! :)

---

### Post by guillermolisi on 2010-04-30
Que motherboard y que chipset tiene ?
Me suena a problemas con ACPI ...

Lo primero que haria de estar en tu situacion es leer los logs, empezando por /var/log/dmesg, luego por /var/log/messages y ver si hay alguna referencia orientadora.

---

### Post by diego8787 on 2010-04-30
Hola tengo un Asus M3N-HT- deluxe (los drivers del bios son los ultimos), hace poquito tuve ubuntu 9.10 y jamas tuve ese problema, solo con esta versión de ubuntu me sale ese error raro :S, actualmente corro windows 7 sin drama, la verdad que no se que habrán hecho en esta versión q me sale eso !

---

### Post by diego8787 on 2010-04-30
Me olvide de decir, el chipset es NVIDIA nForce 780a SLI

---

### Post by diego8787 on 2010-05-03
Les paso mi log, por favor alguien sabe que tengo que hacer para arreglarlo?? (Tengo una nvidia gtx 260 y mother Asus m3n-ht deluxe

[    8.393755] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    8.393760] ACPI: resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM00 [0x1c40-0x1c7f]
[    8.393761] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.393763] nForce2_smbus 0000:00:01.1: Error probing SMB2.



Gracias :D

---

### Post by guillermolisi on 2010-05-03
> **diego8787 said:**
> Les paso mi log, por favor alguien sabe que tengo que hacer para arreglarlo?? (Tengo una nvidia gtx 260 y mother Asus m3n-ht deluxe

[    8.393755] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    8.393760] ACPI: resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM00 [0x1c40-0x1c7f]
[    8.393761] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.393763] nForce2_smbus 0000:00:01.1: Error probing SMB2.

Gracias :D
Problemas con ACPI ... mmm ... si usas acpi=off en la linea de inicio del Grub no podras usar la placa de video nVidia con todo su potencial (por lo menos es lo que me paso cuando usaba 9.04 despues de un cambio de version del kernel ya que el X-server no podia configurarla al no poder acceder a sus caracteristicas internas).
Ademas, sin ACPI no tendras sensores y la maquina rendira de una forma totalmente distinta, menor, a si utilizas ACPI.

Cuando me paso lo reporte al bug squad y de ahi me mandaron a que lo reporte en bugzilla porque era una cuestion del kernel (una regresion que solucionaron con otras versiones posteriores para la motherboard que uso).

---

### Post by the blackbull on 2010-06-14
Hola: Tengo un problema similar con una Compaq Presario 1215US (Athlon 4 1G chipset via686a). Mi log dice lo siguiente:

[8.828369] ACPI: I/O resource vt596_smbus [0x8100-0x8107] conflicts with ACPI region SMIO [0x8100-0x8106]
[8.965801] via686a 0000:00:07.4: base adress not set - upgrade BIOS or use force_addr=0xaddr

La laptop se bloquea y no llega a la pantalla del login. Realice instalacion minima (solo consola) y al instalar los paquetes tambien se bloquea. Hay alguna solucion para esto? Gracias

---

### Post by rojojuan on 2010-09-22
> **the blackbull said:**
> Hola: Tengo un problema similar con una Compaq Presario 1215US (Athlon 4 1G chipset via686a). Mi log dice lo siguiente:

[8.828369] ACPI: I/O resource vt596_smbus [0x8100-0x8107] conflicts with ACPI region SMIO [0x8100-0x8106]
[8.965801] via686a 0000:00:07.4: base adress not set - upgrade BIOS or use force_addr=0xaddr

La laptop se bloquea y no llega a la pantalla del login. Realice instalacion minima (solo consola) y al instalar los paquetes tambien se bloquea. Hay alguna solucion para esto? Gracias

Tengo el mismo problema con un motherboard ECS. Estaba trabajando con la placa de video on board y probé con otra pci-express y todo sigue igual. Estuve viendo que es un bug ya reportado, y no encontré ninguna solución.Habrá alguna que no conozca? Si alguien sabe de alguna desde ya muchas gracias.

---

### Post by rojojuan on 2010-09-23
Buenas noticias: probé el live cd de Ubuntu 10.10 beta y anda bien. Parece problema resuelto. Cuando esté disponible la rc instalaré esa versión.

---

### Post by rojojuan on 2010-09-28
> **rojojuan said:**
> Buenas noticias: probé el live cd de Ubuntu 10.10 beta y anda bien. Parece problema resuelto. Cuando esté disponible la rc instalaré esa versión.

El problema volvió a repetirse. Busqué y encontré otra solución que esta vez parece que anda bien. Al menos arranqué sin inconvenientes unas 20 veces.
Hice lo siguiente:
Modifiqué /etc/default/grub
Edité una línea así: 
GRUB_CMDLINE_LINUX=”acpi=off noapic nolapic”
guardé
update grub.
Espero que pueda servirle a alguien.

---

