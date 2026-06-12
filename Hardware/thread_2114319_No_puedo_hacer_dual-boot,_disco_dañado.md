---
title: "No puedo hacer dual-boot, disco dañado"
date: 2013-02-09
forum: Hardware
---

### Post by fedeavila on 2013-02-09
Buenas a todos! Estaba probando el live de Mint 14 y resulta que al iniciar el proceso de instalación, en la parte de particionado no me figura ninguna opción para hacer dual-boot, o sea cambiar el tamaño de las particiones, etc. 

[IMG]http://dl.dropbox.com/u/20920908/UbuntuForums/ErrorDisco/1.png[/IMG]

El seleccionar "cambiar" sobre la partición NTFS (Windows XP) me sale un cuadro pero sin la opción de modificar el tamaño de la misma. 

[IMG]http://dl.dropbox.com/u/20920908/UbuntuForums/ErrorDisco/2.png[/IMG] 

Sólo eso... Imagino que hay algo que estaré haciendo mal entonces abro, desde el live DVD, la herramienta GParted. 
Sé que desde esa herramienta puedo hacer toda esta tarea previo a la instalación. 

[IMG]http://dl.dropbox.com/u/20920908/UbuntuForums/ErrorDisco/3.png[/IMG]

En principio me resultó raro ver ese icono con el signo de exclamación. 
Hago clic derecho sobre Propiedades para ver qué me tiraba... 

[IMG]http://dl.dropbox.com/u/20920908/UbuntuForums/ErrorDisco/4.png[/IMG]

Me dice que el disco tiene errores y/o sectores físicos dañados. 
Me sugiere que haga un escaneo desde la consola en Windows para ver qué onda. 

Más abajo me indica que no puede leer el contenido del disco porque faltan paquetes para poder hacerlo. 

Me fijo igual si puedo "achicar" la partición y hacer dual-boot como siempre hice. 

[IMG]http://dl.dropbox.com/u/20920908/UbuntuForums/ErrorDisco/5.png[/IMG]

Pero no me deja... La barra superior no se mueve y desde el cuadro de selección sólo me permite "subir" diez megas que supongo quedaron ahí colgados cuando formateé con XP. 

Ahora bien, fui a Windows XP, ejecuté el comando "chkdsk C: /f /r" desde la consola, luego reinicié la máquina para que lo efectúe en el próx. inicio. 
Tardó aprox. una hora, el informe me indicó que tenía 24KB en sectores defectuosos. 
Volví al live de Mint (y luego también al de Ubuntu 1210) y el resultado es exactamente el mismo... 
No hubo ningún cambio. 

Leí por la web que cuando ejecutás la herramienta chkdsk y el error continua (o sea, que no pudo reparar el daño) el disco es como que en cualquier momento estira la pata. 
Me parece raro ya que no hace mucho lo compré, harán dos o tres años. 

Que me recomiendan? Se podrá soluciónar o voy pensando en comprar un disco nuevo? 
Existe alguna otra herramienta similar a chkdsk que puedar llegar a reparar el disco? 


Desde ya, gracias por las respuestas. 

Saludos y buen finde largo!

---

### Post by guillermolisi on 2013-02-11
Y la informacion de SMART, que te dice ?

Fijate que alguna herramienta de consulta SMART para Windows debe haber disponible para revisar y hacer pruebas sobre el disco.

La antigüedad del disco no tiene que ver, necesariamente, con los problemas que pueda tener. Si la forma en que se usa, sobretodo la temperatura habitual de trabajo. Si los discos estan continuamente trabajando a altas temperaturas, digamos 50 °C o mas, terminan cocinandose y empiezan a fallar primero magneticamente y despues electronicamente.

---

### Post by fedeavila on 2013-02-11
> **guillermolisi said:**
> Y la informacion de SMART, que te dice ?

Fijate que alguna herramienta de consulta SMART para Windows debe haber disponible para revisar y hacer pruebas sobre el disco.

La antigüedad del disco no tiene que ver, necesariamente, con los problemas que pueda tener. Si la forma en que se usa, sobretodo la temperatura habitual de trabajo. Si los discos estan continuamente trabajando a altas temperaturas, digamos 50 °C o mas, terminan cocinandose y empiezan a fallar primero magneticamente y despues electronicamente.

Si, la verdad que analizandolo un poco llegué a la conclusión de que pudieron ser varios los factores que provocaron ese "daño" en el disco. Principalmente lo de las altas temperaturas. Sumado además a un problema con mi placa de video que de vez en cuando hace que tenga que reiniciar la PC varias veces (muchas) porque es como que no arranca. 

Googleando un poco encontré una herramienta: [_HDD Regenerator_]("http://www.dposoft.net/hdd.html?abstradrome") es una especie de scandisk que repara estos daños "magnéticos" como vos mencionaste. 

Por suerte tenía sólo 1 sector dañado (que es el máximo que la versión DEMO te repara) y lo hizo bien. Formateé de nuevo con XP, era lo que me recomendaba por algo de la tabla de particiones y, por ahora, todo OK. 

Gracias x la respuesta! Salu2!

---

### Post by guillermolisi on 2013-02-11
Instala smartmontools para seguir de cerca el funcionamiento del disco

---

### Post by fedeavila on 2013-02-11
> **guillermolisi said:**
> Instala smartmontools para seguir de cerca el funcionamiento del disco

Ya lo estoy haciendo! Gracias

---

