---
title: "Consejo sobre Discos IDE &amp; SATA"
date: 2010-07-26
forum: Hardware
---

### Post by atari130xe on 2010-07-26
Gente de nuevo por acá, la pregunta es la siguiente: Tengo un Disco SATA de 250GB que es el que uso actuálmente con Ubuntu Lucid, Por otro lado tengo un disco IDE de 80GB que deseo agregarlo a mi PC, el tema es que hace un par de años intenté hacer algo similar y no me fué bién, simplemente arrancaba con el disco IDE que no tenia OS sino era para backups y almacenamiento y al iniciar entraba primero al IDE por consiguiente no pude si quiera lograr arrancar la PC. Alguien podría indicarme paso a paso como hacer para instalar ese disco a mi actual configuración sin que me ocurra lo mismo? o sea seguir con el SATA con Ubuntu Lucid y agregarle el IDE (Vacío) para guardar data?. Gracias!

PD: Creo que más que nada el inconveniente es con el GRUB en cuanto a la prioridad de Booteo, si no me equivoco.

---

### Post by atari130xe on 2010-07-26
Bueno lo acabo de solucionar, evidentemente cuando intenté hacer lo mismo con Ubuntu 8.04 no era posible, recién armé la PC de la misma forma y funciona perfectamente sin problema alguno con el GRUB, puse como Master al IDE y Como Master al SATA, en la BIOS como prioridad de Booteo al SATA y funciona perfecto. :D

---

### Post by aromo on 2010-07-26
En algunas BIOS tienes que cambiar el orden de arranque para que intente el disco duro (SATA) antes que el CD-ROM (IDE), ya que tratan el canal IDE como CD-ROM sin importar que lo que este conectado sea en realidad un disco duro.

Me alegra que te haya funcionado.

---

### Post by atari130xe on 2010-07-26
> **aromo said:**
> En algunas BIOS tienes que cambiar el orden de arranque para que intente el disco duro (SATA) antes que el CD-ROM (IDE), ya que tratan el canal IDE como CD-ROM sin importar que lo que este conectado sea en realidad un disco duro.

Me alegra que te haya funcionado.

Si! gracias, con Ubuntu 8.04 ni siquiera me funcionó esto, pero evidentemente algo deben haber cambiado porque ahora sí, y sin problema alguno.

REEDITO: Todo estaba bién hasta que puse manos a la obra y reinstalé Ubuntu porque debía hacero sí o sí, aproveché y utilicé el nuevo disco de 80GB para backup, todo bién. Reinstalé Ubuntu Lucid y otra vez el problema jejeje, al parecer Ubuntu hace esto:

Si tienen 2 HD como en mi caso uno SATA y otro IDE, y a pesar de setear el orden de arranque de los discos como SATA y luego IDE al instalar todo de cero Ubuntu instala Grub pero en el disco IDE no en el SATA donde instalé el sistema:
O sea antes de la instalación era así:

sda (250GB SATA) con 4 particiones (/win, /, /home, /swap) o sea SDA
sdb (80GB IDE) con 1 sola partición /backup

Luego de la instalación limpia:

El sda pasó a ser sdb y el sdb pasó a ser sda o sea que el MBR se instaló en el HD de 80GB (sin OS) obviamente cuando inicia la PC que pasa... error de grub (15, 17, etc.) o sea no encuentra las particiones. Que hice? entre a la BIOS y puse en primer lugar en la secuencia de arranque al HD de 80GB, resultado: arranca perfecto. son cosas que realmente no logro comprender, estimo que es demasiado técnico el tema.

---

### Post by biale on 2010-07-26
Hay solo dos cosas para tener en cuenta. La primera es la "enumeración" que hace el BIOS de la computadora. Y la segunda (ojo!) es que el dispositivo en la cadena de arranque tenga algo en el MBR para que pueda arrancar el grub. Atención: solo el grub!

Luego, la sentencias del grub (y que se pueden editar a manopla para probar) tienen que direccionar bien el resto del arranque.

Para eso y como ayuda tenes el comando ls de grub2. Podes probar haciendo

ls (hd0,2),  ls(hd0,2)/boot   y asi siguiendo.

Por ejemplo, en esta computadora tengo un disco rígido con un grub en el MBR que apunta a su partición 2 "/boot" para arrancar por default a Karmic.

Mas un pendrive arrancable y con un grub que apunta a la partición 7 del rígido anterior para arrancar a Lucid.

Y para no estar tocando el Bios, la ultima sentencia de grub del rígido apunta al "MBR" del pendrive. Que a su vez muestra un menu distinto.

---

