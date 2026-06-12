---
title: "Capturar video por puerto firewire"
date: 2010-01-29
forum: Hardware
---

### Post by aledruetta on 2010-01-29
Hola Comunidad!

Tengo una videofilmadora Sony DCR-TRV530 NTSC que graba en formato Digital8. La salida de video es por medio de un puerto firewire IEEE 1394. Quiero capturar lo que tengo filmado en Ubuntu Karmic. He probado con Kino y Kdenlive, hasta ahora no he conseguido ningún resultado.

Ninguna de las dos aplicaciones reconocen que la cámara esté conectada. Seguí las instrucciones que encontré googleando, como: 
verificar que el paquete dvgrab esté instalado;
cargar el módulo 
```
sudo modprobe raw1394
```
permitir que se use el archivo de configuración 
```
sudo chmod o+rw /dev/raw1394
```
abrir Kino con sudo en consola
```
sudo kino
```
y dar play desde la cámara. Pero no tuve suerte.

¿Alguien tiene alguna sugerencia o experiencia al respecto?

Muchas gracias,
Alejandro.

---

