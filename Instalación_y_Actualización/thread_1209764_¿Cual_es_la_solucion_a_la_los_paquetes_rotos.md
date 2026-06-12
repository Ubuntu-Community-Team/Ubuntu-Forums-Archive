---
title: "¿Cual es la solucion a la los paquetes rotos?"
date: 2009-07-10
forum: Instalación y Actualización
---

### Post by zhelo on 2009-07-10
he tenido montones de paquetes rotos cuando descargo programas, se instalan y por culpa de ellos no he podido termianr la instalacion de esos programas, el asunto es que esos paquetes rotos me han traido un gran dolor de cabeza y por la desesperacion he tenido que formatear con ubuntu muchas veces, el asunto es que buscando atravez de la web he leido muchas soluciones pero no se aun por que este problema persiste

> vamos desde inicio:

uso un notebook compaq presario f756, le tengo windows xp y ubuntu 9.04

Cuando tienes problemas con paquetes rotos que haces??:

voy a synaptic y busco el archivo roto, lo desintalo completamente, luego, terminal, aplico "sudo nautilus" y voy a "/var/cache/apt/archives" y borro los paquetes luego
voy a "/var/lib/apt/lists" y borro las listas", luego cierro y busco el programa que fallo, se bajan los paquetes y se instalan

te ha traido problemas esto?:

si, hay veces que al reinstalar el programa me dice que el programa no es posible instalarlo por que hay comfictos con otros ya intalados

has buscado otras soluciones?:
si, ir a synaptic y reparar paquetes rotos, pero no pasa nada, el problema persiste.

que haces cuando no puedes solucionar definitavemente tu problema?:

formateo con ubuntu y nuevamente la misma historia


como veran eso es lo que hago, quiero saber si esa es la mejor solucion a este problema, tambien queiro saber si a uds les pasa lo mismo, que hace... como evitar esto que deverdad aburre


desde ya gracias

---

### Post by bichopro on 2009-07-10
A mi simpre me funciono esto:

Borrar Archivos rebeldes

ok, vamos a ponernos un poco mas "salvajes", por asi decirlo.

Prueba a hacer lo siguiente:

# sudo mv /var/lib/dpkg/info/ /var/lib/dpkg/info_moved

# sudo mkdir /var/lib/dpkg/info

<instala o desintala un paquete cualquiera>

# sudo mv /var/lib/dpkg/info/* /var/lib/dpkg/info_moved

# sudo rm /var/lib/dpkg/info

# sudo mv /var/lib/dpkg/info_moved /var/lib/dpkg/info

---

### Post by flakojaime on 2009-07-10
HOla.

Prueba en consola 

sudo apt-get -f install

Lei por ahi en google que puede ser un problema con tu  /etc/apt/sources.list.

Mira [Aqui]("http://foros.softonic.com/configuracion/problema-ubuntu-86917") y por [aca]("http://www.espaciolinux.com/foros-tema-p76812.html")

Saludos

---

### Post by zhelo on 2009-07-10
> **bichopro said:**
> A mi simpre me funciono esto:

Borrar Archivos rebeldes

ok, vamos a ponernos un poco mas "salvajes", por asi decirlo.

Prueba a hacer lo siguiente:

# sudo mv /var/lib/dpkg/info/ /var/lib/dpkg/info_moved

# sudo mkdir /var/lib/dpkg/info

<instala o desintala un paquete cualquiera>

# sudo mv /var/lib/dpkg/info/* /var/lib/dpkg/info_moved

# sudo rm /var/lib/dpkg/info

# sudo mv /var/lib/dpkg/info_moved /var/lib/dpkg/info


que significa "*"??, y por que dejaste un espacio entre info/ y /var???


>  sudo apt-get -f installese comando tambien lo lei pero nunca lo probe, ahora lo puse y me elimino el paquete mal instalado ahroa toy tratandod e instalarlo


------------------------------------------------------------------------------------------------------------------------------------------------------------------
use sudo apt-get -f install, y me borro el archivo malo(la actualizacion del kermel), actualize mi pc de se bajo otros paquetes malos 
y se quedo ahi, recinie me fui a a modo recovery a reparar, y al iniciar me dio un mensaje de error que decia que debia tratar de arreglar el error en modo recovery, y no me dejo entra a ubuntu, asi que por lo visto tendre que formatear de nuevo =/

---

### Post by radixs on 2009-07-10
> **zhelo said:**
> que significa "*"??, y por que dejaste un espacio entre info/ y /var???


ese comando tambien lo lei pero nunca lo probe, ahora lo puse y me elimino el paquete mal instalado ahroa toy tratandod e instalarlo


------------------------------------------------------------------------------------------------------------------------------------------------------------------
use sudo apt-get -f install, y me borro el archivo malo(la actualizacion del kermel), actualize mi pc de se bajo otros paquetes malos 
y se quedo ahi, recinie me fui a a modo recovery a reparar, y al iniciar me dio un mensaje de error que decia que debia tratar de arreglar el error en modo recovery, y no me dejo entra a ubuntu, asi que por lo visto tendre que formatear de nuevo =/

```
que significa "*"??, y por que dejaste un espacio entre info/ y /var???
```

No sera porque esta moviendo algo de una parte a otra

---

### Post by zhelo on 2009-07-10
> **radixs said:**
> ```
que significa "*"??, y por que dejaste un espacio entre info/ y /var???
```No sera porque esta moviendo algo de una parte a otra

entiendo

---

### Post by nopersona on 2009-07-11
Tanto formateo innecesario, mala costumbre que soluciona [buscado y leyendo. ]("http://www.google.cl/linux?hl=es&q=paquetes+rotos&btnG=Buscar&meta=")

---

### Post by zhelo on 2009-07-12
> **nopersona said:**
> Tanto formateo innecesario, mala costumbre que soluciona [buscado y leyendo. ]("http://www.google.cl/linux?hl=es&q=paquetes+rotos&btnG=Buscar&meta=")

converse con un amigo que es programador, y me dijo que era raro que el problema se repitiera tantas veces y en cada formateada, me dijo tambien que quisas ubuntu no era para mi note debiado a su estructura, y me recomendo otra distribucion de linux

---

### Post by radixs on 2009-07-12
> **zhelo said:**
> converse con un amigo que es programador, y me dijo que era raro que el problema se repitiera tantas veces y en cada formateada, me dijo tambien que quisas ubuntu no era para mi note debiado a su estructura, y me recomendo otra distribucion de linux

Men asi de curioso no mas... podrias adjuntar tu sources.list

```
cat /etc/apt/sources.list
```

---

### Post by zhelo on 2009-07-12
> **radixs said:**
> Men asi de curioso no mas... podrias adjuntar tu sources.list

```
cat /etc/apt/sources.list
```

.....

> zhelo@casa:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse


---

### Post by zhelo on 2009-07-14
> **radixs said:**
> Men asi de curioso no mas... podrias adjuntar tu sources.list

```
cat /etc/apt/sources.list
```


ya lo puse, aun toy esperando alguna respuesta compañero

---

### Post by radixs on 2009-07-14
> **zhelo said:**
> ya lo puse, aun toy esperando alguna respuesta compañero

queria ver si la sources.list esta correcta y asi es,la verdad pienso que se pueda deber tu problema para aun no encuentro la respuesta, seguire investigando ;)

PD: tu tambien investiga :P

---

### Post by zhelo on 2009-07-14
> **radixs said:**
> queria ver si la sources.list esta correcta y asi es,la verdad pienso que se pueda deber tu problema para aun no encuentro la respuesta, seguire investigando ;)

PD: tu tambien investiga :P

encontre esto... porfavor velo=

[http://www.adslfaqs.com.ar/como-instalar-linux-ubuntu-en-una-compaq-f756/](http://www.adslfaqs.com.ar/como-instalar-linux-ubuntu-en-una-compaq-f756/)

pues yo tengo ese note..!!!!!!!!!!!1

sera la soluion esa???

---

### Post by radixs on 2009-07-15
> **zhelo said:**
> encontre esto... porfavor velo=

[http://www.adslfaqs.com.ar/como-instalar-linux-ubuntu-en-una-compaq-f756/](http://www.adslfaqs.com.ar/como-instalar-linux-ubuntu-en-una-compaq-f756/)

pues yo tengo ese note..!!!!!!!!!!!1

sera la soluion esa???

Ahí dice que es la solución es para cuando no puedes instalar ubuntu, no por el tema de los paquetes rotos.

---

### Post by ppellet on 2009-07-15
> **zhelo said:**
> he tenido montones de paquetes rotos cuando descargo programas, se instalan y por culpa de ellos no he podido termianr la instalacion de esos programas, el asunto es que esos paquetes rotos me han traido un gran dolor de cabeza y por la desesperacion he tenido que formatear con ubuntu muchas veces, el asunto es que buscando atravez de la web he leido muchas soluciones pero no se aun por que este problema persiste



como veran eso es lo que hago, quiero saber si esa es la mejor solucion a este problema, tambien queiro saber si a uds les pasa lo mismo, que hace... como evitar esto que deverdad aburre


desde ya gracias

Estimados

No sé si estoy bien con esto, pero > $sudo aptitude autoclean puede ser bueno, al menos para eliminar esos archivos que no nos sirven de nada, luego de cargar, descargar, etc. montones de aplicaciones.

Saludos cordiales a todos,

---

### Post by zhelo on 2009-07-15
ya probe con el clean, solo se borran los paquetes usado y los que ya son viejos o algo asi, pero el problema de aun queda con los programas que fueron instalados gracias a esos paquetes rotos

---

### Post by Carlos C on 2009-07-15
Si los repos están bien, si usas ext3 y no ext4, lo único que se me ocurre es que sea un problema de hardware: o la ram esta mala o el disco duro está malo. Para ver lo del disco duro es mejor correr las utilidades de smartmontools (algo que ya te propuse antes) y para la ram se puede hacer al iniciar el sistema gracias a memtest. Te sugiero que verifiques eso, porque ya no se me ocurre qué otra cosa puede ser.

---

### Post by zhelo on 2009-07-15
> **Carlos C said:**
> Si los repos están bien, si usas ext3 y no ext4, lo único que se me ocurre es que sea un problema de hardware: o la ram esta mala o el disco duro está malo. Para ver lo del disco duro es mejor correr las utilidades de smartmontools (algo que ya te propuse antes) y para la ram se puede hacer al iniciar el sistema gracias a memtest. Te sugiero que verifiques eso, porque ya no se me ocurre qué otra cosa puede ser.


llo de la ram y el disco duro me hacen pensar..... sin embargo me llama mucho la atencion el dico duro, lo he formateado tantas veces, windows xp, vista, 7, ubuntu, mandriva...n uih tantas veces..... sera que gasta????.....
lamentablemente ubuntu no lo tengo en uso asi que tendre que verlo en xp...
tengo el everest, que da registros de todo el pc
te ticna si te mando un informe de ahi?

---

### Post by Carlos C on 2009-07-15
lo que necesitas es saber si el disco duro está fallando y para eso no hay mejor herramienta que las utilidades smart. Da lo mismo si lo haces desde windows o linux, lo importante es que uses smart para verificar que el disco duro funciona correctamente. Eso es diferente a saber si es detectado por el sistema. Te he dado enlaces sobre cómo hacerlo desde ubuntu, verificando las tablas de valores que smart entrega. Lo de la memoria ram, no debieras pensarlo tanto y hacer los test necesarios.

---

### Post by EnriqueK on 2009-07-16
Podrías usar e lLive CD de iinstalación , habilitar los repositorios e instalar algo liviano, de esa manera podrías sacar conclusiones por el jecho de que el disco duro estará inactivo y si los problemas continúan el problema va por otro lado.

---

### Post by frankve on 2009-12-05
Un post cortito pero util.

Si alguna vez has obtenido un error de configuración al instalar un paquete en Ubuntu muy probablemente podrás observar un mensaje de error cada vez que intentez instalar otro paquete. Esto es muy molesto , pero para ello hay un comando que elimina esos paquetes mal configurados o Instalados, simplemente teclea en terminal lo siguiente:


    dijo:

    sudo aptitude purge $(dpkg -l|grep ^rc|awk '{ print $2 }')

Sacado de Taringa

[http://www.taringa.net/posts/linux/4042001/Como-eliminar-un-paquete-mal-configurado-en-Ubuntu.html](http://www.taringa.net/posts/linux/4042001/Como-eliminar-un-paquete-mal-configurado-en-Ubuntu.html)

---

