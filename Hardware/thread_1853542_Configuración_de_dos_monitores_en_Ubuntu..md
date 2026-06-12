---
title: "Configuración de dos monitores en Ubuntu."
date: 2011-10-02
forum: Hardware
---

### Post by daggaz on 2011-10-02
Hola,
Llevo ya un tiempo trabajando con monitores y proyectores extendidos en  Ubuntu, siempre de modo horizontal (un monitor a la izquierda y otro a  la derecha) y en la mayoría de los casos con portátiles; hasta el  momento me había parecido muy sencillo y todo funcionaba bien.
Los problemas comenzaron a aparecer cuando trataba de organizar los monitores de otras maneras a la que viene por *default.*
Ahora, por ejemplo, tengo un monitor arriba y otro abajo; ya que estoy  trabajando con una Netbook conectada a un monitor un poco más grande. El  asunto, es que Ubuntu configura el monitor de arriba (grande), como el  principal, y por lo tanto, el lanzador de Unity (o el de AWN, que es más  molesto por que lo tengo en la parte inferior de la pantalla, en la  frontera entre ambos monitores), aparecen en el monitor de arriba y no  encuentro la manera de indicarle al sistema cual monitor quiero que sea  el principal y cual el secundario...
Buscando en Internet llegué a encontrar información para configurarlos  con tarjetas Nvidia o ATI, pero esta máquina no tiene una gran tarjeta  gráfica, solo la de la *mother board*. También hallé algunos posts en inglés que hablan sobre configurar Xorg, desde el archivo *config*.... Pero desde Ubuntu 10.10, Xorg ya no está donde siempre estuvo.
¿Alguna idea?
 PD: Estoy usando Gnome con AWN + Compiz en Natty (11.04)... Por algún  motivo gasta mucho menos recursos que Unity 2D y sigue sin gustarme el  lanzador a la izquierda, pues mis monitores siguen siendo cuadrados  :<

---

### Post by guillermolisi on 2011-10-05
El archivo /etc/X11/xorg.conf lo podes crear y a partir de eso el Xserver lo tomara en cuenta antes que lo que logre detectar automagicamente.
Con un editor de texto simple, como nano o vim, es suficiente para generarlo con las caracteristicas que requieras.

Aparte, mi recomendacion es que vayas pensando en actualizar esa version 10.10 porque en pocos meses mas se quedara sin soporte.
Antes de hacer la actualizacion, siempre es recomendable hacer backup (clonar el disco, copiar los archivos personales, etc.) y probar en la misma maquina una sesion Live con la version nueva que quieras usar (podes usar 11.04 con Gnome Classic, asi podes seguir aprovechando la geometria de tus monitores.

---

### Post by daggaz on 2011-10-05
Hola Guillermo.
De hecho estoy usando la 11.04, siempre actualizo al par de semanas de publicada una nueva versión de Ubuntu (y tengo /home en una partición diferente).
Lo que decía de la 10.10, es que desde esa versión a mi me pasó que el archivo config de X no aparece como antes... Probaré lo de crearlo ¿Será necesario incluir todas las lineas que normalmente incluye o simplemente las que hacen referencia a la configuración de los dos monitores?

Gracias

---

### Post by guillermolisi on 2011-10-05
> **daggaz said:**
> Hola Guillermo.
De hecho estoy usando la 11.04, siempre actualizo al par de semanas de publicada una nueva versión de Ubuntu (y tengo /home en una partición diferente).
Lo que decía de la 10.10, es que desde esa versión a mi me pasó que el archivo config de X no aparece como antes... Probaré lo de crearlo ¿Será necesario incluir todas las lineas que normalmente incluye o simplemente las que hacen referencia a la configuración de los dos monitores?

Gracias
Desde cierta version de Xserver en adelante se intento darle mas inteligencia de reconocimiento y prescindir del contenido de xorg.conf

Estimo que si solo utilizas las secciones relacionadas con placa de video y monitores deberia funcionar bien.

---

### Post by Yesnovato on 2011-11-07
Saludos a todos en este forum en el cual he estado leindo antes de registrarme pues instale por primera vez Ubuntu 11.10 con la idea de aprender este OS que dicen que es muy bueno pero del cual soy totalmente ignorante por lo que les pido mil disculpa se hago preguntas tontas. Lo primero que me encontre al instalar ubunto es que mis monitores no trabajan correctamente o como estaban configurado en windows 7. Tengo tres monitores un Hans de 28"" en el centro y dos Samsungs de 24" cada uno y dos tarjetas nVidia, una GTX280 y una GTS450. En primer lugar solo arranco el Hans como  un desconocido monitor, hice las actualizaciones de los drivers pero todo siguio iggual, leindo en este forum y en otros pues supe que habia algo parecido al nVidia control de W7, y que en ubuntu es x server nvida setting, pues comence a trabajar alli pero solo logre que reconociera los monitores pero solamente en el Han tengo informacion pero los otros dos esta la pantalla en blanco aunque se ve el mouse como si fuera una cruz y si doy click entonces las dos pantallas se ponen negra, otra cosa que me ocurre es que siempre que hago un cambio y le soy al Apply buton me sale un windows con error, pudieran guiarme o decirme donde leer para resolver mi problema, he leido lo de crear el x server conf, pero ni se como se hace y mucho menos que poner dentro de el. Cualquier ayuda que puedan brindarme se las voy agradecer.
Salu2

---

### Post by daggaz on 2011-11-07
Yesnovato, debe haber una forma de solucionar tu problema; yo he trabajado con hasta cinco monitores (a través de un Matrox) en Ubuntu y me ha funcionado bien (salvo por lo que indico aquí).
Te sugiero que inicies un nuevo post; pues tu problema es diferente al que inicié yo aquí; si puedes da las especificaciones técnicas de todo tu hardware implicado.
Saludos.

---

### Post by Yesnovato on 2011-11-07
> **daggaz said:**
> Yesnovato, debe haber una forma de solucionar tu problema; yo he trabajado con hasta cinco monitores (a través de un Matrox) en Ubuntu y me ha funcionado bien (salvo por lo que indico aquí).
Te sugiero que inicies un nuevo post; pues tu problema es diferente al que inicié yo aquí; si puedes da las especificaciones técnicas de todo tu hardware implicado.
Saludos.
 Gracias por tu replica, estoy seguro que habra una forma pero soy totalmente novato en el mundo de Linux, abrire un nuevo post como me sugieres. Gracias
Salu2

---

