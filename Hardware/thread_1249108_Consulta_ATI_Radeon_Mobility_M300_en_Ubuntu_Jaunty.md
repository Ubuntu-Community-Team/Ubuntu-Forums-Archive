---
title: "Consulta ATI Radeon Mobility M300 en Ubuntu Jaunty 9.04"
date: 2009-08-24
forum: Hardware
---

### Post by tatadeluxe on 2009-08-24
Una persona me envió una consulta, pues había instalado la versión 9.04 de Ubuntu, y en general le ha gustado bastante, el único problema que he tenido es con la tarjeta de vídeo. Tengo un Dell Inspiton 9300, y la tarjeta es ATI Radeon Mobility M300 (M22).
En general los efectos 3D del escritorio andan bien, pero cuando quiero ver una pelicula, la cosa se pone mal... la pelicula se "tupe" entera, se para cada 5 minutos... una lata.

Le solicitamos los siguientes datos:
# Descarga el Script video y Ejecuta el Script video
$ wget [http://www.cec.uchile.cl/~jrovegno/download/video](http://www.cec.uchile.cl/~jrovegno/download/video) && sh video

Con esto es posible detectar el origen del posible problema y analizar si es mejor utilizar el driver propietario(fglrx) o el libre( ati, radeon)

---

### Post by CdK1 on 2009-08-26
Antes que todo, que reprodutor usas? te recomiendo usae mplayer desde la consola:

mplayer archivo.avi y ve que tira...

---

### Post by Patriciologico on 2009-08-31
> **CdK1 said:**
> Antes que todo, que reprodutor usas? te recomiendo usae mplayer desde la consola:

mplayer archivo.avi y ve que tira...


Tata nos presenta un problema, y la forma de actuar ante el para tener la informacion necesaria, ahora solo falta que la persona del problema de sus resultados.

Saludos!

---

### Post by tatadeluxe on 2009-08-31
Dado que el driver de video libre (radeon) le generaba problemas de inestabilidad en Jaunty, instaló el driver privativo (fglrx)
No tengo claro el método que utilizó para instalar el driver privativo, pero el método recomendado es:
> Anda en el menú del panel a : Sitema > Administración > Controladores
de Hardware
Habilita el controlador privativo ATI
Tendrás que tener acceso a internet pues descargará el driver, lo
instalará y después al reiniciar se cargará el nuevo controlador
automáticamente.

La persona después de instalar el driver privativo, obtuvo al iniciar las X en Jaunty una pantalla negra.

Para simplificar las cosas, volvió a instalar la versión Ubuntu Hardy, la cual instala un driver de video por defecto que funciona sin problemas.

Saludos

---

