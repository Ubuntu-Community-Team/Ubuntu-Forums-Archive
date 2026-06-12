---
title: "Problema con el disco rígido. Se murió? O lo puedo rescatar?"
date: 2011-04-02
forum: Hardware
---

### Post by Hadso on 2011-04-02
Estimados foristas. 
Les relato lo que me ha sucedido. 
Tenía instalado Ubuntu 10.10 en mi modesta PC de 6 años de antigüedad.

Traté de particionar el disco rígido con un live cd de Ubuntu 9.10 (tal vez mi primer error) y mientras estaba creando una nueva partición la PC se apagó repentinamente. 

Hasta ahí no hubo mayores problemas. Formatee el disco entero e instalé Arch (por suerte tenía un backup). 

Arch anduvo divino, pero tenía problemas con los drivers. Además, tuve un error a la hora de actualizar el kernel, así que decidí formatear e instalar Arch nuevamente. 

Volví a formatear e instalar Arch, 0 problemas, actualicé el kernel, instalé todo etc. 

Siguieron los problemas con el driver de la placa de video. Mi tiempo y mi paciencia no me dieron mas y decidí volver a Ubuntu. 

**Acá arrancan los problemas: **
Traté de instalar Ubuntu 10.10 desde un USB, creado desde Unetbootin. 
No cheque la integridad de la ISO. 
Comienza la instalación, formatea el disco, copia los archivos, llega a 30% y dice que hay un problema con el CD/ DVD (En este caso USB) y que no puede seguir adelante con la instalación. 

Pensé que era el pen, o tal vez el archivo ISO que bajó Unetbootin. Como sea, bajé la ISO desde la página de Ubuntu. La grabé a _**OTRO USB**_ con Unetbootin. 
Chequee la integridad del ISO, 100% OK. 
Comienza la instalación, formateo (esta vez en Ext3, no 4, porque mi disco es viejo y tengo entendido que es mejor, además, ya había tenido problemas antes con Ext4). 
Comienza la instalción, 30% o más o menos por ahí... **otra vez el mismo problema!**

**Probé instalar Ubuntu desde el CD de la versión 9.10**, que siempre funcionó bien... **MISMO ERROR!**

Ya sin saber qué hacer, probé instalar WindowsXP.
Comienza a formatear en NFST, se apaga!

Ya no se qué hacer... ya no quiero j***r más con el tema, necesito la máquina para laburar y hace una semana y media que estoy dando vueltas. 

Se arruinó el rígido? Hay alguna chance de aunque sea me levante Ubuntu? Con eso me conformo!

Alguna solución provisoria? Por lo menos hasta que pueda comprar una PC. 
Pensé en tomar un pen de 8GB que tengo e instalar el SO en él como si fuera un HD externo... qué opinan? (Akgún buen tutorial para ello?)

Ah, otra cosa, también pienso que los repentinos apaganos se pueden deber a una falta de ventilación, dado que a la vez que arranqué con el primer problema, cuando la PC se apagó mientras realizaba la partición, la había puesto en un nuevo sitio. 

Bueno, si llegaron hasta acá con la lectura, muchas gracias por su tiempo!

Saludos,

---

### Post by gmunioz on 2011-04-03
Sugerencia:
Abre el gabinete, sopletea los coolers. Saca las memorias y limpialas. Revisa el cable del disco rígido que no este doblado.
Instala con el cd la 9.10 con el gabinete sin tapa.

---

### Post by mama21mama on 2011-04-03
luego de hacer lo que te indicaron podrías pesarle el fsck

[fsck - comprobar y reparar sistema de archivos linux]("http://mamalibre.text0.tk/?q=content/fsck-comprobar-y-reparar-sistema-de-archivos-linux")

---

### Post by Hadso on 2011-04-04
> **gmunioz said:**
> Sugerencia:
Abre el gabinete, sopletea los coolers. Saca las memorias y limpialas. Revisa el cable del disco rígido que no este doblado.
Instala con el cd la 9.10 con el gabinete sin tapa.

Caballero: Mil gracias! Ud. me ha ahorrado dinero. 

Si no es mucha molestia, dado que he instalado con el CD de 9.04, cómo actualizo a 10.10 "de un salto"? 

Muy agradecido!

---

### Post by mama21mama on 2011-04-05
tienes que actualizar a 10.04 luego si 10.10.

pero no como quieres.

---

### Post by Hadso on 2011-04-05
Muchas gracias :). 
Saludos,

---

### Post by Hadso on 2011-04-05
Listo. Problema resuelto. Gracias a todos!

---

