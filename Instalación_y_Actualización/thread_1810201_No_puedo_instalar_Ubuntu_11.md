---
title: "No puedo instalar Ubuntu 11"
date: 2011-07-22
forum: Instalación y Actualización
---

### Post by condes on 2011-07-22
Estimados:


No puedo instalar Ubuntu 11. Cuando pongo el CD me sale UNABLE TO FIND A MEDIUM CONTAINING A LIVE FILE SYSTEM. Buscando en internet descubro que es un error común de varias versiones de Ubuntu, sin embargo, a pesar de probar dos o tres posibles soluciones, el problema persiste. Entre ellas intente: 

- Desactivar con shift todas las opciones del instalador de Ubuntu. 
- Tratar de crear una partición linux con el Partition Magic. Sin embargo no se puede crear ninguna partición porque el programa no se abre.

Es evidente que este problema tiene algún vínculo con la forma en que el mather administra los rígidos, lectores de cd, etc. Por eso aclaro que esta compu que tengo ahora, es nueva. Tiene un mather Asus que soporta un CORE I5 y, naturalmente, todo el interior tiene conexiones SATA.

Bueno, si alguien puede ayudarme, agradecido.


SALUDOS

---

### Post by papibe on 2011-07-22
Una vez me pasó eso, me equivoqué en quemar/copiar Ubuntu. Creé un CD de datos y copié el ISO como archivo.

Lo que tenía que hacer era copiar (burn) una imagen a partir del ISO.

Saludos.

---

### Post by condes on 2011-07-22
Estimado:

Es imposible que haya copiado el archivo ISO en vez del contenido de la imagen. El instalador de Ubuntu se abre. Pero tira el error.

---

### Post by nechus on 2011-07-23
¿Has tratado desde un pendrive?

---

### Post by condes on 2011-07-24
Estimado:

No. No he intentado. Sin embargo, del momento que no puede instalarse desde el cd, me parece mucho mas imposible que se pueda desde un pen. De hecho, a varios que le sale el mismo error, les sale por instalarlo desde un pen.

SALUDOS

---

### Post by patraicio on 2011-07-24
No creo que pierdas nada intentando desde un pendrive. Además que por último desde el mismo programa para crear el disco de inicio en un pendrive puedes comprobar si es que la imagen que bajaste está 100% operativa, otra cosa ¿el pc tiene otro S.O? pregunto ya que el cd de ubuntu trae un instalador para windows, si es que tu pc viene con windows podrías probar esa opción.

Saludos!

---

### Post by condes on 2011-07-24
Estimados:

Por empezar, les agradesco su buena voluntad de ayudarme. Sin embargo quiero decirles que me gusta Ubuntu y quiero instalarlo bien, no a medias tintas. Hacer una imagen con USB desde Ubutnu implica que pueda quitarse cierta funcionalidad al software o que después no funcione de forma óptima. Además, la versión 11, no la tengo instalada en ningún lado. Y lo de instalarlo en windows, bueno, eso es solo para pruebas no para instalar el sistema.

En cualquier caso, intenté hacerles caso, dentro de mis posibilidades. Fue así que copie los archivos de la imagen de Ubuntu a un USB. Luego configuré (desde la bios) el USB como disco de arranque pero no funcionó. También, imprimí la imagen ISO a un USB con el programa ULTRA ISO. Pero tampoco funcionó. Solo se abre el otro sistema operativo instalado (Windows).  

Bueno, espero nuevas sugerencias y otra vez gracias.

---

### Post by papibe on 2011-07-24
Yo acabo de instalar 11.04 desde un pendrive y todo bien. Es equivalente a hacerlo con el CD.

Para crear una versión booteable (requerimiento para la instalación en CD y USB pen), tienes que usar un programa especial. Por ejemplo [UNetbootin]("http://unetbootin.sourceforge.net/"), que es multiplataforma. Lo puedes bajar e instalar en windows y con el mismo ISO de Ubuntu, puedes crear un USB booteable para la instalación.

Nota: en UNetbootin no selectes el distro Ubuntu, porque esa opción va a volver a bajar el ISO. La opción buena es algo así como 'desde ISO' y seleccionas la imagen que ya tienes.

Espero que ayude,
Buena suerte.

---

### Post by patraicio on 2011-07-25
> **condes said:**
> Estimados:

Por empezar, les agradesco su buena voluntad de ayudarme. Sin embargo quiero decirles que me gusta Ubuntu y quiero instalarlo bien, no a medias tintas. Hacer una imagen con USB desde Ubutnu implica que pueda quitarse cierta funcionalidad al software o que después no funcione de forma óptima. Además, la versión 11, no la tengo instalada en ningún lado. Y lo de instalarlo en windows, bueno, eso es solo para pruebas no para instalar el sistema.

En cualquier caso, intenté hacerles caso, dentro de mis posibilidades. Fue así que copie los archivos de la imagen de Ubuntu a un USB. Luego configuré (desde la bios) el USB como disco de arranque pero no funcionó. También, imprimí la imagen ISO a un USB con el programa ULTRA ISO. Pero tampoco funcionó. Solo se abre el otro sistema operativo instalado (Windows).  

Bueno, espero nuevas sugerencias y otra vez gracias.

Como dice papibe al crear un disco de arranque desde un dispositivo usb no se pierde ninguna función, ya que lo que hacen los programas como el que él mencionó es tomar TODOS los archivos dentro de la imagen del CD que bajaste y meterlos dentro del pendrive con las funciones de autoarranque, incluso le agregan una pantalla de bienvenida para cuando booteas desde la memoria. La otra opción que te di yo de utilizar el instalador de windows no es para 'probar' ubuntu, ya que esta opción lo que hace es realizar la primera parte de la instalación de ubuntu desde el mismo windows (así como cuando pasas de windows XP > Vista > 7) para luego reiniciar y utilizar los archivos que previamente copió en el disco duro (para no usar ni el cd ni un pendrive). En ambos casos puedes completar e ir actualizando cosas mientras instalas si es que estás conectado a internet.

Saludos!

PD: Disculpa por no haber expresado claramente la respuesta.

---

### Post by condes on 2011-07-25
Estimados, PROBLEMA RESUELTO:


No por favor... gracias a vos por ayudarme. En cualquier caso ya encontre una solucion. Solo modifique una cosa de la bios... en la parte de SATA, hay que cambiar el modo SATA-IDE A SATA-AHCI. Con eso se abre el instalador. Naturalmente, luego de instalado el Ubuntu, no me abre el windows. Pero volvi a configurar todo como estaba antes SATA-AHCIO a SATA-IDE, y todo solucionado.

SALUDOS Y OTRA VEZ GRACIAS

---

### Post by condes on 2011-07-25
Estimados:


Bueno, luego de instalar Ubuntu 11.04 y que todo funcione bien, me dedico a instalar los paquetes de clásico uso (Wine, extras restringidos y alguno mas). El sistema siempre funciona en español, a excepción del Mozilla. Sin embargo, cuando instalo algunos de los paquetes enumerados, el sistema se transforma todo a ingles. En internet encuentro varias soluciones pero todas muy distintas unas de las otras. 
Naturalmente, ya fui a soporte de idiomas. Sin embargo, ahora cuando voy, le pongo para cambiar el idioma y no pasa nada. Probé de desinstalar el español y el ingles y luego volverlos a instalar. Pero no paso nada. Todo sigue en ingles. ¿Que debo hacer para solucionar esto?

SALUDOS

---

### Post by condes on 2011-07-25
Estimados:

Encontre un nuevo problema que tiene relacion con lo anterior. Luego de instalar el sistema descubro que Ubuntu no registra la lectora de cd y dvd. Es como si no existiera. Si pongo el bios en AHCI la reconoce. Con ide no la reconoce. O sea, tengo que elegir entre tener mi lectora de cd o no poder utilizar windows. 
Alguna sugerencia?

---

### Post by RafaelG on 2011-07-27
Condes,

Disculpa pero he movido tu post por conciderar que corresponde a la seccion de Instalacion.

saludos cordiales,

---

