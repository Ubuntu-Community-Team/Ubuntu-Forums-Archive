---
title: "crear particion en ubuntu"
date: 2009-06-03
forum: Instalación y Actualización
---

### Post by hiphosama on 2009-06-03
bueno mi consulta es como poder crear una particion en ubuntu 9,04, la situacion es la siguiente, instale ubuntu y lo hice en todo el disco duro, las particiones que tenia las elimine y deje solo un disco para ubuntu.
ahora no quiero eliminar ubuntu, pero quiero crear particiones y cuales son mas convenientes por versatilidad con otros SO.

saludos

---

### Post by Carlos C on 2009-06-03
Se pueden crear más particiones, pero tienes que ser más específico respecto a lo que deseas. Cuando dices que quieres crear otras particiones para otros sistemas ¿qué sistemas serían? ¿te refieres a otras distribuciones de linux o quieres incluir algún sistema microsoft? ¿de cuantos sistemas estamos hablando? Junto con responder esas preguntas, por favor incluye el resultado que obtienes cuando escribes en el terminal:
```
sudo fdisk -l
```
Saludos.

---

### Post by kamus on 2009-06-03
> **hiphosama said:**
> bueno mi consulta es como poder crear una particion en ubuntu 9,04, la situacion es la siguiente, instale ubuntu y lo hice en todo el disco duro, las particiones que tenia las elimine y deje solo un disco para ubuntu.
ahora no quiero eliminar ubuntu, pero quiero crear particiones y cuales son mas convenientes por versatilidad con otros SO.

saludos

Deberias ocupar gparted (apt-get install gparted) para gestionar,redimensionar tu disco de manera facil y rapida. De todas maneras acuerdate que es un riesgo el mover o redimensionar los bloques (respalda tus archivos antes de meter mano a la tabla de particiones!) ;)

---

### Post by hiphosama on 2009-06-03
> **Carlos C said:**
> Se pueden crear más particiones, pero tienes que ser más específico respecto a lo que deseas. Cuando dices que quieres crear otras particiones para otros sistemas ¿qué sistemas serían? ¿te refieres a otras distribuciones de linux o quieres incluir algún sistema microsoft? ¿de cuantos sistemas estamos hablando? Junto con responder esas preguntas, por favor incluye el resultado que obtienes cuando escribes en el terminal:
```
sudo fdisk -l
```Saludos.


esto me aparece
Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x647e647e

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       14243   114406866   83  Linux
/dev/sda2           14244       14593     2811375    5  Extendida
/dev/sda5           14244       14593     2811343+  82  Linux swap / Solaris



y lo de los sistemas son dos xp y otro libre para ir probando, como fedora mandriva u otros ahi vere. el swap es ? y puedo hacer una particion desde es cd de ubuntu justo cuando me pregunta en que particion acupar y poner manual crear una nueva y despues salir, queda la aprticion o se elimina la recien creada. saludos y gracias

---

### Post by hiphosama on 2009-06-03
> **Carlos C said:**
> Se pueden crear más particiones, pero tienes que ser más específico respecto a lo que deseas. Cuando dices que quieres crear otras particiones para otros sistemas ¿qué sistemas serían? ¿te refieres a otras distribuciones de linux o quieres incluir algún sistema microsoft? ¿de cuantos sistemas estamos hablando? Junto con responder esas preguntas, por favor incluye el resultado que obtienes cuando escribes en el terminal:
```
sudo fdisk -l
```Saludos.

> **kamus said:**
> Deberias ocupar gparted (apt-get install gparted) para gestionar,redimensionar tu disco de manera facil y rapida. De todas maneras acuerdate que es un riesgo el mover o redimensionar los bloques (respalda tus archivos antes de meter mano a la tabla de particiones!) ;)


bien lo tengo pero prefiero quiero saber además si puedo ocupar la particion que realizaría al insertar el cd de ubuntu y desde ahi hacer la particion y despues salir sin instalar ubuntu de nuevo, por que porsupuesto ya lo tengo, solo era para crear la particion.
no me quiero poner cuatico pero solo como consulta si creo la particion y sigo adelante tendre dos sistemas ubuntu, misma version 9,04. cosa loca que se me ocurrio sin fin ni uso

---

### Post by Patriciologico on 2009-06-04
Gparted es la misma utilidad que usa el LiveCd. Creo es lo mejor, lo demas es complicarte. Si usas el LiveCd, tienes dos opciones usar el gparted que trae (que viene siendo lo mismo, pero mas trabajoso, ya que iniciaras desde el live y mas lento) la otra es que comiences la instalacion definas particiones y ver el proceso de instalacion, despues que crea las particiones detener el proceso de instalacion, sino quedaras con dos ubuntus, o uno sobreescrito. Esta ultima opcion como te dije es mas complicada y corres el riesgo de corromper el sistema.

Saludos!

---

