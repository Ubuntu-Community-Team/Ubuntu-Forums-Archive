---
title: "VirtualBox-no reconoce lapiz de memoria USB"
date: 2009-05-25
forum: Hardware
---

### Post by prostata on 2009-05-25
Hoy por fin he instalado virtualbox ya ya puedo ver wxp en mi Jaunty...todo va de perlas en la maquina virtual wxp, excepto que aunque veo todo el wx, este no me reconoce al lapiz de memoria US.

Dentro de VirtualBox he mirado el apartado configuración USB y tengo activado Habilitar controlador USB pero no funciona, he habilitado también enable USB 2.0 (EHCI) controller y tampoco lo reconoce en sesión wxp de virtualbox.

Me temo que me dejo algo que se me escapa...qué puede ser...??

Gracias

---

### Post by guillermolisi on 2009-05-25
> **prostata said:**
> Hoy por fin he instalado virtualbox ya ya puedo ver wxp en mi Jaunty...todo va de perlas en la maquina virtual wxp, excepto que aunque veo todo el wx, este no me reconoce al lapiz de memoria US.

Dentro de VirtualBox he mirado el apartado configuración USB y tengo activado Habilitar controlador USB pero no funciona, he habilitado también enable USB 2.0 (EHCI) controller y tampoco lo reconoce en sesión wxp de virtualbox.

Me temo que me dejo algo que se me escapa...qué puede ser...??

Gracias
Que version de VirtualBox instalaste ?
La OSE (Open Source Edition) NO soporta USB.
La denominada propietaria/cerrada si.

Para usar USB con la OSE hice todo un rodeo aprovechando la facilidad de Shared Folders. Montaba el dispositivo USB, en mi caso un pendrive, en /media/Kingston (por ejemplo) y despues lo accedia desde Shared Folders.

Habria que ver si esto es aplicable, tambien, al caso del lapiz optico.
Si no lo es o no te gusta este "workaround", instalate la version propietaria que soporte dispositivos USB.

---

### Post by prostata on 2009-05-25
> **guillermolisi said:**
> Que version de VirtualBox instalaste ?
La OSE (Open Source Edition) NO soporta USB.
La denominada propietaria/cerrada si.

Para usar USB con la OSE hice todo un rodeo aprovechando la facilidad de Shared Folders. Montaba el dispositivo USB, en mi caso un pendrive, en /media/Kingston (por ejemplo) y despues lo accedia desde Shared Folders.

Habria que ver si esto es aplicable, tambien, al caso del lapiz optico.
Si no lo es o no te gusta este "workaround", instalate la version propietaria que soporte dispositivos USB.


La versión instalada es la Sun Virtualbox 2.2.2.
Por cierto la unidad CD-DVD tampoco la reconoce...

---

### Post by guillermolisi on 2009-05-25
> **prostata said:**
> La versión instalada es la Sun Virtualbox 2.2.2.
Por cierto la unidad CD-DVD tampoco la reconoce...
Las dos alternativas, la OSE y la propietaria, son release 2.2.2

En la configuracion de la VM, habilitaste el uso de CDRom ?
Lo definiste como para que use la unidad del host (la fisica) o para que use una imagen ISO ?

---

### Post by prostata on 2009-05-25
> **guillermolisi said:**
> Las dos alternativas, la OSE y la propietaria, son release 2.2.2

En la configuracion de la VM, habilitaste el uso de CDRom ?
Lo definiste como para que use la unidad del host (la fisica) o para que use una imagen ISO ?

Ignorancia de la primera vez, no los tenía montados ni unidad CDrom ni disketera ahora ya veo las unidades mencionadas, solo me queda por ver el pendrive.....más ideas,,,??

gracias

---

### Post by SLA_leandrin on 2009-05-25
Si estás en pantalla completa con Xp en VirtualBox, salí haciendo CTRL+F.

En la ventana del VirtualBox, abajo a la derecha hay varios íconos. Una vez que enchufes el lapiz de memoria, andate al icono que es como un USB (al lado de una carpetita y de unos monitores celestes) y cliqueá con el botón derecho, debería salirte ahora el dispositivo que has enchufado con un "checkbox". Cliquealo y listo.

Ahora, si querés que cada vez que enchufes ese dispositivo lo levante XP sin que lo vea Ubuntu, tenes que ir a Configuración (Con la máquina virtual apagada) y en USB habilitar el dispositivo (ver imagen adjunta).

Espero que te haya servido, saludos.

---

### Post by prostata on 2009-05-26
> **SLA_leandrin said:**
> Si estás en pantalla completa con Xp en VirtualBox, salí haciendo CTRL+F.

En la ventana del VirtualBox, abajo a la derecha hay varios íconos. Una vez que enchufes el lapiz de memoria, andate al icono que es como un USB (al lado de una carpetita y de unos monitores celestes) y cliqueá con el botón derecho, debería salirte ahora el dispositivo que has enchufado con un "checkbox". Cliquealo y listo.

Ahora, si querés que cada vez que enchufes ese dispositivo lo levante XP sin que lo vea Ubuntu, tenes que ir a Configuración (Con la máquina virtual apagada) y en USB habilitar el dispositivo (ver imagen adjunta).

Espero que te haya servido, saludos.

Gracias, pero por alguna extraña razón cuando inicio virtualbox para windows, la ventana se abre completamente por lo que no puedo ver los iconos de abajo a la derecha que nombras, he modificado la resolución de la pantalla (en windows), para tratar de ver los iconos, pero no hay forma...¿existe algún modo de "ver" la pantalla de manera que los iconos aparezcan??....en el modod acatual no veo ni los menus de arriba y así no tengo formo de comprobar el pendrive..

Saludos

---

### Post by prostata on 2009-05-26
Bien, gracias por tus consejos, te adjunto un pantallazo del escritorio wxp, y observa que abajo si aparecen los iconitos que me indicas, ahora bien, el icno del USB y su desplegable apareece incativo, es decir al pasar el cursor por el icno me indica que no hay dispositivo USB conectado y cundo clico sobre él con el botón derecho el menú desplegable aparece con varios dispositivos genéricos pero inactivo, o sea no tengo forma de marcarlo. Quizás de deba al hecho de no haberle indicado bien el dispositivo USB en la configuración y como ejemplo la imagen que tu me adjuntas. ¿que debo poner textualmente en el filtro habilitar dispositivo...?? Uso varios pendrive de distintas marcas, es que no sé que descripción textual debo poner en ese campo...Finalmente vi que podía agregar filtro desde dispositivo con el pendrive puesto, así lo hice y si lo editas se ve perfectamente la descripción, pero ni por esas...

Gracias por tu paciencia y tu tiempo...

Saludos

[IMG][IMG]http://i43.tinypic.com/oi7ngh.jpg[/IMG][/IMG]

---

### Post by prostata on 2009-05-26
Aquí está la solución para ver mi pendrive en virtualbox:

En el Menu de Gnome>Sistema>Administracion>Usuarios y grupos, le damos a desbloquear y metemos la contraseña de root.  Clikamos en Gestionar grupos y buscamos “vboxusers“, le damos a propiedades y añadimos nuestro usuario tildando la opción.

Gracias por vuestros aportes

Saludos

---

### Post by guillermolisi on 2009-05-26
> **prostata said:**
> Aquí está la solución para ver mi pendrive en virtualbox:

En el Menu de Gnome>Sistema>Administracion>Usuarios y grupos, le damos a desbloquear y metemos la contraseña de root.  Clikamos en Gestionar grupos y buscamos “vboxusers“, le damos a propiedades y añadimos nuestro usuario tildando la opción.

Gracias por vuestros aportes

Saludos
Agregar al usuario que utilizara VBox al grupo "vboxusers" es parte de la instalacion.
Si esto no se hace no funcionara bien. Esta en la documentacion de instalacion del producto.

---

### Post by prostata on 2009-05-26
Todo linux me gusta, me hace sentir cómodo y me obliga a utilizar la cabeza, lo cual me gusta y mucho, ahora quisiera despejar otra duda de virtualbox:

Trabajando en sesión wxp con virtualbox, es conveniente instalar también en wxp, antivirus, espyware...en fin ya sabéis, todo lo que ensucia wxp...??
 Yo diría que no pero como es la primera vez....

gracias

---

### Post by Hei Ku on 2009-05-26
Si, si va a estar conectado a la red, es como cualquier Win. Tenes que ponerle firewall, antivirus, etc.

---

### Post by guillermolisi on 2009-05-26
Para una maquina Windows, sea fisica o virtualizada, valen las mismas consideraciones respecto de la seguridad (entre otras), sin excepcion.

---

### Post by guillermolisi on 2009-11-07
> **oscarenzo said:**
> Hola a todos, aprovecho el post, ya que se está tocando virtualbox, tengo un problema a ver si me pueden hechar un cable, tengo virtualbox ver 3.0.10 r54097, sobre un jaunty, todo va de perlas, pero..., cuando instale el skype, me sale un mensaje de error como que no se puede "read" la memoria, presione aceptar para salir o cancelar para depurar, ya me bota del programa, alguien conoce alguna solución por la que pueda optar?
Esta mensaje va en nuevo thread en software porque es OT para donde estaba, Se habla de Virtual Box pero sobre una particularidad respecto del reconocimiento de un lapiz optico y eso no tiene que ver con Skype.

---

### Post by z37a on 2009-11-07
> **Hei Ku said:**
> Si, si va a estar conectado a la red, es como cualquier Win. Tenes que ponerle firewall, antivirus, etc.

Hay algo aun mejor para hacere, no instalas nada y le creas un snapshot, cuando se te rompa restaura el snapshot y listo, total no creo que vayas a tener datos importantes ahi dentro, si no en el sistema denajo del virtualbox, en este caso en el Ubuntu.

Ups, mil perdones, no me di cuenta que el post era un tanto antiguo!!!!

---

