---
title: "Formatear ubuntu sin perder nada"
date: 2009-07-06
forum: Instalación y Actualización
---

### Post by zhelo on 2009-07-06
no se como arregle mis problemas con los paquetes y bla bla bla.....
tengo caletas de programas descargados, y cosas en la carpeta documentos y cosas asi
..... si llevara el dia en que necesariamente debo formatear (con ubuntu), hay alguna manera de no perder nada al formatear; lo digo, sin tener que respaldar con Pendrive y cosas asi


saludos

---

### Post by aledruetta on 2009-07-06
Si tuvieras "/home" en una partición separada, no tendrías problema al formatear y reinstalar. Los programas que no venían con la distribución original, tendrías que instalarlos nuevamente.

Ahora, si no fuera ese el caso, al formatear perderías todo si antes no hiciste un backup.

Quizá alguien sabe cómo crear una nueva partición (con gparted), copiar ahí "/home", formatear y que todo salga bien. No es mi caso.

Aquí habla de eso:
[http://ubuntuforums.org/showthread.php?t=1200962](http://ubuntuforums.org/showthread.php?t=1200962)

Saludos y suerte,
Alejandro.

---

### Post by nopersona on 2009-07-07
Lo mejor siempre es usar una partición /home separada del sistema base, así conservas las configuraciones tanto del escritorio, programas y demases. Para conservar los paquetes, [puedes generar listas.]("http://sliceoflinux.wordpress.com/2009/01/21/reinstala-ubuntu-y-recupera-facilmente-los-programas-que-tenias-instalados/") 

Lo que hago yo, es partcionar en 3, una para /home, otra para el sistema y una última para archivos y documentos, así, cuando actualizo, sólo renuevo la del sistema y conservo todo. Luego recupero la lista de paquetes. [Antes usaba aptoncd]("http://m4cr0ss.wordpress.com/2008/09/16/respaldar-paquetes-con-aptoncd/#more-418"), pero ya no lo uso, me parece más cómodo generar una lista y renovar, cosa de gustos.

Saludos!
**

---

### Post by EnriqueK on 2009-07-07
Puedes crear una imagen de respaldo de tu sistema , para ello recomiendo el Clonezilla .
Normalmente el clonezilla está basado en Debian, pero existe una versión basada en Ubuntu Jaunty que estimo es la mas apropiada en caso de que temgas tu instalación en EXT 4   [http://sourceforge.net/projects/clonezilla/files/](http://sourceforge.net/projects/clonezilla/files/).
Para usar clonezilla vas a requerir de una partición de tamaño suficiente para almacenar allí la imagen de respaldo y luego la puedes grabar en DVDs y así liberar espacio en DD.

---

### Post by zhelo on 2009-07-07
> **nopersona said:**
> Lo mejor siempre es usar una partición /home separada del sistema base, así conservas las configuraciones tanto del escritorio, programas y demases. Para conservar los paquetes, [puedes generar listas.]("http://sliceoflinux.wordpress.com/2009/01/21/reinstala-ubuntu-y-recupera-facilmente-los-programas-que-tenias-instalados/") 

Lo que hago yo, es partcionar en 3, una para /home, otra para el sistema y una última para archivos y documentos, así, cuando actualizo, sólo renuevo la del sistema y conservo todo. Luego recupero la lista de paquetes. [Antes usaba aptoncd]("http://m4cr0ss.wordpress.com/2008/09/16/respaldar-paquetes-con-aptoncd/#more-418"), pero ya no lo uso, me parece más cómodo generar una lista y renovar, cosa de gustos.

Saludos!



eso que dices, es cuando uno instala ubuntu de forma manual.... yo tambien lo hacia
me creaba el "/ (sistema ext3 tras.)", el "/hom (sistema ext3 tras.)",y el "area de intercambio"..... tu te refieres a eso?, entonces cuando formatee solo debo borrar el "/"??

---

### Post by radixs on 2009-07-07
> **zhelo said:**
> eso que dices, es cuando uno instala ubuntu de forma manual.... yo tambien lo hacia
me creaba el "/ (sistema ext3 tras.)", el "/hom (sistema ext3 tras.)",y el "area de intercambio"..... tu te refieres a eso?, entonces cuando formatee solo debo borrar el "/"??

si creaste la particion /home aparte de / ... si seria lo que mencionas...
ojo que cuando vayas a formatear tienes que asignar el punto de montaje /home a tu particion /home (valga la rebundancia) si no realizas esto no se montara /home

NOTA: nose te vaya a ocurrio montar la particion /home y tikear el formateo, si lo haces pederas todo lo que tengas....

PD: con esto solo puedes recuperar las configuraciones de tu programas, no tu programas, aquellos que instalaste tendras que instalarlos de nuevo, lo bueno es que ya estaran configurados como los tenias antes ;)

---

### Post by nopersona on 2009-07-07
> **radixs said:**
> si creaste la particion /home aparte de / ... si seria lo que mencionas...
ojo que cuando vayas a formatear tienes que asignar el punto de monater /home a tu particion /home (valga la rebundancia) si no realizas esto no se monatara /home

NOTA: nose te vaya a ocurrio montar la particion /home y tikear el formateo, si lo haces pederas todo lo que tengas....

PD: con esto solo puedes recuperar las configuraciones de tu programas, no tu programas, aquellos que instalaste tendras que instalarlos de nuevo, lo bueno es que ya estaran configurados como los tenias antes ;)


+1 a todo.

---

### Post by zhelo on 2009-07-08
pero el cd de ubuntu debo ponerlo una vez en ubuntu, y desde ahi instalar, o debo prender el pc con el cd dentro para botear?

---

### Post by kamus on 2009-07-08
> **zhelo said:**
> pero el cd de ubuntu debo ponerlo una vez en ubuntu, y desde ahi instalar, o debo prender el pc con el cd dentro para botear?

1)Respalda tu informacion en Pendrive, DVD, Disco Duro, etc
2)Cuando vuelvas a instalar tu sistema al momento de gestionar tus particiones asegurate de crear una aparte solo para /home con espacio suficiente (en este lugar quedan los datos para las cuentas de usuario excepto root), con este te evitaras varios futuros dolores de cabeza ...

salu2

---

### Post by zhelo on 2009-07-09
> **kamus said:**
> 1)Respalda tu informacion en Pendrive, DVD, Disco Duro, etc
2)Cuando vuelvas a instalar tu sistema al momento de gestionar tus particiones asegurate de crear una aparte solo para /home con espacio suficiente (en este lugar quedan los datos para las cuentas de usuario excepto root), con este te evitaras varios futuros dolores de cabeza ...

salu2


y que pasa si respaldo la carpeta /home
formateo y una intalado ubuntu, pego la carpeta /home por la ya existente?

---

### Post by AlvaroV on 2009-07-09
> **zhelo said:**
> y que pasa si respaldo la carpeta /home
formateo y una intalado ubuntu, pego la carpeta /home por la ya existente?


Zhelo, en mi humirde opinión te aconsejo que sí no tienes mucha información en tu PC, respalda en un disco o pendrive lo que haya y reintalas desde cero, contruyendo una partición home separada de la "/". Y trabajas de esa forma en adelante, yo desde que aprendí eso, reinstalo Ubuntu cada vez que tengo un problema grave y no pierdo la información que he guardado.

---

### Post by radixs on 2009-07-09
> **zhelo said:**
> y que pasa si respaldo la carpeta /home
formateo y una intalado ubuntu, pego la carpeta /home por la ya existente?

Zhelo.... deja de dar tanto jugo (en buena onda)... creo que si lees atentamente la respuesta que di, veras la solucion.... ;)

[COLOR=Black]***_LEE ESTO_***[/COLOR]

[COLOR=Red][I]> si creaste la particion /home aparte de / ... si seria lo que mencionas...
ojo que cuando vayas a formatear tienes que asignar el punto de montage /home a tu particion /home (valga la rebundancia) si no realizas esto, no se monatara /home

NOTA: nose te vaya a ocurrir montar la particion /home y tikear el formateo, si lo haces pederas todo lo que tengas....

PD: con esto solo puedes recuperar las configuraciones de tu programas, no tu programas, aquellos que instalaste tendras que instalarlos de nuevo, lo bueno es que ya estaran configurados como los tenias antes :wink:[/I][/COLOR]

---

### Post by zhelo on 2009-07-09
vale, gracias

---

### Post by radixs on 2009-07-09
> **zhelo said:**
> vale, gracias

de nada, para eso estamos ;)

---

### Post by zhelo on 2009-07-09
justamente, respalde home, luego puse el ubuntu amd64 y pegue home, al reiniciar todo queda como antes a ecepcion por lo programas que yo mismo debo instalar, pero sus configuraciones fueron guardas
mil gracias

---

