---
title: "Kubuntu JJ: problemas al arrancar laptop a bateria"
date: 2009-05-23
forum: Hardware
---

### Post by sergiom99 on 2009-05-23
Hola gente, sigo encontrando 'detalles' despues de instalar Kubuntu JJ.
Pero lo mas extraño hasta ahora, es que cuando la quiero arrancar a bateria, sin estar enchufada a AC, me pasa que despues del GRUB, queda la pantalla en negro. 
Lo bizarro es que apretando alguna tecla (Siempre lo hice con 'Flecha Derecha') va arrancado, como si le diera cuerda!! WTF!
Alguno tiene una idea de porque pasa esto?
Avisenme si hay que postear alguna salida de algo o algun log.
Saludos- Sergio

---

### Post by guillermolisi on 2009-05-23
> **sergiom99 said:**
> Hola gente, sigo encontrando 'detalles' despues de instalar Kubuntu JJ.
Pero lo mas extraño hasta ahora, es que cuando la quiero arrancar a bateria, sin estar enchufada a AC, me pasa que despues del GRUB, queda la pantalla en negro. 
Lo bizarro es que apretando alguna tecla (Siempre lo hice con 'Flecha Derecha') va arrancado, como si le diera cuerda!! WTF!
Alguno tiene una idea de porque pasa esto?
Avisenme si hay que postear alguna salida de algo o algun log.
Saludos- Sergio
Me imagino que a esta altura ya revisaste el setup de todo lo relacionado con ahorro de energia, ya sea del BIOS como de Ubuntu, particularmente cuando esta en modo "Batt", sin AC cierto ?

---

### Post by sergiom99 on 2009-05-23
si señor, busque cada opcion de Kpowersave para ver si cambia algo.
El BIOS esta siempre igual.

---

### Post by guillermolisi on 2009-05-23
> **sergiom99 said:**
> si señor, busque cada opcion de Kpowersave para ver si cambia algo.
El BIOS esta siempre igual.
Kubuntu 32 o 64 bits ?

---

### Post by sergiom99 on 2009-05-23
32 bits y ext4 el filesystem.
muy extraño....

---

### Post by sergiom99 on 2009-05-24
probe agregando al final de la linea del kernel en el GRUB acpi_osi="Linux" como lei por ahi pero tampoco. 
Hice upgrade del BIOS a la ultima version disponible, pero nada.

---

### Post by sergiom99 on 2009-05-26
*bump*

---

### Post by guillermolisi on 2009-05-26
> **sergiom99 said:**
> *bump*
Te fijaste si en los logs del sistema registra algun evento que de una pista respecto del estado en que ingresa la maquina cuando esta con baterias ? (dmesg, /var/log/messages, etc.)

---

### Post by Mauro22 on 2009-05-26
Estuve buscando y hay un bug ya reporteado:

[https://bugs.launchpad.net/ubuntu/+bug/380044](https://bugs.launchpad.net/ubuntu/+bug/380044)

"When booting my laptop on battery power, Kubuntu JJ freezes after the GRUB. I discovered that pressing (or holding) a key makes the loading process just right. The same for shutdown.
When on AC power, It works just fine.

I use Kubuntu 9.04 2.6.28-11-generic[...] 
I upgraded the BIOS to the latest version provided by HP."


No sos el unico.

---

### Post by sergiom99 on 2009-05-26
soy yo el que lo reporto. en los foros en ingles somos varios.

---

### Post by Mauro22 on 2009-05-26
](*,) q*e *el**u*d !


Gracias, gracias!!

;)

---

### Post by sergiom99 on 2009-05-26
jaja, no importa, vale la intencion igual.

---

### Post by guillermolisi on 2009-05-27
Sergio

Te quedo el kernel anterior ?
En caso que asi sea y aun no lo hayas hecho, probas con ese a ver que pasa ?

---

### Post by sergiom99 on 2009-05-27
> **guillermolisi said:**
> Sergio

Te quedo el kernel anterior ?
En caso que asi sea y aun no lo hayas hecho, probas con ese a ver que pasa ?
Gracias Guille por tus respuestas!
Hice un fresh install, asi que no hay kernels anteriores.
Pero en HH funcionaba perfecto.

Attacheo el syslog y el dmesg, que a proposito la arranque solo a bateria.

un saludo/ Sergio

---

### Post by sergiom99 on 2009-06-01
* bump *

---

### Post by sergiom99 on 2009-06-18
Hoy actualice a
```
$ uname -a
Linux kubuntu 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux
```

pero sigue sin arreglarse.

---

### Post by guillermolisi on 2009-06-18
> **sergiom99 said:**
> Hoy actualice a
```
$ uname -a
Linux kubuntu 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux
```

pero sigue sin arreglarse.
He visto que hay mucha gente con este problema o similar.
Para mi, la cosa viene por el lado del BIOS, mas precisamente del ACPI.

Estoy peleando una instalacion que tambien tiene problemas con ACPI y que solo funciona bien si se inicia con el ultimo kernel de HH. Con los de JJ no funciona bien con ninguno, por lo menos por ahora hasta que encuentre que parametro ACPI tengo que usar efectivamente en la linea de booting en el Grub).

---

### Post by sergiom99 on 2009-06-18
> **guillermolisi said:**
> 
Estoy peleando una instalacion que tambien tiene problemas con ACPI y que solo funciona bien si se inicia con el ultimo kernel de HH. 

Exactamente, en el subforo de laptops comentaban eso, pero a mi no me quedan los viejos kernels porque hice una instalacion nueva.
De cualquier manera, que sentido tendria deshabilitar ACPI en una laptop? No perderia parte del manejo de energia?
Te pregunto porque esa fue una "solucion" propuesta, usarlo con ACPI=off.

Shaun donde estas??? :lolflag:

---

### Post by guillermolisi on 2009-06-18
> **sergiom99 said:**
> Exactamente, en el subforo de laptops comentaban eso, pero a mi no me quedan los viejos kernels porque hice una instalacion nueva.
De cualquier manera, que sentido tendria deshabilitar ACPI en una laptop? No perderia parte del manejo de energia?
Te pregunto porque esa fue una "solucion" propuesta, usarlo con ACPI=off.

Shaun donde estas??? :lolflag:
Si inicias con acpi=off hay cantidad de cosas que no funcionaran correctamente.
Por ejemplo, y este es el problema concretamente que tengo en a maquina que comente, el servidor X no logra acceder a la placa nVidia y te deja sin video.

Tambien deja de funcionar la administracion de energia del monitor y la de la bateria, entre otras cosas.

Si sigo asi terminare experto en tecnologia acpi :D

Probaste iniciando con las opciones noapic, nolapic e irqpoll ?

---

### Post by sergiom99 on 2009-06-19
> **guillermolisi said:**
> 
Probaste iniciando con las opciones noapic, nolapic e irqpoll ?

Sipi y nada. Tambien probé con acpi_osi="Linux" como dicen en el foro de laptop y tampoco naranja. El resto que probó no tuvo solución mas que arrancar con kernels viejos.

Gracias Guille por el aguante!

---

### Post by guillermolisi on 2009-06-19
> **sergiom99 said:**
> Sipi y nada. Tambien probé con acpi_osi="Linux" como dicen en el foro de laptop y tampoco naranja. El resto que probó no tuvo solución mas que arrancar con kernels viejos.

Gracias Guille por el aguante!
Bueno, llegue a estas conclusiones:

O cambio de motherboard (u$s 90.- para una Intel decente compatible con el procesador y RAM que tengo)

O sigo usando el ultimo kernel de HH que funciona bien con las tablas ACPI de esas motherboards hasta que venga alguan solucion, ya sea por el lado del kernel o porque tengo u$s para gastar sin mayor dolor.

En tu caso podemos arreglar que te juntes con los .deb del ultimo kernel de HH para que los instales en tu notebook y sigas siendo feliz por un tiempo mas sin estar presionado por el cambio de maquina.

---

### Post by sergiom99 on 2009-06-19
Pense en bajarme un kernel viejo, pero en realidad eso seria un ugly-fix y prefiero que se arregle como corresponde. No se que problemas podria tener con otras cosas el cambio de kernel.
Tampoco me molesta tanto cuando eventualmente arranco a bateria mantener alguna tecla apretada.

espero poder ayudar a solucionar el BUG.

---

### Post by guillermolisi on 2009-06-19
> **sergiom99 said:**
> Pense en bajarme un kernel viejo, pero en realidad eso seria un ugly-fix y prefiero que se arregle como corresponde. No se que problemas podria tener con otras cosas el cambio de kernel.
Tampoco me molesta tanto cuando eventualmente arranco a bateria mantener alguna tecla apretada.

espero poder ayudar a solucionar el BUG.
Bueno. Instale el kernel 2.6.24-24 de HH, completo y sin problemas de dependencias.

Si tenes file systems en EXT4 no funciona (mi caso para / y /home).
The end.

Luego probe con el kernel 2.6.28-13, up to date, con las opciones noapic nolapic irqpoll (las tres juntas porque de lo contrario no sirve ni solas ni de a pares) y comenzo a funcionar pero al ratito se colgo toda la maquina. Asi que a partir de ahora comence la campaña de recepcion de aportes "pro nueva motherboard" porque volver a EXT3 todo el disco me saldra tan caro como eso por el tiempo que le tengo que dedicar.

---

### Post by pablo.s on 2009-06-19
Guille, en unos meses vas 
a poder probar con Karmic
Koala (o ahora, si probás
con la alpha 2).

Acá dejo el calendario por
si quieren saber las fechas.
[ATTACH]118286[/ATTACH]

---

### Post by guillermolisi on 2009-06-19
> **pablo.s said:**
> Guille, en unos meses vas 
a poder probar con Karmic
Koala (o ahora, si probás
con la alpha 2).

Acá dejo el calendario por
si quieren saber las fechas.
[ATTACH]118286[/ATTACH]
Si, es una chance pero por lo que pude leer en la lista de quienes intervienen en el kernel y sus patches, el tema de esta placa y su implementacion ACPI parece no ser prioritario por ser tan especifico.

Si bien hay otro hardware que tambien tiene algunos problemas con ACPI, parciales como por ejemplo monitoreo de carga de bateria, sensores, etc., este problema es un crash error rotundo pero solo para esa placa.

---

### Post by pablo.s on 2009-06-19
Y no te animás a compilar
un 2.6.30 con los módulos
que necesitás? En algún lado
se debe poder conseguir el 
config del 2.6.24-24 que estás
utilizando...

---

### Post by guillermolisi on 2009-06-19
> **pablo.s said:**
> Y no te animás a compilar
un 2.6.30 con los módulos
que necesitás? En algún lado
se debe poder conseguir el 
config del 2.6.24-24 que estás
utilizando...
Como animar me animo ya que no tengo nada que perder ni se rompera nada (con Unix me canse de compilar y linkeditar kernels) pero ... empece por el principio (el comunitario) reportando otro caso al bug que ya esta abierto en Launchpad (bug # 37237) asi, si lo arreglan, sirve tanto para el que puede, quiere y sabe compilar como para el que no.

El config del 2.6.24-24 lo tengo en un server (de ahi saque los .deb necesarios para la prueba fallida que comentte).

---

### Post by sergiom99 on 2009-06-20
yo tambien tengo el / en ext4, asi que volver a HH no seria posible.

Le mande un PM a Shaun ("*the artist formerly known as vor*") para que opine en este thread el que la tiene clara con powersettings y laptops, pero aun no ha aparecido :-(

---

### Post by sdennie on 2009-06-20
Podes postear los logs pero con una pausa bastante largo (un minunto seria perfecto) antes de apretar una tecla?  Seria mas facil a entender exactamente caundo la maquina deja de funcionar.

Por ahora estoy pensando que es un problema con el soporte de WMI (una cosa de BIOS que normalmente solo se usa en Windows).  El kernel de Hardy no sabe nada de WMI pero Jaunty si (no se con Intrepid) asi que si hay un bug en el DSDT con las cosas de WMI (que antes no estaban usados) puede ser el problema.

---

### Post by sergiom99 on 2009-06-20
Aca los subo.
Deje entre 90 y 120 segundos sin tocar nada que me fui a calentar cafe :-P

gracias Shaun!

PS: tambien los subi al BUG.
[https://bugs.launchpad.net/ubuntu/+bug/380044](https://bugs.launchpad.net/ubuntu/+bug/380044)

---

### Post by sdennie on 2009-06-20
> **sergiom99 said:**
> Aca los subo.
Deje entre 90 y 120 segundos sin tocar nada que me fui a calentar cafe :-P

gracias Shaun!

PS: tambien los subi al BUG.
[https://bugs.launchpad.net/ubuntu/+bug/380044](https://bugs.launchpad.net/ubuntu/+bug/380044)

Hmmm.  Probaste con "nopat" y/o "nomtrr" como opcion en grub?  Por PAT, el kernel dice:

> 
CONFIG_X86_PAT:                                                          Use PAT attributes to setup page level cache control.                     PATs are the modern equivalents of MTRRs and are much more flexible than MTRRs.

Say N here if you see bootup problems (boot crash, boot hang, spontaneous reboots) or a non-working video driver.


Y veo que estas usando PAT:

```

[    0.540022] Switched to high resolution mode on CPU 0
[    0.540035] Switched to high resolution mode on CPU 1

```

---

### Post by sdennie on 2009-06-20
Me equivoque.  "nopat" no va a hacer nada.  No se con nomtrr.

---

### Post by sdennie on 2009-06-20
Triple post!  (Por suerte ninguna de los otros mods hablan castellano)

Tambien podes probar "nousb".  La pausa tuya viene con USB asi que es algo para probar.

---

### Post by sergiom99 on 2009-06-21
Shaun, probe de iniciar primero con 'nousb' y nada, solo perdi los puertos USB.
Y despues volvi a bootear con 'nomtrr' y tampoco nada.
(aclaro que los edite en la linea del GRUB y los puse sin comillas)

---

### Post by sdennie on 2009-06-23
La unica otra cosa que puedo reccomendar es compilar un "custom DSDT".  Parece muy dificil pero, no es TAN malo.  Yo antes tenia una laptop Toshiba que tenia un BIOS tan malo que, sin hacer un DSDT custom, no aprendio los coolers, el sonido no funciono, etc.  Solo conozco a guias en ingles y esa parece un "all in one" que no habia antes: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by sergiom99 on 2009-06-23
hmmm. alguna chance de que se arregle desde el kernel y/o Ubuntu?

---

### Post by sdennie on 2009-06-23
> **sergiom99 said:**
> hmmm. alguna chance de que se arregle desde el kernel y/o Ubuntu?

A veces si, pero, fijate:

> 
This guide will help you fix your DSDT file to fix common ACPI problems on any Debian based OS. With Mint 6/Ubuntu 8.10, I started having a lot of problems with my laptop thermal temps, **and not wanting to boot without holding down a keyboard key.**


("Y sin querer bootear sin apretar una tecla").

---

### Post by sergiom99 on 2009-06-23
Si, lo estoy leyendo y el tipo tambien tiene una HP.  Dice que se puede "romper" la instalacion del OS, asi que voy a probar en un par de dias cuando tenga un poco mas de tiempo (y valor!)
Gracias!

---

### Post by sdennie on 2009-06-23
> **sergiom99 said:**
> Si, lo estoy leyendo y el tipo tambien tiene una HP.  Dice que se puede "romper" la instalacion del OS, asi que voy a probar en un par de dias cuando tenga un poco mas de tiempo (y valor!)
Gracias!

Naaa.  Un custom DSDT es un parte del initrd asi que es solo aplicable a los kernels que tienen el initrd armado con ese DSDT.  Asi que si tenes 2 kernels que funcionan, podes probar con uno y ni importa si rompes ese kernel.  Podes arreglarlo facilmente (sacar el DSDT nuevo y re-armar el initrd por ese kernel) y probar de vuelta.

---

### Post by sergiom99 on 2009-06-23
Eso me deja mas tranquilo.
O sea que en cada upgrade de kernel tengo que recompilar DSDT?

Desde HH que no tenia que recompilar nada al actualizar!

---

### Post by sdennie on 2009-06-23
> **sergiom99 said:**
> Eso me deja mas tranquilo.
O sea que en cada upgrade de kernel tengo que recompilar DSDT?

Desde HH que no tenia que recompilar nada al actualizar!

No, el initrd se hace automaticamente cuando se instala un kernel nuevo.  Vive en /etc/initramfs-tools que es una plantilla para instalar kernels con la informacion que necesita para bootear.  Si no re-armas el initrd por otros kernels, no pasa nada.  Si booteo antes sigue booteando.

---

### Post by sergiom99 on 2009-06-24
Shaun, voy a probar de compilar el DSDT con el howto que me pasaste.
Me dio un par de errores al compilar que los estoy tratando de solucionar en ese thread y sigo.

---

### Post by sergiom99 on 2009-06-25
Woohoo!
Ya lo probe y quedo perfecto, gracias a la ayuda de 67GTA que me dio una mano con los errores del DSDT.

En realidad habria que arreglar lo que sea que haya cambiado en Ubuntu desde HHeron a JJ, pero mientras tanto esto nos permite zafar.

Si alguien llega aca buscando por el modelo de laptop (HP DV6646us) aca dejo attachado el archivo del DSDT arreglado.
**[COLOR="Red"]NOTA: SOLO SIRVE PARA ESTE MODELO DE LAPTOP![/COLOR]**
(Como armar el tuyo, en este excelente how-to [1])

Gracias Shaun por la ayuda y mantengo la promesa de una birra la proxima vez que nos crucemos.
-Sergio

[1] [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by sdennie on 2009-06-25
Buenisimo.

Podes tambien postear el DSDT original?  Quiero ver si lo que dije originalmente era correcto (que el problema es el kernel puede ver los depositos WMI ahora).

---

### Post by sergiom99 on 2009-06-25
> **sdennie said:**
> Buenisimo.

Podes tambien postear el DSDT original?  Quiero ver si lo que dije originalmente era correcto (que el problema es el kernel puede ver los depositos WMI ahora).

Porsupollo. Aca esta.

---

