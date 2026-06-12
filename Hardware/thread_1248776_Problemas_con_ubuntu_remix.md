---
title: "Problemas con ubuntu remix"
date: 2009-08-24
forum: Hardware
---

### Post by Guillermo 911 on 2009-08-24
Hola me llamo Guillermo y soy completamente nuevo en ubuntu, tengo un problema con mi netbook. Hace un par de días le instalamos con un amigo ubuntu remix a mi acer one, todo bien asta que tratamos de conectarnos a Internet vía wifi. Encontramos una pagina que nos decía q era usual que no reconociera la tarjeta y daba las intrusiones como activarla, el caso es q no se que hacer una vez que introduzco la primera línea en el terminal por q abre otra ventana y no se si debo seguir escribiendo en la nueva ventana o el terminal. He probado escribiendo en la nueva pagina q abre pero al momento de guardar me indica q no me encuentro autorizado y quedo ahí. La línea q pongo en el terminal es:
gedit /etc/modprobe.d/blacklist.conf 

y lo que escribo en la nueva pagina es: 

blacklist ath_pci
blacklist ath_hal
blacklist acer_wmi   

aca dejo el link de la pagina 

[http://www.cesarius.net/activar-tarjeta-inalambrica-en-acer-aspire-one-10-d250-con-ubuntu-netbook-remix-904/](http://www.cesarius.net/activar-tarjeta-inalambrica-en-acer-aspire-one-10-d250-con-ubuntu-netbook-remix-904/)    

espero q me puedan ayudar
saludos 
Guille

---

### Post by gmunioz on 2009-08-24
Hola gui.....:

En principio, te sugiero leas toda la documentación

que encuentres sobre Ubuntu.

Las distribuciones GnuLinux no son más difíciles que

el operativo de Microsoft, son mejores y distintas.

Como referencia, te informo que para hacer modificaciones

en un sistema GnuLinux, debes actuar como administrador,

algunas distribuciones o como usuario con permisos

temporarios de administrador, Ubuntu.

Por consiguiente para activar tu wi-fi debes:

Seguir estos pasos:

Pulsa Aplicaciones - Accesorios - Terminal

En la consola que se abre escribe y pulsa luego enter

[HTML]sudo su[/HTML]

Pon tu contraseña de usuario, no se verá nada en la

consola y pulsa enter.

Luego continua con las ordenes:

[HTML]gedit /etc/modprobe.d/blacklist.conf[/HTML]

Agrega estas líneas:

[HTML]blacklist ath_pci
blacklist ath_hal
blacklist acer_wmi[/HTML]

Guarda el archivo, cierralo y abre:

/etc/modules

Si no lo encuentras cierra gedit y ejecuta:

[HTML]gedit /etc/modules[/HTML]

Agrega la linea:

[HTML]ath5k[/HTML]

Guarda el archivo, cierra gedit

Para instalar el más reciente driver ath5k, ejecuta

en la consola la orden

[HTML]apt-get install linux-backports-modules-jaunty
[/HTML]

Desinstala los módulos que puedan interferir ejecutando:

[HTML]modprobe -r ath5k acer_wmi ath_pci ath_hal[/HTML]

Instala el módulo ath5k mas reciente ejecutando

[HTML]modprobe ath5k[/HTML]

Cierra la consola

Reinicia.

Aclaración, otro procedimiento sería el de ejecutar

cada una de las ordenes anteponiendo sudo, sin ejecutar

previamente sudo su.

---

### Post by Guillermo 911 on 2009-08-25
Hola gmunioz, gracias por la ayuda pero aun no he podido hacer funcionar la targeta. luego de poner la linea: 

apt-get install linux-backports-modules-jaunty

me dice q el paquete no ha sido encontrado, sigui para ver q ocurría y coloque el resto de las lineas pero al reiniciar el netbook sigue sin reconocer la tarjeta wifi.

espero q me puedan ayudar

---

### Post by gmunioz on 2009-08-25
Hola gui...:

Lo que ocurre, es que necesitas estar conectado a

la red, para bajar los paquetes desde el servidor.

En este sitio:

[http://packages.ubuntu.com/search?suite=jaunty&section=all&arch=any&searchon=names&keywords=linux-backports-modules-jaunty](http://packages.ubuntu.com/search?suite=jaunty&section=all&arch=any&searchon=names&keywords=linux-backports-modules-jaunty)

Los encuentras, puedes bajarlos desde otro ordenador

con conexión a Internet, copiarlos a un directorio e

instalarlos con la orden, en consola, estando en el 

directorio donde lo copiaste:

[HTML]sudo dpkg -i *.deb[/HTML]

o mediante:

[HTML]sudo su

dpkg -i *.deb[/HTML]

Los que necesitas son los:

Package linux-backports-modules-jaunty-generic

Desde aqui bajas el paquete para 64 bits amd64

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_amd64.deb)

Desde aqui bajas el paquete de 32 bits i386

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_i386.deb)

---

### Post by Guillermo 911 on 2009-08-25
gmunioz gracias nuevamente, pero a que te refieres con copiarlos en un directorio?? un pendrive? de ser eso como hago para que el computador lo reconozca, he tratado de conectarlo pero no lo reconoce. 

gracias por la ayuda.

Guille

---

### Post by josecuervo86 on 2009-08-25
Con directorio, imagino, se refiere a una carpeta

---

### Post by gmunioz on 2009-08-25
Hola gui...:

Lo que en MsWindows son carpetas, son los directorios.

Puedes trabajar sin problemas en /home/tuusuario/

en mi caso, tengo un directorio (carpeta) 

/home/miusuario/install/ donde copio los archivos

.deb para instalar manualmente mediante dpkg

Si no estas conectado, por falta de conexión

te bajas los paquetes desde otro ordenador, los

copias a un pendrive, insertas el pendrive  en

tu netbook y copias los archivos a la carpeta

que hayas creado. No es conveniente ejecutar dpkg

desde en el pendrive directamente.

Ubuntu debe reconocer el pendrive insertado sin 

problemas. Si no lo hiciera, cargas nautilus, el

navegador de archivos y en la ventana de la izquierda

te aparecerá el pendrive sin montar, con un click o

con la opción del botón derecho lo montas. No olvides

desmontarlo antes de extraerlo.

---

### Post by Guillermo 911 on 2009-08-25
gmunioz disculpa mi ignorancia pero a q te refieres con: 

"copiarlos a un directorio e instalarlos con la orden, en consola, estando en el"

lo que no entiendo es lo de en consola. como en la consola llego a donde esta guardado el archivo ???

copie los archivos en /home/guille/install

gracias

---

### Post by josecuervo86 on 2009-08-26
te manejas de esta manera:

```
cd Directorio X/Directorio Y/Directorio donde esta el archivo
```

-Home
----Directorio X
--------Directorio Y
------------Directorio donde esta el archivo

En el ejemplo "Directorio donde esta el arcivo" se encuentra dentro del "Directorio Y", que a su vez, esta dentro del "Directorio X" y este ultimo esta en tu Home
Espero que te haya quedado claro

---

### Post by Guillermo 911 on 2009-08-26
hola, primero dar las gracias por la paciencia q han tenido.

he seguido lo que me han dicho y por fin logre instalar el paquete q me falataba pero me lanza este error 

dpkg: problemas de dependencias impiden la configuración de linux-backports-modules-2.6.28-15-generic:
 linux-backports-modules-2.6.28-15-generic depende de linux-image-2.6.28-15-generic; sin embargo:
  El paquete `linux-image-2.6.28-15-generic' no está instalado.
dpkg: error al procesar linux-backports-modules-2.6.28-15-generic (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 linux-backports-modules-2.6.28-15-generic

puede q se deba a q trate de instalar el paquete de 64 bits???

que puedo hacer ??

---

### Post by gmunioz on 2009-08-27
Hola:

De aqui bajas el paquete que te falta:

[http://packages.ubuntu.com/jaunty/linux-image-2.6.28-15-generic](http://packages.ubuntu.com/jaunty/linux-image-2.6.28-15-generic)

Tanto este como el anterior debe responder al sistema original

instalado:

[HTML]....i_386  para 32 bits

----amd64  para 64 bits[/HTML]

Pones los dos paquetes juntos y los instalas con la misma orden

[HTML]sudo dpkg -i *.deb[/HTML]

---

### Post by Guillermo 911 on 2009-08-27
hola 
nuevamente 

instale el nuevo paquete junto con el anterior pero al momento de escribir la linea: 

apt-get install linux-backports-modules-jaunty

me sigue diciendo que no encontró el paquete linux-backports-modules-jaunty

otra cosa que me llama la atencion que al poner las linieas que me abrian otro archivo para escribir las lineas 

blacklist ath_pci
blacklist ath_hal
blacklist acer_wmi  

y

ath5k

ya están, influye eso en algo???

saludos y gracias por la ayuda
Guille

---

### Post by gmunioz on 2009-08-28
Hola gui....:

1- apt-get, instala paquetes desde los repositorios,

de internet, de una red local o del ordenador, los

repositorios son directorios (carpetas) con subdirec-

torios conteniendo paquetes, y con una serie de archivos

indice que le indican, a apt-get, todos los paquetes que

requieren ser instalados para que una aplicación

determinada funcione.

El listado de repositorios se encuentra en el archivo

/etc/apt/sources.list.

Como no estas aun conectado, ni tienes un repositorio local,

naturalmente, apt-get te informa que no puede encontrar el 

paquete mencionado.

Si recorres y relees tu post, veras que has bajado ya esos

paquetes y los has instalado mediante dpkg 

2- dpkg, es la aplicación que te permite instalar los

paquetes .deb, descargados en forma manual de los 

repositorios o de sitios de desarrollo y alojados en un

directorio (carpeta) de tu ordenador.

Conclusión: los paquetes estan instalados, tu dispositivo

tendría que estar reconocido, debes leer acerca de como

ponerlo en funcionamiento.

---

### Post by Guillermo 911 on 2009-08-28
gracias Gabriel, te pasaste 


saludos 

Guille

---

### Post by V3rity on 2009-11-17
> **gmunioz said:**
> Hola gui...:

Lo que ocurre, es que necesitas estar conectado a

la red, para bajar los paquetes desde el servidor.

En este sitio:

[http://packages.ubuntu.com/search?suite=jaunty&section=all&arch=any&searchon=names&keywords=linux-backports-modules-jaunty](http://packages.ubuntu.com/search?suite=jaunty&section=all&arch=any&searchon=names&keywords=linux-backports-modules-jaunty)

Los encuentras, puedes bajarlos desde otro ordenador

con conexión a Internet, copiarlos a un directorio e

instalarlos con la orden, en consola, estando en el 

directorio donde lo copiaste:

[HTML]sudo dpkg -i *.deb[/HTML]

o mediante:

[HTML]sudo su

dpkg -i *.deb[/HTML]

Los que necesitas son los:

Package linux-backports-modules-jaunty-generic

Desde aqui bajas el paquete para 64 bits amd64

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_amd64.deb)

Desde aqui bajas el paquete de 32 bits i386

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_i386.deb)
Hola! tambien soy nueva en Linux, pero tengo el mismo problema, sigo todas estas instrucciones y el tutorial que aparece en cesarius y nada, no logro ver la parte de red inalambrica en mi acer aspireone. Me dijeron que instalara el "madwifi" y lo hice por synaptic y nada... Alguna otra idea?
Gracias!

---

