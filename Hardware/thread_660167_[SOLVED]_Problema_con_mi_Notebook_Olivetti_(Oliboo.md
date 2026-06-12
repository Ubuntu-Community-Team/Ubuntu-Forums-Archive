---
title: "[SOLVED] Problema con mi Notebook Olivetti (Olibook 520)"
date: 2008-01-06
forum: Hardware
---

### Post by Ropechoborra on 2008-01-06
Me compre una notebook olivetti Olibook 520.
El problema es que no puedo instalar ubuntu! 
Cuando intento correr el live cd, luego de poner Start or Install ubuntu aparece el logo y ahi se cuelga.
Probe borrando el quite splash, noapic, nolapic, noacpi, no_timer_check, tambien con el CD Alternativo de ubuntu, con versiones mas viejas, hasta con el Knoppix 3.2 (un cd que tenia de antes) y tampoco. En algunas, la pantalla no se ve, en otras directamente se tilda. Probe tmb con SafeGraphics, pero nada. Googleo y no hay mucha info en esta notebook.

Si alguien tiene alguna idea aviseme!

[B]System Details:

Manufacturer: SICSA
Processor: Intel Pentium Dual CPU T2310 1.46 1.47
1Gb ram ddr2
VGA: SiS 307ELV
Audio Realtek ALC662
LAN Realtek RTL8201CL
Modem Motorola
WLAN LiteOn WN6301L
Card Reader: Realtek RTL5158[/B]

Iniciando ubuntu 7.04 live cd sin quiet splash los ultimos mensajes de consola son:

[I][   2.672626] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   2.672789] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   2.672953] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   2.673120] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[  2.676243] ACPI: Thermal Zone [TZ01] (51 C)
[  3.656000] Time: acpi_pm clocksouyrce has been installed.
Donde.
Begin: Mounting root file system... ...
[   3.980000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[   3.980000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   3.980000] SIS5513: chispet revision 1
[   3.980000] SIS5513: not 100% native mode: will probe irqs later
[   3.980000] SIS5513: SiS968 ATA 133 (2nd gen) controller
[   3.980000] ide0: BM-DMA at 0x1080-0x108, Bios settings: hda:DMA, hdb:pio
[ 4.192000] usbcore: registered new interface driver usbfs
[ 4.192000] usbcore: registered new interface driver hub
[ 4.192000] usbcore: registered new device driver usb
[ 4.192000] SCSI subsystem initialized
[/I]
Iniciando la misma version pero en Safe Graphics:

[I][   2.672626] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   2.672789] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   2.672953] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   2.673120] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[  2.676243] ACPI: Thermal Zone [TZ01] (51 C)
[  3.656000] Time: acpi_pm clocksouyrce has been installed.
Donde.
Begin: Mounting root file system... ...
[ 4.192000] usbcore: registered new interface driver usbfs
[ 4.192000] usbcore: registered new interface driver hub
[ 4.192000] usbcore: registered new device driver usb
[ 4.196000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[ 4.196000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[ 4.196000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[ 4.196000] ohci_hcd 0000:00:03.0: irq 16, io mem 0xd4104000
[ 4.308000] usb usb1: configuration #1 chosen from 1 choice
[ 4.308000] hub 1-0:1.0: USB hub found
[ 4.308000] hub 1-0:1.0: 4 ports detected[/I]
__________________

**Actualizando: Probe con un Cd live de Knoppix 5.0 y anduvo, quiza puede ser problema de drivers?**

---

### Post by faktorqm on 2008-01-07
Y mas o menos tendrias que dejar todo como esta y ponerle solo "noapic", si no te anda, "nolapic", si no te anda, los dos juntos. lo del quiet splash es para que veas la salida, sino ves justamente el splash y no podes ver la info que te tira. 

te fijaste si hay algun update de bios para ese problema? en windows no te tira ningun drama? 

si te fijas en ambos casos te tira exactamente el mismo error, por lo tanto, problemas de graficos no es, y lo del time check tampoco por que te dice que lo hizo bien eso. es el apic el problema. espero que te haya servido, salu2!

---

### Post by qntal on 2008-01-07
si con varios linux te tira ese problema se me hace que puedas estar necesitando un update del bios.

yo tengo una oliveto 420, la que salía $1999 el año pasado, y ubuntu me detectó todo de una (salvo el i810).

lo que no me gusta es el SiS que vi por ahí... no se qué onda la relacion de ese chipset con linux.

---

### Post by faktorqm on 2008-01-07
es el controlador ide, el que maneja el disco, no pasa one. salu2!

---

### Post by jorgito on 2008-01-08
Pregunta tonta...
Instalaste la de 32 bits, no?

Yo tengo una Olivetti 820 y una 610, con ninguna de las dos tuve problemas, salvo que no pude usar el live CD con la 610. Por lo demas reconocio todo todo.

Saludos!

---

### Post by Ropechoborra on 2008-01-09
> **jorgito said:**
> Pregunta tonta...
Instalaste la de 32 bits, no?

Yo tengo una Olivetti 820 y una 610, con ninguna de las dos tuve problemas, salvo que no pude usar el live CD con la 610. Por lo demas reconocio todo todo.

Saludos!

Si, estaba provando con el live de 32 bits, aunque ahora que veo es de 64, pasa que no lo decia por ningun lado. De todas formas no creo que sea ese el problema. Ahora voy a probar con la imagen de 64 bits.

Tambien voy a ver que pasa con el Bios update, no tengo mucha idea de como se hace, pero voy a googlearlo un toque.

Que hiciste con la 610 al final?

---

### Post by juanlb on 2008-01-11
Yo tengo una Olibook 520 también y pude hacer andar Ubuntu con las siguientes directivas al kernel:

noapic nolapic acpi=off irqpoll

Probé todas las combinaciones, y de la única manera que arranca es con los cuatro parámetros.
Después, cuando arrancó no podía poner la resolución en 1280 x 800, pero supongo que ese es otro tema.

---

### Post by qntal on 2008-01-12
juanlb si tenés video intel necesitás instalar 915resolution

sudo apt-get install 915resolution

sudo reboot

y listo

---

### Post by Ropechoborra on 2008-01-13
Bueno, como era de esperarse tambien tengo el mismo problema de video, te dejo este link (pero todavia no me funciona :P)

[http://ubuntuforums.org/showthread.php?p=4128993#post4128993](http://ubuntuforums.org/showthread.php?p=4128993#post4128993)

El video, tengo entendido que es SiS 672

Gracias por tu post anterior! :)

---

### Post by ojvulluz on 2008-01-18
hola ropechoborra!!

yo tengo la misma notebook que vos, y solucione lo del video usando el driver que ofrece sis para el feisty (7.04) copias los archivos en la carpeta del xorg y con el dpkg-reconfigure le cambias VESA por SIS. Asi logre hacer andar el 1280x800.
como soy medio nuevo acá, no se si se pueden postear archivos, cualquier cosa, me mandas un privetti y te los paso.

otra cosa: a vos te funca el wireless? porque mi no, y es lo unico que me falta (en realidad, al lector de tarjetas no le di bola) si te funcó, decime porfa como hiciste...

saludos desde Mendoza

ojvulluz

---

### Post by niko_3100 on 2008-01-18
Te funca con compiz con esos drivers que le metiste?

---

### Post by ojvulluz on 2008-01-18
hola niko!

todavia no me he puesto con el"maquillaje" de la cosa, pues mi urgencia es con la placa wlan. en el foro de donde saqué la data decian que aun no se puede habilitar el soporte 3D para esta placa de video, solo daban la solucion para tener un video 2D decente, en 1280 x 800, ero no instale todavia el compiz manager ni nada de eso.
vos tambien tenes una oli520? te anduvo la version de 64bits? te anduvo la placa wireless?

saludos desde Mendoza

ovu

---

### Post by ojvulluz on 2008-01-18
me contesto a mi mismo: no funca compiz: le habilité las ventanas gelatinosas (me encantan...) y nada de nada... habrá que seguir esperando. llevo 25% del dvd de ubuntu Hardy... alguien ya lo probó?

saludos desde Mendoza

ojvulluz

---

### Post by niko_3100 on 2008-01-19
Hardy todavia esta bastante inestable, la verda dque la notebook la uso para laburar y no puedo probar hardy. Por otro lado no tengo la oli 520 tengo una compaq v3415 y video nvidia asi que le instale los drivers propietarios y compiz me anda a pleno. Te comento yo tube que hacer andar la placa wireless, una broadcom, con el driver de win xp, con wine y con ndiswrapper, no es dificil no se si te servira a vos esa solucion.

---

### Post by ojvulluz on 2008-01-19
bueno, yo no neceité wine, porque el driver que use en XP para correr la placa wireless , y estoy esta en una crpeta con el sys y el inf sueltos, asi que segun los tutoriales que use para configurar ndiswrapper no era necesario correr el setup, pero, ahora que me lo sugería, creo que voy a reinstalar todo, y probaré usar el instalador del driver a a ver qué onda.

instale virtualbox, y tampoco me reconocio el XP virtual la placa, estoy mas desorientado que no se qué.

gracias por la preocupación.

cuando tenga andando de nuevo ubuntu, volveré, y estoy pensando proponer un thread para usuarios de notebooks olivetti, ya que son accesibles y parecen ser muy buenas, por lo menos las que mis amigos tienen... con XP o Vista, juas!!!

nos leemosç



ovu

---

### Post by martin199 on 2008-02-17
Hola gente! Estoy muy tentado a comparme la olibook 520; ¿pueden confirmarme que anda todo? ¿Pudieron conectarse via wifi? ¿Usan ndiswrapper? ¿Con que drivers? ¿Dónde los consiguieron? Y al final , ¿Con X todo bien? ¿Da 1200x800? ¿Algún problema con el sonido? 

Desde ya les agradezco cualquier sugerencia/consejo/opinión que puedan darme. 

Saludos,

Martín

---

### Post by rbarbe on 2008-02-19
Buenas tardes, estoy mas que interesado en esta máquina porque esta a muy buen precio si las estrellas se alinean ($1999 si la compras con tarjeta del banco rio y 12 cuotas sin interés!!!).

¿Levanta el Live CD? tengo el Ubuntu y el Kubuntu, asi que voy a ver si me dejan probar alguno ....

Despues les comento como me fué...

---

### Post by EstebanC on 2008-02-24
Estoy por comprar una olibook 520, pero lei en algunos lados ([http://www.elblogdelasquejas.com/olibook-520-falladas-en-musimundo.php](http://www.elblogdelasquejas.com/olibook-520-falladas-en-musimundo.php)) que vienen con pixeles quemados y por eso están mas baratas... es cierto?

saludos!

---

### Post by SLA_leandrin on 2008-02-25
Un amigo se la compró en Garbarino, efectivamente le vino con un pixel quemado. Ahora, creo que por el precio es un defecto tolerable. El tema es que no te avisen que tiene esa falla...

---

### Post by jorgito on 2008-03-10
Hola a todos, 

Ropechoborra: Perdon por la demora en responder, pero estaba afuera... con la 610 ningun problema salvo que el no instalaba desde el Live CD de Feisty. Lo hice desde el alternate y todo OK. 
Las dos maquinas arrancaron con Feisty con wireless y con lector de tarjetas operativos sin ningun drama. El video requirio algun toque manual porque no reconocia la resulucion correcta pero con el 915/resolution quedo OK.

La actualizacion a gusty fue simple tambien y esta vez con el video lu unico que tuve que hacer es elegir la resulucion que queria (que con Feisty no estaba disponible).

Con respecto a los pixeles quemados no tuve problemas, las dos las compre en Garbarino y me las dejaron abrir para chequear eso y estaban las dos OK. Creo que la politica de SICSA es decir que si la pantalla tiene HASTA 4 pixeles mal la maquina esta OK. Eso no quiere decir que haya maquinas de primera y maquinas de segunda con diferentes precios.

Espero que sirva...


Saludos para todos!

---

### Post by sajnox on 2008-03-10
> **ojvulluz said:**
> 
instale virtualbox, y tampoco me reconocio el XP virtual la placa, estoy mas desorientado que no se qué.
ovu

Si el sistema no te reconoce la placa menos lo va a hacer una maquina virtual. 

AL correr una maquina virtual, la maquina virtual no corre sobre el hardware real, sino sobre hardware que el SO host le asigna. Y como te imaginaras no puede asignar un hard que no tiene

Espero se entienda

Saludos

---

### Post by jpmorelli on 2008-03-10
...lo de los pixeles quemados es un defecto "tolerable" aunque nada gracioso pero lo hacen desde Olivetti hasta Compaq, Toshiba, etc. , todos tienen una cantidad máxima de posibles pixeles quemados que no son objeto de reclamo ni garantía alguna. Como siempre, todo esto está explicado en letra chiquita. 
Que las Olivetti sean más baratas es porque son notebook clones, yo vi un par y estaban perfectas, un poco escasas de recursos pero bueno, todo depende de la configuración que compres...
Suerte ! y fijate las Compaq Serie F7XX , hay modelos muy bien armados y tienen muchos descuentos ! Aclaro que no es chivo... no se ofendan los de otras marcas por favor :lolflag:

---

### Post by jomax01 on 2008-03-13
Hola, yo tambien tengo el mismo problema. El driver de video ya lo hice andar. Si quieren les paso la forma de solucionarlo. Ahora mis problemas son que para que botee debo pasarle las opciones **noapic nolapic acpi=off** y con eso pierdo el manejo de energia de la notebook y ni hablar que el wireless hasta ahora no logre hacerlo funcionar. 
Si alguien tiene ideas, escucho atentamente.

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

---

### Post by jomax01 on 2008-03-14
Joya, hoy voy a probar reinstalando Ubuntu. Ahora por motivos de laburo, le meti un guindous.
Si me anda te aviso. 
Salu2 y mil gracias

Jomax

---

### Post by niko_3100 on 2008-03-14
Provalo cuando levantas el live CD te da la opcion creo que apretando alguna de las f1 o f5 para editar lo mismo.

---

### Post by jomax01 on 2008-03-15
Mira, lo probe desde el live cd y tampoco. La unica opcion para que la notebook botee es ponerle las opciones **noapic nolapic acpi=off irpoll**. De esta forma la maquina prende. Aun no probe la estabilidad del sistema pero algo es algo. El principal problema (ni siquiera pienso en hacer andar la wireless) es que la maquina no sabe si trabaja con electricidad o bateria, los usb por algun motivo no funcionan y obviamente cuando le doy un *init 0* baja el sistema pero no desconecta la corriente del equipo. Yo se que tal vez sean tonterias, pero no saber cuanto te queda de energia o no tener habilitados los puertos USB jode y mucho.
Te agradeceria si tenes alguna otra informacion me avisaras.

Salu2 

JoMaX

---

### Post by niko_3100 on 2008-03-16
Pone todo esos parametros y agrega este apm=power-off   apm es el administrador de energia anterior a acpi aunque tambien tendrias que agregarlo al kernel porque esta pero no lo toma el kernel.

---

### Post by jomax01 on 2008-03-16
Lamento decirte que no funciono. Sigue haciendo lo mismo. Ya por el solo hecho de ponerle **acpi=off**  eso ya desconecta las opciones de energia. O sea, la maquina anda con su bateria pero para el sistema aun sigue funcionando con energia electrica. La verdad me esta cansando. Suerte que esta notebook no es la mia sino ya estaria pensando seriamente en cambiarla.

Salu2

---

### Post by niko_3100 on 2008-03-16
claro pera... no funciono poruqe no se le agregaste el modulo al kernel.. fijate si esto te sirve: 

[http://www.ubuntu-es.org/index.php?q=node/856](http://www.ubuntu-es.org/index.php?q=node/856)

Esta tambien parece buena...

Add the word apm to
/etc/modules
sudo gedit /etc/modules

This will load the apm module on boot.
sudo modprobe apm
to load it now.

and install apmd

You got apm.

---

### Post by jomax01 on 2008-03-25
Bueno. Me demore en responder, pero tampoco funciono.
Sino le pongo las opciones noapic nolapic acpi=off irqpoll no hay forma de que levante.
Por ahora la voy a dejar asi y ver que onda cuando salga ubuntu 8.04
Me gano la muy hija de mil........jajajajaja

Salu2

---

### Post by JoACoV on 2008-04-19
Hola yo tengo una olivetti 520-5250 (la que viene con 2gb de ram) y obviamente tenía el mismo problema, peeeero el viernes en internet encontre este comando de arranque:

** pci=assign-busses apic miantimer idle=pool reboot=cold,hard**

no se como es que trabaja, pero con la version de 64 bits booteo de una (no probe con la de 32 bits) y me anda todo, incluyendo la getión de energía y combinación de teclas para prender la antena wireless.

ahora tengo un par de cuestiones: 

1. no puedo terminar de configurar el video en 1280 x 800 (lo tengo andando en 1280x768 )
2. si bien "encuentra" la antena no puedo configurar la red inalámbrica.

Quizás estos sean problemas menores pero soy muy novato en linux así que están fuera de mi alcance.

Bueno al menos ahora podemos bootear la olivetti sin deshabilitar el acpi lo que es un avance, por favor si alguien puede decirme como proceder con la antena y el video, les estaría muy agradecido.

---

### Post by Hei Ku on 2008-04-20
con la placa de wireless probaste de usarla usando ndiswrapper? No es la solucion ideal, pero dicen que anda bien.

Por si no sabes, ndiswrapper te permite usar en linux los drivers de la placa que vienen para win

---

### Post by JoACoV on 2008-04-20
en realidad probe ndisgtk (que creo que está basado en ndiswrapper pero con front grafico) con el driver de xp (al de vista no me lo tomo) y no anduvo.

Igual metí tanta mano tratando de configurar la antena que rompí el sonido (?) así que ahora estoy reinstalando el sistema para intentarlo de nuevo.

Con el video tampoco hay caso, sigo en 1280x768 y me salen como unas franjas horizontales de pixeles un poco más claros (supongo que son producto de la mala configuración)

cualquier cosa si alguien encuentra algo avise

---

### Post by Ropechoborra on 2008-04-25
Buenas de nuevo!

Perdon el cuelgue pero estuve realmente ocupado estos tiempos y sin internet en casa, por ende cero oportunidades de seguir probando ubuntu. Lamentablemente tuve que continuar con el Vista que viene instalado.
Se da que este sabado (mañana :D) tiene lugar el FLISOL (Festival Lationamericano de Instalacion de SoftLibre) aca en Mar del plata y eso me pone todas las pilas para volver con ubuntu! :) Asique espero estar instalandolo y resolviendo problemas en poco tiempo.

Fue re alentador ver todos los usuarios que se coparon con este tread ya que al principio no habia casi nada de info en Olibooks y ahora parece que somos algunos cuantos mas.

Nos mantenemos al tanto.

Saludos.-

---

### Post by Ropechoborra on 2008-04-26
Actualizando: 

Ubuntu 8.04, y 7.10 no funcionan a no ser que se deshabilite el apic, lo que seria perjudicial para algunos programas que lo utilicen, no acepta la antena wireless y demases problemas..

El problema: Debe estar en como el Kernel de Ubuntu maneja el hardware (vaya uno a preguntarle a los desarrolladores xP)
Posible solucion: Muy desalentadora pero lo unico que pude hacer es:

Instalar Ubuntu 7.04 e iniciar con los siguientes parametros de boot:

pci=assign-busses apic miantimer idle=pool reboot=cold,hard

De esta forma no se deshabilita el apic y la placa wireless puede ser "enchudada" con la tecla Fn + F10
A esto hay que bajar los drivers correspondientes para utilizarla.

Solución 2: Cambiar de distro a uno que si pueda manejarlo. (Estuve probando con Knoppix 5.0 y anda sin ningun problema, con las mas nuevas debe ser igual).

---

### Post by JoACoV on 2008-04-29
Me confundí con el comando, no es  

```
pci=assign-busses apic miantimer idle=pool reboot=cold,hard
```sino

```
 pci=assign-busses apic miantimer _idle=poll_ reboot=cold,hard
```con eso les debería bootear en gutsy y hardy, por lo menos a mí me anda (tambien con la de 32 bits)

---

### Post by Ropechoborra on 2008-04-29
> **JoACoV said:**
> Me confundí con el comando, no es  

```
pci=assign-busses apic miantimer idle=pool reboot=cold,hard
```sino

```
 pci=assign-busses apic miantimer _idle=poll_ reboot=cold,hard
```con eso les debería bootear en gutsy y hardy, por lo menos a mí me anda (tambien con la de 32 bits)

Aggg!! Eso cambia mucho las cosas! ya me habia resignado a usar la 7.04 ! Bueno, gracias por la data. Apenas tenga la 8.04 lo pruebo! :)

Pudiste hacer andar el video ?

Aca hay un tread relacionado [http://ubuntuforums.org/showthread.php?p=4819719](http://ubuntuforums.org/showthread.php?p=4819719)

Y los drivers del wireless?

Si puedo hacer funcionar todo pronto salgo con un howto para los clientes de sicsa :P

---

### Post by JoACoV on 2008-04-29
no, no hice andar el driver del video, voy a probar con esa info..

el driver del wireless, probe usar los del xp con ndiswrapper y encuentra las redes pero no se conecta, asi que no se que otra cosa probar

---

### Post by finatai on 2008-05-02
Gracias a ustedes puedo escribir esto desde una Olibook 520 con Ubuntu 8.04 a travez del wireless
La opcion para instalar es la indicada mas arriba:
pci=assign-busses apic miantimer idle=poll reboot=cold,hard
La misma la modifique en el menu.lst del grub.
Para hacer funcionar la placa wireless use el ndiswrapper con los drivers del 98, con los del XP detectaba las redes pero no era posible conectarse.

Solo resta arreglar la resolucion de la pantalla para que tome 1280*800

---

### Post by niko_3100 on 2008-05-02
Entonces con hardy levanto bien con esos parametros?? Es posible decir que con hardy las olibook 520 andan bien??

---

### Post by marcelo08 on 2008-05-03
Podria alguien explicar a un novato donde esta el menu.lst del grub   
y donde tipear la entrada pci=assign...
Tambien tengo una Oli y no me carga hardy (32 bit)ya instalado.
Mil Gracias¡¡¡[FONT="Arial"][/FONT]

---

### Post by finatai on 2008-05-03
Cuando boteas apreta F6 aparece una serie de opciones para iniciar, una de ellas es una linea de parametros para el kernel la cual termina con algo asi como :

quiet splash --

Te paras sobre esta linea y editas la misma para que quede:

quiet splash pci=assign-busses apic ...  --
(remplaza los ... por el resto de los parametros mensionados anteriormente.

El sistema va a botear y vas a poder instalarlo.
Una vez instalado cuando reinicies la PC va a aparecer el menu del grub
donde seleccionas para editar la linea. Volves a editar los parametros del kernel para poder bootear la maquina, de lo contrario se cuenlga al mostrar la pantalla.

Ya logueado en Ubuntu, desde la terminal tipeas lo siguiente:

    sudo gedit /boot/grub/menu.lst

Este es el menu de configuracion del Grub
Buscas la linea correspondiente al inicio de Ubuntu y modificas los parametros del kernel agregando las opciones indicadas anteriormente.

Cuando modificas los parametros de inicio agregalos al final de la linea antes de los -- finales.

Si puedo lo escribo mas claro mas tarde, ahora no me da para mas ;-)

---

### Post by Ropechoborra on 2008-05-03
Estoy esperando tener un poco de tiempo para resolver el tema de los drivers de video y wireless y postear un howto bien detallado. 

Alguien tiene los drivers de Win98 para la placa wireless de la olivetti 520 ?

Gracias.-

---

### Post by marcelo08 on 2008-05-03
Buenisimo, gracias por la ayuda. Ahora estoy usando el Firefox de Hardy(por cable)
Aunque todavia no logro acceder al menu grub ,cuando tipeo: sudo gedit/... en la terminal ,me dice: command not found .
No se si estoy equivocado ,o que.
Otra vez, necesito ayuda.
Gracias de nuevo.:)

---

### Post by Hei Ku on 2008-05-03
entre gedit y la / va un espacio. :)

Hace una cosa, selecciona el comando abajo, boton derecho, copiar.
sudo gedit /boot/grub/menu.lst

despues en la terminal, apretas Shift+Insert y eso te pega el comando.

---

### Post by marcelo08 on 2008-05-03
Ya pude editar en el grub .Me estaba comiendo el espacio entre gedit y /...
Ahora arranca de una .
Lo que sigue es la pantalla,todo un desafio para mi.
Gracias ¡¡¡:guitar:

---

### Post by marcelo08 on 2008-05-05
Driver de wireless, lo descargue de la pagina   de Realtek.com.tw

---

### Post by marcelo08 on 2008-05-06
Alguien pudo arreglar la pantalla ?
Aunque sea con eldriver 2d ?

---

### Post by Ropechoborra on 2008-05-06
El tema del video no tuve tiempo de probarlo ya que no tengo conexion a internet. Pero creo que se arregla con esto:

[http://ubuntuforums.org/showthread.php?t=615094&page=8](http://ubuntuforums.org/showthread.php?t=615094&page=8)

En el post de pjasnos.

---

### Post by gertlm on 2008-05-07
Hasta aca a mi todo me funciono perfecto, pero tengo que decir que con el ubuntu 8.04 tambien hice esto:

sudo mv /lib/xorg/modules/drivers/sis_drv* /usr/lib/xorg/modules/drivers/

despues de seguir los pasos de ese tutorial, porque no me tomaba los drivers de video. es mas eso de mover los archivos a otro directorio esta en el mismo post pero mas abajo, por las dudas lo aclaro aca para que quede claro

---

### Post by Ropechoborra on 2008-05-12
Estoy intentando hacer funcionar el wifi. Instale el ndiswrapper y el ndisgtk. Hice esto con los drivers de Win98, XP y vista, con ninguno me da resultado.

Me toma el device y lo reconoce cuando esta prendido pero no tengo ninguna interfaz de red wireless de modo que no puedo conectarme :(

Alguien tiene idea que puedo hacer? quiza olvide algun paso =/

Gracias!.

rope@RopHierr:/etc/ndiswrapper/net8187b$ sudo ndiswrapper -i /media/disk/Wiiiii\ Fi/RTL8187B/Win98/net8187b.inf 
sudo: cannot get working directory
installing net8187b ...
/bin/pwd: no se pudo encontrar el directorio en `..' con el i-nodo correspondiente

rope@RopHierr:/etc/ndiswrapper/net8187b$ ndiswrapper -l
net8187b : driver installed
** device (0BDA:8189) present**

root@RopHierr:/# ndiswrapper -m
module configuration already contains alias directive
module configuration already contains alias directive

root@RopHierr:/# iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

root@RopHierr:/# lshw -C network
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:03:0d:76:9c:da
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s

---

### Post by Larva Total on 2008-06-10
> **Ropechoborra said:**
> Estoy intentando hacer funcionar el wifi. Instale el ndiswrapper y el ndisgtk. Hice esto con los drivers de Win98, XP y vista, con ninguno me da resultado...

Perro, pudiste sacar esto? A mi me pasa lo mismo, reconoce la placa pero no la puedo conectar.

Saludos,


         Larva Total

---

### Post by Claus_ on 2008-06-18
> **Larva Total said:**
> Perro, pudiste sacar esto? A mi me pasa lo mismo, reconoce la placa pero no la puedo conectar.

Saludos,


         Larva Total

¿Cual es el inconveniente?
Tengo una 520 y logré hacerla funcionar ok

Saludos

---

### Post by nyko513 on 2008-06-19
Hola a todos.. estuve leyendo un poco todo esto y la verdad que estoy bastante decepcionado. Tengo la Olibook 520 y actualmente la estoy usando con XP. **Nunca use Linux** y estaba decidido a probarlo ya que mis amigos me habían convencido que era = de facil que guindows, pero me encuentro con todo esto!! Alguien me puede asegurar que no voy a tener problemas? la verdad q perdi un poco las ganas de probarlo.. Muchas Gracias igual! y perdonen si viole alguna regla.. es la primera vez que escribo en este foro.

---

### Post by Claus_ on 2008-06-19
> **nyko513 said:**
> Hola a todos.. estuve leyendo un poco todo esto y la verdad que estoy bastante decepcionado. Tengo la Olibook 520 y actualmente la estoy usando con XP. **Nunca use Linux** y estaba decidido a probarlo ya que mis amigos me habían convencido que era = de facil que guindows, pero me encuentro con todo esto!! Alguien me puede asegurar que no voy a tener problemas? la verdad q perdi un poco las ganas de probarlo.. Muchas Gracias igual! y perdonen si viole alguna regla.. es la primera vez que escribo en este foro.

Vas a renegar pero vas a poder usarla 10 puntos.
De entrada, vas a tener que bootear con las opciones:
```
pci=assign-busses apic miantimer idle=poll reboot=cold,hard
```
que figuran antes en el Thread
Lo que no hay disponible por ahora es un driver 3D, por lo que nada de Compiz

---

### Post by nyko513 on 2008-06-19
ya lo logre bootear.. pero no me anime a instalarlo. porque tengo conexion a internet por medio de wi fi. por lo que tengo miedo de quedarme sin conexion a Internet. para colmo estoy medio lejos del router, por lo q la señal ya de por si es baja.. asi que no se.. q driver instalo para que la placa inalámbrica funcione bien?

---

### Post by Claus_ on 2008-06-19
> **nyko513 said:**
> ya lo logre bootear.. pero no me anime a instalarlo. porque tengo conexion a internet por medio de wi fi. por lo que tengo miedo de quedarme sin conexion a Internet. para colmo estoy medio lejos del router, por lo q la señal ya de por si es baja.. asi que no se.. q driver instalo para que la placa inalámbrica funcione bien?

Instalá NDISwraper y usá los drivers de Win XP o 98 si no funciona.
Fijate en  [http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-funcionando-en-ubuntu-710-usando-ndiswrapper/]("http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-funcionando-en-ubuntu-710-usando-ndiswrapper/") por ejemplo.

---

### Post by JoACoV on 2008-07-12
solucion definitiva para el video (2D) --> [http://www.lucaswells.com.ar/wordpress/?p=2](http://www.lucaswells.com.ar/wordpress/?p=2)

Sigo sin hacer andar el wireless:(

si a alguien le funciono la placa wi-fi (RLT8187B)

por favor postee los drivers que uso

---

### Post by Claus_ on 2008-07-13
> **JoACoV said:**
> solucion definitiva para el video (2D) --> [http://www.lucaswells.com.ar/wordpress/?p=2](http://www.lucaswells.com.ar/wordpress/?p=2)

Sigo sin hacer andar el wireless:(

si a alguien le funciono la placa wi-fi (RLT8187B)

por favor postee los drivers que uso

¿no la podés encender con Fn+F10 o no podés conectarte?
Si es encenderla, tenés que bootear con los parámetros:
```

... ro quiet splash pci=assign-busses apicmaintimer idle=poll reboot=cold,hard
```

para ponerlo permanente editá menu.lst en boot/grub/

Si es por los drivers, instalá NDISwraper y usá los drivers de Win XP o 98 que te hayan venido o de:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B")

Por otro lado, yo tenía problemas para conectarme y era que no se entedía mi Linux con el WEP del modem, por lo que tuve que desactivarlo.
Suerte

Olvidate de esos drivers, el que funciona es el de win98:

---

### Post by JoACoV on 2008-07-13
Es por el driver, detecta las redes pero no se conecta (ndiswrapper), probé con los que me traia la maquina y los de realtek y no pasa naranja.

Voy a probar con esos que posteaste ahi y despues les digo si me funciono
[B]
EDIT: No, no me funcionó. Alguna sugerencia?[/B]

---

### Post by Claus_ on 2008-07-15
> **JoACoV said:**
> Es por el driver, detecta las redes pero no se conecta (ndiswrapper), probé con los que me traia la maquina y los de realtek y no pasa naranja.

Voy a probar con esos que posteaste ahi y despues les digo si me funciono
[B]
EDIT: No, no me funcionó. Alguna sugerencia?[/B]

Desactivá la protección WiFi del modem, especialmente si es un Huawei. 
Los drivers que te pasé son los que tengo funcionando en este momento.

---

### Post by fofato on 2008-07-16
Hola amigos disculpen por revivir un post per no tengo mucho conociento en linux y recientemente compre una olibook con algunas de las siguientes caracteristicas:

olbook 520 wvse cm530
-ram 1gb
-hd sata: 120gb WDC WD1200BEVS-00UST0
-tarjeta grafica: SIS Mirage 3 Graphics (SIS 672)
-tarjeta de sonido: realtek HD Audio output
-red: Realtek RTL8187B Wireless 802.11g 54Mbps USB 2.0 Network Adapter
      SiS191 Ethernet Controller

 Les paso a contar mi problema: antes tenia una pc viejita por lo q baje muchas distro live como ser puppy,gparted,feather,danm small,etc
las cuales me funcionaban bien en aquella pc.
 Ya q tenia a mano estos cds intente instalarlos en la olivetti pero no llegaba a concluir  ya sea con mensajes en la pantalla o directamente bloqueada, la unica q 
arranco fue puppy linux pero NO me reconoce el disco duro. Esto me parecio normal ya q por ser distro para viejas pc supuse q no tendrian soporte SATA.
 Un amigo me paso mandriva 2006/2007 y al concluir la instalacion me daba cierto error en la config de video por lo q yo desde winXP veo q esta instalado el SO pero no puedo iniciarlo ya q nuevamente se bloquea,
probe tambien con UBUNTU 6.06 y al intentar arrancar el dvd la pantalla se volvia practicamente loca! lineas horizontales desplazandose por toda la pantalla.
 Al pasar todo esto es me me decidi buscar algun tipo de informacion o ayuda y llegue a esta página, luego de leer los problemas de esta notebook con el video, llego a ver el live cd de ubuntu
solo cuando coloco 800x600 o 640x480 al iniciar el dvd (sino nuevemente lineas horizontales) y sume sus aportes:
	noapic nolapic acpi=off irqpoll
o
	pci=assign-busses apic miantimer idle=poll reboot=cold,hard

Pero nuevamente cuando intento la instalacion NO ME RECONOCE EL HD, entonces de todas las distribuciones livecd q probe solo 
se cargaron puppy y ubuntu pero sin reconocerme el disco. 
¿hay algun error q estoy cometiendo?
no probe una version superior de ubuntu debido a q no poseo internet en casa y empece todo esto ayer ¿hacerlo seria la solucion?
Espero me ayuden con este problema, gracias por su tiempo.

---

### Post by juanlb on 2008-07-29
Bueno, no soy un usuario muy experimentado, pero me puse hacer las pruebas y fui tomando nota.
Ahora estoy haciendo este post desde mi Olibook 520 con Ubuntu, con resolución de 1280x800 usando Wireless.

Esto que posteo no es mas que una RECOLECCIÓN de cosas que encontré en la red.
Lo expongo ordenado y lo mas claro posible para que otros en mi misma condición de principiantes logren usar la Olibook.

Todas las correcciones a este post serán muy bienvenidas.

Aquí va:

**************************************************

_BOOT_
Para que la notebook bootee correctamente agregar directivas al kernel.
Para eso, en el momento en que levanta las opciones de boot, presionar "e", luego
elegir la linea "kernel", volver a presionar "e" y agregar esta línea al final:

>   pci=assign-busses apic miantimer idle=poll reboot=cold,hard


**************************************************
_VIDEO_

Para que el video se pueda configurar en 1280 x 800 (no logré que funcione la máxima profundidad de colores, pero es totalmente usable)

Las intrucciones iniciales las saqué de:
[http://ubuntuforums.org/showthread.php?t=615094&page=8](http://ubuntuforums.org/showthread.php?t=615094&page=8)

Esto es lo que hice yo:

**Desde una consola:**
> 
  sudo apt-get build-dep xserver-xorg-video-sis

  sudo apt-get install displayconfig-gtk

  tar -xjf intelsrc.tar.bz2  *(Este archivo lo puse en el dropboks indicado mas abajo)*

  cd 2d-driver

  ./configure --prefix=/usr

  sudo make install

**Reiniciar**

**Desdes una consola:**

  > sudo gedit /etc/X11/xorg.conf

Buscar la parte que dice  'Section "Device"' y modificarla de esta forma:

  Section "Device"
  Identifier "**sis**"
  EndSection

**Grabar y reiniciar**

**Desde una consola:**
> sudo displayconfig-gtk

Solapa "Tarjeta Gráfica"
Controlador:
  "Seleccionar el controladorpor el nombre"
     Sis Silicon Int...

Solapa "Pantalla"
Modelo: Generico -> LCD Panel 1280x800 -> Aceptar
Resolución: 1280x800

Aceptar -> Mantener la configuración

**Reiniciar.**

**************************************************
_RED WIRELESS_


Gestor de Paquetes de Synaptic
Configuración -> Repositorios
Descargar Desde: "Servidor Principal"
Marcar todos los repositorios
Aceptar
Recargar

Luego buscar e instalar el ndisgtk (si no agregamos los repositorios, no aparece)

Bajar de [https://www.dropboks.com/](https://www.dropboks.com/)
User: [email]ubuntu@olibook520.com[/email]
Pass: ubuntu

El archivo: WLAN_win_8187B_6.1063.zip
Descomprimirlo

Iniciar el ndisgtk (Inicio -> Sistema -> Administracion -> Windows Wireless Drivers)

"Instalar nuevo controlador"
Ubicación -> (Buscar el directorio de Win98 dentro del directorio del archivo ZIP recién descomprimido)

Apagar la placa y volverla a prender (Fn + F10 y Fn + F10 de nuevo)

Atención: Con un router marca X Micro no me pude conectar por wireless, pero con el resto de los routers que probé, no tuve problemas

---

### Post by Claus_ on 2008-07-30
Una aclaración. La opción correcta para el booteo es "... apicmaintimer ..."
Yo la tenía como lo pusiste, lo corregí y no noté diferencia.

---

### Post by Lucasjfc on 2008-07-30
Dos preguntas tengo. 

¿Hiciste andar la aceleración 3D de la placa de video?
¿Pudiste conectarte a redes con seguridad WPA y WPA2?

---

### Post by juanlb on 2008-07-30
Gracias Claus_ por la aclaración!
(¿Tenés idea cuál es la diferencia?)

Lucasjfc:
No hice andar la aceleración 3D, de hecho no puedo usar compiz.
Ahora mismo estoy conectado a una red con seguridad WPA en mi casa, no probé WPA2.
Por otro lado, en lo de un amigo que tambien tiene WPA no me puedo conectar...

No se si ayuda mucho, pero es mi experiencia

---

### Post by Claus_ on 2008-07-30
> **Lucasjfc said:**
> Dos preguntas tengo. 

¿Hiciste andar la aceleración 3D de la placa de video?
¿Pudiste conectarte a redes con seguridad WPA y WPA2?

No hay todavía un driver 3D para estas placas SiS, al menos para el público. Se cree que SiS lo tiene desarrollado pero no lo liberó todavía.
Estoy conectado con WAP2 en este momento, lo que no me funcionó es WEP.

---

### Post by nicoblest on 2008-07-31
Hola a todos, soy nicolas de rosario,argentina. les cuento q soy nuevo en esto y gracias a todos los comentarios q dejaron aca pude instaar ubuntu cambiar la resolucion e instalar la placa wifi. mi problema es q detecta las redes y llegue a conectarme si le saco la seguridad. pero cuando activo la contraseña de la red, que es wpa-psk no puedo hacer q se conecte.probe con todo lo q dicen aca y no hay caso.

---

### Post by Lucasjfc on 2008-07-31
> **Claus_ said:**
> No hay todavía un driver 3D para estas placas SiS, al menos para el público. Se cree que SiS lo tiene desarrollado pero no lo liberó todavía.
Estoy conectado con WAP2 en este momento, lo que no me funcionó es WEP.

Gracias y a juanlb también, ahi me estoy bajando el archivo para probarlo, y les comento que tal.

Saludos

---

### Post by totesman on 2008-11-01
Hola a todos!!! la verdad que es un gusto leer estos foros porque te aclaran muchas cosas. tengo una olivetti 520, en la cual no me andaba ninguna distro de linux, hasta que llegue a este foro, y en este momento la tengo funcionando con ubuntu 7.10. ya pude solucionar el tema del boteo y de la wireless, video todavia no pero no tengo duda que a corto plazo lo voy a solucionar siguiendo las indicaciones de este excelente foro.
Hago una aclaración que tal vez a alguien le pueda servir porque a mi me paso: al momento de botear la pc, probe con una de las primeras soluciones que encontre que fue modificar los parametros del inicio con la linea: "noapic nolapic acpi=off irqpoll".Con esto efectivamente la pc arranco pero no tenia manejo de energia, ni me detectaba la wireless. despues probe con la otra linea que decian de pci=busses-assign... pero aqui ocurrio el problema que yo a esta linea la agregue detras de la citada anteriormente es decir:"noapic... pci=busses-assign". una vez hecho esto la pc dejo de botear ya que estas lineas combinadas parece que crean conflictos. la solucion fue eliminar la linea noapic... y dejar solamente la otra en el inicio del kernel. Bueno espero que sirva para algo y muchas gracias a todos los que aportan en este foro:lolflag:

---

### Post by Ropechoborra on 2009-03-29
Reviviendo para actualizar.

Pude solucionar los problemas del Wireless con un driver de linux liberado por Realtek.

Pueden obtenerlo de aqui: 

> [http://rapidshare.com/files/214842416/rtl8187b_linux_26_1_.1039.1107.2008.tar.gz](http://rapidshare.com/files/214842416/rtl8187b_linux_26_1_.1039.1107.2008.tar.gz)

Basicamente lo descomprimi utilizando 

> sudo tar -xvvzf rtl8187b_linux_26_1_.1039.1107.2008.tar.gz

luego ingrese al directorio y segui los pasos del ReadMe

basicamente es hacer (con sudo) 

> make
make install
reboot
./wlan0up

Luego lo configure con la interfaz grafica y voaila!

Lo que si, hay que hacer ./wlan0up cada vez que iniciamos la maquina, creo que se soluciona eso agregando el archivo a las automatizaciones de linux, (no recuerdo bien donde)

Recuerden borrar cualquier otro driver que hayan instalado (como el de ndiswrapper) porque quiza pueda generar conflictos con el nuevo driver.)


Actualizando: Tenemos ahora un Wiki en las paginas de ubuntu para los problemas de nuestra Olibook. 

[http://www.guia-ubuntu.org/index.php?title=Olivetti_520](http://www.guia-ubuntu.org/index.php?title=Olivetti_520)

Disfrutenlo ! :)

---

### Post by eimor on 2009-04-15
Grande Ropeeeeeeee.... yo tengo otra notebook (msi con video geforce). El tema es que un amigo se compro la 530 con core2duo y 2 gb de ram, le instale xp, pero obviamente yo tiro pa lado de linux, por eso le mostre mi notebook y queria a toda costa el ubuntu. La cosa es que antes de probar algo google y lo primero que aparecio fue lo tuyo, y despues vi la wiki que te mandaste, SOS GROSO FLACO. Aviso para todos que el kernel de linux (o sea todas las distribuciones, lease ubuntu, mandriva, fedora, suse, TODAS) tiene un bug que progresivamente te daña el rigido, para todos los que no hayan oido del tema les aviso que para solucionarlo basta con instalar ubuntu 8.04.2 o si les da fiaca, usar el famoso "ugly fix" para evitar el numero elevado en el Load cycle count en el rigido, para mayor informacion leanse eso, es de interes para todos los que usan linux en notebooks con rigidos tradicionales (los pioneros que tenga rigido de estado solido, estan a salvo). Si mas me despido no sin antes volver a agradecerte, lo tuyo la verdad que genial):P

---

### Post by fmercerat on 2009-04-21
Les comento que instale la version 8.10, lo que voy a decir seguramente se aplique a 9.04

A partir de ahora Ubuntu reconoce automaticamente la placa wireless, el unico cambio serio, es que cambio el xorg, por lo anto hay que bajar un nuevo driver para este nuevo xorg desde aca: [http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads) pero sigue siendo 2D

---

### Post by Ropechoborra on 2009-04-28
> **fmercerat said:**
> Les comento que instale la version 8.10, lo que voy a decir seguramente se aplique a 9.04

A partir de ahora Ubuntu reconoce automaticamente la placa wireless, el unico cambio serio, es que cambio el xorg, por lo anto hay que bajar un nuevo driver para este nuevo xorg desde aca: [http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads) pero sigue siendo 2D

El driver wireless que viene por defecto en la 9.04 me conectaba a la red wifi pero no a internet.. No se por que. Lo solucioné instalando este driver:

[http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314](http://ubuntuforums.org/attachment.php?attachmentid=111328&d=1240801314)

---

### Post by Pablin on 2009-08-02
Buenas gente, les comento que vengo siguiendo este post desde hace masomenos un año, tengo una Olibook 520 y gracias a este post logré instalar Kubuntu.

Ahora estoy tratando de ver el tema del Driver del WiFi pero no hay caso, me descargo el archivo, sigo todos los paso y cuando hago el $make me tira este error:

```

make[1]: se ingresa al directorio `/lib/modules/2.6.27-7-generic/build'
make[1]: *** No hay ninguna regla para construir el objetivo `modules'.  Alto.
make[1]: se sale del directorio `/lib/modules/2.6.27-7-generic/build'
make: *** [all] Error 2

```
Y Debido a eso no puedo instalar el nuevo driver.
Espero por favor me puedan ayudar y desde ya muchas gracias.
Abrazos!

---

### Post by Hei Ku on 2009-08-02
> **Pablin said:**
> Buenas gente, les comento que vengo siguiendo este post desde hace masomenos un año, tengo una Olibook 520 y gracias a este post logré instalar Kubuntu.

Ahora estoy tratando de ver el tema del Driver del WiFi pero no hay caso, me descargo el archivo, sigo todos los paso y cuando hago el $make me tira este error:

```

make[1]: se ingresa al directorio `/lib/modules/2.6.27-7-generic/build'
make[1]: *** No hay ninguna regla para construir el objetivo `modules'.  Alto.
make[1]: se sale del directorio `/lib/modules/2.6.27-7-generic/build'
make: *** [all] Error 2

```
Y Debido a eso no puedo instalar el nuevo driver.
Espero por favor me puedan ayudar y desde ya muchas gracias.
Abrazos!

Probá ejecutar primero el comando  ./configure
antes de make.

---

### Post by Pablin on 2009-08-03
**Hei Ku** Gracias por responder, hice eso pero no hubo caso, me sigue dando dicho error.
Además ahora que hice la actualización del SO a la v9.04, ya no me funciona el driver de Video, solo me levanta el VESA. Probé con el .deb que dicen arriba pero no me deja instalar porque dice que ya está instalado y funcionando el otro driver. Así que ahora estoy sin Video y sin Wifi y por si fuera poco tampoco me levanta el sonido... pero bueno eso es otro problema que veré como resolver mas adelante...
Abrazos!

EDITO: Ya resolví mi drama con el VIDEO y el SONIDO, solo desinstalé el driver de video con dpkg y el sonido lo resolví borrando el .xine de mi home.
Pero sigo sin poder hacer andar el tema del Wifi... me sigue tirando ese mismo error.
Abrazos!

---

### Post by finatai on 2009-11-11
Yo utilice este driver:

[http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9_i386.deb]("http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9_i386.deb")

Para instalarlo hay que ejecutar este comando:
```
sudo dpkg -i xorg-driver-sis671_0.9_i386.deb
```
Reinicias la PC
Para que funcione hay que editar el archivo xorg.conf. Como no existe el mismo lo creee de la siguiente forma:
```
sudo stop gdm
```
Esto mata la interfaz gráfica y entras en modo texto
```
sudo Xorg -configure
```
Este comando generara un archivo xorg.configure.new, el cual lo copie como /etc/X11/xorg.configure
Reinicie la PC y ya pude configurar la resolucion de la pantalla.
Supongo que puede editarse el xorg.conf para que no sea tan largo pero aun no lo probe.

---

### Post by Nahamen on 2010-01-20
Hola y perdon por no haber posteado antes. 
Para bootear CUALQUIER DISTRO de linux deben editar la parte del booteo del LiveCD o el DVD tambien que es booteable y poner al final de toooodas esas cosas raras dejando un solo espacio lo siguiente: nohz=off 
Y listo. 

Provecho!! :popcorn:

---

### Post by mip_argentina on 2010-08-11
Hola tengo una olivetti 520, 
Actualicé a U 10.4 y tengo driver de video, en 9.04 andaba joya.
No encontré una solución, alguién puede indicarme si hay.

Gracias!!!!

---

### Post by guillermolisi on 2010-08-11
> **mip_argentina said:**
> Hola tengo una olivetti 520, 
Actualicé a U 10.4 y tengo driver de video, en 9.04 andaba joya.
No encontré una solución, alguién puede indicarme si hay.

Gracias!!!!
Y cual seria el problema ? No esta claro solucion a que estas buscando.

---

### Post by mip_argentina on 2011-01-15
Tengo resoluciòn de 600 * 800 y no se como cambiarla, creo que no tengo el driver de video para esta notebook.

---

### Post by mip_argentina on 2011-01-15
ahora si estoy en problemas, 
intenté aplicar la solucion de [http://www.ubuntu-es.org/node/134597](http://www.ubuntu-es.org/node/134597), cambié el xorg.conf y ahora no arranca.( reinicia pero la pantalla no queda estable) no tengo opción de loguearme.

Gracias

---

### Post by guillermolisi on 2011-01-16
> **mip_argentina said:**
> ahora si estoy en problemas, 
intenté aplicar la solucion de [http://www.ubuntu-es.org/node/134597](http://www.ubuntu-es.org/node/134597), cambié el xorg.conf y ahora no arranca.( reinicia pero la pantalla no queda estable) no tengo opción de loguearme.

Gracias

Fijate si te deja entrar en una consola con Alt+Fn (con n de 1 a 6).

Si te deja, borra o renombra el archivo /etc/X11/xorg.conf para que vuelva a iniciarse como al principio.

Inclusive seria bueno tener vista del contenido de ese archivo para ver como te quedo. Tal vez con un par de toques pueda quedar funcionalmente util.

---

