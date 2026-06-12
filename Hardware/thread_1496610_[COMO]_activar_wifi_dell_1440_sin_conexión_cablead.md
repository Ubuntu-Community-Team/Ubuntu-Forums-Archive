---
title: "[COMO] activar wifi dell 1440 sin conexión cableada"
date: 2010-05-29
forum: Hardware
---

### Post by granjero on 2010-05-29
buenas, espero que esto le sirva a alguien.

compré una dell 1440 estando de vacaciones. odié el win7 que vino. y decidí no esperar a a volver a casa para ponerle ubuntu 10.04

la instalación fué sin problemas hasta que me di cuenta que no arrancaba la placa wifi.

lo que hice para que funcione fue lo siguiente.

1. en Sistema>Administración>Origenes del Software tildé la opción de instalar desde el cd
2. cliquié en Sistema>Administración>Controladores de Hardware
3. ahí descubrió que me faltaban los drivers de la placa wifi.
4. le di instalar y CHAN! error. ahí me fijé en el log que me decía el error 

/var/log/jockey.log

esta fue la parte que por instinto me pareció que era la que importaba

```
010-05-27 19:04:33,235 WARNING: Package fetching failed: Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb File not found
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb File not found
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb File not found
```


agarré el cd de ubuntu 10.04 y fui buscando esos paquetes .deb uno por uno.

no recuerdo el orden exacto de los dos primeros pero si se los instala en el orden incorrecto tira un error.

primero instalé /pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb
segundo /pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb
y tercero /pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb

y después de reiniciar ya tenía wireless!

ojalá le sirva a alguien!


salud!

---

### Post by alfplayer on 2010-05-29
Con el CD de Ubuntu en la lectora la instalación debería ser automática después de elegir el controlador en Controladores de Hardware.

---

### Post by granjero on 2010-05-29
yo creía lo mismo. desde el live session lo instalaba bien.

pero una vez instalado ubuntu cuando le ponía que instale me tiraba un error. es el error que copié más arriba del log que me decía la ventanita.

si querés te paso el log completo.

salud!

---

