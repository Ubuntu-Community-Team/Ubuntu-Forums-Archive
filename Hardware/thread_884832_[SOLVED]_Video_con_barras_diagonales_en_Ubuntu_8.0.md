---
title: "[SOLVED] Video con barras diagonales en Ubuntu 8.04.1"
date: 2008-08-09
forum: Hardware
---

### Post by atari130xe on 2008-08-09
Foro, mi hna. acaba de regalarle una PC para el dia del niño a mi sobrino, eh que viene con Vista Starter edition pre instalado (es una PC marca Gfast Intel dual core 2ghz con 1Gb de memoria), trae un monitor Wide Screen marca LG w1952s de 19" y un chip de video Via Chrome9 HC IGP Family WDDM (ni siquiera sé cuanta memoria tiene). Con vista funciona bien, pero al probarle el Live CD de Ubuntu 8.04.1 arranca bién pero la pantalla tiene barras diagonales atravesadas de Izq. a derecha que me parten la imagen en 2, probé cambiar la resolución de la placa pero las barras no desaparecen, alguna sugerencia? gracias!

---

### Post by Hei Ku on 2008-08-09
Las VIA son un dolor de cabeza. Esta el driver Unichrome, que es propietario, aunque VIA tiene intenciones de abrirlo. Y esta el OpenChrome, que es libre, pero con menos funcionalidad. Fijate cómo lo está tomando, y si podes probar el otro, a ver cuál funciona mejor.

---

### Post by atari130xe on 2008-08-09
Bueno, logré entrar en modo live cd y ver la pantala "normal" pero únicamente entrando en modo de graficos seguro. Veremos como sigue la historia...

PD: encont&#341;e esto en el sitio de VIA, serán los drivers correctos?
[http://linux.via.com.tw/support/downloadFiles.action]("http://linux.via.com.tw/support/downloadFiles.action")

---

### Post by Hei Ku on 2008-08-10
Fijate en el foro que ya ayudamos a alguien a configurar los drivers VIA

---

### Post by atari130xe on 2008-08-10
> **Hei Ku said:**
> Fijate en el foro que ya ayudamos a alguien a configurar los drivers VIA

Gracias Hei Ku sencillamente al instalar (nunca había echo una instación de Ubuntu particionando directamente desde el CD, siempre usé Gparted Live CD) probé a particionarlo e instalarlo listo, todo automáticamente se hizo sin ningún problema hice glxgears y tiene hasta aceleración 3D, impresionante! concluyo que Ubuntu asi y todo con defectos y todo es muy noble a la hora de instalarla. Los problemas se daban al correr el live cd de manera "normal" al elegir "modo gráfico seguro" ahi cargaba el driver VESA y entraba sin problemas. Gracias :)

---

### Post by Hei Ku on 2008-08-10
Buenisimo. O sea que al instalar anduvo todo joya? Punto para Ubuntu! 

Podemos afirmar que hay un Vista menos en la ciudad? :)

---

### Post by atari130xe on 2008-08-11
Asi es, un Vista menos en Buenos Aires jejeje, si supieran la performance que tiene Ubuntu a la que tiene Vista con esta misma configuración es increíble el rendimiento y eso que Ubuntu Hardy no es precisamente muy liviano, pero la diferencia es muy notoria en esta misma PC.
Ahora solo me resta regalarle una placa de video pci express y tiene una linda maquinita, el chip integrado Via Chrome9 por ejemplo no levanta compiz pero si tiene aceleracion 3d (glxgears y los engranajes giran bien) encima la memoria es shared o sea que le quita memoria al sistema. :)

---

