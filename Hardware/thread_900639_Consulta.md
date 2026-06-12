---
title: "Consulta"
date: 2008-08-25
forum: Hardware
---

### Post by losoollenos on 2008-08-25
Hola como andan todos, espero que muy bien. Quiero comentarles que hace algun tiempo probe Ubuntu unos dias y no llegue a empezar siquiera a agarrarle la mano, pero aca estamos con intenciones de seguir porfiando....
Tambien quisiera saber si conseguire los drivers o si los necesitare para mi pc: core 2duo 8200, msi p-35neo, nvidia 8600gt, sata II 250gb seagate.
Agradeceria si me recomiendan una guia sencilla pero completa y/o cualquier sugerencia.
Desde ya muchas gracias y hasta pronto !!!!

Saludos

---

### Post by pol666 on 2008-08-25
Una ves que instalas y actualizas el sistema instala los driver nvidia.
Tenes que ir a sistema>administracion>Controladores de Hardware Restringidos

y ahi se instalan solos, reinicias y listo, no necesitas ma driver....

ah para, no e que es la msi. es una placa de red?

---

### Post by losoollenos on 2008-08-25
> **pol666 said:**
> Una ves que instalas y actualizas el sistema instala los driver nvidia.
Tenes que ir a sistema>administracion>Controladores de Hardware Restringidos

y ahi se instalan solos, reinicias y listo, no necesitas ma driver....

ah para, no e que es la msi. es una placa de red?

es el mother...

---

### Post by pol666 on 2008-08-25
bueno entonses solo la placa nvidia...

¿ Tenes alguna placa wi-fi o wireless?


Respecto a la guia, yo jamas me lei una guia, baje pero nunca las leì. Te recomiendo que busques en youtube los videos tutoriales de ubuntu, esos estan muy buenos

---

### Post by victor_nesta on 2008-08-26
Yo te recomiendo que para la Nvidia instales el EnvyNG, que te detecta la placa y te instala los drives mas la aplicación Nvidia X Server Settings.

Abrí una consola y ejecuta lo siguiente.
```
**sudo aptitude install envyng-core envyng-gtk**
``` 

Sino en Sistema/Administracion/Gestor de paquetes Synaptic. Busca envyng-gtk
Importante que sea el -gtk y no el -qt, este ultimo es para KDE.

Una ves que lo instalas te vas a Aplicaciones/Herramientas del sistema/EnvyNG 

Abrís la aplicación y instalas los drivers 

Ah. me olvidaba. Yo tengo un Mother MSI P-35 Platinium. Quedate tranqui te detecta todo.



Saludos.

---

### Post by User21 on 2008-08-26
Tengo la Nvidia 8500GT de 512Mb y Ubuntu solito me preguntó si quera instalar los drivers privativos de la misma. Le di que si, y salio todo andando. La interfase de Ubuntu es muy intuitiva. Con un tiempito de uso, vas a ver que comodo se te hace todo. 
Para cualquier problema, estamos a tu disposición.

---

### Post by losoollenos on 2008-08-26
> **victor_nesta said:**
> Yo te recomiendo que para la Nvidia instales el EnvyNG, que te detecta la placa y te instala los drives mas la aplicación Nvidia X Server Settings.

Abrí una consola y ejecuta lo siguiente.
```
**sudo aptitude install envyng-core envyng-gtk**
``` 

Sino en Sistema/Administracion/Gestor de paquetes Synaptic. Busca envyng-gtk
Importante que sea el -gtk y no el -qt, este ultimo es para KDE.

Una ves que lo instalas te vas a Aplicaciones/Herramientas del sistema/EnvyNG 

Abrís la aplicación y instalas los drivers 

Ah. me olvidaba. Yo tengo un Mother MSI P-35 Platinium. Quedate tranqui te detecta todo.



Saludos.
Bueno por ahora solo llegué al 95% de la instalación y me tira error fatal al instalar grub, cómo lo soluciono?
Por otro lado, tiene Ubuntu algo tipo "Administrador de dispositivos" para ver si no necesita ningun driver?, cómo se si toma al disco como sata o sataII?. Muchas gracias

Saludos

---

### Post by fmsismo on 2008-08-26
La controladora de tu máquina autodetecta si el disco es sata o sataII.  Después el linux le "habla a la controladora" pero no le importa si es sata o sata II a medida que desagota la cola le pasa o pide más info.  Eso te es transparente.

Te tira algo más de información cuando falla el brub?  Estas poniendo que lo instale en el sector maestro del disco?

---

### Post by losoollenos on 2008-08-26
Puede ser que decía algo como install/...., después lo intento de nuevo y anoto bien todo lo que sale.
Lo que si probé es instalando como venía predeterminado en hd0 o algo así y después en hd5 (seleccionando en "avanzadas" en uno de los pasos), igual salió el error.

Saludos

---

### Post by losoollenos on 2008-08-26
Bueno lo que dice tal cual es: "la ejecución de -grub-install(hdo)- falló""esto es un error fatal".
Les comento como estoy haciendo por las dudas. Ya tengo tres particiones, en una XP, otra solo guardo cosas y en la otra instalaré Ubuntu. Arranco con el cd Ubuntu 8.04 selecciono idioma país, no creo partición swap porque supongo que dos gigas de ram es suficiente; tampoco formateo antes de la instalacion, se lo pido en el paso 4 o 5 donde selecciono la partición en donde instalar, tipo ext3 y el /; luego no importo nada (creo que es el paso 6) y hay uno más que no me acuerdo pero nada importante creo y empieza hasta llegar al 95% que aparece el error. Avisenmé por favor cualquier aclaración.

Saludos

---

### Post by losoollenos on 2008-08-26
Ya solucioné lo de la instalación, probé formateando antes con gparted y asi no hubo problemas. Pero probé en desinstalar algunas aplicaciones y me quedó la pantalla como un DOS. Algunas preguntitas:
- Se puede instalar Ubuntu solo y después elegir que aplicaciones usar?
- Donde puedo averiguar que función tiene cada una?
- Cómo puedo deshacer la desinstalación que me dejó con el "DOS"?
- Estaba bien que el monitor de sistema indicaba un consumo de 152 mb de ram?

GRACIAS

Saludos

---

### Post by pol666 on 2008-08-26
DOS [IMG]http://www.nforo.net/images/smilies/zombie.gif[/IMG]

---

### Post by losoollenos on 2008-08-26
Para aclara : DOS= deoese de windows...

---

