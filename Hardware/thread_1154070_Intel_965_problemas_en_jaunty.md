---
title: "Intel 965 problemas en jaunty"
date: 2009-05-09
forum: Hardware
---

### Post by dmela2012 on 2009-05-09
Hola, soy bastante nuevo en ubuntu, empecé con intrepid, y no habia tenido problemas, si con la parte de wifi, que por suerte con jaunty funciona todo de una.

Mi problema es que cuando pasé a Jaunty, hice una instalacion de 0, tengo problemas con mi placa de video intel 965, estuve tratando de leer, y encontre dos soluciones, una actualizar el kernel, pero no me funcionaron, cuando hago todo, y agrego el método uxa en el xorg.conf no inicia, me salta un cartel de error, y que tengo que volver a la version anterior o algo así, la cosa que no me deja usar el método uxa, que vi que es lo que recomiendan, porque el anterior ya está desactiva. Ya pude habilitar compiz, pero el problema, es una notebook la que tengo, una acer 5315-2608, me parpadea el monitor, cuando no la use, ponele 10 seg y muevo el mouse o toco el teclado, y antes con intrepid no pasaba, y en windows tampoco pasa, pero ya me trate de leer las paginas que encontre pero no lo pude solucionar, no tengo muy buen ingles, así que tal vez no supe seguir algunas explicaciones de foros en ingles. Espero su ayuda. muchas gracias, ya que me encanta este sistema operativo!!

---

### Post by guillermolisi on 2009-05-09
> **dmela2012 said:**
> Hola, soy bastante nuevo en ubuntu, empecé con intrepid, y no habia tenido problemas, si con la parte de wifi, que por suerte con jaunty funciona todo de una.

Mi problema es que cuando pasé a Jaunty, hice una instalacion de 0, tengo problemas con mi placa de video intel 965, estuve tratando de leer, y encontre dos soluciones, una actualizar el kernel, pero no me funcionaron, cuando hago todo, y agrego el método uxa en el xorg.conf no inicia, me salta un cartel de error, y que tengo que volver a la version anterior o algo así, la cosa que no me deja usar el método uxa, que vi que es lo que recomiendan, porque el anterior ya está desactiva. Ya pude habilitar compiz, pero el problema, es una notebook la que tengo, una acer 5315-2608, me parpadea el monitor, cuando no la use, ponele 10 seg y muevo el mouse o toco el teclado, y antes con intrepid no pasaba, y en windows tampoco pasa, pero ya me trate de leer las paginas que encontre pero no lo pude solucionar, no tengo muy buen ingles, así que tal vez no supe seguir algunas explicaciones de foros en ingles. Espero su ayuda. muchas gracias, ya que me encanta este sistema operativo!!
Hasta hace poco este problema, muy discutido en el foro y en la lista de e-mail, estaba sin resolver ya que la tecnologia UXA de Intel es muy nueva y por lo tanto poco probada y fuertemente inestable.

Si haces una busqueda en el foro de Ubuntu-ar con "intel 965" veras todos los intercambios y opiniones vertidas al respecto y si alguien le contro la vuelta, tambien.

---

### Post by pablo.s on 2009-05-09
Según he leido en otros sitios, una
de las soluciones es instalar los
drivers viejos de Intel (por ejemplo
los de Intrepid)

---

### Post by leonardomdq on 2009-05-09
Mira, me encontre con el mismo problema cuando actualize a Jaunty porque este chipset Intel esta en Blacklist, lo pude solucionar con lo siguiente:

1. Abrir una terminal y digitar lo siguiente (o simplemente copiar y pegar):

```

**sudo gedit /usr/bin/compiz**

```2. y buscar** "blacklist"** y borrar hasta **"unset T"**, pero si no quiere borrarlo solamente coloque almohadillas **"#"** así:


```

**# blacklist based on the pci ids **
**# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details**
**#T="   1002:5954 1002:5854 1002:5955" # ati rs480**
**#T="$T 1002:4153" # ATI Rv350**
**#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965**
**#T="$T 8086:2a02 " # Intel GM965**
**#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)**
**#BLACKLIST_PCIIDS="$T"**
**#unset T**

```3. Ahora toca copiar y pegar: **"gstreamer-properties"**, aquí se abre una ventana que dice **"Selector de sistema multimedia"** y en la pestaña de "Vídeo" en la** "Salida predeterminada"**, se selecciona:

```
[B]
X Windows System (Sin Xv), o también (No Xv)[/B].

```4. Por último, reinicias y listo. Tiene que salir andando el compiz y todos los efectos.


Suerte ;)

---

### Post by staar on 2009-05-09
según leí, hay una actualización, hasta donde sé, aún en 'proposed', que soluciona este tema con esta placa, es cuestión de esperar a que sea suficientemente testeada y sea aprobada...

saludos

---

