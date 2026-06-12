---
title: "Problemas laptop HDD en Hardy, ganas de volver a GG"
date: 2008-06-04
forum: Hardware
---

### Post by sergiom99 on 2008-06-04
Hola gente,
les cuento q estoy MUY preocupado. Ayer descubri [**este thread**]("http://ubuntuforums.org/showthread.php?t=805570") [1] en el subforo de laptops sobre un bug que mata los discos rigidos antes de tiempo. No termino de entender si estoy afectado y como arreglarlo definitivamente.
Si alguno mas experimentado puede mirarlo y darme una opinion lo agradezco mucho. (al pie dejo el output del diagnostico)

Por otro lado, el reciente upgrade a HH desde GG, "rompio" unas cuantas cosas (compiz/emerald/themes, el poweroff/reboot desde Kmenu, algun otro seteo/programa) y cada vez que hago updates y baja un nuevo kernel, HH anda peor.
Asi que no se si hacer una instalacion de cero de HH o bien volver a GG, tambien de cero.

El tema del disco me preocupa mucho, Uds saben que no es facil adquirir una laptop y/o sus repuestos, asi que ver acortado el tiempo de vida del disco no me hace gracia. Hasta volveria a XP (desde donde estoy escribiendo ahora) si no pudiera controlarlo en Ubuntu. Prefiero ponerlo en la desktop y luchar para que mi vieja lo use que quemar el disco.
Perdon si fue largo o si parece extremista, pero la verdad desde que empezo a andar mal, cuando antes andaba barbaro y desde que vi lo de los HDD que estoy bajoneado con Ubuntu en la notebook.
Un saludo para todos-- Sergio

```
**Disco: TOSHIBA MK1637GSX HDD.**
Tue Jun  3 21:13:23 ART 2008
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       16607
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       36 (Lifetime Min/Max 13/51)
sergio@kubuntu:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Tue Jun  3 22:24:28 ART 2008
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       16725
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       37 (Lifetime Min/Max 13/51)

``` Aprox 100-110 load_cycles /hora
```
My system:
Kubuntu HH
2.6.24-17-generic i686 kernel
KDE 3.5.9
Qt 3.3.8b
```

[1] [**[1] **]("http://ubuntuforums.org/showthread.php?t=805570")

---

### Post by anarko on 2008-06-04
Yo no confiaria que windows tenga en cuenta ese tipo de cosas.... no lo hace con los USB, tienen el "mismo" problema, tienen una cierta cantidad de escrituras y windows escribe todo el tiempo en los pendrives, asesinandolos cruelmente, linux en cambio cachea y solo escribe cuando el pendrive es desmontado.
Fijate en lo que dicen en el thread de la solucion al problema [[link]]("http://ubuntuforums.org/showpost.php?p=5031046&postcount=3") que saques la cuenta de cuantos load cicles tenes por dia y veas si afecta a ese estimativo de 600.000, aunque lo hacen para 3 años, aca en argentina 3 años para una notebook es muy poco para lo caras que son ellos las cambian cada 1 o 2.

---

### Post by faktorqm on 2008-06-05
No te persigas men, si nos ponemos paranoicos vamos mal! Hay muchas cosas de hardware que son solo compatibles con windows, como el famoso frecuency scaling en micros AMD, lo que nombras vos, lo que nombra aca anarko de los pendrive's, son todas realidades que aparecen todo el tiempo. Los pendrive's tienen 15000 errores de escritura, y siempre la unica solucion es formtearlos.... Al contrario de lo que piensa la mayoria de la gente, es mejor escribir 500mb de un saque en un pendrive, y no escribir 1mb, largar, escribir, largar, ¡¡500 veces!!
Yo sinceramente, lo que haria en tu caso, es no preocuparme, este problema no es nuevo, ya tiene muchos años y no lo pueden solucionar, los discos rigidos lamentablemente son el peor dispositivo de la pc, es el mas mecanico y el mas lento y a su vez el mas importante, por que es el encargado de guardar tus datos.... asi que todo mal! jajajaj
Saca las cuentas del periodo de vida estimado por el fabricante, y cuanto te puede llegar a durar a vos, y despues busca a ver cuanto le duro a uno con windows, y vas a ver que es lo mismo o la diferencia es despreciable.
Salu2!

---

### Post by sergiom99 on 2008-06-05
gracias a ambos por su respuesta.
Es cierto lo que dice anarko del precio, eso es mi preocupacion.
Los pendrive, tal vez no sea tan asi, yo tengo un U3 de 2gb que corro el thunderbird todo el dia, desde hace 2 años y se la banca (por suerte).


Con respecto a reinstalar, que me conviene: Fresh install de HH o GG?
GG anduvo perfecto hasta el upgrade. Pero no tengo ganas de probar si un fresh install de HH tambien anda bien o no para despues volver.

---

### Post by faktorqm on 2008-06-05
Al menos a mi me sirvió mas HH. GG me parecio un desastre, te digo, me dio toda la sensacion de realmente era una HH beta la GG, no andaba nada y es lentisima. Yo tengo una pc medio pelo y la diferencia de velocidad entre GG  y HH es muy notable, al punto de que antes de que saliera HH me instale 7.04 para "aguantar" por que iba para atras.
Capaz a uno con una pc nueva y grossa ni se dio cuenta :P Aparte las versiones de los programas estan actualizadas, hay muchisimas mejoras. Como digo siempre, esto no es como M$, que la version nueva es mas lenta, hace lo mismo y solo tiene la interfaz grafica mejorada.... realmente hay muchas mejoras en HH. La unica critica que tengo es que pusieron firefox beta en una LTS. o sea, para mi hubo manejo politico ahi, pero bueno, eso escapa al thread. 
Cuando tengamos guia para compilar el kernel, (llamado para Meduza... Meduza atendé!! jajaj) vas a notar más todavia la velocidad y vas a poder controlar mejor tus modulillos. Salu2!

---

### Post by anarko on 2008-06-05
Instalacion lipia de HH, toda la vida.

---

### Post by niko_3100 on 2008-06-05
Instalacion de cero de Hardy, vas a mejorar todo seguro.

---

### Post by Mister X on 2008-06-05
Hola, primero, no te desesperes ;) el "problema" no nace en el sistema operativo sino en el manejo que hace el propio HD de sus cabezas (de todas maneras el SO puede influir en esto mediante el uso particular que haga del disco).
Los HD de las laptops para protegerse de los eventuales golpes y movimientos bruscos lo que hacen es estacionar periodicamente las cabezas fuera del area de los platos, el tema es que esto produce un desgaste, en la mayoria de los HD la vida util es de 600.000 "cabeceos". Vos hiciste un promedio entre dos mediciones, fijate que el comando smartctl tambien te da el tiempo total que lleva encendido el HD, hacé la cuenta con ese valor y vas a llegar a datos mas precisos.

A mi particularmente en linux no me hace el "cabeceo" periodicamente y si lo hace en XP, asi que no es ni un bug de Ubuntu ni de Hardy en particular.

De todas maneras con el comando hdparm se puede deshabilitar esta funcion del disco, pero solamente te lo aconsejo si el calculo que hacés te dice que se va a acortar demasiado la vida util del HD, creo que un valor normal es de 1 cabeceo cada 2 o 3 minutos.

---

### Post by sergiom99 on 2008-06-05
gracias MisterX.
Dicen que tiene que estar por debajo de los 50/hora.
El calculo me da alrededor de 100/hora.

---

### Post by Mister X on 2008-06-05
> **sergiom99 said:**
> gracias MisterX.
Dicen que tiene que estar por debajo de los 50/hora.
El calculo me da alrededor de 100/hora.

Si, ese es un valor demasiado alto. Para deshabilitar el APM (advanced power management) del HD:
```
sudo hdparm -B 255 /dev/sda
```

eso lo deshabilita totalmente, tambien podes setear un valor entre 0 y 255, 0 es un manejo mas agresivo y 255 totalmente deshabilitado.
Acordate que si lo haces en la consola te va a durar hasta el proximo reinicio, para tenerlo siempre vas a tener que ponerlo en un srcipt que se ejecute al inicio o editar el archivo hdparm.conf
Otra cosa: el comando hdparm es muy poderoso y podes hacer muchas cosas con el HD, incluso dañarlo, asi que tomá la precaucion de saber lo que estas haciendo con este comando.

saludos

---

### Post by ajonat on 2008-06-05
Tal cual lo que dijo Mister X.
Por otro lado, este no es un tema propio de Ubuntu o Linux, lo que pasa es que es posible de verlo en nuestros sistemas. Si uno utilizara windows y se le muere el disco a los 3 años, seguramente diría que el disco era de mala calidad (en realidad lo son) y que esa fue la razón, pero nunca sabría la causa intrínseca de por qué se rompió el disco.
Con esto digo que instalar windows en la notebook no asegura nada ya que simplemente no tenes la información necesaria para saber que está pasando detrás de bambalinas.
Lo que yo haría es utilizar el paquete laptop-mode como dice en el thread y configurarlo para que depende si está en batería o no, aproveche el aggresive power management. Si ves que igualmente te aumenta mucho el cycle count, entonces lo mejor es deshabiltarlo definitivamente.

Saludos!

---

### Post by sergiom99 on 2008-06-05
gracias por tu respuesta. como dije al arrancar, en este tema tengo mas dudas que otra cosa.
no entendi mucho acerca del laptop-mode (como lo habilito, etc, etc). si me tiran un tip lo agradezco.

---

### Post by narf y akim on 2008-06-06
Hola, yo también estuve muy preocupado al principio con este tema. Con las instrucciones de ubuntu-demon se corto el load count cycle en mi máquina, que me estaba volviendo loco, principalmente por el ruidito tic-tic que hace el disco a cada rato, incluso en inactividad. En algunas máquinas el parking es más silencioso y pasa desapercivido. Usé el valor 254 para el modo AC y batería. No creo que tenga problemas con el tema de los golpes, igual no la uso en el micro. Con el tema de la temperatura tampoco tuve problemas hasta ahora (el ugly fix lo hice en enero).
Creo que es bueno que los usuarios de portátiles estén al tanto del problema. Abajo copio el arreglo que seguí yo de ubuntu-demon: 

[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

> 1) revert any previous fixes. remove all 99-hdd-spin-fix.sh files if any. comment the lines you added in /etc/hdparm.conf to fix this issue if any.
2) make a file named "99-hdd-ugly-fix.sh". The important thing is starting with "99".
Code:

$sudo gedit 99-hdd-ugly-fix.sh

3) make sure the file contains the following lines (fix it if you have PATA HDD):
Code:

#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda # you might need 255 or a different value
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 128 /dev/sda
fi

4) copy this file to 4 locations:
Code:

$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/resume.d/
$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/start.d/
$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/ac.d/
$sudo install 99-hdd-ugly-fix.sh /etc/acpi/battery.d/



---

### Post by guillermolisi on 2008-06-06
Coincido 100% con Faktorqm.

Tuve un dilema similar cuando pase de DD a FF. Ni lo dude e hice una instalacion limpia con FF. Hoy estoy con HH habiendo hecho dos full upgrades y la verdad es que HH me parecio lo mejor de Ubuntu a la fecha.

---

### Post by sergiom99 on 2008-06-06
anoche hice el clean install y parece haber quedado perfecto.
hoy me pongo a trabajar con el HDD. que es un "PATA HDD"?
(chistes malos aparte.)

---

### Post by guillermolisi on 2008-06-06
PATA HDD es Parallel ATA, la tecnologia de los discos rigidos que usan una tira plana de cables, en general entre 40 y 80 cables, ancha.

Esta tecnologia evoluciono al Serial ATA (o SATA) que es lo mismo pero en lugar de que los bits viajen en paralelo, van uno tras del otro a muy alta velocidad.

---

### Post by lega on 2008-06-07
estuve leyendo este thread y no entiendo nada, pero me preocupa,:( compré un Compaq f755la hace menos de un mes, y le instalé HH en una partición, en otra tiene Vista pero el uso de este utimo es nulo, si alguien me puede explicar en cristiano (se muy poco de ingles como para entender los links que pusieron)que es lo que hay que hacer para saber los ciclos y que para arreglarlo o tomar alguna precaución, estaré muy agradecido.
Saludos.

---

### Post by sergiom99 on 2008-06-07
**@lega:** mira yo tampoco estoy 100% seguro, pero aplique el fix que posteo aca 'narf y akim' y que hizo ubuntu_daemon para el otro thread.
La idea es que cuando este enchufado no se pase parkeando las cabezas del disco, pero si lo haga cuando estas en bateria para protegerlo de golpes y ahorrar bateria.

simpre tenes que ir mirando como se mueve el conteo de Load_Cycle y la Temp con
```
 $ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)' 
```

eso es lo que entendi: el fix y monitorear que no se pase de temp y que no suba el Cycle_Count por mas de 50/hora aprox.

PS: para los que decian que en WIN no saben monitorearlo, encontre que con el Everest lo pueden ver dentro de la parte de SMART en Almacenamiento.

---

