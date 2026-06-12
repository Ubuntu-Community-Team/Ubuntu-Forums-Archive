---
title: "Problema google earth en ubuntu 11.04"
date: 2011-06-16
forum: Instalación y Actualización
---

### Post by flakojaime on 2011-06-16
Sres

Estoy con un pequeño problema. 

Se me ocurrio instalar el google earth en mi flamante 11.04 con unity y al final de la instalacion me sale esto:

[B]installArchives() failed: Configurando install-info (4.13a.dfsg.1-6ubuntu3) ... 
/etc/environment: lnea 2: UNITY_FORCE_START: orden no encontrada 
dpkg: error al procesar install-info (--configure): 
 el subproceso instalado el script post-installation devolvi el cdigo de salida de error 127 
Se encontraron errores al procesar: 
 install-info 
Configurando install-info (4.13a.dfsg.1-6ubuntu3) ... 
/etc/environment: lnea 2: UNITY_FORCE_START: orden no encontrada 
dpkg: error al procesar install-info (--configure): 
 el subproceso instalado el script post-installation devolvi el cdigo de salida de error 127 [/B]

Intente desinstalar y no he podido, incluso con el  paquete de limpieza. Me dice que esta siendo usado por sinaptics.

Revise por el google y nada me resulta.

Lo peor de todo es que ahora no me deja actualizar ni instalar programas ni paquetes nuevos.

Agradezco sus recomendaciones.

saludos!!:)

---

### Post by RafaelG on 2011-06-16
Flakojaime;

Podrias probar con estos comandos:

Intenta:
```
sudo dpkg --configure -a
```Luego:
```
sudo apt-get update
```Terminar:
```
sudo apt-get upgrade
```Nos avisas como te fue por favor.

Saludos cordiales,

---

### Post by flakojaime on 2011-06-16
Hola Rafael.[B]


[COLOR=Blue]root@XPS1730:~# sudo dpkg --configure -a[/COLOR][/B]
[B]Configurando install-info (4.13a.dfsg.1-6ubuntu3) ...
/etc/environment: línea 2: UNITY_FORCE_START: orden no encontrada
dpkg: error al procesar install-info (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 127
Se encontraron errores al procesar:
 install-info[/B]


[COLOR=Blue]**root@XPS1730:~# sudo apt-get upgrade**[/COLOR]
[B]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se actualizarán los siguientes paquetes:
  flashplugin-installer libxml2 libxml2-utils python-libxml2
  xserver-xorg-input-synaptics
5 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se necesita descargar 972 kB/1049 kB de archivos.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Des:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main libxml2 i386 2.7.8.dfsg-2ubuntu0.1 [607 kB]
Des:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main libxml2-utils i386 2.7.8.dfsg-2ubuntu0.1 [78,0 kB]
Des:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security/main python-libxml2 i386 2.7.8.dfsg-2ubuntu0.1 [287 kB]
Descargados 972 kB en 29seg. (32,5 kB/s)                                       
Preconfigurando paquetes ...
Configurando install-info (4.13a.dfsg.1-6ubuntu3) ...
/etc/environment: línea 2: UNITY_FORCE_START: orden no encontrada
dpkg: error al procesar install-info (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 127
Se encontraron errores al procesar:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/B]
Este fue el resultado de los comandos.


1 Edit:

Solucion encontrada [aqui]("http://hatteras.wordpress.com/2008/07/23/error-127-en-synaptic-solucionado/")
**Ejecutando en una terminal en modo root el comando:  [COLOR=Blue]apt-get remove &#8220;nombre-del-paquete&#8221;[/COLOR]**

apt-get remove install-info

luego:

$ sudo apt-get update
$ sudo apt-get upgrade

Ahora lo que me queda por averiguar, de donde o a que pertenecía el "install-info"


Gracias !!!!!

---

