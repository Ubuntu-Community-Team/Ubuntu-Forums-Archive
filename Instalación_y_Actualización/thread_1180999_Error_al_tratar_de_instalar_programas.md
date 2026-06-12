---
title: "Error al tratar de instalar programas"
date: 2009-06-07
forum: Instalación y Actualización
---

### Post by zhelo on 2009-06-07
soy nuevo en ubuntu, me gusto muchisimo quiero migrar a linux para siempre, creo en el sofwarre libre, y estudio ing. civil en informactica...
y quiero su ayuda para consagrarme en ubuntu...
mi problema:

mi problema va en que baje ubuntu 9.04 y decidi iinstalarlo ya que éste reciebe inmediatamente el wifi de todos lados, el asunto va al momento de _bajar_ los programas por "agregar o quitar " y por "gestor de paquetes sinoticos" (o algo asi), me bajo programas, por ej : amsn, y al instalar me tirar errores, me dice que los paquetes estan rotos, voy al gestor de paquetes... para reparar y nada sucede.... formatee de nuevo el pc con ubuntu 9.04, esta ves si se instalo el amsn, pero al bajar JAva u cualqueir otro, en plena instalacion (obiamnete despues de haber bajado los paquetes) me tira error y no puedo seguir instalado ese programa, trato de desintalar completamente los programas rotos para reisntalar, pero el problema sigue.

que pasa?

---

### Post by Carlos C on 2009-06-07
Hola. Es muy difícil darte una respuesta porque no estás dando la información necesaria. Lo mejor sería que presentaras un caso particular con datos exactos. Es decir, decirnos qué paquete o programa trataste de instalar, cómo lo hiciste y pegaras acá el mensaje de error que te aparece.

Por favor evita escribir título como " ayuda porfavor!!" y usa uno que describa el problema en cuestión. Acabo de borrar el thread que abriste antes ya que era una réplica de éste y estaba, además, mal ubicado.

Te recomiendo que mires [B][acá.]("http://ubuntuforums.org/showthread.php?t=1162750")

[/B]Saludos!

---

### Post by zhelo on 2009-06-07
perdon por el doble tema, es que no sabia bien donde postear

ya mira el caso que me pasa siempre-......

cuando bajo eclipse; para programar; uso anadir o quitar para descargarlo, se descarga el paquete, cuando se instala me aparace un icono rojo al lado del lugar en donde esta la fecha;, luego en el instalado me dice "error de una parte del paquete", (en este caso pongamosle paquete x); error del paquete x asi que pongo cerrar, el programa no se instalado, luego hago click en el icono rojo y me dice que hay un paquete roto y que debo reparalo; voy a ....synaptic busco el paquete X, pongo reparar...aplciar.... se instala algo de nuevo, creo que es el pauqte x de eclipse;.... luego me avisa que hay un error en el paquete x, asi que me puse a desibntalar el eclipse.... trato de reinstalar de nuevo, y me sale el mismo error.... lo mas curioso de esto es que cuando me pasa eso de los errores mi ubuntu anda malisimo, onda el amsn se me pega caleta, el skin de la barra de tarea se trasnforma en otro que nah que ver, y cosas asi....
hable con un amigo y me dijo que podia ser la interfaz; pero he formateado varias veces mi pc con ubuntu (tengo 120 de disco, 50 para windows 7 y el resto para ubuntu).....
no entiendo que pasa, ayer use el terminal para instalar pero tambien me tira errores en algunos programas y nuevamente la misma historia....
me puse a buscar en una web de ubuntu  y me baje ubuntu 9.04 amd64 (ya que mi procesador es de esos), espero que se soluciones el problema cone so pero no se bien.....

a uds les pasa eso cuando se bajan programas y tratan de instlalros??

---

### Post by Carlos C on 2009-06-07
Nuevamente el mismo problema, no estás escribiendo el error exacto. Por favor trata de instalar un programa desde Synaptic, espera que aparezca el error y copia acá lo que te salga. Si no nos dices el error exacto puede ser cualquier cosa y no es posible ayudarte.

Saludos.

---

### Post by CdK1 on 2009-06-08
Pequeño truquillo, se llama "apt-get", más fácil de usar y si tiene error te los muestra claramente, ahora para lo tuyo has esto:

Como siempre:

apt-get update 
apt-get -f install

si el error persigue:

cd /var/lib/dpkg/info
ls | grep "paquete roto"

Ejemplo:

ls | grep amsn
rm amsn.postinst   ==> el archivo *.postinst es el que hay que borrar

Luego de nuevo:

apt-get -f install
apt-get upgrade
apt-get install paquete

---

### Post by zhelo on 2009-06-08
[IMG]http://i39.tinypic.com/219uud0.png[/IMG]
aca la  imagen, trate de bajarme el  JDK para programar y me tiro ese error, trate de desintalarlo completamente usando el  gestor de paqueuete synaptic y me salio esto

> E: /var/cache/apt/archives/openjdk-6-jre-lib_6b14-1.4.1-0ubuntu7_all.deb: lectura insuficiente en buffer_copy (error en dpkg-deb durante `./usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar')
E: /var/cache/apt/archives/libxt-dev_1%3a1.0.5-3ubuntu1_i386.deb: sistema de ficheros del archivo tar dañado - archivo de paquete dañado
E: /var/cache/apt/archives/ttf-wqy-zenhei_0.8.34-cvs20081027-0ubuntu1_all.deb: lectura insuficiente en buffer_copy (error en dpkg-deb durante `./usr/share/fonts/truetype/wqy/wqy-zenhei.ttc')


que onda?

---

### Post by zhelo on 2009-06-08
> **CdK1 said:**
> Pequeño truquillo, se llama "apt-get", más fácil de usar y si tiene error te los muestra claramente, ahora para lo tuyo has esto:

Como siempre:

apt-get update 
apt-get -f install

si el error persigue:

cd /var/lib/dpkg/info
ls | grep "paquete roto"

Ejemplo:

ls | grep amsn
rm amsn.postinst   ==> el archivo *.postinst es el que hay que borrar

Luego de nuevo:

apt-get -f install
apt-get upgrade
apt-get install paquete


creo que te falto escribir "sudo", y trate, pero el problema sigue
 pero no entiendi esto :

> si el error persigue:

cd /var/lib/dpkg/info
ls | grep "paquete roto"

Ejemplo:

ls | grep amsn
rm amsn.postinst   ==> el archivo *.postinst es el que hay que borrar


---

### Post by Patriciologico on 2009-06-09
¿Puedes redimensionar la imagen para que no exceda el ancho de pantalla?

---

### Post by kamus on 2009-06-09
> **zhelo said:**
> soy nuevo en ubuntu, me gusto muchisimo quiero migrar a linux para siempre, creo en el sofwarre libre, y estudio ing. civil en informactica...
y quiero su ayuda para consagrarme en ubuntu...
mi problema:

mi problema va en que baje ubuntu 9.04 y decidi iinstalarlo ya que éste reciebe inmediatamente el wifi de todos lados, el asunto va al momento de _bajar_ los programas por "agregar o quitar " y por "gestor de paquetes sinoticos" (o algo asi), me bajo programas, por ej : amsn, y al instalar me tirar errores, me dice que los paquetes estan rotos, voy al gestor de paquetes... para reparar y nada sucede.... formatee de nuevo el pc con ubuntu 9.04, esta ves si se instalo el amsn, pero al bajar JAva u cualqueir otro, en plena instalacion (obiamnete despues de haber bajado los paquetes) me tira error y no puedo seguir instalado ese programa, trato de desintalar completamente los programas rotos para reisntalar, pero el problema sigue.

que pasa?

Tienes configurado tu ubicación como Chile ? quizás hay algún repositorio donde va a buscar algún paquete que por alguna razon esta con problemas. 

Quizas deberías intentar chequear en synaptic la configuración de tus repositorios (Abrir Synaptic->Configuración->Repositorios) y verificar que este marcado Chile como servidor y en caso que hayas agregado algun repositorio de terceros eliminalo y vuelve a actualizar la lista (recargar). Luego puedes intentar una actualización parcial para ver si dpkg/apt logra automáticamente arreglar el problema.

Salu2

---

### Post by blackxored on 2009-06-09
Primero que todo RTFM. 

1. yelp
2. [http://www.ubuntu.com/community](http://www.ubuntu.com/community)

3. Leeme:

Todo parece indicar que no has actualizado tus listas. El software en la mayoria de las distribuciones modernas, y las no tan modernas (como Slackware adoptando este modelo), se maneja en repositorios, dichos repositorios llevan un indice de los paquetes (software si vienes de Windows) existentes en el mismo. Si tienes un indice viejo, es bastante comun que no encuentres determinada version ya que se le hacen revisiones (ej. ubuntu(1++) y actualizaciones (upstream 2.0.1-0ubuntu1 ) por tanto tienes varias opciones. En synaptic marcas recargar es la mas sencilla. 
En una terminal sudo apt-get update -y
Bajo KDE entonces usarias adept. 
Luego que actualizes tus listas marca una actualizacion completa, y luego localiza (si quedaran) los paquetes rotos , bajo el filtro 'Broken'. 

Espero te ayude.

---

### Post by gmunioz on 2009-06-09
Hola bla....:

He aqui una solución drástica:

1- Carga nautilus con permisos temporarios de administrador.

Pulsando: Aplicaciones - Accesorios - Terminal

Ejecutando en la consola que se abre

sudo nautilus

2- En nautilus

a- Presiona control + H, para ver archivos ocultos

b- Navega hasta /var/cache/apt/archives

borra todos los archivos existentes

entra a /var/cache/apt/archives/partial

borra todos los archivos existentes

c- Navega hasta /var/lib/apt/list

borra todos los archivos existentes

entra a /var/lib/apt/list/partial

borra todos los archivos existentes

3- Cierra nautilus

4- Cierra la consola (Terminal)

5- Inicia synaptic (Sistema - Administración - Gestor de paquetes)

a- Pulsa en Configuración - Repositorios - Pestaña software de Ubuntu

Descargar desde: Servidor principal

b) Activa todos los repositorios  menos en actualizaciones proposed y 

backports

c- Acepta 

d- Recarga

Intenta ahora instalar las aplicaciones que necesites.

Saludos.
Gabriel.
[B]Solo doy soporte para Ubuntu - 22 - Mad Karmic & Gnome-shell User.
[/B]

---

### Post by CdK1 on 2009-06-09
En consola:

sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade

Pega los errores que te salgan en consola...

---

### Post by zhelo on 2009-06-09
> **gmunioz said:**
> Hola bla....:

He aqui una solución drástica:

1- Carga nautilus con permisos temporarios de administrador.

Pulsando: Aplicaciones - Accesorios - Terminal

Ejecutando en la consola que se abre

sudo nautilus

2- En nautilus

a- Presiona control + H, para ver archivos ocultos

b- Navega hasta /var/cache/apt/archives


[COLOR=Red]cuando escrito sudo nautilus, me parace una carpeta llama root, y no parace , al apretar control+h como dices, se aparecen carpetas nuevas, pero niuna llamada
var, para poder llegar a donde tu dices (/var/cache/apt/archives)[/COLOR]


> Tienes configurado tu ubicación como Chile ? quizás hay algún repositorio donde va a buscar algún paquete que por alguna razon esta con problemas. 

Quizas deberías intentar chequear en synaptic la configuración de tus repositorios (Abrir Synaptic->Configuración->Repositorios)
[COLOR=Red]en donde decia serivodores.... decia chile, y en la cajita habia una linea =), al paracer si estaba marcada, al recargar
me paraceio esto 
[U]
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 7D2C7A23BF810CD5[/U][/COLOR] 

> sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
[COLOR=Red]al poner sudo apt-get install me salio (solo copie donde decia error):
[U]Leyendo lista de paquetes... Hecho
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 7D2C7A23BF810CD5
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas[/U][/COLOR] 

[COLOR=Red]al pegar
sudo apt-get -f install, lo errores que salieron fueron:[/COLOR]

[COLOR=Red][U]Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  python-utidylib libtidy-0.99-0 python-feedparser python-chardet
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
2 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
Configurando ttf-dejavu-extra (2.28-1) ...
/etc/defoma/hints/ttf-dejavu-extra.hints: Unable to open, or empty.
dpkg: error al procesar ttf-dejavu-extra (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de ttf-dejavu:
 ttf-dejavu depende de ttf-dejavu-extra; sin embargo:
 El paquete `ttf-dejavu-extra' no está configurado todavía.
dpkg: error al procesar ttf-dejavu (--configure):
 problemas de dependencias - se deja sin configurar
No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
                                        Se encontraron errores al procesar:
 ttf-dejavu-extra
 ttf-dejavu
E: Sub-process /usr/bin/dpkg returned an error code (1)[/U]

al poner sudo apt-get upgrade los errores fueron:
[U]
Se utilizarán 0B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Configurando ttf-dejavu-extra (2.28-1) ...
/etc/defoma/hints/ttf-dejavu-extra.hints: Unable to open, or empty.
dpkg: error al procesar ttf-dejavu-extra (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de ttf-dejavu:
 ttf-dejavu depende de ttf-dejavu-extra; sin embargo:
 El paquete `ttf-dejavu-extra' no está configurado todavía.
dpkg: error al procesar ttf-dejavu (--configure):
 problemas de dependencias - se deja sin configurar
No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
                                        Se encontraron errores al procesar:
 ttf-dejavu-extra
 ttf-dejavu
E: Sub-process /usr/bin/dpkg returned an error code (1)[/U][/COLOR]

---

### Post by Carlos C on 2009-06-09
> **blackxored said:**
> Primero que todo RTFM. 

Evita ese tipo de comentarios, van contra el CoC y no están permitidos en este foro.

---

### Post by zhelo on 2009-06-09
> **Carlos C said:**
> Evita ese tipo de comentarios, van contra el CoC y no están permitidos en este foro.
usha ya disculpa weon, si tengo problema con el software libre de linux, y toy deseperado por usarlo

---

### Post by Iced_R on 2009-06-09
Podrías dejar a DPKG que reconfigure tu sistema. la orden sería **sudo dpkg --configure** o algo así. O en su defecto, si cuentas con una conexión a Internet, podrías utilizar la consola de Linux para recuperar condoros (en el GRUB, antes de cargar Ubuntu, abajo de la opción de arranque de Ubuntu hay una opción de una consola, que no recuerdo bien cómo sale escrita, pero sé que está entre el arranque de Ubuntu y el memtest xD). Ahi hay unas opciones interesantes, como el chequeo de tus archivos de sistema y un reconfigurador, que trabaja con DPKG y necesita de una conexión a Internet. Capaz que arregles tu problema (se nota que no leí el post entero? xDD)


Saludos. Si tienes más problemas, avisa, que aquí te ayudaremos entre todos :D

---

### Post by CdK1 on 2009-06-09
Ya, lo haremos bastante rápido..., tú error está en los repositorios y en estos dos packages: 
ttf-dejavu-extra
ttf-dejavu

Así que esto harás:

Antes que todo, no me gusta SUDO, así que logueate como root y ejecuta lo siguiente:

cd /var/lib/dpkg/info
ls | grep ttf-dejavu*

Te debería tirar los dos packages con problemas de la siguiente manera: (busca esos dos)

ttf-dejavu.postinst
ttf-dejavu-extra.postinst

Fijate en la extensión "*.postinst"

Luego, borralos y ejecuta apt-get update && apt-get -f install

Y me pegas lo que salió...

---

### Post by Carlos C on 2009-06-09
> **zhelo said:**
> usha ya disculpa weon, si tengo problema con el software libre de linux, y toy deseperado por usarlo
Tranquilo, el comentario no era para ti, si te fijas, a quien cito es a blackxored. Tu no has infringido ninguna norma o algo por el estilo.

Saludos.

---

### Post by zhelo on 2009-06-09
> **CdK1 said:**
> Ya, lo haremos bastante rápido..., tú error está en los repositorios y en estos dos packages: 
ttf-dejavu-extra
ttf-dejavu

Así que esto harás:

Antes que todo, no me gusta SUDO, así que logueate como root y ejecuta lo siguiente:

cd /var/lib/dpkg/info
ls | grep ttf-dejavu*

Te debería tirar los dos packages con problemas de la siguiente manera: (busca esos dos)

ttf-dejavu.postinst
ttf-dejavu-extra.postinst

Fijate en la extensión "*.postinst"

Luego, borralos y ejecuta apt-get update && apt-get -f install

Y me pegas lo que salió...


como me logueo como boot?,
 y cuando te refieres a ejecuta esto "cd /var/lib/dpkg/info
ls | grep ttf-dejavu*", que quiere decir??
disculpa soy ultra noob para esto

---

### Post by CdK1 on 2009-06-09
como me logueo como boot?,
 y cuando te refieres a ejecuta esto "cd /var/lib/dpkg/info
ls | grep ttf-dejavu*", que quiere decir??
disculpa soy ultra noob para esto

Vamos por pasos:

como me logueo como boot?, ==> Siempre es bueno leer, dije "loguarse como root", root=superusuario

y cuando te refieres a ejecuta esto "cd /var/lib/dpkg/info
 ls | grep ttf-dejavu*", que quiere decir  ==> Es cuando abres una terminal y ejecutas comandos. tipo DOS recuerdas?

Ahora al grano:

1° te recomiendo entrar al canal IRC /server irc.freenode.net #Ubuntu-cl

HAS ESTO:

Abres una terminal, desde Gnome; Aplicaciones ==> Accesorios ==> gnome-terminal

y escribe esto:

cd /var/lib/dpkg/info
sudo rm ttf-dejavu.postinst
sudo ttf-dejavu-extra.postinst
sudo apt-get update
sudo apt-get -f install

Y avisas...

---

### Post by moreback on 2009-06-10
jajaja al final es más fácil usar comando con sudo, te ahorras miles de explicaciones de como logearse como root.

SLd.s

---

### Post by CdK1 on 2009-06-10
Soy de la idea de "loguearse", así es más difícil cometer un error que no quieras... :/

---

### Post by radixs on 2009-06-10
> **moreback said:**
> jajaja al final es más fácil usar comando con sudo, te ahorras miles de explicaciones de como logearse como root.

SLd.s

No son tantas explicaciones, solo basta con tipear en la terminal

sudo bash :-D

---

### Post by augias on 2009-06-10
A nadie le parecio rara esta linea de error? 

> **zhelo said:**
> 
[COLOR=Red]en donde decia serivodores.... decia chile, y en la cajita habia una linea =), al paracer si estaba marcada, al recargar me paraceio esto 
[U]
W: **Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release** Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 7D2C7A23BF810CD5[/U][/COLOR]

Hace referencia a hardy, la version 8.04, mientras que en su primer post especifica que instaló la versión 9.04. 

zhelo: puedes constatar que instalaste la version 9.04 (jaunty)? Si es asi, ¿puedes mostrarnos el contenido de el archivo sources.lst? 

tipea ```
gedit /etc/apt/sources.list

```
y copia y pega lo que dice ese archivo porfa, eso me tiene perplejo.

---

### Post by zhelo on 2009-06-10
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

### Post by zhelo on 2009-06-10
> **gmunioz said:**
> Hola bla....:

He aqui una solución drástica:

1- Carga nautilus con permisos temporarios de administrador.

Pulsando: Aplicaciones - Accesorios - Terminal

Ejecutando en la consola que se abre

sudo nautilus

2- En nautilus

a- Presiona control + H, para ver archivos ocultos

b- Navega hasta /var/cache/apt/archives

borra todos los archivos existentes

entra a /var/cache/apt/archives/partial

borra todos los archivos existentes

c- Navega hasta /var/lib/apt/list

borra todos los archivos existentes

entra a /var/lib/apt/list/partial

borra todos los archivos existentes

3- Cierra nautilus

4- Cierra la consola (Terminal)

5- Inicia synaptic (Sistema - Administración - Gestor de paquetes)

a- Pulsa en Configuración - Repositorios - Pestaña software de Ubuntu

Descargar desde: Servidor principal

b) Activa todos los repositorios  menos en actualizaciones proposed y 

backports

c- Acepta 

d- Recarga

Intenta ahora instalar las aplicaciones que necesites.

Saludos.
Gabriel.
[B]Solo doy soporte para Ubuntu - 22 - Mad Karmic & Gnome-shell User.
[/B]
[COLOR=Red]hice ahora lo que dices, pero al recargar me sale esto:


El repositorio puede no estar disponible, o no se ha podido conectar con él debido a algún problema con la red. Si está disponible, se usará una versión anterior del índice erróneo. En caso contrario, el repositorio será ignorado. Compruebe la conexión de su red y verifique que la dirección del repositorio en las preferencias es la correcta.
[U]Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2)  El subproceso bzip2 devolvió un código de error (2)
Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.[/U]



[/COLOR]

---

### Post by augias on 2009-06-10
> **zhelo said:**
> 

# deb [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://cl.archive.ubuntu.com/ubuntu/](http://cl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse


# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner



prueba borrar los # en esas cuatro lineas. esta vez para tener derechos a editar el documento, tendras que escribir: ```
sudo gedit /etc/apt/sources.list
```

cuando hayas guardado los cambios, cierralo, abre una consola y tipea ```
sudo apt-get update
```
y prueba instalar tus programas. 


pd: A mi me pasó que no podia instalar X paquete porque se instaló mal. lo que tuve que hacer era buscar esos paquetes en synaptic y elegir "eliminar completamente" y aplicar. luego me dejo instalar y updatear ok. Ojala estos tips puedan ayudarte, pero no estoy 100% seguro de entender el problema. 

Suerte!

---

### Post by zhelo on 2009-06-10
no no se arreglo nada =/
lo que me da rabia es este paquete 
[COLOR=Red][U]ttf-dejavu-extra
[COLOR=Black]que ni siquiera lo puedo eliminar por que em tira erro al desibtalar completamente[/COLOR]
[/U][/COLOR]

---

### Post by gmunioz on 2009-06-10
Hola zhe...:

1- He abierto en el navegador la dirección:

```
http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2
```

Y esta disponible actualmente, asi que si intentas nuevamente debe 

poder descargar si problemas.

2- Si te aparece error del paquete:

```
ttf-dejavu-extra
```

 Despues de haber realizado todos los pasos que te indiqué, el problema

es un poco mas complicado.

Existe un archivo indispensable, cuya pérdida te puede inutilizar el

sistema y es:

```
/var/lib/dpkg/status
```

En el se registra, tal como lo sugiere su nombre, el status de todos 

los paquetes del sistema.

Para intentar solucionar tu problema, sin arruinar el sistema:

a- Haz una copia de repaldo del archivo, en una consola 

(aplicaciones - accesorios - terminal) ejecutas:

```
sudo cp /var/lib/dpkg/status status.res
```

b- Edita el archivo, en la misma consola ejecutas:

```
sudo gedit /var/lib/dpkg/status
```

Buscas en el archivo las líneas que comienzan con:

```
Package: ttf-dejavu-extra
```

Que comprenden más o menos todas estas:

```
Package: ttf-dejavu-extra
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 5760
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ttf-dejavu
Version: 2.28-1
Replaces: ttf-dejavu (<< 2.20-1)
Depends: defoma, ttf-dejavu-core
Conflicts: ttf-dejavu (<< 2.20-1)
Conffiles:
 /etc/defoma/hints/ttf-dejavu-extra.hints 9fbbd17b12739f999000c9d34ad8eddd
Description: Vera font family derivate with additional characters
 DejaVu provides an expanded version of the Vera font family aiming for
 quality and broader Unicode coverage while retaining the original Vera
 style. DejaVu currently works towards conformance with the Multilingual
 European Standards (MES-1 and MES-2) for Unicode coverage. The DejaVu
 fonts provide serif, sans and monospaced variants.
 .
 This package includes additional variants, such as oblique, italic,
 bold-oblique, bold-italic and the condensed forms.
 .
 DejaVu fonts are intended for use on low-resolution devices (mainly
 computer screens) but can be used in printing as well.
Original-Maintainer: Debian Fonts Task Force <pkg-fonts-devel@lists.alioth.debian.org>
Homepage: http://dejavu.sourceforge.net/

```

Seguramente esta línea:

```
Status: install ok installed
```

No dice eso.

c- Tienes dos opciones:

Borras todas estas líneas, y el paquete no figurará.

O cambias la línea para que quede como la del ejemplo 

y el paquete figurará como instalado sin estarlo, elige

la que mas te parezca adecuada.

Guarda el archivo, cierra gedit, cierra la consola, 

y en teoria el error tendría que haber desaparecido.

Ante cualquier error fatal, como borrar todo el contenido

del archivo, ejecutando en consola:

```
sudo cp /var/lib/dpkg/status.res status
```

Recuperas el archivo original.

---

### Post by zhelo on 2009-06-10
niun prblema con lo que dices, lo hize y too bien 

trate de bajar el jdk de sun, y me salio esto

> E: /var/cache/apt/archives/ttf-wqy-zenhei_0.8.34-cvs20081027-0ubuntu1_all.deb: lectura insuficiente en buffer_copy (error en dpkg-deb durante `./usr/share/fonts/truetype/wqy/wqy-zenhei.ttc')
E: /var/cache/apt/archives/openjdk-6-jre-lib_6b14-1.4.1-0ubuntu7_all.deb: lectura insuficiente en buffer_copy (error en dpkg-deb durante `./usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar')
E: /var/cache/apt/archives/libaccess-bridge-java_1.24.0-0ubuntu2_all.deb: sistema de ficheros del archivo tar dañado - archivo de paquete dañado
E: /var/cache/apt/archives/icedtea-6-jre-cacao_6b14-1.4.1-0ubuntu7_i386.deb: sistema de ficheros del archivo tar dañado - archivo de paquete dañado

no se que onda... siempre me sale error en los paquetes
ya no se que asm hacer

---

### Post by gmunioz on 2009-06-10
Hola zhe...:

Esos mensajes de error, corresponden a fallas en los paquetes

de las aplicaciones.

O estan mal construidos o se han descargado mal o se han 

copiado mal.

Prueba instalar otros paquetes, de poco tamaño.

Si se instalan bien es problema de los paquetes.

Si todos tienen problemas, es algo en tu ordenador

memorias ram, excesivo overlock calentamiento por deficiencia

de los coolers, etc. etc., que impiden la copia correcta de los

archivos.

---

### Post by CdK1 on 2009-06-10
Otra manera es borrarlos y volver a usar apt-get, ejemplo:

rm /var/cache/apt/archives/ttf-wqy-zenhei_0.8.34-cvs20081027-0ubuntu1_all.deb

Y así con los que te da error...

---

### Post by zhelo on 2009-06-10
> **gmunioz said:**
> Hola zhe...:

Esos mensajes de error, corresponden a fallas en los paquetes

de las aplicaciones.

O estan mal construidos o se han descargado mal o se han 

copiado mal.

Prueba instalar otros paquetes, de poco tamaño.

Si se instalan bien es problema de los paquetes.

Si todos tienen problemas, es algo en tu ordenador

memorias ram, excesivo overlock calentamiento por deficiencia

de los coolers, etc. etc., que impiden la copia correcta de los

archivos.

trate de instalar amarok me tiro error
trate de instalar otra wea, chica y se instalo...
jdk de nuevo y error ¬¬

---

### Post by kamus on 2009-06-10
> **CdK1 said:**
> Otra manera es borrarlos y volver a usar apt-get, ejemplo:

rm /var/cache/apt/archives/ttf-wqy-zenhei_0.8.34-cvs20081027-0ubuntu1_all.deb

Y así con los que te da error...

apt-get clean

Limpia todo el cache de los paquetes descargados ;)

---

### Post by Patriciologico on 2009-06-11
> **moreback said:**
> jajaja al final es más fácil usar comando con sudo, te ahorras miles de explicaciones de como logearse como root.

SLd.s

De acuerdo contigo. No solo es mas facil usarlo (en Ubuntu que viene activado)

Sino va en contra del código de conducta del foro. Las idea es seguir la filosofía de Ubuntu en las respuestas (hacelo facil) y no pedir que el recien iniciado lo haga como a nosotros nos gusta. ¿es sensato pedir compilar una aplicacion cuando se puede usar synaptic?

> **CdK1 said:**
> 

Así que esto harás:

Antes que todo, no me gusta SUDO, así que logueate como root y ejecuta lo siguiente:




Pedir usar root (como ordenaste) complica innecesariamente la solucion al problema original, ya que root no esta activado, y eso suma un problema mas a la persona que esta aprendiendo.

Saludos

---

### Post by zhelo on 2009-06-11
usha será que uso un ubutnu de 32 bits y no de 64 (ya que la arquitecura de  mi note es de 64 bits) pero en windows el de 32 me corre bien

---

### Post by augias on 2009-06-11
yo ocupe ubuntu 32 bits por un año y medio antes de instalar 64 bits. no es un problema.

---

### Post by zhelo on 2009-06-11
entonces cual será el problema ???

a uds les pasa eso que cuando bajan programas se les instalan mal?
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
he instalado 5 programas sin error :O

---

### Post by kamus on 2009-06-11
> **zhelo said:**
> entonces cual será el problema ???

a uds les pasa eso que cuando bajan programas se les instalan mal?
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
he instalado 5 programas sin error :O

Nop , no me pasa .

Estimado no te sale mas facil en estos momentos reinstalar ubuntu para partir todo bien desde una instalacion limpia? 

Salu2

---

### Post by CdK1 on 2009-06-11
> **Patriciologico said:**
> De acuerdo contigo. No solo es mas facil usarlo (en Ubuntu que viene activado)

Sino va en contra del código de conducta del foro. Las idea es seguir la filosofía de Ubuntu en las respuestas (hacelo facil) y no pedir que el recien iniciado lo haga como a nosotros nos gusta. ¿es sensato pedir compilar una aplicacion cuando se puede usar synaptic?




Pedir usar root (como ordenaste) complica innecesariamente la solucion al problema original, ya que root no esta activado, y eso suma un problema mas a la persona que esta aprendiendo.

Saludos

Si no sabe loguearse como root "ahora", que está recieén aprendiendo, tendrá varios problemas más adelante..., esto de "hacelo fácil" puede tener repercuciones, prefiero el "hacelo bien" ;)

---

### Post by zhelo on 2009-06-11
siempre que formateo se me presenta este problema, toy chato de formatear

---

### Post by nopersona on 2009-06-11
> **zhelo said:**
> siempre que formateo se me presenta este problema, toy chato de formatear

Ya has probado cambiar el servidor desde donde se descargan los paquetes? Abres synaptic y configuración>repositorios>software de ubuntu>descargar desde:

Yo recuerdo que antes, allá por feisty, el servidor proncipal me daba muchos problemas similares, o que simplemente no encontraba paquetes, lo cambié por una francés. y cero porblemas. Actualmente uso el servidor Chileno, y jamás he tendio algún problema.

---

### Post by CdK1 on 2009-06-11
Si el servidor no los encuentra, no trata de instalarlos ;), el error es otro...

---

### Post by zhelo on 2009-06-12
no el problema del servidor ya lo vi
ayer me di cuenta _que uso ubuntu para intel sin embago mi tarro es un amd 64x2_

---

### Post by CdK1 on 2009-06-12
Tengo un PC con FreeBSD i386, siendo mi procesador un AMD2 64... y funcina de maravillas...

---

### Post by radixs on 2009-06-12
> **zhelo said:**
> no el problema del servidor ya lo vi
ayer me di cuenta _que uso ubuntu para intel sin embago mi tarro es un amd 64x2_

Yo tambien ocupe ubuntu para 32bits con un AMD x64 y ningun problema.

---

### Post by blackxored on 2009-06-12
Primero sorry por el RTFM ;)

Segundo, mira hazme lo siguiente, por favor:

1. sudo aptitude clean
2. sudo aptitude update -y\
3. Abre Synaptic. -> Custom Filters -> Broken
4. Purge todos los paquetes que te salgan como broken.
5. Marca "Descartar todos los cambios"
6. Cambia de mirror a [http://archive.ubuntu.com](http://archive.ubuntu.com)
7. Actualiza tus listas de nuevo
8. Trata de instalar paso por paso el software que te llevo al error.

En el caso de java como explique, puede ser que hayas marcado la doc y no se haya bajado bien, borrar el archivo postin... y luego veremos. 

Saludos.

EDIT: Si desarrollas con eclipse, tienes varios metodos, pero lo mejor es que vayas a la web oficial para estar un tanto mas actualizado 3.2 por 3.4.

Ademas, para un entorno "realmente" compatible recomiendo sun-java6-jdk en lugar de openjdk. (He tenido algunos fallos al correr en Windows). 
Todo parece indicarme que no se bajaron bien algunos paquetes; por lo que te recomende limpiar el cache, las listas, y actualizarlo todo de nuevo. Rectifico, no creo que sea problema de mirror. Solo asegurate de actualizar antes de instalar nada.

---

### Post by Patriciologico on 2009-06-15
> **CdK1 said:**
> Si no sabe loguearse como root "ahora", que está recieén aprendiendo, tendrá varios problemas más adelante..., esto de "hacelo fácil" puede tener repercuciones, prefiero el "hacelo bien" ;)

Entiendo. El código de conducta no lo escribí yo, pero como decidimos migrar aca, pienso que se han de respetar las reglas de quienes nos alojan.

Saludos!

---

### Post by Jonathan Dud Rodriguez on 2009-06-15
copia tu sources.list

xx@xxx: gedit /etc/apt/sources.list


y copias el contenido del archivo y lo enviaS..

saludos

---

### Post by Psycopatologic on 2009-06-16
> **radixs said:**
> Yo tambien ocupe ubuntu para 32bits con un AMD x64 y ningun problema.

Yo suo ubuntu 64 bits con un AMD64 3000+ y ningun drama, al menos con hardy, con jaunty hay un par de issues que no tengo tiempo de corregir je. Yo prefiero correr la version que corresponda a mi arquitectura por que asi aprovecho al maximo las capacidades de mi pc, ya sea en ram, cpu y aplicaciones. Lo unico malo es que a veces algunas aplicaciones tienen ciertos conflictos por que estan hechos para i386 (32 bits), pero son generalmente juegos como el ePSXe que busca unas librerias de 32 bits que no vienen por defecto pero con todo el software productivo que me interesa no hay problemas.

Jaja eso fue un off-topic =P

Con respecto al error, quizas tu sourcelist esta corrupto, como dice el amigazo de arriba dale

$ sudo gedit /etc/apt/sources.list

y lo pegas

lo otro, yo por lo que lei tienes problemas para instalar con el comando apt-get install osea desde los repositorios, has tratado de instalar programas desde paquetes como por ejemplo con .deb o .tar? 

Con los .deb los bajas directo y los instalas = que en window$ (son equivalentes a los exe), amsn si no me equivoco viene en .deb. Si no le das en el terminal

$ sudo apt-get install build-essential 

si logras instalar, bajate un programa en tar, descomprimes en el desktop y te vas al terminal y pones

$ cd /nombredetupc/home/Desktop/nombredelacarpeta

$ ./configure

$ sudo make

$ sudo make install 

(o los dos juntos $ sudo make && make install )

ojo: fijate que venga un archivo que se llame make y uno que se llame install

trata con eso mientras arreglas lo de los repositorios. Saludos

---

### Post by Carlos C on 2009-06-16
> **Jonathan Dud Rodriguez said:**
> copia tu sources.list

xx@xxx: gedit /etc/apt/sources.list

Hola, la verdad es que eso ya lo hizo, ya copió el contenido de su archivo unas páginas más atrás. Importante leer todo el thread para dar soporte ;)

zhelo, acabo de tener el mismo problema en un computador con el paquete sun-java6-jre. La solución pasó por usar un método un poco extremo:
```
sudo dpkg -r --force-remove-reinstreq sun-java6-jre
```
y en tu lugar preferiría como reemplazo el paquete openjdk-6-jre.

---

### Post by CdK1 on 2009-06-17
man apt-get; man dpkg; eres estudiante de Ing. Informática, no es por ser pesado, pero leer un poco no le hace mal a nadie... 6 páginas para un error de un package... a mi aprecer es un poco "extremo" ;)

---

### Post by zhelo on 2009-06-17
formatee mi pc, le puse ubuntu y tuve otro problema con el paquete, la mejor solucion es desintalar el programa en que viene el paquete
luego en terminal
> sudo nautilus
control+h
y luego irse a la carpeta donde se guardan los pquetes, borrarlos y volver a tratar con el programa

---

### Post by Carlos C on 2009-06-18
¿Significa que finalmente el problema se solucionó?

---

### Post by nopersona on 2009-06-19
U, ya me perdií, en qué va esta novela? :popcorn:

---

### Post by Carlos C on 2009-07-02
Continuando con el tema jeje. Zhelo, creo que puedes tener un problema con tu disco. Lo digo porque hasta ahora siempre tienes problemas a la hora de instalar paquetes, por alguna razón las instalaciones resultan corromperse. No es lo único que puede estar fallando, pero partamos por el disco. Te propongo que utilices las herramientas SMART para monitorear el estado de tu disco. Puedes ver como hacerlo en este enlace:

[http://blockdeubuntu.blogspot.com/2008/07/utilizar-las-utilidades-smart-para.html](http://blockdeubuntu.blogspot.com/2008/07/utilizar-las-utilidades-smart-para.html)

Creo que lo más conveniente es que corras un "long test".

---

### Post by zhelo on 2009-07-02
eso de los paquetes es verdad,..... formatee mi note de nuevo con ubuntu, baje java por terminal... oo bien..... 
baje netbeans por agregar o quitar y error.....
too mal ahora =/.......

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

eso fue lo que paso con lo que diuce el blog que me diste 
> zhelo@querencia:~$ sudo fdisk -l

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf4426658

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6530    52450304    7  HPFS/NTFS
/dev/sda2            6531       14593    64766047+   5  Extendida
/dev/sda5            6531       14258    62075128+  83  Linux
/dev/sda6           14259       14593     2690856   82  Linux swap / Solaris
zhelo@querencia:~$ sudo smartctl -i /dev/sda
sudo: smartctl: command not found
zhelo@querencia:~$  smartctl -i /dev/sda
El programa «smartctl» no está instalado actualmente.  Puede instalarlo escribiendo:
sudo apt-get install smartmontools
bash: smartctl: orden no encontrada
zhelo@querencia:~$ sudo smartctl -i /dev/sda
sudo: smartctl: command not found
zhelo@querencia:~$ 




---

### Post by CdK1 on 2009-07-02
Tengo la idea de que definitivamente es problema de disco... usa smartools para verificarlo...

---

### Post by zhelo on 2009-07-02
> **CdK1 said:**
> Tengo la idea de que definitivamente es problema de disco... usa smartools para verificarlo...

osea que lo bajo??
"sudo apt-get install smartmtools"??

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------


baje netbeans, error en los paquetes........ me fui a sinaptyc, desintale netbeans... no se pudo por error en los paquetes rotos... desintale paquetes rotos.... luego terminal--> sudo nautlis--> y fui al lugar donde se guardan los paquetes y los borre.... luego a "agregar o quitar" bajar netbeans, se bajo sin problemas y se instalo sin problemas..... ahora lo toy usando....
solo de aviso para que ven los sintomas raros de todo esto
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
taba navegando en youtube... y se abre algo que busca codec de sonido .... los baje y una vez instalado.. me cerraron el firefox.. y acada vez que lo abria se cerraba.. reinicie y la barra de inicio y de ventanas se les cambio el tema a uno ordinario, trato de abrir mozilla y se cierra a los 5 sg

---

### Post by Patriciologico on 2009-07-02
Zhelo descuadraste la pagina nuevamnete, editalo por favor.

Saludos

---

### Post by zhelo on 2009-07-02
todo todo lo que habia en mi disco duro, windows linux tooo....
le puse windows primero, luego linux... hasta ahora no he tenido problemas

---

### Post by radixs on 2009-07-02
> **zhelo said:**
> todo todo lo que habia en mi disco duro, windows linux tooo....
le puse windows primero, luego linux... hasta ahora no he tenido problemas

Te refieres a que formateaste todo.. eh instalaste de nuevo???

---

### Post by zhelo on 2009-07-03
> **radixs said:**
> Te refieres a que formateaste todo.. eh instalaste de nuevo???

si

---

### Post by Carlos C on 2009-07-03
> **zhelo said:**
> osea que lo bajo??
"sudo apt-get install smartmtools"??

-----------------------------------------------------------------------------------------------------------------


baje netbeans, error en los paquetes........ me fui a sinaptyc, desintale netbeans... no se pudo por error en los paquetes rotos... desintale paquetes rotos.... luego terminal--> sudo nautlis--> y fui al lugar donde se guardan los paquetes y los borre.... luego a "agregar o quitar" bajar netbeans, se bajo sin problemas y se instalo sin problemas..... ahora lo toy usando....
solo de aviso para que ven los sintomas raros de todo esto
---------------------------------------------------------------------------------------------------------------------------
taba navegando en youtube... y se abre algo que busca codec de sonido .... los baje y una vez instalado.. me cerraron el firefox.. y acada vez que lo abria se cerraba.. reinicie y la barra de inicio y de ventanas se les cambio el tema a uno ordinario, trato de abrir mozilla y se cierra a los 5 sg

Ok, voy a cerrar tus otros threads y dejaremos sólo este abierto. Por favor tienes que empezar a concentrarte o pocos tendrán la intención de ayudarte. Te pido ayuda con lo siguiente:

1. Por favor deja de instalar cosas, si no sabes cuál es el problema, que estés alterando el sistema no ayuda mucho. Deja de instalar programas, por favor.
2. Pon atención a lo que estás haciendo y LEE. Esto es no es broma, si no lees nadie va a querer ayudarte. Un ejemplo, cuando te pongo un enlace para que uses las herramientas smart la idea era que leyeras el contenido, no que copiaras los comandos sin detenerte a pensar lo que haces. ¿Acaso debes instalar el paquete smartmontools? Obviamente sí, lo dice la página que te propuse, además de que obviamente no podrás usar algo que no esté instalado. Por favor, hombre, concentrate.

Ya estimado, instale el paquete, LEA lo que le sugerí y luego postee los resultados.

---

