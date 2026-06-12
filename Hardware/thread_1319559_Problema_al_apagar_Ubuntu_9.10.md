---
title: "Problema al apagar Ubuntu 9.10"
date: 2009-11-08
forum: Hardware
---

### Post by Thrallez on 2009-11-08
actualizé del Ubuntu 9.04 al 9.10 en mi laptop Toshiba. la versión 9.04 funcionó perfectamente, pero ahora al apagar la laptop se cierra ubuntu y se queda la panatalla negra y pone "[ 2485.432150] Buffer I/O error on device loop0, logical block 594064"
tengo que apretar el botón para que se termine de apagar, y cuando la enciendo de uelta hace un escaneo para ver que pasa y no me dice nada... 
Ubuntu está instalado dentro de Windows. 
A alguien le pasa lo mismo?

---

### Post by josecuervo86 on 2009-11-08
Hola Thrallez, tu problema es un bug confirmado **[0]**, pero supuestamente hay una solución: tenes que editar **/etc/rc6.d/S40umountfs** cambiando las lineas

```
fstab-decode umount -f -r -d $WEAK_MTPTS **[COLOR="Red"]por[/COLOR]** fstab-decode umount -r -d $WEAK_MTPTS
```
y```
fstab-decode umount -f -v -r -d $WEAK_MTPTS **[COLOR="Red"]por[/COLOR]** fstab-decode umount -v -r -d $WEAK_MTPTS
```

Supuestamente cambiando esas lineas el problema se soluciona.

**[0]** [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589)

---

### Post by Thrallez on 2009-11-08
Gracias por responder cuervo, pero... se me olvidó mencionar que soy bastante nuevo en Ubuntu, así que eso que me has dicho medio que me suena a chino :S jeje te imporataría explicarlo un poco más profundamente??

---

### Post by josecuervo86 on 2009-11-08
Como, no, lo primero que tendrias que hacer es hacer un backup del archivo S40umountfs , para eso abri una terminal y pone:
```
sudo gedit /etc/rc6.d/S40umountfs
```pone tu contraseña y dale [Enter]. Te va a abrir un editor de texto. Anda a **Guardar como** y guardalo en alguna carpeta asi te queda un respaldo. Luego busca las lineas que te menciono arriba y cambialas por las correspondientes. Guarda y sali.

Luego proba apagando para ver si funca! :)

---

### Post by Thrallez on 2009-11-08
Ok, ya casi que estoy! jaja el tema ahora es que no me deja modificar ese archivo! encontré el archivo, lo abrí con el gedit (porque "mostrar" no muestra nada y "ejecutar como terminal"/"ejecutar" no ejecuta nada...) y encontré las líneas. corto y pego pero no me deja guardarlo!! se abre solamente en modo "solo lectura". me fijé en propiedades y dice que yo "no soy el propietario, por eso no puedo cambiar estos permisos"... un último esfuerzo??

---

### Post by Mauro22 on 2009-11-08
Anda a Aplucaciones - accesorios - terminal y escribí el comando que te dio josecuervo86. Al darle enter, te pide tu contraseña ( no se va a ver ), dale enter.  Ahí vas a poder.

---

### Post by guillermolisi on 2009-11-08
> **Thrallez said:**
> Ok, ya casi que estoy! jaja el tema ahora es que no me deja modificar ese archivo! encontré el archivo, lo abrí con el gedit (porque "mostrar" no muestra nada y "ejecutar como terminal"/"ejecutar" no ejecuta nada...) y encontré las líneas. corto y pego pero no me deja guardarlo!! se abre solamente en modo "solo lectura". me fijé en propiedades y dice que yo "no soy el propietario, por eso no puedo cambiar estos permisos"... un último esfuerzo??
Tenes que ingresar textualmente las lineas de comando que te paso Jose en una Terminal/consola. De esa forma no tendras los problemas de permisos que mencionas.

---

### Post by Thrallez on 2009-11-08
Listo!! Mil gracias a todos che!! lo que hice fue poner en una terminal

"sudo -s"
[FONT=monospace]
[/FONT] y asi empecé a operar desde root; copié la ruta 

"sudo gedit /etc/rc6.d/S40umountfs"

Y se abrió el documento con gedit y cambié las cosas! hace un pequeño pitido al apagarse, PERO SE APAGA!! :P mil gracias gente!!

---

### Post by josecuervo86 on 2009-11-08
Buenisimo! Che, el pitido es del speaker del gabinete? o sale por los parlantes? si es del gabinete proba esto: en una consola pone:

```
sudo gedit /etc/modprobe.d/blacklist
```

y ahi agregas esta linea

```
blacklist pcspkr
```

---

### Post by Sugusana on 2010-09-01
Hola!
He probado todas las soluciones que he encontrado por ahí con resultado nulo. Alguien puede ayudarme?? Deciros que soy totalmente nueva en esto, así que explicarlo para tontxs, please!
[LEFT]*[I]Solucion 1:* [/I]* Abren una terminal. Escriben: sudo gedit /etc/modules. Una vez viendo el archivo modules,le insertan la linea "apm power_off=1".*..
**Hecho. Guardo. Apago. No se apaga.**
*Solucion 2:* * Abren una terminal. Escriben: sudo gedit /etc/default/grub. En la linea GRUB_CMDLINE_LINUX="" , agregan entre las comillas despues del "=" acpi=force...*
**Imposible hacerlo. Archivo en blanco.**
*[I]Solucion 3:* Abren una terminal. Escriben: sudo gedit /etc/rc6.d/S40umountfs. Buscan las lineas 'fstab-decode umount -f -r -d $WEAK_MTPTS' y  'fstab-decode umount -f -v -r -d $WEAK_MTPTS' y les borran a ambas el  "-f".[/I]
**Ya me aparece sin las -f.**
No sé qué más puedo hacer!!
Gracias.
[/LEFT]

---

### Post by guillermolisi on 2010-09-01
Sugusana, estas usando la version 9.10 u otra de Ubuntu ?

---

### Post by Sugusana on 2010-09-03
Creo que sí, que la 9.10.

---

### Post by guillermolisi on 2010-09-03
Disculpame que sigas con las preguntas, que tienen como objetivo ubicarnos en tu contexto, que maquina estas usando ? Es una Toshiba como la del primer post de este hilo o es una maquina distinta ?

Si es distinta a la del primer post, podrias darnos marca y modelo ?

Tenes alguna razon por la cual no quieras actualizar la version que decis estar usando a la ultima vigente, la 10.04 de Ubuntu ?

---

### Post by Sugusana on 2010-09-04
Es una Pentium 4.
Motivos para no actualizar: porque no sé como se hace. El ubuntu 9.10 me lo instaló un amigo.
Siempre que me salen actualizaciones las pongo. No es eso, nor? 
Gracias.
Saludos!

---

### Post by guillermolisi on 2010-09-04
Con las actualizaciones instalas mejoras y parches de seguridad a la misma version que estas usando.

Para pasar de version, ademas de tener al dia la 9.10, tenes que usar el Administrador/Gestor de Actualizaciones y ahi veras que en la parte superior tenes un mensaje avisandote de que hay una nueva version, la 10.04, para aplicar via Internet.

---

### Post by Sugusana on 2010-09-08
Ok. Muchas gracias. Ya he instalado la nueva versión. 
(Me ha costado lo mío, porque en el gestor de actualizaciones no me salía ningún aviso, pero tras preguntarle a google, en configuración - actualizaciones - puse en "mostrar nuevas versiones" la pestañita de "ediciones normales" y ya sí me salía el aviso)
De todas formas, el problema persiste. Esto sigue sin apagarse hasta que no lo hago a lo bruto.
Socorro!!

---

### Post by josecuervo86 on 2010-09-08
Sugusana, proba instalando este paquete **[0]**. Es un [fix]("https://bugs.launchpad.net/wubi/+bug/468589/comments/89") propuesto en launchpad para este error que tenes., y por los comentarios realmente resuelve el problema.


**[0]**

**Si tenes ubuntu 32 bits instala este **[http://archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu12_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu12_i386.deb")

**si tenes ubuntu 64 bits instala este **[http://archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu12_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu12_amd64.deb")

---

### Post by guillermolisi on 2010-09-08
> **Sugusana said:**
> Ok. Muchas gracias. Ya he instalado la nueva versión. 
(Me ha costado lo mío, porque en el gestor de actualizaciones no me salía ningún aviso, pero tras preguntarle a google, en configuración - actualizaciones - puse en "mostrar nuevas versiones" la pestañita de "ediciones normales" y ya sí me salía el aviso)

Eso es tener actitud ! :D

---

### Post by Sugusana on 2010-09-09
Jo, muchas gracias por vuestra ayuda. Me temo que mi problema es irresoluble!
Al abrir el archivo me sale: "Error. Ya hay una versión posterior instalada."
Snif, snif,...

---

### Post by josecuervo86 on 2010-09-09
Por lo que comentas estas en la última versión del paquete, o sea que no se trata del problema anterior sino de otro que he visto en launchpad, donde el que tiene la culpa es el "splash". Proba esto: Abrí una terminal y tipea:
```
sudo gedit /etc/default/grub
```
Te va a abrir un archivo de texto. Despues busca la linea donde dice:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
y comentala, o sea agrega al principio de la letra el caracter numeral (#) para que te quede asi:
```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Guarda y sali del editor.

Despues en terminal pone lo siguiente:
```
sudo update-grub2
```

Despues reinicia y fijate si podes apagar la maquina normalmente

---

### Post by Sugusana on 2010-09-10
Pues con esa solución sigo teniendo el mismo problema que tenía sin haber actualizado la versión. Es decir, que el archivo "grub" sale en blanco. :sad:
Gracias mil de todas formas.

---

### Post by josecuervo86 on 2010-09-10
Entonces si no entiendo mal, debes estar usando la versión vieja del grub, o sea grub-legacy. Podrias fijarte si tenes un archivo llamado **menu.lst** en **/boot/grub**?

---

### Post by Sugusana on 2010-09-23
Hola, Josecuero86 no entiendo lo que dices. De todas formas, hablando con un amigo, me dijo que no era grave el problema, que no pasaba nada por tener que apagar del botón y que seguramente se solucionaría en próximas actualizaciones :confused:
Asi que igual me doy por vencida y espero...
Gracias a todos por vuestra ayuda.

---

