---
title: "Sobre ext4"
date: 2009-04-23
forum: Hardware
---

### Post by leosr on 2009-04-23
Hola.
Aún no istalé Jaunty... cómo es el tema de ext4? hay que formatear la partición o se puede convertir de ext3 a ext4 sin perder los datos?

Salu2

---

### Post by Hernán-Amaya on 2009-04-23
entrá acá que se habla del tema.

[http://ubuntu-ar.org/node/217](http://ubuntu-ar.org/node/217)

---

### Post by luks911 on 2009-04-23
Todo depende. ¿Ya tenés una versión previa? Si es así y en lugar de actualizar instalás desde cero porque tenes / y /home en particiones separadas, podés tener tu / en ext4 y dejar /home como está, en ext3. Eso lo elegís en la instalación.
Creo que hay formas de convertir una partición de ext3 a ext4, pero no durante la instalación, es algo complejo y sí o sí hacé un backup antes.

---

### Post by leosr on 2009-04-23
> **luks911 said:**
> Todo depende. ¿Ya tenés una versión previa? Si es así y en lugar de actualizar instalás desde cero porque tenes / y /home en particiones separadas, podés tener tu / en ext4 y dejar /home como está, en ext3. Eso lo elegís en la instalación.
Creo que hay formas de convertir una partición de ext3 a ext4, pero no durante la instalación, es algo complejo y sí o sí hacé un backup antes.

En / y /home tengo ext3. Donde hay más movimiento de archivos es en /home, por eso creo que me conviene pasarlo a ext4.

Si hago una instalación desde cero formateo el / en ext4, hasta ahí no hay problema. El /home lo tengo en una partición aparte, en el link que me pasó Hernán dice lo siguiente: 
"...Si tenes particiones / y /home, con el kernel 2.6.28 podes cambiar /home a ext4 y no vas a tener ningún problema. Esta complicadísimo sólo si tratas de usar ext4 por el root."
Lo que no dice es cómo se hace para pasar de ext3 a ext4.

Gracias a los dos.

---

### Post by luks911 on 2009-04-23
Acá[0] hay información al respecto. Insisto: backup previo.


[0] [http://ubuntulife.wordpress.com/2009/03/07/convertir-de-ext3-a-ext4/](http://ubuntulife.wordpress.com/2009/03/07/convertir-de-ext3-a-ext4/)

---

### Post by leosr on 2009-04-23
> **luks911 said:**
> Acá[0] hay información al respecto. Insisto: backup previo.


[0] [http://ubuntulife.wordpress.com/2009/03/07/convertir-de-ext3-a-ext4/](http://ubuntulife.wordpress.com/2009/03/07/convertir-de-ext3-a-ext4/)

Gracias. Lo leí, es medio complicado...

Qué pasa si hago una copia de seguridad del /home, hago una instalación desde 0 borrado el /home actual y formateandolo en ext4? Después desde un livecd copio la copia de seguridad el "nuevo" /home.
Se puede? Cómo lo hago? disculpen, soy novato todavía.

Salu2.

---

### Post by luks911 on 2009-04-23
A ver si entendí: hacés copia de tu home, instalás todo desde cero en ext4 y "pisás" el nuevo home con los datos de tu home original. No soy experto, pero no me parece para nada descabellado. Debería quedar en ext4 y con los datos viejos que recuperes del backup.
Estaría bueno que alguien con más experiencia opine, aunque creo que debería funcionar y, en el peor de los casos, tenés el backup.

---

### Post by staar on 2009-04-23
eso es justamente lo que, personalmente, hago e hice el otro dia cuando instale Jaunty...
OJO, no copio toodo el home, solo mis carpetas con documentos y archivos, y, de las ocultas, .config (configuraciones de algunos programas) .scripts (para conky) .themes .fonts .icons, etc...
aunque vos podrías elegir las de los programas que quieras, puede ser .wine, por ejemplo, lo que si NO recomiendo que copies directamente, son la de gnome, .gnome2, y los archivos de configuración de estado que hay en el home (esto lo experimente al pasar de hardy a ubuntu, y se me armó EL bardo, tuve que borrar mi usuario y empezar de nuevo)...
si no sabes de que es una carpeta, o si es de un programa que no uses, dejala, siempre podes volver a configurar después...

ah, no hace falta que lo hagas desde un livecd, directamente desde el ubuntu esta bien ;-)

saludos

---

### Post by z37a on 2009-04-24
> **leosr said:**
> Gracias. Lo leí, es medio complicado...

Qué pasa si hago una copia de seguridad del /home, hago una instalación desde 0 borrado el /home actual y formateandolo en ext4? Después desde un livecd copio la copia de seguridad el "nuevo" /home.
Se puede? Cómo lo hago? disculpen, soy novato todavía.

Salu2.

Asi lo hice yo ciando instale el alpha, por lo que lei las unidades transformadas de ext3 a ext4 andan mejor que el ext3, peor si es ext4 nativo tengo entendido que anda mucho mejor!!!

PD: Aprovecha y eliminate archivos demas que tengas en el /home!!!!! siempre hay algo demas y viene bien una limpieza!!!!

---

### Post by leosr on 2009-04-28
Gracias a todos! cuando tenga tiempo voy a probar y les cuento.

---

