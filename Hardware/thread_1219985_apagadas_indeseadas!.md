---
title: "apagadas indeseadas!"
date: 2009-07-22
forum: Hardware
---

### Post by granjero on 2009-07-22
buenas, les cuento lo que me anda sucediendo...

primero mi la descripción de la pc:

soft:
Ubuntu  9.04
nucleo linux 2.6.28-13-generic

hard:
ram: 2gb (dos plaquitas de 1gb)
procesador: AMD 64 X2 Dual Core 5200+
HD: 360gb sata. 
video: Nvidia 8600gt (con sus driver privativos instalados correctamente)

Instalé un juego (el lineage II)(corre via wine) y cuando estoy jugando al rato la pc se apaga como si nada.

mis teorías son o placa de video o algún problema con la ram.

lo raro es que cuando vuelvo a encender la pc arranca y no tira ningún error, ni me dice la pc se apagó incorrectamente ni nada...

ayer le corrí el memtest desde el grub y a la mitad del proceso la pc se apagó. Eso quiere decir que alguna ram está rota?

a alguien se le ocurre que probar? o que archivo ver para encontrar el problema!

muchas gracias!

salud!

pd: En güindous con juegos similares me había pasado algo así pero se lo adjudique a bill gates... en ubuntu con el uso de escritorio anda de lujo la máquina!

---

### Post by staar on 2009-07-22
si tuvieras problemas de memoria, lo más probable es que tuvieras errores, no que se apage la pc (aunque puede pasar)

se me ocurren dos cosas, que la fuente esté fallando o calentando, o que sea el procesador el que se esté recalentando...

verificá la fuente primero, si está limpia, si el ventilador anda, si está tirando voltajes dentro de lo aceptable...

fijate también el ventilador del procesador, limpialo y aceitalo bien...

podés usar algún programita para verificar el uso de procesador, las temperaturas y los voltajes, y al mismo tiempo exigir la pc (con un juego por ejemplo) para darte cuenta que puede estar pasando...

saludos

---

### Post by guillermolisi on 2009-07-22
Mas informacion en un caso similar en este thread:

[http://ubuntuforums.org/showthread.php?t=1203026](http://ubuntuforums.org/showthread.php?t=1203026)

---

### Post by granjero on 2009-07-22
primero me disculpo porque en realidad el título del post debería haber sido "***_reinicios indeseados_***". la máquina no queda apagada. se apaga de repente y se enciende.

les cuento un poco más sobre el problema.

el mother de la máquina es un "asus m3a" 

en la bios le desactive el monitor de temperatura del chip hace mucho tiempo porque siempre me daba temperaturas elevadísimas y creía que ese era el problema. hasta que me compré un tester con termómetro y nunca tuve lecturas ni cercanas a los 109º C que me decía la bios...
la temperatura la medi entre los fierritos del disipador del chip 

viendo la lectura de 109ºC toque el disipador del chip y ni quemaba. 


Por otro lado previo a la actualización a JJ había hecho un conky para que me muestre las temperaturas de lsmodules o algo así y también me daba temperaturas raras. algunas bajo cero e instantaneamente de 80ºC.

creo que el mother no lee bien las temp del chip

en el GUI de nvidia-config la temperaruta de la placa de video no sube de los 54ºC. 

La fuente es una fuente de 450W que vino con el gabinete todo marca vitsuba. No calienta y el interior del gabinete lo mantengo bastante limpio pasándole la aspiradora cada unos meses y limpieando bien todos los ventiladores. 

nunca tuve temperaturas elevadas como cuenta el muchacho en el link que me paso guillermolisi.

Hoy cuango llegue a casa le voy a sacar una RAM y ver si se apaga y cambiarla por la otra y ver que pasa para descartar que un modulo de la ram este chongo....

qué mas puedo probar?

gracias!

---

### Post by guillermolisi on 2009-07-22
> **granjero said:**
> primero me disculpo porque en realidad el título del post debería haber sido "***_reinicios indeseados_***". la máquina no queda apagada. se apaga de repente y se enciende.

les cuento un poco más sobre el problema.

el mother de la máquina es un "asus m3a" 

en la bios le desactive el monitor de temperatura del chip hace mucho tiempo porque siempre me daba temperaturas elevadísimas y creía que ese era el problema. hasta que me compré un tester con termómetro y nunca tuve lecturas ni cercanas a los 109º C que me decía la bios...
la temperatura la medi entre los fierritos del disipador del chip 

viendo la lectura de 109ºC toque el disipador del chip y ni quemaba. 


Por otro lado previo a la actualización a JJ había hecho un conky para que me muestre las temperaturas de lsmodules o algo así y también me daba temperaturas raras. algunas bajo cero e instantaneamente de 80ºC.

creo que el mother no lee bien las temp del chip

en el GUI de nvidia-config la temperaruta de la placa de video no sube de los 54ºC. 

La fuente es una fuente de 450W que vino con el gabinete todo marca vitsuba. No calienta y el interior del gabinete lo mantengo bastante limpio pasándole la aspiradora cada unos meses y limpieando bien todos los ventiladores. 

nunca tuve temperaturas elevadas como cuenta el muchacho en el link que me paso guillermolisi.

Hoy cuango llegue a casa le voy a sacar una RAM y ver si se apaga y cambiarla por la otra y ver que pasa para descartar que un modulo de la ram este chongo....

qué mas puedo probar?

gracias!
Ademas de revisar las memorias, fijate que entre las aletas de los disipadores de la motherboard no haya tierra acumulada. Eso le quita superficie de disipacion.

El disipador de la CPU estara haciendo contacto pleno con el encapsulado del procesador ? El disipador podria estar frio porque la transferencia es defectuosa.

Si bien las fuentes de Vitsuba me parecen razonablemente buenas, no seria la primera vez que una falla, particularmente cuando el consumo de corriente es intenso (por la placa de video con la aceleracion 3D al maximo).

---

### Post by granjero on 2009-07-23
buenas...
les cuento como viene el asunto!

abrí la máquina, le pegue una súper limpiada, saque las dos memorias, les pasé la aspiradora por los slots y las puse al revés de como estaban. una limpieza general a ventiladores y al disipador del chip.

> El disipador de la CPU estara haciendo contacto pleno con el encapsulado del procesador ? El disipador podria estar frio porque la transferencia es defectuosa.

todo lo anterior lo hice antes de leerte ché! igualmente ayer puse la pc a andar con dos juegos a la vez, uno en cada escritorio....  les dejo una snapshot del monitor de sistema...


en promedio los cpu durante una hora anduvieron al 80% y la ram al 50% máximo...

no se apagó ayer... hoy no tengo tiempo de seguir haciendo pruebas pero seguro mañana o el sábado la pongo a andar como loca a ver si se reinicia de nuevo....

---

### Post by guillermolisi on 2009-07-23
Antes de que hagas algo mas :), limpiaste la fuente ?

Mira que no es lo mismo soplar que aspirar. Para que la maquina quede libre de polvo, pelusas y hollin, nada mejor que el aire comprimido (esto ya lo leiste en el otro thread).

---

### Post by granjero on 2009-07-24
la fuente no la desarmé pero le saque un montón de pelusa de pelo de gato que tenía en el ventilador que saca aire pa fuera!

lo del aire comprimido lo leí pero no tengo compresor... voy a ver si un amigo que tiene un aerógrafo me presta el motorcito...

ahora que llegó el findesemana pensaba darme una panzada de juegos a ver que le pasa a la pc!

muchas gracias por sus respuestas!

---

### Post by guillermolisi on 2009-07-24
> **granjero said:**
> la fuente no la desarmé pero le saque un montón de pelusa de pelo de gato que tenía en el ventilador que saca aire pa fuera!

lo del aire comprimido lo leí pero no tengo compresor... voy a ver si un amigo que tiene un aerógrafo me presta el motorcito...

ahora que llegó el findesemana pensaba darme una panzada de juegos a ver que le pasa a la pc!

muchas gracias por sus respuestas!
No te hagas muchas ilusiones con el aerografo. Antes de terminar comprandome un compresor hice muchos experimentos, con el fin de ahorrarme unos morlacos, y conclui que era La Herramienta.

---

