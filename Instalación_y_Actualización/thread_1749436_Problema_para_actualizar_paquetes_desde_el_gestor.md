---
title: "Problema para actualizar paquetes desde el gestor"
date: 2011-05-04
forum: Instalación y Actualización
---

### Post by Aidalee on 2011-05-04
[FONT=Comic Sans MS]Hola soy nueva en ubuntu por q a mi jefe se le ocurrio instalar este nuevo sistema, cuando lo vi me parecio muy muy hermoso, pero con el paso de los dias algunas cositas me tienen al cojer la loma. Resulta q hace mas de 15 dias estoy tratando de actualizar y cuando lo estoy actualizando me sale este error que e visto que a muchos le ha pasado errores parecidos pero como este no he encontrado. Ah tengo la version 9.04
[B]Esto es lo que sale en el gestor de actualizaciones:
[/B]
No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_karmic-security_main_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

**Y entrando al gestor de paquetes me sale este parecido error:**
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_karmic-security_main_binary-i386_Packages
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report.

Por Dios estoy desesperada, no puedo ver videos, ni algunas fotos, nada de nada. No puedo descargar nada por q me da error, ni siquiera escuchar musica, nada nadaaaaaaaaaa... :???::cry: Ayuda porfissssss!
Gracias de antemano y espero me den una solucion!

Ah Saluditos desde Rep Dominicana!:biggrin:

Saludos[/FONT]

---

### Post by RafaelG on 2011-05-04
[SIZE=2][COLOR=Navy]Aidalee,

Bienvenida a el Forum Ubuntu, a continuacion dejo Link con ayuda para poder entender la división que utilizamos para ingresar nuevos Post en el forum:[/COLOR][/SIZE][SIZE=2]
[/SIZE] 
[SIZE=2][http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)[/SIZE]

[SIZE=2][COLOR=Navy]También te pido que leas las normas que intentamos aplicar en el foro para que tu experiencia en el mismo sea más efectiva:[/COLOR][/SIZE]
[SIZE=2]
[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)[/SIZE] 

------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[SIZE=2]En referencia a tu inconveniente verifica si ejecutando los siguientes comandos desde una terminal se soluciona el problema.

Intenta primero:[/SIZE] [SIZE=2]
```
sudo dpkg --configure -a
```Luego:
```
sudo apt-get update
```Para terminar:
```
sudo apt-get upgrade
```Saludos cordiales,[/SIZE]

---

### Post by bichopro on 2011-05-04
El principal problema es que la versión del sistema es muy antigua, una vez que tengas la ultima versión no deberías tener ningún inconveniente. Sigue los pasos de arriba (terminal es una aplicación que encuentras en el menú)

---

### Post by Aidalee on 2011-05-05
Infinitas gracias, justo ayer en la noche vino el chico q habia instalado Ubuntu y arreglo el problema, ya puedo escuchar mucsica, ver videos y demas!

Lo de la terminal ya lo habia hecho y no me habia resultado. 

Pero gracias de todas maneras!

---

