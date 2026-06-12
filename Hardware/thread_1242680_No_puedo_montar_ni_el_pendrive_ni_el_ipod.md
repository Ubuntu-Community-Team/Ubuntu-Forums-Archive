---
title: "No puedo montar ni el pendrive ni el ipod"
date: 2009-08-17
forum: Hardware
---

### Post by foodyart on 2009-08-17
Estoy mas perdido que un pulpo en un garaje , cuando conecto el ipod al pc me dice que el volumen no se puede montar , lo mismo me pasa con el pendrive , el caso es que antes si reinicializaba el pc lo montaba ahora ni eso y por supuesto el amorok ni lo ve en fin no se que hacer soy nuevo en esto de linux-ubuntu agradeceria algo de ayuda gracias de antemano

---

### Post by Carlos C on 2009-08-19
Hola. Por favor copia aquí el error exacto que te muestra el sistema cuando intentas montarlo desde el terminal. También puedes buscar el error escribiendo en el terminal "dmesg" luego de intentar montar el pendrive.
Saludos.

---

### Post by solipanta on 2012-09-24
tengo un problema similar, me da este error cuando trato de borrarlo con el creador de discos de arranque

org.freedesktop.UDisks.Error.Failed: Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdb, start=0, size=8351866880, type=0x0c
Entering MS-DOS parser (offset=0, size=8351866880)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed

---

