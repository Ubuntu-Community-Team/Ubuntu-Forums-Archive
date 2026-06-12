---
title: "Despesperación a más no poder: &quot;Error al actualizar el gestor de actulizaciones&quot;"
date: 2012-10-22
forum: Instalación y Actualización
---

### Post by yumbo on 2012-10-22
Hola,

Como a mucha otra gente, a la hora de intentar actualizar el gestor de actualizaciones me ha salido un error y el maldito símbolo de prohibido. Tengo instalado Ubuntu 12.04 y hace un par de semanas me salió el siguiente error al intentar actualizar:

[U]
No se ha podido inicializar la información de los paquetes[/U]

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de esto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-es, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'



El contenido de mi _sources.list_  es:

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted



Por favor, necesito ayuda. No controlo casi nada de Ubuntu y esto me sobrepasa, no sé qué hacer. ¿Alguien me puede echar una mano?

Infinitas gracias :-)

---

### Post by 3nG3ndR0 on 2012-10-22
a mi paso en ocasiones y lo soluciones cambiado des donde descarga las fuentes desde el servidor chileno por el servidor principal, prueba a lomejor te funciona

---

### Post by yumbo on 2012-10-23
Hola 3nG3ndR0,

He hecho lo que me decías y nada, no ha funcionado, me da el mismo error independientemente del servidor que elija para la descarga (principal u otro). Si tienes alguna otra sugerencia... dímelo que lo pruebo :-)

De todas maneras, muchas gracias. A ver si a alguien se le ocurre algo para que la actualización funcione  :-)

---

### Post by yumbo on 2012-11-17
Bueno gente,  sigo sin poder actualizar el gestor de actualizaciones así que no puedo hacer prácticamente nada con el ordenador como administrador del equipo salvo navegar por internet, que no es poco :-)

Así que, como no me deja instalar nada, ni programas, ni actualizaciones... estoy empezando a tener serios problemas. A ver si me podéis echar una mano por favor.

Gracie mille

---

### Post by charlymx on 2012-11-23
Hola intenta con estas instrucciones para solucionar el problema:


pulsa alt+F2
escribe: gksudo nautilus
le das tu contraseña
 Con lo anterior abres el gestor de archivos con privilegios ¡Cuidado con lo que haces a partir de ahora!
 entra en: sistema de archivos
en: var
en: lib
en: apt
en: lists
 pulsa: ctrl+A (para seleccionar todo el contenido)
pulsa: suprimir (para mandarlo a la papelera de root)
cierra el gestor de archivos "
 haciendo estos pasos ya puedes ejecutar el upate-manager, y  actualizar normalmente, si hay dependencias rotas por el error prueba  con 
 " sudo apt-get -f  " 
 

Espero haberte sido util.......

Charlymx desde mexico "arrieros somos y en el camino nos encontramos"

---

### Post by yumbo on 2012-12-21
Muchísimas gracias [charlymx]("http://ubuntuforums.org/member.php?u=1400310")!!!!!! Ha funcionado!!!!

Así que vuelvo a tener el ordenador a pleno rendimiento. Esta solución me la apunto para futuras ocasiones... Si no es por tí no sé que hago, volver a Windows?????????;)

---

### Post by yumbo on 2012-12-23
Se me había olvidado cambiar el título del hilo por [SOLUCIONADO].

---

