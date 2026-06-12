---
title: "Ubuntu 9.04 vs Tarjeta ATI Radeon 9550 (RV350)"
date: 2009-05-13
forum: Hardware
---

### Post by elchinoek on 2009-05-13
Bueno la cuestion es que me instalé el excelente Ubuntu 9.04 :p y no solo que me pareció espetacular sino que empezé a poner un montón de cosas que hay y la verdad que es inigualable lo que se puede hacer con este SO, pero....
Se me ocurrió poner el juego ese alien y vi que no tenía instalada la placa de video entonces me detuve un segundo en instalarla, bajó solo el driver todo ok, solo había que reiniciar y ahi empezó el calvario.
Uno de mis monitores dice:

Attention
out of range
H: 74.9 Khz  V: 59.9 Hz

Obvio que hay q cambiar la frecuencia de la pantalla pero no se como ni de donde y no se vé nada apenas viene la parte de logeo.
En Window$ vas a F8 iniciar como modo grafico o algo así y lo hace automáticamente, si esta m.. lo hace seguro que en linux con Ctrl+Alt+F1 entro, me logeo y de ahi ir a algun lado para bajar la frecuencia a 60hz y que se pueda ver en el monitor.
Busqué por ahi pero nada.
Otra es reinstalar todo de nuevo pero debe haber alguna configuración para poder usar esta tarjeta gráfica.
Asi que saludos a toda la comunidad y espero que alguno me pueda dar una mano en este tema.
Chaucha!!!):P

---

### Post by staar on 2009-05-13
el archivo donde se encuentran las configuraciones del servidor grafico es el /etc/X11/xorg.conf, tendrías que modificarlo para agregarle los rangos que soporta tu monitor...

logueate en una consola (Ctrl+Alt+F1) y poné ```
sudo nano /etc/X11/xorg.conf
``` se te va a abrir el archivo con el editor de textos nano, andá hasta la sección 'Monitor' y agregale dos líneas con los valores de HorizSync y VertRefresh de TU monitor (buscalos en el manual), te quedaría así: ```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

``` OJO este es un ejemplo de MI xorg.conf, seguramente vos vas a tener un Identifier diferente y no vas a tener ni VendorName ni ModelName...

saludos

---

### Post by Hei Ku on 2009-05-13
Te referis a que el driver bajo ok, pero para ese modelo de placa deberias usar el driver libre, no el privativo. O sea, si te bajaste el driver de la pagina de ATI, no te va a funcar.

Cuales usaste?

---

### Post by fmsismo on 2009-05-13
> **Hei Ku said:**
> Te referis a que el driver bajo ok, pero para ese modelo de placa deberias usar el driver libre, no el privativo. O sea, si te bajaste el driver de la pagina de ATI, no te va a funcar.

Cuales usaste?

Según tengo entendido el driver libre lo deberías tener instalado en el sistema y tiene aceleración 3d.

---

### Post by Blackaiser on 2009-10-27
Bueno señores, yo uso la ati 9550, instale los paquetes con el Synaptic y arregle el xorg.conf como digo el amigo arriba... y FUNCO DE UNA!!!! muchas gracias...

---

