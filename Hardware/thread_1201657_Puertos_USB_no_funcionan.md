---
title: "Puertos USB no funcionan"
date: 2009-07-01
forum: Hardware
---

### Post by Davidcardenas on 2009-07-01
Hola

necesito ayuda, soy algo nuevo en Ubuntu, tengo una IBM thinkpad T43, y sucede que cuando conecto algo a los puertos USB (impresora, pendrives, o disco duro externo), los reconoce por un par de minutos, y luego desaparecen.

Es buscado en muchas partes, pero no he encontrado una solución satisfactoria

Desde ya les agradezco su ayuda
Dcardenas

---

### Post by Carlos C on 2009-07-01
Movido al subforo Hardware. Por favor lee acá antes de publicar tus dudas:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)


Respecto a tu problema, qué ocurre si al desaparecer el dispositivo escribes en el terminal:
```
lsusb
```
Dime si lo encuentra.

Saludos.

---

### Post by Davidcardenas on 2009-07-02
Si, si los reconoce, de hecho hasta he podido aceesar y trabajar con los datos, pero pasan un par de minutos y se desmonta, a veces vuelve a montarse y en otras (la mayoria) no lo hace, (esto tambien me sucede con un disco externo y la impresora)

esto es lo que sale de ejecutar el comando lsusb en la terminal

dcardenas@dcardenas-laptop:~$ lsusb
bus 005 Device 002: ID 0951:1607 Kingston Technology
bus 005 Device 002: ID 0000:0000
bus 004 Device 002: ID 0000:0000
bus 003 Device 002: ID 0000:0000
bus 002 Device 002: ID 0000:0000
bus 001 Device 002: ID 0000:0000

no es un problema fisico, ya que con Windows esto no sucede, te adjunto tambien el resultado de ejecutar el comando dmesg

gracias

---

### Post by Carlos C on 2009-07-02
Cuando se desmonta la unidad y haces un lsusb ¿vuelve a montarse?. Mirando el archivo que adjuntas tengo la impresión de que usas un hub para ampliar la cantidad de puertos usb disponibles. ¿Este problema te pasa sólo cuando usas tu hub o también te pasa al conectar los dispositivos directamente a los puertos usb?

---

### Post by Davidcardenas on 2009-07-02
la verdad es que no uso hub, el notebook solo tiene dos puertos fisicos disponibles, despues de que demonto la unidad, en algunas ocaciones lo vuelve a montar de manera automatica, otras veces ejecutando lsusb o lspci, y muchas veces de plano no lo vuelve a montar

Gracias

---

### Post by kamus on 2009-07-02
> **Davidcardenas said:**
> Hola

necesito ayuda, soy algo nuevo en Ubuntu, tengo una IBM thinkpad T43, y sucede que cuando conecto algo a los puertos USB (impresora, pendrives, o disco duro externo), los reconoce por un par de minutos, y luego desaparecen.

Es buscado en muchas partes, pero no he encontrado una solución satisfactoria

Desde ya les agradezco su ayuda
Dcardenas

Podrias entregarnos algunos detalles como que version de ubuntu tienes instalada?

Salu2

---

### Post by Davidcardenas on 2009-07-02
por supuesto,

tengo instalada la version 8.04.2 LTS

---

### Post by kamus on 2009-07-02
> **Davidcardenas said:**
> por supuesto,

tengo instalada la version 8.04.2 LTS

No has probado en modo live la ultima version estable 9.04?, lo mas probable es que se haya solucionado el problema aunque es bastante raro no has descartado algun problema de hardware?.

Salu2

---

### Post by moreback on 2009-07-03
> **Davidcardenas said:**
> la verdad es que no uso hub, el notebook solo tiene dos puertos fisicos disponibles, despues de que demonto la unidad, en algunas ocaciones lo vuelve a montar de manera automatica, otras veces ejecutando lsusb o lspci, y muchas veces de plano no lo vuelve a montar

Gracias


Se supone que lo desmontas para extraerlo físicamente, no? Si no lo haces es probable que si intentas acceder nuevamente a él se monte automáticamente.

---

### Post by Davidcardenas on 2009-07-03
Hola,

con 9.04 sucede lo mismo, también se desconecta después de un par de minutos, y no es un problema físico de los puertos, ya que con Windows XP, no presenta problemas de este tipo, con respecto al uso, siempre desmonto las unidades, y también esto de que se desconectan los puertos,afecta cuando conecto otro tipo de unidades como un disco duro externo.

buscando en la internet, he encontrado las siguientes propuestas:
 1.- Actualizar la Bios del Notebook
 2.- hacer un sudo gedit /boot/grub/menu.lst y agregar la siguiente linea : 

Kernel          /boot/vmlinuz-2.6.24-19-generic root=/dev/hda3 ro quiet splash noapic irqpoll pci=routeirq 

Que me sugieren ustedes
De ante mano gracias

---

### Post by moreback on 2009-07-03
Yo creo es mejor comenzar por actualizar la BIOS.

La segunda línea está mal.

Saludos.

---

### Post by kamus on 2009-07-04
> **Davidcardenas said:**
> Hola,

con 9.04 sucede lo mismo, también se desconecta después de un par de minutos, y no es un problema físico de los puertos, ya que con Windows XP, no presenta problemas de este tipo, con respecto al uso, siempre desmonto las unidades, y también esto de que se desconectan los puertos,afecta cuando conecto otro tipo de unidades como un disco duro externo.

buscando en la internet, he encontrado las siguientes propuestas:
 1.- Actualizar la Bios del Notebook
 2.- hacer un sudo gedit /boot/grub/menu.lst y agregar la siguiente linea : 

Kernel          /boot/vmlinuz-2.6.24-19-generic root=/dev/hda3 ro quiet splash noapic irqpoll pci=routeirq 

Que me sugieren ustedes
De ante mano gracias

Claramente juega con los parametros del kernel, deja como ultima instancia una actualizacion de BIOS ya que es un proceso complejo y muchas veces el fracaso lleva un efecto mas o menos critico en los resultados ;)

---

