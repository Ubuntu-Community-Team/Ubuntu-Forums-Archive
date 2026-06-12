---
title: "Compaq Armada E500 ó deshabilitar USB via OS"
date: 2009-08-30
forum: Hardware
---

### Post by juandeargentina on 2009-08-30
Estimados, ¿como les va?

Les comento...se me rompió la "patita" interna del usb en una Note Armada E500...esto repercute en mi equipo ya que no tengo instalado las X (tengo instalado la ultima versión de Ubuntu Server) y esta haciendo constantemente loop en la pantalla con la siguiente leyenda.

"[##.#######] hub 1-0:0.1.0: over_current change on port 1]"
y asi infinitamente haciendo imposible loguearse. 

Ya por BIOS intente deshabilitarlo pero hay de todas las opciones MENOS la de deshabilitar USB (tener en cuenta que es un equipo muy viejo).

Me imagino que tendré que bootear con algun live CD y solucionarlo via X de esta manera si puedo acceder (tenía Xubuntu instalado antes).

Les agradezco de antemano,
abrazo

---

### Post by Mauro22 on 2009-08-30
En todas las consolas de hace lo mismo? 

Alt+F1, Alt+F2, Alt+F3 etc hasta el 6 son consolas...


:confused:

---

### Post by juandeargentina on 2009-08-30
> **Mauro22 said:**
> En todas las consolas de hace lo mismo? 

Alt+F1, Alt+F2, Alt+F3 etc hasta el 6 son consolas...


:confused:

en todas....:sad:

Por eso es que digo que la solución tiene que venir por algun archivo de configuración que deshabilite la opcion de que tire mensajes de error de hw por consola ¿Me explico?

---

### Post by staar on 2009-08-30
probaste evitando que se cargen los módulos de usb, mandándolos a la blacklist?

saludos

---

### Post by juandeargentina on 2009-08-30
> **staar said:**
> probaste evitando que se cargen los módulos de usb, mandándolos a la blacklist?

saludos

Gracias por responder.

¿Como hago eso que decis?

---

### Post by staar on 2009-08-30
agregando el nombre de el/los módulo/s (supongo que será uhci_hcd si es USB 1.1, ehci_hcd si es 2.0, no sé si usbcore también) al archivo /etc/modprobe.d/blacklist.conf precedido de la palabra *blacklist*...

otra forma es usando la opción de inicio del kernel *nousb* (supongo que no hace falta explicar que hace :-P), en el grub, antes de iniciar, apretás *e* para editar la entrada, te movés hasta la línea que empieza con *kernel*, apretás de nuevo *e*, y al final agregás *nousb*, después apretás *b* para bootear, para que el cambio sea permanente hacés lo mismo en el menu.lst

saludos

---

### Post by juandeargentina on 2009-08-30
> **staar said:**
> agregando el nombre de el/los módulo/s (supongo que será uhci_hcd si es USB 1.1, ehci_hcd si es 2.0, no sé si usbcore también) al archivo /etc/modprobe.d/blacklist.conf precedido de la palabra *blacklist*...

otra forma es usando la opción de inicio del kernel *nousb* (supongo que no hace falta explicar que hace :-P), en el grub, antes de iniciar, apretás *e* para editar la entrada, te movés hasta la línea que empieza con *kernel*, apretás de nuevo *e*, y al final agregás *nousb*, después apretás *b* para bootear, para que el cambio sea permanente hacés lo mismo en el menu.lst

saludos

Como dicen los americanos...."works like a charm" (o algo asi).

Probé directamente editando la linea con nousb 

pero como es de esperarse, en el boteo me tiro un error (creo que en el disco, nose) 

Ahora seguramente si no lo puedo encontrar en internet lo vuelvo a postear en otro thread. No lo hago aca para no confundir y mantener cierto orden.

Desde ya nuevamente muchas gracias a vos y a todos los que intentaron ayudarme, muy buena la ayuda.

Saludos

---

### Post by Hei Ku on 2009-08-30
Pero te funcionó o no? No me quedó claro. 

Y si te anduvo, cuál fue la opcion que te anduvo?

Asi otros pueden aprovechar tu experiencia.

---

### Post by juandeargentina on 2009-08-30
> **Hei Ku said:**
> Pero te funcionó o no? No me quedó claro. 

Y si te anduvo, cuál fue la opcion que te anduvo?

Asi otros pueden aprovechar tu experiencia.

Perdon, debí haber sido mas claro en mi respuesta.

La solución que funcionó fue editar el grub,
antes de que comience a cargar Ubuntu apretas ESC para ingresar al GRUB.

Luego sobre la linea que dice kernel apretas e 
al final de la linea pones nousb y luego apretas ENTER
despues b

ahora ya no me aparece mas el error de loop constante.

---

### Post by juandeargentina on 2009-09-02
Estimados, 
lamento molestarlos nuevamente.

Luego de aplicar la solución descripta en el post anterior tuve otro problema...se colgaba en la parte de Loading Hardware Drivers. 
Como esto ya me había ocurrido previamente con la versión Desktop de Jaunty procedí a resolverlo de la misma manera que lo había hecho antes. Reinstalar el sistema con la 8.04

Con eso resolví ese problema pero lamentablemente volvió a surgir el problema original de este thread y esta vez no funcionó editando el Grub como me indicaron. :(

Por lo que vuelvo al problema original esta vez con otra versión UBUNTU Server 8.04 LTS

Esta vez probe editando el GRUB y poniendo en la blacklist esto:

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbcore
blacklist usbkbd
blacklist uhci_hcd

¿Alguna otra idea? :confused:

---

### Post by guillermolisi on 2009-09-02
Es que a mi entender faltan exponer los parametros del Grub con que inicia JJ e II, como para ver si hay alguna diferencia del tipo noacpi, pci=<algo>, etc.

---

### Post by juandeargentina on 2009-09-02
> **guillermolisi said:**
> Es que a mi entender faltan exponer los parametros del Grub con que inicia JJ e II, como para ver si hay alguna diferencia del tipo noacpi, pci=<algo>, etc.


Ok, entiendo tu punto pero no sé como seguir o brindar que tipo de info adicional.

---

### Post by guillermolisi on 2009-09-02
> **juandeargentina said:**
> Ok, entiendo tu punto pero no sé como seguir o brindar que tipo de info adicional.
Por ejemplo, asi:

En una consola/terminal ingresas ```
less /boot/grub/menu.lst
``` y pegas la salida para que la veamos todos.
Lo que me interesa ver son las lineas como esta > kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=72c5d05e-b996-4634-9cd3-130716ed6404 ro **acpi=off** quiet splash donde destaque una opcion sobre ACPI activada en mi maquina cuando inicio con uno de los kernels que tengo.

Si tenes mas de un kernel me gustaria confirmar si hay diferencias por ese lado.

---

### Post by juandeargentina on 2009-09-02
> **guillermolisi said:**
> Por ejemplo, asi:

En una consola/terminal ingresas ```
less /boot/grub/menu.lst
``` y pegas la salida para que la veamos todos.
Lo que me interesa ver son las lineas como esta  donde destaque una opcion sobre ACPI activada en mi maquina cuando inicio con uno de los kernels que tengo.

Si tenes mas de un kernel me gustaria confirmar si hay diferencias por ese lado.

Guillermo, gracias por responder! te paso lo que me pediste.

[menu.lst]
title           Ubuntu 8.04.3 LTS, kernel 2.6.24-24-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-24-server root=UUID=303cc8e7-7e4d-437d-a982-8b6c17039150 ro quiet splash nousb
initrd          /boot/initrd.img-2.6.24-24-server
quiet

title           Ubuntu 8.04.3 LTS, kernel 2.6.24-24-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-24-server root=UUID=303cc8e7-7e4d-437d-a982-8b6c17039150 ro single
initrd          /boot/initrd.img-2.6.24-24-server

title           Ubuntu 8.04.3 LTS, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
[/menu.lst]

Como veras tambien esta la linea nousb que agregué.

---

### Post by guillermolisi on 2009-09-02
Bueno, no tenes nada raro y un solo kernel para probar.

La informacion que he visto sobre el caso habla de usar las opciones que estas utilizando, agregar a la blacklist las unidades USB y remover de memoria los modulos que manejan los USB de la maquina.

Sobre esta ultima estrategia hay quienes dicen que cuando colocan el pendrive el modulo se vuelve a cargar por efecto del automount.

La verdad, se me quemaron los papeles y lo que mas me llama la atencion es ese comportamiento erratico que llevo a pensar que la solucion nousb funcionaba.

---

### Post by juandeargentina on 2009-09-02
> **guillermolisi said:**
> Bueno, no tenes nada raro y un solo kernel para probar.

La informacion que he visto sobre el caso habla de usar las opciones que estas utilizando, agregar a la blacklist las unidades USB y remover de memoria los modulos que manejan los USB de la maquina.

Sobre esta ultima estrategia hay quienes dicen que cuando colocan el pendrive el modulo se vuelve a cargar por efecto del automount.

La verdad, se me quemaron los papeles y lo que mas me llama la atencion es ese comportamiento erratico que llevo a pensar que la solucion nousb funcionaba.

Claro, yo pienso lo mismo, me llamo muchisimo la atención de porque una distribución si y otra no (mas que distribución kernel seria)

La ultima opción, mas que solución sería un parche. 

¿No sabes como puedo hacer para que el...¿kernel? no me tire mas esos errores por consola? 
O sea, que de alguna manera, los ignore, en vez de tirarlos por tty los tire en null.

Desde ya te agradezco.

---

### Post by guillermolisi on 2009-09-02
> **juandeargentina said:**
> Claro, yo pienso lo mismo, me llamo muchisimo la atención de porque una distribución si y otra no (mas que distribución kernel seria)

La ultima opción, mas que solución sería un parche. 

¿No sabes como puedo hacer para que el...¿kernel? no me tire mas esos errores por consola? 
O sea, que de alguna manera, los ignore, en vez de tirarlos por tty los tire en null.

Desde ya te agradezco.
Ahora que lo mencionas, entre la 8.10 y la 9.04 hay diferencias, sobre todo en el kernel y ahi es donde pudo haber iniciado con algun parametro especial en el Grub.
Pense que tenias un kernel de cada version, por eso mi mensaje anterior sobre las opciones de inicio en el Grub.

Si no tenes forma de deshabilitar los USB desde el BIOS, la forma mas prolija y definitiva seria arreglar la maquina :) porque esos conectores estan en corto (el mensaje que te da lo dice clarito: exceso de consumo de corriente. Y tenes suerte que no se te apaga la maquina).

Creo que si redireccionas esos errores a /dev/null por ahi se ira el resto de los mensajes y eso si que no es bueno para nada.

---

### Post by juandeargentina on 2009-09-03
> **guillermolisi said:**
> Ahora que lo mencionas, entre la 8.10 y la 9.04 hay diferencias, sobre todo en el kernel y ahi es donde pudo haber iniciado con algun parametro especial en el Grub.
Pense que tenias un kernel de cada version, por eso mi mensaje anterior sobre las opciones de inicio en el Grub.

Si no tenes forma de deshabilitar los USB desde el BIOS, la forma mas prolija y definitiva seria arreglar la maquina :) porque esos conectores estan en corto (el mensaje que te da lo dice clarito: exceso de consumo de corriente. Y tenes suerte que no se te apaga la maquina).

Creo que si redireccionas esos errores a /dev/null por ahi se ira el resto de los mensajes y eso si que no es bueno para nada.

Guillermo, gracias por responder, evidentemente el mensaje de nousb en el 8.04 no tiene el mismo efecto en Jaunty. Pero SI sabemos que en Jaunty funciona. 
Conclusión: existe la posibilidad de habilitar dicha opción a través del kernel del equipo.

Si bien sabemos que 8.04 es una versión anterior que Jaunty no creo que ese parametro "no exista". Y ahí es donde quiero llegar.

Por lo que veo, no es algo sencillo, lo que pido a los foristas es si de ultima me pueden guiar de como buscar ese parametro en la web, ya que al buscarlo generalmente me manda a cualquier lado (la mayoría es de como deshabilitar para los pendrives). 

Lo de arreglarla no es una opción porque el usb esta soldado a la mother y arreglar eso me sale el precio de una notebook nueva (ni soñando!!). 

Resumiendo son dos preguntas.

1) como "busco" para esa versión la documentación el homonimo de Jaunty "nousb"

2) Como puedo mandar esos mensajes a algo como /dev/null 
Esto lo usaria unicamente en las situaciones que 'si o si' necesite loguearme a través de consola.

Y si pregunto en el foro de inglés de Ubuntu ¿tendré mas suerte?

Gracias de nuevo Guillermo por tu tiempo!

---

### Post by guillermolisi on 2009-09-03
He visto comentarios sobre nousb con fecha 2005, asi que por lo menos en esa epoca ya existia. Inclusive he leido arreglos en el kernel a raiz de haber incorporado esa opcion.

Si los mensajes los envia el kernel, no veo forma de distinguir entre uno relacionado con usb y otro relacionado con otro driver/hardware de la maquina. Todos irian por igual a /dev/null (salvo que me equivoque en mi apreciacion).

Busque en Google usando "how to disable usb", "disabling usb" y alguna que otra variante en funcion de lo que recibia como resultado. No me fije en Ubuntu Forums (recomendable antes de abrir un thread en Ingles).

---

### Post by juandeargentina on 2009-09-03
> **guillermolisi said:**
> He visto comentarios sobre nousb con fecha 2005, asi que por lo menos en esa epoca ya existia. Inclusive he leido arreglos en el kernel a raiz de haber incorporado esa opcion.

Si los mensajes los envia el kernel, no veo forma de distinguir entre uno relacionado con usb y otro relacionado con otro driver/hardware de la maquina. Todos irian por igual a /dev/null (salvo que me equivoque en mi apreciacion).

Busque en Google usando "how to disable usb", "disabling usb" y alguna que otra variante en funcion de lo que recibia como resultado. No me fije en Ubuntu Forums (recomendable antes de abrir un thread en Ingles).

Bueno no van a creerlo pero lo solucioné.

¿Que hice? 
sudo apt-get upgrade
por lo que leí hizo algún upgrade al kernel pero lo raro es que no le cambio la versión me sigue apareciendo 2.6.24-24 Por lo que en conclusión no tengo ni idea porque se solucionó. 

Hice un homero, 
muchas gracias a todos!

---

### Post by guillermolisi on 2009-09-03
> **juandeargentina said:**
> Bueno no van a creerlo pero lo solucioné.

¿Que hice? 
sudo apt-get upgrade
por lo que leí hizo algún upgrade al kernel pero lo raro es que no le cambio la versión me sigue apareciendo 2.6.24-24 Por lo que en conclusión no tengo ni idea porque se solucionó. 

Hice un homero, 
muchas gracias a todos!
Por lo pronto aplicaste los ultimos parches de seguridad para kernel Linux 2.6.

Seguro que ahora funciona bien ?

---

### Post by juandeargentina on 2009-09-04
> **guillermolisi said:**
> Por lo pronto aplicaste los ultimos parches de seguridad para kernel Linux 2.6.

Seguro que ahora funciona bien ?

Recontra seguro, y no tuve que reiniciar ;)

(igual despues reinicie para comprobar)

---

