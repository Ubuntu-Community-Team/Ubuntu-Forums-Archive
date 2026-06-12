---
title: "[SOLUCIONADO] Consulta memoria Ram?"
date: 2009-05-25
forum: Hardware
---

### Post by radixs on 2009-05-25
¿Cuanta es la memoria máxima que soporta ubuntu 9.04 jaunty 32bits?

Actualmente tengo 2GB. de ram instalada en el pc, hoy me puse a mirar en las tiendas por la web y vi que las memorias están bastante baratas como para invertir en el pc.

Mi intención es comprar 2x2 GB 800 MHZ, pero antes quiero saber si ubuntu me soportara 4 GB. de memoria ram (Dual-Channel).

---

### Post by moreback on 2009-05-25
Creo que todo sistema de 32 bits debiera aceptarte como máximo 4GiB de RAM ya que es la máxima cantidad de memoria que se puede direccionar con 32 bits.

Si quieres más ya tendrías que pensar en 64 bits.

Saludos.

---

### Post by guillermolisi on 2009-05-25
> **moreback said:**
> Creo que todo sistema de 32 bits debiera aceptarte como máximo 4GiB de RAM ya que es la máxima cantidad de memoria que se puede direccionar con 32 bits.

Si quieres más ya tendrías que pensar en 64 bits.

Saludos.
Salvo que utilices el kernel de ubuntu-server (que posee otra letencia respecto del desktop) 32 bits que viene preparado para "ver" mas alla de los 4Gb RAM (con el hardware adecuado para 64bits, claro esta). No es lo mismo que usar un kernel de 64 bits pero puede ser una solucion aceptable, segun sea el caso.

---

### Post by kamus on 2009-05-26
> **radixs said:**
> ¿Cuanta es la memoria máxima que soporta ubuntu 9.04 jaunty 32bits?

Actualmente tengo 2GB. de ram instalada en el pc, hoy me puse a mirar en las tiendas por la web y vi que las memorias están bastante baratas como para invertir en el pc.

Mi intención es comprar 2x2 GB 800 MHZ, pero antes quiero saber si ubuntu me soportara 4 GB. de memoria ram (Dual-Channel).

Si van a correr en dual channel es plenamente una característica de tu placa madre, deberás revisar el manual o la documentación para ver si esta soportado y también dependerá de los módulos de memoria que compres (en tiendas locales venden unas Corsair XMS2 pareadas que funcionan en dual channel). Sobre si reconocera los 4GB no debes preocuparte si instalas la distro para AMD64 (64 bits) ya que la arquitectura de 32 bits tiene esa limitación con respecto a la cantidad de memoria instalada en el sistema, si no tendrás que instalar el kernel-server para que reconozca toda tu RAM pero no seria lo optimo para sacarle el maximo rendimiento a tu equipo.

Salu2

---

### Post by radixs on 2009-05-26
Gracias por las respuestas se les agradece al 100%. en conclusiones la memoria máxima que soporta la versión 32 bits es 4GB.

---

### Post by pagondel on 2009-05-28
para saber la cantidad de memoria que soporta tu sistema:

```
sudo dmidecode -t 16 | grep Maximum
```

Saludos!

PD: Llegue tarde, pero nunca esta de mas un comando util xD

---

### Post by 3nG3ndR0 on 2009-05-30
> **pagondel said:**
> para saber la cantidad de memoria que soporta tu sistema:

```
sudo dmidecode -t 16 | grep Maximum
```Saludos!

PD: Llegue tarde, pero nunca esta de mas un comando util xD

buen dato pagondel, pero dicen que la versión 32 bit soporta 4 gb. Con el comando publicado sale esto:

```
Maximum Capacity: 8 GB
```

Solo es para salir bien de la duda.

---

### Post by pagondel on 2009-05-30
Si 3nG3ndR0, esa fue pifia mia... Lo q pasa es que el comando te devuelve la cantidad de memoria soportada por tu computador, no por el sistema operativo ;). Si estas interesado en saber mas acerca dnidecode [Carlos_C](http://blockdeubuntu.blogspot.com/2009/05/usar-dmidecode-para-acceder-la-tabla-de.html) escribio un post bastante completo en su blog ;)

Saludos!

---

### Post by radixs on 2009-05-30
> **pagondel said:**
> Si 3nG3ndR0, esa fue pifia mia... Lo q pasa es que el comando te devuelve la cantidad de memoria soportada por tu computador, no por el sistema operativo ;). Si estas interesado en saber mas acerca dnidecode [Carlos_C]("http://blockdeubuntu.blogspot.com/2009/05/usar-dmidecode-para-acceder-la-tabla-de.html") escribio un post bastante completo en su blog ;)

Saludos!

Gracias por la info...

---

### Post by guillermolisi on 2009-06-01
> **3nG3ndR0 said:**
> buen dato pagondel, pero dicen que la versión 32 bit soporta 4 gb. Con el comando publicado sale esto:

```
Maximum Capacity: 8 GB
```

Solo es para salir bien de la duda.

Con el hardware que tenes y usando el kernel para server podrias direccionar hasta esos 8Gb RAM.

El tema de la latencia pasaria desapercibido si no haces edicion de audio (para esto ultimo es recomendable el kernel de Ubuntu Studio que es real-time, minima latencia).

Para un uso de escritorio comun y corriente y ante la necesidad de usar 8Gb RAM, usar un kernel con algo mas de latencia no hace mucha diferencia.

Con probar no se pierde nada ya que si con ese kernel no te gusta como responde la maquina podes iniciarla con el generic (pero no vas a poder direccionar mas alla de los 4Gb RAM).

---

