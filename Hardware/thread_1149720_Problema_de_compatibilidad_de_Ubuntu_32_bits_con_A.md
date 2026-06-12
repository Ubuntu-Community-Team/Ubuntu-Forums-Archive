---
title: "Problema de compatibilidad de Ubuntu 32 bits con AMD 64 X2? Instalo Ubuntu 64bits?"
date: 2009-05-05
forum: Hardware
---

### Post by Tenisfan on 2009-05-05
Hola gente, abro un nuevo post sobre un [problema]("http://ubuntuforums.org/showthread.php?t=1146656") que tengo en con el manejo de las ACPI en mi Ubuntu 9.04 de 32 bits Ahora trataré de explicitar mas claramente de que se trata el problema, creo que tendré que reinstalar poniendo una versionde 64 bits. Por favor ayuda, es la primera vez que me meto en Linux!
[U]
[FONT=Arial Black]Equipo:[/FONT][/U] El equipo sobre el cual está instalado el SO es una notebook marca Toshiba Satellite A215-S5822, con las siguientes características:

[LIST]
[*]Procesador AMD Turion 64X2 TL60, 2.00GHz, Chipset AMD M690v (Bios Phoenix v1.80), 2Gb Ram, 200 Gb HD, placa grafica ATI X1200, Atheros® 802.11a/g/n wireless-LAN, 10/100 Ethernet, card reader 5 in 1, webcam, puerto firewire.
[/LIST]
[FONT=Arial Black]_Que funciona?_: [/FONT]
Instalación sin problemas, tengo el disco compartido con XP, y otra partición mas de respaldo. Funciona el video, el sonido, wifi, placa de red, la web cam, todo sin problemas, los puertos USB. No tuve que poner ningun driver adicional. (El card reader no funciona, el firewire no lo probé)
[FONT=Arial Black]_Problema_s: [/FONT]
1-Ubuntu no "detecta" la batería: pongo entre comillas, porque el sistema sigue funcionando lo mas bien, pero me aparece el ícono de enchufado a la red AC, y por lo tanto no me avisa cuanta batería me queda. Cuando voy a administración de energía, no aparece ningún apartado para la batería (es como si fuese un equipo desktop)
2-No puedo ajustar el brillo del monitor, ni el volumen con la ruedita, tampoco funciona la tecla Fn, para ajustar el brillo, en otras cosas.

Uno de los foreros me dijo que podía ser lo de las ACPI, asi que me puse a investigar todo el fin de semana, llegué a la conclusión de que todos esos problemas definitivamente estan relacionados con las benditas ACPI, por alguna razón se produce un fallo cuando esta cargando el SO y se producen los problemas. Cuando carga, me muestra esta pantalla:
> Boot from (hd0,5) ext3 c9e177e5-4d6a-a255.41fd71394ef0
Starting up...
[   0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[   0.024001] ..MP-BIOS bug: 8254 timer not conected to IO-APIC
[   0.000000] PNPBIOS fault..attempting recovery.
[   0.000000] PnPBIOS: Warning! Your PnP BIOS caused a fatal error.Attempting to continue
[   0.000000] PnPBIOS: Ypu may need to reboot with the "pnpbios=off" option to operate stably
[   0.000000] PnPBIOS: Check with your vendor for an updated BIOS
[   0.000000] PnPBIOS: get_dev_node: unexpected status 0x37
[   0.000000] ata1: softreset failed (device not ready)Ahora, resulta que decidí probar con un CD de la versión 8.04 de 64 bits, y ahi si funcionaron las ACPI!!!:confused: Entonces me baje la 9.04 de 64 bits y tambien anduvo perfecto!! 
Pero estuve leyendo que no hay muchos programas desarrollados para 64 bits, que todavía hay ciertas incompatibilidades con java y flash, y cosas por el estilo...
[FONT=Arial Black][SIZE=2]La pregunta es, entonces, ¿podré arreglar el problema en 32 bits? ¿O debo necesariamente instalar la versión de 64 bits? Y si no me queda otra, ¿Cómo hago para desinstalar la de 32bits?[/SIZE][/FONT]
[FONT=Arial]Veo que el post se hizo enorme, perdón por ello:(, pero me pareció q en el anterior no se habia entendido el problema, y realmente quiero resolverlo, desde ya gracias a la comunidad por ayuda, y espero sus respuestas!![/FONT]
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by luks911 on 2009-05-05
A ver, primero probá con esto. Entrá al GRUB, lo hacás al inicio presionando Esc. Editá la línea que se parece a esta

```
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/sda1 ro quiet splash 
```

sólo se parece, la tuya va ser distinta. Para editarla te parás sobre la línea y presionás "e". Al final de la línea agregá

```
pnpbios=off
```

Le das enter, y apretás "b" para bootear.
Lo vi en Ubuntu-es para un problema parecido que recibe un mensaje de error como el tuyo. Si funciona avisá y hay que editar el GRUB de forma definitiva. Si no sirve, al reiniciar el cambio que hiciste no se mantiene.

Para más detalle sobre los cambios en las opciones del GRUB: [http://doc.ubuntu-es.org/GRUB#Modificar_las_opciones_de_inicio](http://doc.ubuntu-es.org/GRUB#Modificar_las_opciones_de_inicio)

Si tenés que instalar 64bits, con pisar la instalación anterior alcanza, no se desinstala.

---

### Post by oktubrer on 2009-05-06
Yo uso hace rato la versión de 64bits, creo que desde Hardy, y sacando el flash, que al principio tenía su vuelta para hacerlo funcionar, nunca tuve problemas.  
Ahora ni siquiera el flash me genera inconvenientes, y con respecto a software te diría que están disponibles el 95% como mínimo que los disponibles para 32bits.  Eso sí, es una desktop, quizás en notebook hay algún otro tema, tanto no sabría decirte.

---

### Post by faktorqm on 2009-05-08
Yo igual hay algo que no me termina de cerrar. El reconocimiento o no de las funciones ACPI no dependen de la arquitectura del microprocesador ni del software asociado a eso, es decir, si tenes un micro de 64 bits e instalas algo de 32 bits o de 64 bits el reconocimiento de hardware por parte de este sistema operativo deberia ser el mismo (sea gnu/linux o no).

Mi pregunta es, probaste con la misma versión de ubuntu (quiero creer que 9.04) en 32 bits y en 64 bits, y cuando instalaste 64bits te anduvo y con la de 32 bits no? 

Para mi que el arreglo (o el problema) es otro y no depende de la arquitectura del microprocesador. Salu2!

---

### Post by fmsismo on 2009-05-08
> **faktorqm said:**
> Yo igual hay algo que no me termina de cerrar. El reconocimiento o no de las funciones ACPI no dependen de la arquitectura del microprocesador ni del software asociado a eso, es decir, si tenes un micro de 64 bits e instalas algo de 32 bits o de 64 bits el reconocimiento de hardware por parte de este sistema operativo deberia ser el mismo (sea gnu/linux o no).

Mi pregunta es, probaste con la misma versión de ubuntu (quiero creer que 9.04) en 32 bits y en 64 bits, y cuando instalaste 64bits te anduvo y con la de 32 bits no? 

Para mi que el arreglo (o el problema) es otro y no depende de la arquitectura del microprocesador. Salu2!

Es como dice faktorqm no es problema del procesador.  El problema del chipset.  Por más que saltes al 64 o 32 bit vas a estar en la misma.  Si no lo hiciste, proba con la versión 9.04 que es la más nueva e incorporó drivers nuevos.

Saludos

---

### Post by Tenisfan on 2009-05-08
> **faktorqm said:**
> Yo igual hay algo que no me termina de cerrar. El reconocimiento o no de las funciones ACPI no dependen de la arquitectura del microprocesador ni del software asociado a eso, es decir, si tenes un micro de 64 bits e instalas algo de 32 bits o de 64 bits el reconocimiento de hardware por parte de este sistema operativo deberia ser el mismo (sea gnu/linux o no).

Mi pregunta es, probaste con la misma versión de ubuntu (quiero creer que 9.04) en 32 bits y en 64 bits, y cuando instalaste 64bits te anduvo y con la de 32 bits no? 

Para mi que el arreglo (o el problema) es otro y no depende de la arquitectura del microprocesador. Salu2!
Mira, la verdad que mis conocimientos sobre hardware y software en general son las de un usuario medio, así que una respuesta técnica no te puedo dar. Lo que te puedo decir es que efectivamente me bajé primero la versión 9.04 de 32 bits y las funciones ACPI NO andaban, desconozco a que se debe el problema. Probé con la versión anterior, también de 32 y nada, seguía todo igual. Me leí cualquier cantidad de infoen cuanto foro había para tratar de encontrar alguna solución y no encontré nada, aunque varias personas tenían el problema que les mencioné. Por último probé una Hardy Heron de 64...Y ahí si me andaban las funciones!! Así que me bajé la 9.04 de 64 bits, y anduvo todo fenómeno!
Lo que si comprobé yo mismo,  es que la versión de 32 bits en otra notebook toshiba parecida a la mía pero con micro Intel si andaban las ACPI, por lo que deduzco que hay alguna diferencia entre los micro de intel y AMD (o en sus complementos, llámese motherboard, chipset, la BIOS, etc..) que hace que la versión de 32 bits ande bien en uno y en otro no.
Lo que si está claro es que la mayoría de los fabricantes diseñan para Windows y no para Linux, en los soportes oficiales no encontré nada de nada...
Con respecto al software, hasta ahora no tuve mayores problemas corriendo en 64 bits, noto que consume un poquito mas de RAM, se me colgó un par de veces [COLOR=Red](off topic: cual es el Ctrl-Alt-Del de Uuntu??)[/COLOR]pero el desempeño del sistema tampoco es muy diferente al de 32 bits, por lo menos en las aplicaciones usuales.
La unica falla que encuentro es el tema del video, no se desempeña tan bien como en la de 32 bits, tengo como un destello del monitor cada tanto, como si titilara la imagen, pero voy a abrir otro post para comentarlo. 
Gracias por las respuestas, Saludos

---

### Post by Tenisfan on 2009-05-08
Bueno, antes que nada gracias a todos los que se tomaron la molestia de responder el post, con este doy por finalizado (y resuelto) el tema de las Funciones ACPI. 
Como puse en la respuesta anterior, no tengo idea a que se debe el problema, pero la solución que yo encontré es instalar directamente la versión de 64 bits. 
En resumen, puedo decirles que la notebook anda casi al 100%, tengo audio, video, wifi, red, webcam, los botones multimedia, el lector de tarjetas lee SD card (las XD no me las toma, las de Sony no las probé)...casi casi todo:)!

Hata ahora me corrieron casi todos los programas (se me colgaron un par de jueguitos), pero en general, bastante bien, se ve que mejoró mucho el desarrollo en 64 bits, aparte la mayoría de los repositorios se consiguen
Bueno, espero que este post le sirva al que tenga un problema parecido, saludos!!

---

### Post by guillermolisi on 2009-05-09
> **Tenisfan said:**
> Bueno, antes que nada gracias a todos los que se tomaron la molestia de responder el post, con este doy por finalizado (y resuelto) el tema de las Funciones ACPI. 
Como puse en la respuesta anterior, no tengo idea a que se debe el problema, pero la solución que yo encontré es instalar directamente la versión de 64 bits. 
En resumen, puedo decirles que la notebook anda casi al 100%, tengo audio, video, wifi, red, webcam, los botones multimedia, el lector de tarjetas lee SD card (las XD no me las toma, las de Sony no las probé)...casi casi todo:)!

Hata ahora me corrieron casi todos los programas (se me colgaron un par de jueguitos), pero en general, bastante bien, se ve que mejoró mucho el desarrollo en 64 bits, aparte la mayoría de los repositorios se consiguen
Bueno, espero que este post le sirva al que tenga un problema parecido, saludos!!
Me alegro que paraceria lo tengas solucionado.

Igual el mensaje que comentaste te daba al inicio te indicaba que el problema no estaba en una supuesta incompatibilidad con el procesador sino con el chipset/BIOS (como ya te han comentado muy bien).
> [   0.000000] PnPBIOS: Ypu may need to reboot with the "pnpbios=off" option to operate stably
[   0.000000] PnPBIOS: Check with your vendor for an updated BIOSMe parece que era lo que tenias que hacer/probar para usar 32 bits con esa maquina antes de pasar a 64.

---

### Post by ing.jose on 2010-02-22
> **guillermolisi said:**
> Me alegro que paraceria lo tengas solucionado.

Igual el mensaje que comentaste te daba al inicio te indicaba que el problema no estaba en una supuesta incompatibilidad con el procesador sino con el chipset/BIOS (como ya te han comentado muy bien).
Me parece que era lo que tenias que hacer/probar para usar 32 bits con esa maquina antes de pasar a 64.
BUENAS AMIGOS HE LEIDO LOS PROBLEMAS Q ESTAMOS FRECUENTANDO CON EL PROCESADOR **AMD TURION 64x2,  **ACABO DE INSTALAR LA VERSION 9.04 "AMD64", YA QUE ESTE ES EL CONJUNTO DE INSTRUCCIONES ADECUADA PARA ESTE PROCESADOR QUERIA SABER Q USTEDES OPINA Y RECOMIENDA?...GRACIAS

PO: SON UN USUARIO NUEVO EN LINUX

---

### Post by Tosh78 on 2010-02-24
Yo tengo instalada la version 9.10 de 64 bits y me funciona perfecto. Hasta ahora no tuve ningun problema de compatibilidad. Eso si, el uso que le doy es bastante tranquilo: peliculas, musica, ofimatica e internet.

---

