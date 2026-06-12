---
title: "presentarme y consultar por wireless"
date: 2008-01-18
forum: Hardware
---

### Post by ojvulluz on 2008-01-18
hola a todos, sos Osvaldo Vülluz, desde Mendoza. Uso este increible OS desde hace unos tres años, y recientemente he adquirido una portatil (olivetti 520, core 2 duo, 120Gb, 1 gb RAM) con wVista, que duró apenas segundos. Ya esta corriendo Ubuntu 7.10 (32bits version), con casi todo andando, solo me falta, (y me es esencial para poder por fin renunciar a speedy) configurar la placa wireless, una LiteOn WN6301L, con chipset realtek RTL8187B. Encontré unas cuantas soluciones posibles en el foro (el driver modificado por xcuervo, el uso de ndiswrapper con el driver nativo de windows 98...) pero ninguna hizo funcionar la placa, es más, lspci, lsusb y lshw no dan cuenta de que la placa exista. Debería ponerse en funcionamiento con la combinación de teclas Fn+F10,pero, nada de nada.
ruego a los miembros del foro que tengan la misma notebook me ayuden a solucionar esto, incluso reinstalaría todo de nuevo de ser necesario. Si necesitan copia de los archivos de configuración, los posteo.

Agradecido desde ya, los saludo desde el pie de la cordillera de los Andes.

---

### Post by margori on 2008-01-18
Me parece muy extraño que no te reconozca una placa PCI.

Segun lo que lei en [esta]("http://ubuntuforums.org/archive/index.php/t-660167.html") pagina, podrias arrancar por actualizar la BIOS.

Buscate tambien en [bugs.launchpad]("https://bugs.launchpad.net/ubuntu/") si existe publicado algun bug sobre esta olivetti.

Segun la lista [ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/") ese chipset esta probado que funciona.

Soy también de Mendoza, Palmira justamente. Si lo necesitas ofresco mi humilde ayuda en forma mas personal.

---

### Post by ojvulluz on 2008-01-19
Hola loco!!

la placa de red no es PCI, es usb (aunque viene onboard, una cosa bien rara)(por lo menos, en windows funciona como un dispositivo USB 2.0).
Respecto a ndiswrapper, el driver existe, se instala bien, pero al darle 

ovulluz@ovulluz-laptop:~$ ndiswrapper -l
net8187b : driver installed
ovulluz@ovulluz-laptop:~$  

deberia decir "hardware present", más no ve la placa, La placa se activa con la combinación de teclas Fn +F10, pero, nada de nada. momentáneamente virtualizaré un windows XP e intentaré que funcione así, pero espero encontrarle la vuelta a la cosa. 

Te agradezco muchisimo tu ayuda, y estamos tan cerca (yo vivo en Godoy Cruz) que no faltará oportunidad de comernos un asadito ubuntero.

saludos

osvaldo.

---

### Post by tato026 on 2008-03-03
Hola a todos!!

Tengo el mismo problema con Olibook 500 y Ubuntu..
ojvulluz encontraste como hacer?? creo que va por el lado de las combinaciones de teclas, pero no encontre todavia como hacer para activar fn+F10. me andan algunas como ser la del sonido y del brillo pero esta justamente no..

Apreciaria si alguien tiene algo al respecto.

Saludos desde la costa patagonica!!

---

### Post by tezequiel on 2008-03-06
Hola gente, éste es mi primer post.
Tengo el mismo problema: Adquirí hace unos días una Olibook 500, y no encuentro manera de activar la wireless. Probé con el driver de Windows y con el driver nativo de XCuervo, pero sigo sin ver la wlan. La combinación Fn+F10 no hace prender la lucesita de la wireless y bueh... Alguno avanzó en algo? 

Saludos!
Ezequiel

---

### Post by jomax01 on 2008-03-13
Hola, te hago una consulta. Yo tambien tengo una olibook 520 y si pude instalar ubuntu con el video bien configurado, pero en las opciones de boteo le tengo que poner **noapic nolapic acpi=off** sino no carga. Obviamente la placa wireless tampoco me anda.
Alguna idea, lo instalaste con las mismas opciones? Avisame pues me urge utilizar linux en esa notebook.

Salu2

JoMaX
[email]jomax01@gmail.com[/email]

---

### Post by niko_3100 on 2008-03-13
Respuesta sacada del usuario apokalyptica79 y que ni da reescribir:

Hola Tosh78, encontré algo a ver si te sirve:
Hacé nano /etc/modules y al final del fichero poné apm power_off=1, lo guardás y lo cerrás.
Ahora tenés que modificar el menu.lst, nano /boot/grub/menu.lst, buscás la opcio con la que carga habitualmente ubuntu y al final de, por ejemplo:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=15397d47-9855-44af-9009-72f157a9b33f ro quiet splash

Ponés lo siguiente acpi=off apm=power-off
Quedando de la siguiente manera:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=15397d47-9855-44af-9009-72f157a9b33f ro quiet splash acpi=off apm=power-off

Guardás y cerrás y para verificar si esto funciona correctamente reiniciá la pc y probalo.
Espero que te sirva.
Saludos.

Gracias a la wiki (que si la conozco) me entere que tanto acpi y apm son los responsables de administrar la energia, por ahi no anda bien con acpi pero si con apm, por lo menos para mi lo mas importante es qeu te deja apagar el monitor despues de un tiempo de estar inactivo, no me interesa tanto qeu apageu el disco o se suspenda bla bla bla...

---

### Post by tezequiel on 2008-03-19
Hola a todos de nuevo.
Alguno avanzó con la placa wireless?

---

### Post by fmercerat on 2008-03-22
Tengo la olibook 520, acabo de probar con mil versiones de ubuntu, por ahora la version mas actual donde me funciono la fn+f10 fue la 7.04, y ni tube tiempo para probar si andaba, por lo que me parece es un problema con el kernel, ya que pude bootear algunas versiones muy viejas de linux sin ningun problema. igualmente me oparece que lo mejor va ser esperar hasta abril con la version final 8.04, si alguien avanza con la placa por favor avise

---

### Post by jomax01 on 2008-03-25
joya.....y si tendremos que esperar la version final de 8.04

Salu2

---

### Post by edmartinmg on 2008-06-11
Hola a todos la solucion para activar wireless en ubuntu u otra distribución es agregar  en el grub en las opciones de arranque del kernel como el siguiente:

/boot/vmlinuz-2.6.24-18-generic root=UUID=98239bd4-1e2c-44ad-8c38-e49178c42e2b ro quiet splash pci=assign-busses apic miantimer idle=poll reboot=cold,hard

eso lo agregas en el menu.lst de grub, para que pueda arrancar sin agregar nada despues.
y ahora si funciona la tecla fn+f10, para activar el inalambrico.

---

### Post by sayid on 2008-06-11
> **edmartinmg said:**
> Hola a todos la solucion para activar wireless en ubuntu u otra distribución es agregar  en el grub en las opciones de arranque del kernel como el siguiente:

/boot/vmlinuz-2.6.24-18-generic root=UUID=98239bd4-1e2c-44ad-8c38-e49178c42e2b ro quiet splash pci=assign-busses apic miantimer idle=poll reboot=cold,hard

eso lo agregas en el menu.lst de grub, para que pueda arrancar sin agregar nada despues.
y ahora si funciona la tecla fn+f10, para activar el inalambrico.

Hola, primero que nada les comento que yo soy dueño de una Olibook 520 hace 2 días (un excelente regalito), y al igual que todos ustedes me encontré con el problema principal, el Live CD de ubuntu 8.04 (Hardy Heron) no booteaba.

La solución mágica para que el CD arranque fue agregarle los siguientes parámetros al kernel: pci=assign-busses apic miantimer idle=poll reboot=cold,hard como lo explicó anteriormente Edmartinmg.

Aún con este cambio la placa de red wireless -con el bendito chipset rtl8187b- seguía sin funcionar, por lo que decidí googlear hasta encontrar la solución. Para que se vayan alegrando les comento que en este momento estoy posteando con mi placa inalámbrica. Para hacerla funcionar probé hacer lo del link [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/) y todo salió andando, aunque con los siguientes inconvenientes:
 * los drivers los levanto a mano cada vez que la uso (momentaneamente).
 * No anda con el protocoo WEP (directamente cuelga la máquina).
 * No anda con ni WPA, ni WPA2.

Para la placa de video funcionaba pero con VESA (ya se habrán dado cuenta con el mplayer lo mal que anda). Es por eso que decidí instalar el driver que da soporte para las placas SiS (lo malo que no es 3D). Si necesitan info sobre esto lo voy a postear.

Por último les digo que estoy luchando con una webcam genius eye, la cual logré hacerla funcionar pero se ve muuuy oscuro (tengo esperanzas en poder pasarle algunos parametros más al driver para que vaya mejorando y se vea como en ese programita (creo que se llama Windows jeje)). 

Todo aquel que quiera ayuda o contribuir con algo de este notebook por favor ayude!

Alguien sabe la descripcion de hardware completa de esta máquina: tiene bluetooth, infrarrojo??

Yo por mi parte todo lo que sepa lo publicaré. 
Saludos,

Sayid...

 
PD: Futuras metas para configurar la Olibook: hacer funcionar placa con drivers 3D, soporte de WEP,WPA,WPA2 de wireless. Si alguien sabe algo por favor avise.

---

### Post by faktorqm on 2008-06-13
Hola, yo acá hice andar la 8168 (creo, ya ni me acuerdo) [http://ubuntuforums.org/showthread.php?t=784616](http://ubuntuforums.org/showthread.php?t=784616) y no tendria problema de hacer un super how to :P para esta placa, pero por supuesto necesito la colaboracion de ustedes por que no tengo la placa xD asi que si estan dispuestos.... manos a la obra!

Aparte necesitaria saber si en la pagina de realtek estan aunque sea alguna version para linux, por que hay algunas placas que no vienen, quiero entrar a realtek.com.tw pero me dice... conexion fallida... estara caida? Salu2!!

---

### Post by sayid on 2008-06-13
Hola a todos nuevamente, después de un largo rato de pruebas me di cuenta que la placa con chipset Realtek 8187b no funcionaba porque la versión de drivers que estaba utilizando era una denominada rtl8187b-modified-jadams-2-1-2008.tar.gz (3728K).

Por tal razón decidí volver a la base del problema, que fue bajarme los drivers de la página de [cuervo]("http://www.datanorth.net/~cuervo/rtl8187b/"). Apliqué el parche que esta en la misma página y pude obtener lo mismo con una GRAN diferencia, el protocolo WEP funcionado :).

Si necesitan ayuda sobre alguna cosa en particular de lo anterior no duden en consultar.

Por ahora sigo a la espera de un driver mejorado, ya que la señal que recibo es pésima (tengo que estar muy cerca del router para lograr que se conecte). 

Lamentablemente ninguna de las desventajas nombradas en mi post anterior se logró reparar :(, a alguien se le ocurre algo?

Saludos,
Sayid...

---

