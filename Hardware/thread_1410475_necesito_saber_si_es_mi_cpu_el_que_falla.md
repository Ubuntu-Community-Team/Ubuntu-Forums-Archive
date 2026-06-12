---
title: "necesito saber si es mi cpu el que falla"
date: 2010-02-18
forum: Hardware
---

### Post by granjero on 2010-02-18
Buenas ubunteros...

hace un tiempo hice un post sobre unos apagones de mi pc

[http://ubuntuforums.org/showthread.php?t=1219985&highlight=apagadas+indeseadas](http://ubuntuforums.org/showthread.php?t=1219985&highlight=apagadas+indeseadas)

el tema es que sigue sucediendo cada tanto. sobre todo cada vez que fuerzo el procesador. ya sea algún juego en winchot o cuando corro una maquina virtual y sincronizo mi ipod o cuando hago mil cosas a la vez

la maquina es:

mother: ASUS M3A
procesador: AMD X2 5200+ dualcore
RAM 2GB
fuente: vitsuba 450W
disco rígido: sata 360GB


los chantas del servicio técnico al que la mandé me dijeron que era el mother, lo cambié por otro del mismo modelo y el problema persiste. por suerte me devolvieron la plata y yo el mother que me vendieron.
después me dijeron que instalaron winchot en un disco rígido de ellos y que no les falló más.

acá en casa con winchot o ubuntu desde discos rígidos distintos sigo con la misma falla

ahora estoy en tratativas con AMD para hacer valer la garantía internacional. pero antes quiero saber si hay algún software para forzar el chip a que ande con todo por un tiempo a ver si se apaga.

el tema es que cuando se apaga y rebootea me dice cpu over temperature.

entonces estoy casi seguro que el tema es el chip pero quiero algo que lo fuerce para estar bien seguro

se me ocurre algo como un calculador de cifras de pi o yo que se.

gracias por su tiempo!

si el post iba en software me disculpo!

salud!

---

### Post by granjero on 2010-02-18
estuve haciendo pruebas

conecté un disco IDE que tengo que tiene una instalación win$$$ 
desenchufé el disco sata
prendí la máquina y mientras cargaba el antivirus y demás porquerías del inicio se apagó
la prendí y &#347;á&#263;áté!!!! ***foto 1*** 
entro al bios y ***foto 2*** toque el disipador y estaba _caliente_
le mando ventilador para que baje la temp conecto el disco sata donde tengo ubuntu booteo. 

todo bien...

instalé sensors-applet y sensord para tener mediciones.

lo que no logro es visualizar voltajes, me falta leer el man de sensord que deja un log por algún lado

abrí todas las aplicaciones me puse a rotar el cubo y mil cosas para ver si le saltaba la tapa, pero no se apagó pero los sensores echaban humo. ***foto 3*** la temperatura de abajo de todo es la de trabajo normal.

que opinan?

salud!

---

### Post by guillermolisi on 2010-02-19
Me parece que hay algo en esa placa que no esta bien. Puede ser que el cooler con su ventilador de CPU no este bien montado, le falte grasa siliconada por ejemplo, o que el ventilador no este conectado donde debe ir y actua con otro sensor (el del chipset/motherboard por ejemplo que trabaja a menor temperatura).
Si llega a ser esto que digo seria una razon que explicaria porque las rpm de ese ventilador no llegan a 3000 o mas considerando la temperatura del procesador.
Estoy suponinedo que la fuente esta debidamente dimensionada para esa mother y es de buena calidad porque ni no es asi un corrimiento en los valores de tension de la fuente podria provocar problemas similares.

---

### Post by granjero on 2010-02-19
gracias guillermo por responder. te cuento: el disipador y el cooler están bien colocados... el ventilador del disipador está conectado a donde dice el manual del mother...

la fuente es una vitsuba de 450W que supongo funciona bien... igual mi idea es comprar una de 750W en estos días...

pero las temp que muestran los sensores no son lindas...

escucho sugerencias...

gracias por todo

---

### Post by guillermolisi on 2010-02-19
Ok. La fuente no me parece de mala calidad y considerando el resto de lo que afirmas, se me ocurre revisar las opciones del BIOS respecto de como gestiona la velocidad de rotacion del ventilador del procesador y todo otro aspecto vinculado que esa motherboard y ese BIOS posean.

---

### Post by mama21mama on 2010-02-19
A mi me pasa lo mismo pero me dijeron que son los capasitores electroliticos del mother; ahora ando probandola por dos meses al mother.
Pero le cuesta arrancar en frio, se apaga sola.

---

### Post by granjero on 2010-02-20
mama21mama que mother tenés?

yo que sea un problema del mother lo descarté porque en un momento el service me dijo que era el mother y por dos días tuve un mother nuevo (misma marca y modelo) pero la falla seguía...

y AMD me dice que les mande el chip que ellos en 30 dias lo prueban y si está fallando me lo cambian...

pero quiero estar seguro antes de mandarlo....

que herramienta uso para medir los voltajes que midan los sensores del mother??

salud!

---

### Post by guillermolisi on 2010-02-20
> **granjero said:**
> 
que herramienta uso para medir los voltajes que midan los sensores del mother??

salud!
El BIOS de esa motherboard no tiene una seccion donde se exponen los valores de tension de la fuente en operacion, con la maquina encendida pero en modo setup de BIOS ?
Si bien no es lo mismo que en regimen esperando un poco y tomando nota de como varian los valores podras saber como funciona la fuente.

Para sensar via Ubuntu tenes lm-sensors, que deberias estar usando si tenes los sensores para el entorno grafico de Gnome.

---

### Post by mama21mama on 2010-02-20
> **granjero said:**
> mama21mama que mother tenés?

yo que sea un problema del mother lo descarté porque en un momento el service me dijo que era el mother y por dos días tuve un mother nuevo (misma marca y modelo) pero la falla seguía...

y AMD me dice que les mande el chip que ellos en 30 dias lo prueban y si está fallando me lo cambian...

pero quiero estar seguro antes de mandarlo....

que herramienta uso para medir los voltajes que midan los sensores del mother??

salud!

biostart gf7050v-m7 se 
luego del rayo que me quemara la fuente, placa de red y el router de mi isp empezo a apagarce. :s

---

### Post by granjero on 2010-02-20
tengo instalado lm-sensors
corrí ```
sudo sensors-detect
``` y sólo detecta 2 modulos

#----cut here----
# Chip drivers
it87
k8temp
#----cut here----


no debería detectar más?

---

### Post by guillermolisi on 2010-02-21
> **granjero said:**
> tengo instalado lm-sensors
corrí ```
sudo sensors-detect
``` y sólo detecta 2 modulos

#----cut here----
# Chip drivers
it87
k8temp
#----cut here----


no debería detectar más?
Esos son los controladores/modulos que permiten acceder a los sensores, luego cada uno puede trabajar con uno o mas sensores de la motherboard. lm-sensors reconoce chips controladores, no motherboards. Mas informacion en Ingles [en su FAQ]("http://www.lm-sensors.org/wiki/FAQ/Chapter2").

Aqui va un ejemplo extractado del sitio de lm-sensors.org:
```
ruik@ruik:/tmp$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +36°C

w83627ehf-isa-0290
Adapter: ISA adapter
Case Fan:    0 RPM  (min =    0 RPM, div = 32)
CPU Fan:  1670 RPM  (min =    0 RPM, div = 4)
Aux Fan:  1418 RPM  (min = 4272 RPM, div = 4)
Sys Temp:    +33°C  (high =   -65°C, hyst =   -34°C)  
CPU Temp:  +33.0°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp:  +37.0°C  (high = +80.0°C, hyst = +75.0°C)
```

---

### Post by granjero on 2010-03-02
no termino de cazarle la onda al tema de los sensores y lmsensors....

pero anduve haciendo pruebas....

cuando conecto mi disco sata donde tengo ubuntu, en general la pc anda con temperaturas mas o menos normales: entre 40ºC y 65ºC salvo que la exija donde la temp levanta bastante pero no se apaga.

pero cuando la booteo desde dos ide distintos donde en uno tengo winchot y en el otro intenté instalarlo. la temp vuela y se apaga. 

no se si es que los ide son viejitos y están para la basura (aunque la aplicación para discos duros de ubuntu dice que andan bien. o que el mother está con un problema para con los discos IDE (lo cual sería raro porque como ya conté antes en un momento tuve un mother nuevo igualito a este y la falla persistía) 

no se que más hacer...

algún técnico de confianza?

salud!

---

### Post by granjero on 2010-03-15
el otro día deje descargando unas cosas y cuando me levanté CHAN!!!!!

este cartel....

me imagino que se guardó un log con el error. donde lo encuentro? ya estoy en tratativas con AMD para que me chequeen el procesador y si esto es importante pasarselos....

les dejo una foto de lo que pasó...

---

### Post by guillermolisi on 2010-03-15
Los logs generalmente estan en /var/log. Vas a ver que dentro de ese directorio hay muchos pero los que te interesaran en primera instancia seran syslog, dmesg y messages.

---

### Post by granjero on 2010-04-09
bueno gente al final le mandé el chip a AMD y me mandaron uno nuevo. así que pareciera ser que era que estaba fallado.

recién armé ayer la máquina de nuevo, pero noto que está andando siempre debajo de los 47ºC y en el monitor de sistema se ve que trabajan mucho menos los núcleos.

el finde voy a ver si instalo algún juego para forzarlo un poco y ver que pasa....

AMD resultó bastante responsable a la hora de hacer cumplir la garantía. Solo es engorroso el trámite con DHL, la empresa de correo, pero el resto fue bastante simple.

salud!

---

### Post by 5e6a5t1an on 2010-04-09
Hola!

Yo tuve muchos problemas de ese tipo, y casi siempre lo solucione con grasa siliconada. El tema es que esa bandita que le ponen al procesador, una vez que se cambia el disipador se deteriora y no hace buen contacto, por eso, cada vez que por algún motivo tengo que remover el disipador uso siempre grasa siliconada para volver a colocarlo.
Bueno, esa es mi experiencia personal, espero que les sea útil.

Saludos.

---

