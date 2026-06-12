---
title: "Intrepid: Problemas en la Compaq F756La"
date: 2008-11-24
forum: Hardware
---

### Post by vk-cdg on 2008-11-24
Abro este Thread para no ensuciar el de la placa WiFi de este mismo canal.

Maquina: Compaq F756La standar (1 Gb RAM)

Hice una instalación desde cero de Intrepid en formateando la misma partición donde estaba Hardy y mantuve el /home y el swap.
El arranque con el Live CD fue correcto, sin nada que me hiciera sospechar algo al respecto. Luego de terminada la instalación, saco el CD y procedo a arrancar con el SO instalado, pero este se queda "detenido" en proceso de carga... como explicarlo.... a ver.. explico coloquialmente... en el usplash, la barrita naranja va de un lado al otro como "El Auto fantástico" 2 veces y luego empieza a completarse progresivamente desde la izquierda hacia la derecha. Bueno, se queda en la primera parte, cuando va de un lado al otro. Probé dejarla 5, 10, 30 minutos y nada. 
Lo raro es que si presiono enter, barra espaciadora o cualquier otra tecla avanza un poquito y si la dejo apretada avanza y completa el proceso, es decir... termina de arrancar y me muestra el GDM Theme como para que me loguee.... luego de ahí todo anda normal de lo poco que configuré.

Al apagar el equipo, la historia es mas o menos similar, se queda en cierta parte del usplash theme y no avanza a menos que mantenga presionada cualquier tecla.

Como el martes rindo un recuperatorio y lo hago con la notebook, decidí no perder tiempo inversigando y volví a Hadry, pero me intriga saber a que se debe y me gustaría poder instalar Intrepid.

Calculo que la proxima vez que intente (el proximo fin de semana) haré una actualización.

---

### Post by niko_3100 on 2008-11-24
Que raro, fijate de que cuando instalas ubuntu este conectado a internet asi te baja las ultimas actualizaciones, va a atardar mucho mas la instalacion pero ya vas a estar al dia pr ahi no lo tira mas. Yo no tengo el splash del principio, en el grub le pongo "nosplash" asi me muestra los procesos que se van cargando cuando arranca si algo tira error te indica y despues es mas facil saber cual es el problema, a parte de ser mas linux y menos windows.

---

### Post by luks911 on 2008-11-24
Otra sugerencia: usá el alternate CD para instalar, es menos "lindo" pero más rápido y puede que sirva para eliminar tu problema. Yo lo usé, je. Y para hacer lo que dice niko, de ver qué es lo que pasa cuando se congela, también podés apretar ctrl+alt+F1 cuando termina de pasar por el grub y te aparece el usplash. Vas a ver los procesos que se ejecutan y vas a tener más datos de cuándo se cuelga.

---

### Post by vk-cdg on 2008-11-24
> **niko_3100 said:**
> ...fijate de que cuando instalas ubuntu este conectado a internet asi te baja las ultimas actualizaciones...

Tomé especial recaudo (le saqué el bleca a la PC de escritorio y se lo puse a la notebook + resetear el router) de estar conectado a internet. Desde el live CD, antes de instalar navegué por internet para verificar que tenía conexión.

> **niko_3100 said:**
> Yo no tengo el splash del principio, en el grub le pongo "nosplash" asi me muestra los procesos que se van cargando cuando arranca si algo tira error te indica y despues es mas facil saber cual es el problema...

Voy a probar con esto a ver si veo algo. Tnk por el dato.



> **luks911 said:**
> Otra sugerencia: usá el alternate CD para instalar, es menos "lindo" pero más rápido y puede que sirva para eliminar tu problema.

Ok, pruebo con eso. Lo raro es que el problema no lo tengo en la instalación, sino una vez que está instalado. No debería tener que ver si lo instalé con uno un otro CD no?
De todas formas no cuesta nada, ya lo he usado para mi Dell del trabajo.

> **luks911 said:**
> Y para hacer lo que dice niko, de ver qué es lo que pasa cuando se congela, también podés apretar ctrl+alt+F1 cuando termina de pasar por el grub y te aparece el usplash. Vas a ver los procesos que se ejecutan y vas a tener más datos de cuándo se cuelga.

Gracias por este dato también, mas fácil que andar modificando el grub.

---

### Post by leandr0f on 2008-11-25
Al aparecer el menú de Grub, abpretá la tecla "e" en la línea normal de inicio para editarla, y borrá donde dice "quiet" y "splash", dale Enter y iniciá con "b", así quitás el usplash y te muestra todo el proceso de arranque.
Es similar a presionar Ctrl+Alt+F1, salvo que con esta combinacion de teclas no muestra mucha info porque tiene el "quiet" en la línea del Grub.

---

### Post by Flechagorda on 2008-11-27
vk-cdg..........
Como va........

Sabes que me pasa exactamente lo mismo pero desde el LiveCD, no lo instale todavia......ahora estoy con XP, pero el otro dia tuve que formatear un Pendrive y use el livecd de II....
Y tenia que apretar Enter o los cursores......
Voy a ver si lo instalo a ver si anda.........

---

### Post by vk-cdg on 2008-11-28
Yo ahora no me acuerdo si me pasaba con el LiveCD o no. Este fin de semana si tengo un ratito lo pruebo de nuevo con el LiveCD y te cuento.

Yo quería poner intrepid, por el tema de los USB luego de ibernar y por el manejo de energía que dicen es mas eficiente, pero bue.....

---

### Post by Flechagorda on 2008-11-28
Perdon por el desvirtue, pero como te anda con tanto calor?
El disco mio se pone que se derrtie! te quema las manos!!!

---

### Post by vk-cdg on 2008-11-28
Si, se pone "quenchi"!!!
Esta semana la usé solamente el martes en la facultad para rendir un recuperatorio de java, después no  a usé mas dado que el 1/12 empiezo con los finales.

Calculo que en días como los que hizo y mas en mi caso que soy de usarla "a upa" se debe poner al rojo.

---

### Post by ricardo1825 on 2008-12-01
Hola .. tengo el mismo equipo .. y pasa exactamente lo que mencionas, el arranque se pega, busque, hice de todoy aún no lo soluciono ... hay varios problemas en el arranque, el primero es un error del Kinit .... dice que no puede hacer resume con el UUID ..del disco .. verifique en los foros ... y se debe corregir el initframe .... actualizando el UUId del disco donde tienes el /boot ....... lo hice .. pero seguia igual .. segui examinado el arranque .. y tambien hay problemas "aparentemente" de hardware : Unable to enumerate USB device on port 2 ....... lo cual tambien deja pegado el arranque .. a lo cual edite .. para que no haga ni resume .. ni noapic nousb .. en el arranque .. pero sigue igual ..... no me funciono ..... en Hardy todo va de maravilla .... intenet tambien hacer un update de hardy funcionando bien a intrepid ... pero se daña igual que si hiciera una instalación limpia ......  conclusión .. no pude utilizar intrepid en la laptop ... en mi desktop funciona bien .... aunque no se porque en nuevo network manager no guarad mis preferencias .... le doy una ip estatica ... que solo dura durante la sesión .. una vez reinicio ... pierdo lños datos de red ...... la verdad hay muchos problemas al rededor de intrepid ..... será que saliuo antes de tiempo ....  me dieron ganas de probar fedora 10 a ver como va en mi laptop ...

---

### Post by Hei Ku on 2008-12-03
Poner un punto aparte de vez en cuando no molesta. ;)

Encontraron algun error reportado de esto? Porque pareciera ser un error particular de esta notebook o mother.

---

### Post by Flechagorda on 2008-12-03
El bug ya esta reportado en launchpad

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

Parece algo con Nvidia MCP67......

Lei los primeros comments, porque despues se desvirtua completamente.....

---

### Post by luks911 on 2008-12-03
Los que tienen el problema en el booteo, ¿conectada a la electricidad o usando la batería o ambos?

---

### Post by vk-cdg on 2008-12-04
En mi caso fue enchufado!

---

### Post by luks911 on 2008-12-04
> **vk-cdg said:**
> En mi caso fue enchufado!

Ah, OK. Porque una de las soluciones que mencionan en el bug es enchufarla para bootear y como tengo también la Nvidia MCP67 pero siempre la uso sin la batería...

Ahora veo que dice 
```
The main issue has two different workarounds for me:

1. Attach the power cord during boot
2. Add nolapic in kernel options
```

Tal vez habría que probar agregar nolapic, aunque en mi caso no está y funciona.

---

