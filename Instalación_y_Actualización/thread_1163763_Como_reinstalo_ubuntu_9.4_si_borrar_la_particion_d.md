---
title: "Como reinstalo ubuntu 9.4 si borrar la particion de xp!!???"
date: 2009-05-19
forum: Instalación y Actualización
---

### Post by ceskai on 2009-05-19
Que tal ..!  Que bueno que se activo nuevamente el foro..! la verdad es de mucha utilidad ..
 
Bueno...
Resulta que tengo ubuntu 9.4 obtenido desde la actualización de ubuntu 8.10. Estuve leyendo por internet y me encontré con varios comentarios que es mejor instalar ubuntu 9.4 desde cero ..! .. la cosa es que en mi equipo esta particionado en wn xp (40gb) y Ubuntu (40gb). Ahora quiero reinstalar desde cero ubuntu 9.4 , pero sin borrar la partición de xp .. En resumen,  quiero eliminar el sistema ubuntu actual e instalar desde cero 9.4 pero sin tocar la particion de xp, ya que lo ocupo solo por office 2007. 
Quiero instalarlo de manera correcta ; refiarese al sistema de particiones manuales .. 

Otra  pregunta en relacion a este mismo tema; 
Cuando uno divide un disco , donde en una particion se instala xp, quedando el resto del disco libre para instalar ubuntu!!! .... si en la instlacion de ubuntu , elijo la opcion de instalar el sistema en el espacio libre del disco.  Esto es lo mismo que instlar con la opcion manual (hacer las particiones manualmente) ????? el sistema queda igual de rapido?? .. 

Bueno espero que me puedan orientar y guiar como hacerlo ...
Saludos ..! ):P

Detallo el resumen de las instalaciones que tengo en mi pc :

[B]Disco /dev/sda: 80.0 GB, 80026361856 bytes 
255 cabezas, 63 sectores/pista, 9729 cilindros 
Unidades = cilindros de 16065 * 512 = 8225280 bytes 
Identificador de disco: 0x37713770 
 
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema 
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS 
/dev/sda2            3825        9729    47431912+   5  Extendida 
/dev/sda5            3825        9545    45953901   83  Linux 
/dev/sda6            9546        9729     1477948+  82  Linux swap / Solaris [/B]

**Espesificaciones del pc** 
 
Fabricante del sistema Hewlett-Packard 
Modelo del sistema HP Pavilion dv2000 (RR040LA#ABM) 
Tipo de sistema X86-based PC 
Procesador x86 Family 6 Model 14 Stepping 8 GenuineIntel ~1861 MHz 
Ram 512 
Intel(R) PRO/Wireless 3945ABG Network Connection 
lspci |grep VGA 
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by Carlos C on 2009-05-19
Hola. Sobre tus dudas. Lo que debes hacer es instalar Ubuntu y en el momento del particionado lo mejor es que escojas la opción manual. La razón es que si escoges que instale en el espacio libre te instalará ubuntu en dos particiones: una pequeña para tu swap (area de intercambio) y otra para todo lo demás. En cambio si haces una partición manual puedes hacer tres particiones, de manera de separar Ubuntu en tres particiones: "/home","/" y swap. De esa manera, si alguna vez quieres reinstalar Ubuntu puedes formatear la partición "/", manteniendo todos tus archivos contenidos en el "/home".
Como esto debe ser algo complicado de entender te recomiendo que leas esta página:

[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

Por último, quiero agregar que para no perder tu windows lo que debes hacer es instalar Ubuntu en la partición donde esta tu Ubuntu actual. En el enlace que te doy lo explican bien.

Saludos.

---

### Post by 3nG3ndR0 on 2009-05-20
> **ceskai said:**
> Que tal ..!  Que bueno que se activo nuevamente el foro..! la verdad es de mucha utilidad ..
 
Bueno...
Resulta que tengo ubuntu 9.4 obtenido desde la actualización de ubuntu 8.10. Estuve leyendo por internet y me encontré con varios comentarios que es mejor instalar ubuntu 9.4 desde cero ..! .. la cosa es que en mi equipo esta particionado en wn xp (40gb) y Ubuntu (40gb). Ahora quiero reinstalar desde cero ubuntu 9.4 , pero sin borrar la partición de xp .. En resumen,  quiero eliminar el sistema ubuntu actual e instalar desde cero 9.4 pero sin tocar la particion de xp, ya que lo ocupo solo por office 2007. 
Quiero instalarlo de manera correcta ; refiarese al sistema de particiones manuales .. 

Otra  pregunta en relacion a este mismo tema; 
Cuando uno divide un disco , donde en una particion se instala xp, quedando el resto del disco libre para instalar ubuntu!!! .... si en la instlacion de ubuntu , elijo la opcion de instalar el sistema en el espacio libre del disco.  Esto es lo mismo que instlar con la opcion manual (hacer las particiones manualmente) ????? el sistema queda igual de rapido?? .. 

Bueno espero que me puedan orientar y guiar como hacerlo ...
Saludos ..! ):P

Detallo el resumen de las instalaciones que tengo en mi pc :

[B]Disco /dev/sda: 80.0 GB, 80026361856 bytes 
255 cabezas, 63 sectores/pista, 9729 cilindros 
Unidades = cilindros de 16065 * 512 = 8225280 bytes 
Identificador de disco: 0x37713770 
 
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema 
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS 
/dev/sda2            3825        9729    47431912+   5  Extendida 
/dev/sda5            3825        9545    45953901   83  Linux 
/dev/sda6            9546        9729     1477948+  82  Linux swap / Solaris [/B]

**Espesificaciones del pc** 
 
Fabricante del sistema Hewlett-Packard 
Modelo del sistema HP Pavilion dv2000 (RR040LA#ABM) 
Tipo de sistema X86-based PC 
Procesador x86 Family 6 Model 14 Stepping 8 GenuineIntel ~1861 MHz 
Ram 512 
Intel(R) PRO/Wireless 3945ABG Network Connection 
lspci |grep VGA 
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

yo estaba igual que tu, pero ocupe la misma partición de ubuntu, la realice manual. en la partición de linux seleccionas de que tipo sera ext3, ext4 y el punto de montaje osea **/** y activas la opción formatear.

---

### Post by Carlos C on 2009-05-20
> **3nG3ndR0 said:**
> yo taba igual que tu ocupe la misma partición de ubuntu lo realice manual, y en la partición de linux seleccionas de que tipo ext3, ext4 y el punto de montaje osea **/** y activas la opción formatear

Estimado, recuerda que este foro es visitado mayoritariamente por gente cuyo idioma nativo no es el castellano. Por favor evita los errores de tipeo y pon atención a cómo escribes para que se entienda(una coma y un punto de vez en cuando). Yo soy chileno y sé como instalar Ubuntu, pero leo tu post y quedo medio perdido ;)

Saludos.

---

### Post by ceskai on 2009-05-21
[FONT=&quot][SIZE=3]Que tal , gracias por todas las respuestas..

Bueno la cosa es que tuve problemas después de instalar, con la parte grafica y el Home  ... el cambio que hice fue el siguiente 

**/dev/sda5 3825 9545 45953901 83 Linux > La cambie por **ext4 y le di montaje **/**
Me salieron mensajes de error con respecto al home , después reinicie y no pude ingresar mas a mi sesión , me aparecía una pantalla azul que decia que mi sistema grafico tenia problemas…Bueno y la cosa es que ahora prefiero instalar todo desde cero incluyendo xp. Por eso voy a describir los pasos que hare para que me orienten y de una vez por todas tener Ubuntu 9.4 instalado de manera correcta …..=)[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]
1ro . Desde el cd de instalación de xp borrare todas las particiones que tengo, incluidas las de Ubuntu. Me quedaría el disco vacío , creo la partición **C (20GB) **quedándome 60 gb libres… en este punto donde tengo una duda….**Ah este espacio libre , le doy un formato ntfs o no lo toco? Continuamos…..**[/SIZE][/FONT][SIZE=3]

**[FONT=&quot]2do.[/FONT]**[/SIZE]   [FONT=&quot][SIZE=3] Luego de haber instalado xp , con todos los drivers .. Empiezo con la instalación de Ubuntu … llegando al punto del particionado manual..Según el manual que Carlos me recomendó  dice que este debería ser la estructura ideal :[/SIZE][/FONT][SIZE=3]

**[FONT=&quot](La asignación de gb en la partición primaria 1 y lógica 4 solo corresponde a mi caso)[/FONT]**
[/SIZE]      
[LIST]
[*][FONT=&quot][SIZE=2]Partición primaria 1: **ntfs**,      para Windows XP (20gb)[/SIZE][/FONT]
[*][FONT=&quot][SIZE=2]Partición primaria 2: **ext3      o ext4 ?**, para la raíz **/** (7 gb) [/SIZE][/FONT]
[*][FONT=&quot][SIZE=2]Partición primaria 3:      partición extendida ¿? [/SIZE][/FONT]
[LIST]
[*][FONT=&quot][SIZE=2]Partición lógica 4: **linux-swap**,       para la memoria de intercambio **1024       gb** [/SIZE][/FONT]
[*][FONT=&quot][SIZE=2]Partición lógica 5: **ext3       o ext4?**, para los datos personales (**/home**) **El resto del disco**[/SIZE][/FONT]
[/LIST]
 
[/LIST]
  [SIZE=3]**Bueno la duda que tengo  en esta parte es cuando llego a la partición primaria 3. ****Como la creo ****[FONT=&quot]?[/FONT]**[/SIZE][FONT=&quot][SIZE=3] ya que la opciónes que salen en el recuadro de configuración de la partición;  es primaria o lógica , mas el tipo de montaje ,  al principio o al final y la opción de formateo….Como la configuro?  Que volumen le doy?[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=&quot][SIZE=3]Después creo la lógica 4 y 5 con el espacio restante del disco, cada una con sus respectivos montajes…  y dimensiones. **Estas se sacan de la primaria 3??? …. Como hago eso?**[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=&quot][SIZE=3]3ro l**as particiones ext3 las cambio a ext4?**[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=&quot][SIZE=3]Ya esta todo descrito al parecer queda bien claro y espero que le sirva a otros que estén en las mismas… ojala me puedan ayudar…[/SIZE][/FONT][SIZE=3]
[/SIZE]   [FONT=&quot][SIZE=3]SALUDOS….;)[/SIZE][/FONT]

---

### Post by Carlos C on 2009-05-21
> [SIZE=3]**Bueno la duda que tengo  en esta parte es cuando llego a la partición primaria 3. ****Como la creo ****[FONT=&quot;]?[/FONT]**[/SIZE][FONT=&quot;][SIZE=3] ya que la opciónes que salen en el recuadro de configuración de la partición; es primaria o lógica , mas el tipo de montaje , al principio o al final y la opción de formateo….Como la configuro? Que volumen le doy?[/SIZE][/FONT][SIZE=3]

[/SIZE]   [FONT=&quot;][SIZE=3]Después creo la lógica 4 y 5 con el espacio restante del disco, cada una con sus respectivos montajes…  y dimensiones. **Estas se sacan de la primaria 3??? …. Como hago eso?**[/SIZE][/FONT]Las particiones extendidas se hacen únicamente cuando necesitas tener más de 4 particiones primarias, que es el límite permito en la tabla de particiones. En el fondo una partición extendida es lo mismo que una partición primaria, pero que en su interior contiene una serie de particiones "lógicas", que en la práctica funcionarán como si fueran particiones primarias. De esa manera puedes tener todas las particiones que quieras. Por esta razón cuando haces una partición lógica esta queda inmediatamente en /dev/sda5. Aun cuando tu tabla de particiones tenga menos de cuatro particiones, a primera partición lógica quedará en sda5. En tu caso veo que usarás cuatro particiones, por lo tanto puedes perfectamente usar sólo particiones primarias.

> [FONT=&quot;][SIZE=3]3ro l**as particiones ext3 las cambio a ext4?**[/SIZE][/FONT][SIZE=3]

[/SIZE]ext3 es el sistema por defecto, ya que ext4 es más rápido, pero resulta algo menos inestable aún. Yo uso ext4 y no he tenido problemas. Creo que debes tomar una decisión y para eso es cuestión de busques información en internet.

Espero haber resuelto tus dudas.
Saludos.

---

