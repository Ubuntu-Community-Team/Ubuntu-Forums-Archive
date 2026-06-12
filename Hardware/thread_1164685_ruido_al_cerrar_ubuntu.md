---
title: "ruido al cerrar ubuntu"
date: 2009-05-19
forum: Hardware
---

### Post by drazhe on 2009-05-19
Pues, cada vez que apago el sistema con ubuntu, la computadora hace un beep insoportable, al viejo estilo Adblid de las maquinas viejas de antes de la existencia de placas de sonido, me gustaria saber si hay alguna manera de sacarselo... 
no me estoy refiriendo al sonidito de inicio y cierre del sistema, sino a un beep que hace justo despues de apretar el boton de apagar sistema...

---

### Post by josecuervo86 on 2009-05-19
De una, a mi tambien me lo hace, no busque demasiado pero me encantaria sacar esa espera de 60 segundos "al cuete"

---

### Post by guillermolisi on 2009-05-19
Por casualidad, tienen habilitada la alarma del fan de la CPU, el del procesador, para que avise si bajo de cierta cantidad de vueltas ?

---

### Post by josecuervo86 on 2009-05-19
Ahora me fijo, igual supongo que no viene por ese lado ya que en II no lo hacia, pero igual me voy a fijar. En cuanto a los 60 segundos de espera alguien tiene alguna idea?

---

### Post by drazhe on 2009-05-19
la verdad es que no tengo idea, soy bastante neuvo en ubuntu, y lo de los 60segundos aparecio en la 9.04, en la maquina de escritorio tuve la 8.04 y 8.10 (que aun tengo) y los 60segundos no estan, pero el ruido ese si...

---

### Post by guillermolisi on 2009-05-19
Vos te referis a mantener apretado el boton o a 60 segundos de sonido ?

Si es de mantener apretado el boton, lo configuras en el BIOS para que se apague apenas presionas (si no bajaste el SO, aguantate el shutdown forzado).

---

### Post by josecuervo86 on 2009-05-19
Imagino que lo de los 60 segundos viene por el lado que ext4 demora 60 segundos en guardar los datos (o lo hace cada 60 segundos) y esta para evitar problemas de perdidas de datos. Igual estaria bueno sacarselo

---

### Post by josecuervo86 on 2009-05-19
> **guillermolisi said:**
> Vos te referis a mantener apretado el boton o a 60 segundos de sonido ?

Si es de mantener apretado el boton, lo configuras en el BIOS para que se apague apenas presionas (si no bajaste el SO, aguantate el shutdown forzado).

Me parece que se refiere a lo mismo que a mi: cuando apretas en apagar, te aparece una cuenta regresiva de 60 segundos y cuando esta termina te suena un BIP terrible :D

---

### Post by guillermolisi on 2009-05-19
> **josecuervo86 said:**
> Imagino que lo de los 60 segundos viene por el lado que ext4 demora 60 segundos en guardar los datos (o lo hace cada 60 segundos) y esta para evitar problemas de perdidas de datos. Igual estaria bueno sacarselo
Debe ser lo que necesita para llevar a cabo el Sync del sistema de archivos (cierra todo y guarda el journal con el resultado. Inclusive debe actualizar el contador para el proximo fsck).

---

### Post by josecuervo86 on 2009-05-19
Pero guille... a vos tambien te lo hace no? Porque estoy googleando posibles soluciones y no encuentro nada.

---

### Post by josecuervo86 on 2009-05-19
Bueno, lo de los 60 segundos creo que ya esta solucionado. Vas a donde dice tu nombre de usuario en la barra y le das click con el boton derecho del mouse, despues vas a prefrencias y destildas la casilla donde dice "solicitar confirmación al cerrar sesión, reinicar y apagar". Sigo buscando lo del beep, aunque por lo visto no somos a los únicos que le sucede

---

### Post by guillermolisi on 2009-05-19
No, no tengo ese "placer" :)

Tampoco estoy usando ext4 y no tengo alarma audible por bajas revoluciones del fan de la CPU, asi que mi caso no sirve de mucha referencia aunque use JJ.

Tengo un server con mother aBit (AMD) que le desactive la alarma porque sonaba hasta que entraba en regimen y luego hasta que se apagaba totalmente la maquina (se terminaba de descargar la fuente). En ese server tengo HH.

---

### Post by drazhe on 2009-05-19
a mi el beep ese me pasaba desde la 8.04 que instale en la pc de escritorio... el problema es que en la notbuk el beep es muy fuerte y molesta un monton!

gracias por el dato de los 60segundos! es bastante molesto volver a dar la confirmacion.. jejejeje

---

### Post by josecuervo86 on 2009-05-19
No traigo buenas noticias. O tal vez si, pero la cosa es que no hay forma "legal" de sacar ese beep (o al menos no la encuentro todavia). Pero tengo la forma alternativa y en dos presentaciones:

[Aclaración] De aqui en adelante cada uno se hace responsable de lo que haga. Yo no recomiendo ninguna de las dos formas y ni siquiera las voy a probar[/Aclaración]

1- Desconectar el cable del parlantito interno (obvia)
2- "Blacklistear" **pcspkr** y **snd_pcsp** en /etc/modprobe.d/blacklist

Les dije que no eran buenas, pero fue lo único que encontre. Tampoco es que se te va a romper la maquina, pero preferiria simplemente que no lo hiciera.

Hay una 3ra opción que la encontre aca:
[http://www.pcworld.com/article/138903-2/postinstall_tips_for_ubuntu_710.html]("http://www.pcworld.com/article/138903-2/postinstall_tips_for_ubuntu_710.html")
que hay gente a la que le funciono

Igual esperaría a ver si sale alguna solución oficial

EDIT: por lo visto somos afortunados, ya que solo tenemos un solo beep, ya que hay un bug reportado de entre 4 y 10 beeps al apagar el equipo

---

### Post by staar on 2009-05-19
el beep ese que dicen, es el speaker interno de la pc? porque si es ese se puede poner el modulo pcspkr en la blacklist para que no lo cargue y listo, aunque se quedan sin el speaker, este se usa solo para errores graves y en las consolas (y la verdad creo que la mayoría lo debe tener desactivado desde las preferencias de Sonido)

hagan un ```
sudo gedit /etc/modprobe.d/blacklist
``` y agregen una línea así ```
blacklist pcspkr
``` guarden, cierren, reinicien y cuenten...

se que es un hack, un poco 'feito', pero es la única manera que encontré para hacerlo callar, sin desenchufarlo, al speaker (cuando empeze con ubuntu me tenía loco)

saludos

EDIT: uh, josé no alcanzé a ver tu post, bueh, es la misma solución...

---

### Post by josecuervo86 on 2009-05-19
Jaja staar, me parece que lo voy a tener que implementar nomas. Igual voy a seguir el bug asi puedo volver a conectar el speaker interno.
Por último les dejo el enlace al bug para que lo lean (bastante divertido):

[URL="https://bugs.launchpad.net/ubuntu/+bug/363532"]
https://bugs.launchpad.net/ubuntu/+bug/363532[/URL]

---

### Post by staar on 2009-05-19
wait, que leyendo el enlace que pusiste vi que hay un comando, xset, que parece que puede apagar el speaker, por lo menos cuando funciona como la bell del sistema...

sería ```
xset b off
``` probalo y contá si funca...

saludos

---

### Post by drcdebaca on 2009-05-20
Ud. pueden tratar...

[http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/](http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/)

Es en ingles, lo siento.

Amor y Pesetas

---

### Post by dirty fingers on 2009-05-20
a mi aparte de cuando cierro el sistema me hace el bip cuando me llega un mail.

---

### Post by Mauro22 on 2009-05-20
Yo en control de volumen tengo el canal Beep que justamente controla el 'beep' jejej... (no tengo otra forma de aclararlo).

Lo 'mutean' y todos felices.

vean el screenshot:

---

### Post by leonardomdq on 2009-05-20
a mi tambien me aparecen los beeps, silencie el parlante interno y listo

---

### Post by hictio on 2009-05-20
> **josecuervo86 said:**
> Bueno, lo de los 60 segundos creo que ya esta solucionado. Vas a donde dice tu nombre de usuario en la barra y le das click con el boton derecho del mouse, despues vas a prefrencias y destildas la casilla donde dice "solicitar confirmación al cerrar sesión, reinicar y apagar". Sigo buscando lo del beep, aunque por lo visto no somos a los únicos que le sucede


José sabés alguna otra manera de llegar a ese menú? Una de las primeras cosas que saco del Panel (para ganar espacio) es ese applet, y me da fiaca volver a ponerlo solo por esto :D ;)
Estuve buscándo la opción para configurar esto por todos lados y no lo pude encontrar.

Muchas gracias.

---

### Post by josecuervo86 on 2009-05-20
Ni idea hictio, la única manera que encontre de llegar es asi. Igual yo probaria de darle click derecho en el boton que vos tenes para apagar la maquina, deberia darte esas opciones tambien, no?

---

### Post by z37a on 2009-05-20
Otro mas con el beep, pero no creo que la solución ideal sea la de silenciar al parlante del sistema!!!, Generalmente este suena cuando hay algún error, puede venir por ese lado acá también? Por que con Intrepid o Hardy eso no me pasaba.

Igualmente es un error menor también pero si tiene solucion bienvenida es!!!!

PD: Me suscribí a la lista de launchpad del bug!!!

---

### Post by alberto71 on 2009-05-20
Hola. Lo que me resultó más fácil para evitar el infame beep, fue tipear:

```
sudo modprobe -r pcspkr
```

Los 60 segs, como dijeron, se anula desde el selector de usuarios. Pero dado que instalé con ext4 no sé si no traerá problemas al apagar/reinciar el equipo.

Por cierto, tuve que pelear como nunca para hacer andar el "alfajor del diablo". Las versiones anteriores fueron un paseo...

Saludos.

---

### Post by josecuervo86 on 2009-05-20
> **z37a said:**
> Otro mas con el beep, pero no creo que la solución ideal sea la de silenciar al parlante del sistema!!!
Obviamente, y por eso aclare que no lo recomiendo

> PD: Me suscribí a la lista de launchpad del bug!!!

Me too!!

---

### Post by Hei Ku on 2009-05-20
> **alberto71 said:**
> Hola. Lo que me resultó más fácil para evitar el infame beep, fue tipear:

```
sudo modprobe -r pcspkr
```



Esta solucion te sirve para la sesion, pero al reiniciar lo vas a tener otra vez.

---

### Post by dirty fingers on 2009-05-20
> **Mauro22 said:**
> Yo en control de volumen tengo el canal Beep que justamente controla el 'beep' jejej... (no tengo otra forma de aclararlo).

Lo 'mutean' y todos felices.

vean el screenshot:

a mi no me da bola ese control de mute.

tengo una nvidia soundstorm.

---

### Post by hictio on 2009-05-20
> **josecuervo86 said:**
> Ni idea hictio, la única manera que encontre de llegar es asi. Igual yo probaria de darle click derecho en el boton que vos tenes para apagar la maquina, deberia darte esas opciones tambien, no?

Ja ja ja, si fue lo primero que probé cuando inicié la búsqueda, pero no camina por ese lado, abre la ventana de diálogo tradicional de la confirmación de apagado.

Gracias igual.

---

### Post by josecuervo86 on 2009-05-20
> **hictio said:**
> Ja ja ja, si fue lo primero que probé cuando inicié la búsqueda, pero no camina por ese lado, abre la ventana de diálogo tradicional de la confirmación de apagado.

Gracias igual.

Jaja, vas a tener que tomar coraje y agregar ese boton al panel, como los machos (?)

---

### Post by hictio on 2009-05-20
> **josecuervo86 said:**
> Jaja, vas a tener que tomar coraje y agregar ese boton al panel, como los machos (?)

José otra pregunta, vos usás tu Ubuntu en una laptop? Yo si, y el tema es, a través de esa ventana de diálogo, accedo a la opción de poner en stand by, o hivernar, etc.
Si saco la opción de activarlo por ahí me quedaría la opción del atajo de teclado nada más? Digo la tecla Function que la ponga a dormir...

---

### Post by majatu on 2009-05-20
> **alberto71 said:**
> Hola. Lo que me resultó más fácil para evitar el infame beep, fue tipear:

```
sudo modprobe -r pcspkr
```

Los 60 segs, como dijeron, se anula desde el selector de usuarios. Pero dado que instalé con ext4 no sé si no traerá problemas al apagar/reinciar el equipo.

Por cierto, tuve que pelear como nunca para hacer andar el "alfajor del diablo". Las versiones anteriores fueron un paseo...

Saludos.

a mi me hacia los beeps cuando apagaba la pc y puse ese comando que nombras o uno parecido, la cosa es que ahora la maquina me arranca con el sonido directamente silenciado y lo tengo q destildar a mano...

alguna idea de como arreglarlo?

un saludo

---

### Post by alberto71 on 2009-05-21
Hmmm, con eso debería funcionar. Lo probé en 3 instalaciones diferentes sy anduvo. Por las dudas, probá con activar de vuelta el parlante con

```
sudo modprobe pcspkr
```

para luego desactivarlo con

```
sudo modprobe -r pcspkr
```

También, en **Sistema / Preferencias / Sonido ** podés desmarcar la opción *Reproducir efectos de sonido al pulsar botones* y también *Reproducir sonido de alerta*.

Pero creo que lo mejor es probar los 2 comandos modprobe pcspkr, que deberían funcionar perfectamente.

Saludos.

---

### Post by josecuervo86 on 2009-05-21
> **hictio said:**
> José otra pregunta, vos usás tu Ubuntu en una laptop? Yo si, y el tema es, a través de esa ventana de diálogo, accedo a la opción de poner en stand by, o hivernar, etc.
Si saco la opción de activarlo por ahí me quedaría la opción del atajo de teclado nada más? Digo la tecla Function que la ponga a dormir...

No, lo tengo en la desktop. A mi vieja se lo instale en la laptop, pero esta a 600km y no lo puedo probar. Seguramente alguien tiene una laptop por aca no?

---

### Post by dirty fingers on 2009-05-21
basta de joda ! cortemos el cable del speaker !
jaja por suerte mi bios tira los errores hablados por la salida de sonido.

---

### Post by drazhe on 2009-05-22
por lo que pude leer, todos son usuarios expertos en ubuntu y linux en general, me sorprende que el problema lo tirara yo que soy un extremo novato en este asunto...
con respecto a los 60 segundos de confirmacion, es solo eso una confirmacion de cierre, si se lo sacas, lo unico que no va a hacer es pedir la confirmacion, el SO va aterminar con todos los procesos antes de apagarse, y no se va a tomar los 60 segundos.. no se porque pusieron tanto tiempo o porque viene esa opcion por default.
Con lo del sonido, tengo miedo, porque si bien en la notbuk el sonido es mas fuerte ya que estoy mas cerca de los circuitos, tampoco quiero romperla... ejejeje
Gracias a todos por las ayudas y recomendaciones que me dieron...

---

### Post by sp33d3rs on 2009-05-22
> **drazhe said:**
> por lo que pude leer, todos son usuarios expertos en ubuntu y linux en general, me sorprende que el problema lo tirara yo que soy un extremo novato en este asunto...
con respecto a los 60 segundos de confirmacion, es solo eso una confirmacion de cierre, si se lo sacas, lo unico que no va a hacer es pedir la confirmacion, el SO va aterminar con todos los procesos antes de apagarse, y no se va a tomar los 60 segundos.. no se porque pusieron tanto tiempo o porque viene esa opcion por default.
Opino lo mismo de los 60 segundos.. jamás los deje, y nunca tuve problemas apagando la pc.

---

### Post by josecuervo86 on 2009-05-22
> Opino lo mismo de los 60 segundos.. jamás los deje, y nunca tuve problemas apagando la pc.

Sigo pensando que es por lo del journaling de ext4, que supuestamente guarda los datos cada 60 segundos, pero tampoco me cierra demasiado esa opción. Estaria bueno una confirmación por parte de gente mas instruida en el tema.

---

### Post by hictio on 2009-05-22
> **josecuervo86 said:**
> Sigo pensando que es por lo del journaling de ext4, que supuestamente guarda los datos cada 60 segundos, pero tampoco me cierra demasiado esa opción. Estaria bueno una confirmación por parte de gente mas instruida en el tema.

Pero esa ventana de confirmación es anterior a ext4 como file system, en Intrepid también estaba, de hecho, había una discusión al respecto de varias páginas [Disable 60 second shut down timer?](http://ubuntuforums.org/showthread.php?t=978289) (el problema del beep que hay ahora con Jaunty no se menciona, obviamente)

---

### Post by staar on 2009-05-22
> **drazhe said:**
> por lo que pude leer, todos son usuarios expertos en ubuntu y linux en general, me sorprende que el problema lo tirara yo que soy un extremo novato en este asunto...
con respecto a los 60 segundos de confirmacion, es solo eso una confirmacion de cierre, si se lo sacas, lo unico que no va a hacer es pedir la confirmacion, el SO va aterminar con todos los procesos antes de apagarse, y no se va a tomar los 60 segundos.. no se porque pusieron tanto tiempo o porque viene esa opcion por default.
Con lo del sonido, tengo miedo, porque si bien en la notbuk el sonido es mas fuerte ya que estoy mas cerca de los circuitos, tampoco quiero romperla... ejejeje
Gracias a todos por las ayudas y recomendaciones que me dieron...

no tengas miedo, no la vas a romper, ni mucho menos, simplemente evitas que el sistema cargue el módulo que necesita para usar el speaker interno de la pc, osea que simplemente no lo vas a usar, va a estar ahi, apagado, nada más...

saludos

---

### Post by z37a on 2009-05-22
Y a nadie se le ocurrio que solo tal vez, los 60 segundos se pudieron por si con el mouse le pfias a lo que queres clickear???? O que para muchos(me incluyo) en el 8.10 le resultaba molesto que se apagara de 1 y el 8.04 tenia un menu a la hora de apagar para que esto no pase? Se me ocurren miles de rasones mas alla de lo técnico para esto, y obviamente como es de gusto esta la forma de deshabilitarlo.

PD: Si lo dijera con furia seria mayuscula, solo lo digo en tono chistoso, pero no se como escribir en tono de chiste!!!!

---

### Post by drazhe on 2009-05-22
> **z37a said:**
> Y a nadie se le ocurrio que solo tal vez, los 60 segundos se pudieron por si con el mouse le pfias a lo que queres clickear???? O que para muchos(me incluyo) en el 8.10 le resultaba molesto que se apagara de 1 y el 8.04 tenia un menu a la hora de apagar para que esto no pase? Se me ocurren miles de rasones mas alla de lo técnico para esto, y obviamente como es de gusto esta la forma de deshabilitarlo.

PD: Si lo dijera con furia seria mayuscula, solo lo digo en tono chistoso, pero no se como escribir en tono de chiste!!!!

el 1ero ubuntu que instale fue el 8.04 y al apretar el boton para apagar sistema, me saltaba otra ventana donde daba las opciones apagar, reiniciar, hibernar, suspender y no me acuerdo la 5ta, le dabas al apagar nuevamente y ahi se apagaba (haciendo el molesto beep) pero se apagaba de 1, la confirmacion seria la 2da vez que apretas el boton de apagar no hace falta el contador, en la 8.10 despues de acualizar lo mismo, cuando le daba al apagar aparecia un menu diferente, pero con estas 5 opciones mencionadas anteriormente y al igual que en la anteior a la 2da vez que le das apagar se apagaba (volviendo a hacer el molesto beep), cuando instale la 9.04 comenzo a aparecerme el cartel ese de los 60 segundos, ya no mas gracias a que me dijern como sacarlo, el problema sigue siendo el beep ese... en la pc de escritorio estaba medio lejos del speaker, asi que el beep se escuchaba pero no tanto, en la notbuk estoy al lado y es muy insoportable... jejeje...

---

### Post by lega on 2009-05-22
yo tengo deshabilitada la opción de esperar los 60 segundos y a veces, no siempre, me hace varios beeps, como tres! pero no siempre a veces hace solo uno, me voy a fijar si habiltando nuevamente la espera de 60 seg.deja de hacer tantos beeps, porque cuando los hace me hace pensar que algo está mal :)

---

