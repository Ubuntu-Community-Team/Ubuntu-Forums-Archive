---
title: "problema con dependencia al actulizar"
date: 2010-02-11
forum: Instalación y Actualización
---

### Post by 3nG3ndR0 on 2010-02-11
hola actulize a kde 4.4 y no me deja instalar esta actualización esta retenida: **kipi-plugins **

```
ariel@ariel-desktop:~$ sudo aptitude full-upgrade
Leyendo lista de paquetes... Hecho               
Creando árbol de dependencias                    
Leyendo la información de estado... Hecho        
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho 
Los siguientes paquetes están ROTOS:             
  kipi-plugins                                   
Se instalarán los siguiente paquetes NUEVOS:     
  libcv1{a} libcvaux1{a} libhighgui1{a}          
1 paquetes actualizados, 3 nuevos instalados, 0 para eliminar y 0 sin actualizar.                                                                               
Necesito descargar 7311kB de ficheros. Después de desempaquetar se usarán 5280kB.                                                                               
No se satisfacen las dependencias de los siguientes paquetes:                   
  kipi-plugins: Depende: libkdcraw7 (>= 4:4.3.5) pero no es instalable          
                Depende: libkipi6 (>= 4:4.3.5) pero no es instalable            
Las acciones siguientes resolverán estas dependencias                           

Mantener los paquetes siguientes en la versión actual:
kipi-plugins [1.0.0-1ubuntu1~karmic1+ppa1 (karmic, now)]

La puntuación es 120

¿Acepta esta solución? [Y/n/q/?] 
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 1 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
¿Quiere continuar? [Y/n/?]
Escribiendo información de estado extendido... Hecho
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido
Inicializando el estado de los paquetes... Hecho

ariel@ariel-desktop:~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido
Inicializando el estado de los paquetes... Hecho
Se han retenido los siguientes paquetes:
  kipi-plugins
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 1 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido
Inicializando el estado de los paquetes... Hecho

```alguna idea de como solucionar esto porfa.

---

### Post by moreback on 2010-02-13
Desactiva el ppa al que pertenece ese paquete kipi-plugins.

Sistema -> Administración -> Orígenes del software

---

