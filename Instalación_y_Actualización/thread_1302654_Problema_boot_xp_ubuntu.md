---
title: "Problema boot xp ubuntu"
date: 2009-10-27
forum: Instalación y Actualización
---

### Post by eurofe on 2009-10-27
hola todos

soy nuevo en el mundo de ubuntu y ya empecé a cometer mis primeros errores. en mi compu tenia vista, luego instalé xp en dual boot, y ya que vista es lo peor de lo peor y que windows me esta causando muchos problemas, décidi de lanzarme con ubuntu.
instalancion sin ningun problema y al parecer funciona perfecto...pero cuando pongo windows xp "Windows could not start because the following file is missing or corrupt: Windows\System32\Hal.dll" 
me puedo imaginar que el problema es que en la particion de vista estaban todas las cosas para cargar xp, y como la formatié, yo causé el problema.

el punto es como solucionar el problema, ya que por el instante no estoy listo para dejar defenitivamente windows y no me gustaria tener que reinstalar vista.

alguien me puede dar alguna idea para solucionar el problema, si es posible sin ayuda del cd de windows que no tengo idea donde lo dejé.
ademas hay que tomar en cuenta que no tengo accèso a windows directamente.

por si es necesario, mi compu es un hp pavillon (no me acuerdo bien el numero creo que 2000) instalé 9.04 en ext4 (me imagino que va a ser util para el upgrade).

gracias por leer este mensaje 
y muchas gracias si me ayudan.

pd: creo que me equivoqué de foro, no se como borrar ni cambiar este mensaje

---

### Post by PabloBS on 2009-10-27
Hace un año a mi me pasó un problema parecido.  La diferencia era que tenía Vista en dualboot con Ubuntu (en ese entonces 8.10).  También era nuevo, solo tenía un mes de tener la configuración, y de estar en el mundo de Linux.  Windows Vista me daba muchos problemas y al final, me decidí a quitarlo por completo.  Fue una decisión radical, y tuve una curva de aprendizaje fuerte, pero ahora no me lamento de la decisión.  

Para tu problema en específico podrías tratar de montar la partición de Windows en Ubuntu y copiar sobre el archivo corrupto uno nuevo (de otro sistema) en su directorio.  Es básico pero me ha funcionado. Si no funciona, deberías considerar dejar Windows en definitiva.

Si tu maquina la usas para cuestiones domésticas, no debería irte mal. Si utilizas aplicaciones pesadas (simuladores, AutoCAD, etc.), considera conseguir un nuevo disco de XP.  Y si crees que vas a extrañar los juegos de Windows, en Ubuntu aún los puedes jugar. En ese caso, los podrías correr con WINE y PlayOnLinux.  En los foros existe bastante tratamiento de estos temas.  Yo mismo corro en mi Ubuntu la serie Command and Conquer.

Haz la prueba.  Aprenderás mucho y no te arrepentirás.  Yo fui usuario de productos Microsoft por 18 años antes de cambiarme a Ubuntu el año pasado.  Ahora solo uso Windows en la oficina, porque no me dan opción, pero en mi casa solo se usa Ubuntu y sus derivados.

Saludos, y suerte.

---

### Post by Patriciologico on 2009-10-27
Hola eurofe, bienvenido.

 Muevo tu consulta a "Instalacion y Actualizacion" porque no publicaste en el lugar correcto, por favor lee las normas (en mi firma).

Saludos!

---

### Post by eurofe on 2009-10-28
Gracias PabloBS

no tuve tiempo de tratar de solucionar el problema como tu me decías cuando encontré una solución simple. solo había que cambiar el numero de la partición en el archivo boot.ini. estaba en 2 y lo pasé 1.

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]


multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /fastdetect 

por otro lado, no tengo la intención de volver a Windows, ubuntu funciona perfecto, no le tengo mucho aprecio a bill gates, los principios económicos de open source me parecen acertados y los principios éticos de freesofwere me parecen importantes.
Con ubuntu solo tengo tres problemas: maxqda un programa de analysis de texto, que no he logrado hacerlo funcionar con wine; con los programas para escuchar musica, ya que no he encontrado ninguno que sea simple e incluya un ecualizador gráfico (como itunes); finalmente, me da lata que no exista nada para defragmentar, que lamentablement necesito para solucionar los problemas que windows causa en mi disco externo.
por lo de tu oficina, yo tenia el mismo problema. La solución que encontré, es instalar ubuntu en un disco duro externo y bootear desde el disco externo usando un CD (no tengo acceso al bios), funciona perfecto y no veo ninguna diferencia de velocidad.

Gracias por tu ayuda 

saludos

---

### Post by moreback on 2009-10-30
[Banshee]("apt:banshee") trae ecualizador!

---

### Post by Carlos C on 2009-10-30
y para defragmentar no existe nada por ahora, pero lo habrá en el futuro como parte de [ntfsprogs]("http://www.linux-ntfs.org/doku.php?id=ntfsprogs") (que está en los repositorios):

[http://www.linux-ntfs.org/doku.php?id=ntfsdefrag](http://www.linux-ntfs.org/doku.php?id=ntfsdefrag)

---

### Post by Patriciologico on 2009-10-30
Amarok y Exaile tambien incluyen ecualizador.

---

### Post by eurofe on 2009-11-05
gracias a todos por sus respuestas,
estoy muy contento de al fin tener un ecualizador gráfico

---

