---
title: "Problemas con inicios o reinicios"
date: 2012-09-19
forum: Hardware
---

### Post by Vero1 on 2012-09-19
Hola,

Hace un tiempo que vengo teniendo algunos problemas.
Uso Ubuntu 12.04 en estos momentos.

Casi en cada encendido o reinicio me sale la comprobaciòn de los discos. En algunos casos informa:

status DRDY ERR
error ICRC ABRT
SRST failed (errorno = 16)
initctl- failed
I/O error
o
de solo lectura

He pasado ya fsck -cfv en todas las particiones y encontró un montón de errores por ejemplo en la partición donde está la raíz o sea sdb2.

Tambien informa que hay bloques no contíguos en todas las particiones.

Bloques malos no hay.

La verdad que todo ésto me hace perder un montón de tiempo porque tengo que reiniciar varias veces hasta que "engancha" el Grub.

Alguna sugerencia?

Gracias y saludos
p.d.
no quiero reinstalar porque falta poco para la salida de Quetzal.

---

### Post by Vero1 on 2012-09-26
> **Vero1 said:**
> Hola,

Hace un tiempo que vengo teniendo algunos problemas.
Uso Ubuntu 12.04 en estos momentos.

Casi en cada encendido o reinicio me sale la comprobaciòn de los discos. En algunos casos informa:

status DRDY ERR
error ICRC ABRT
SRST failed (errorno = 16)
initctl- failed
I/O error
o
de solo lectura

He pasado ya fsck -cfv en todas las particiones y encontró un montón de errores por ejemplo en la partición donde está la raíz o sea sdb2.

Tambien informa que hay bloques no contíguos en todas las particiones.

Bloques malos no hay.

La verdad que todo ésto me hace perder un montón de tiempo porque tengo que reiniciar varias veces hasta que "engancha" el Grub.

Alguna sugerencia?

Gracias y saludos
p.d.
no quiero reinstalar porque falta poco para la salida de Quetzal.

Aparte de que no se soluciona lo expuesto, ahora se agrega otro problema con Firefox.
Tengo todas las ventanas cerradas o sea cerrado el navegador pero cuando quiero correrlo me sale un cartel que dice que si no cierro lo que tengo abierto no puede abrir la aplicación.
Dónde puedo comprobar cual es el problema?

Gracias

---

### Post by guillermolisi on 2012-10-06
Si hace rato venis experimentando este problema, mi mejor sugerencia es que vayas pensando en cambiar el disco rigido o la controladora del disco (que seguramente es parte de la motherboard).

Lo del FFox puede ser parte del sintoma, con base en el mismo problema.

Como sabes efectivamente que el disco no posee bloques dañados/malos ?

---

### Post by Vero1 on 2012-10-07
Hola guillermolisi, gracias por contestar.

Sé que no hay bloques malos porque he pasado en varias ocasiones fsck -cfv.

En cuanto al controlador del disco, cómo se puede saber que falla o eso lo puede detectar un técnico?

Porque el disco no es tan viejo todavía o nada tiene que ver?

En cuanto a FFox hay una actualización de seguridad que no he podido instalar. Se descarga pero no se instala. Aparentemente es un problema de programación ya que de Launchpad me informaron que no es un bug, así que escribí a Launchpad otra vez sobre el tema, enviando copia de lo que se informa en el detalle del error.

saludos

---

### Post by guillermolisi on 2012-10-07
fsck con las opciones (o sin ellas) no revisa bloques defectuosos del disco rigido. Solo (como si esto fuera poco) repara la estructura del file system para dejarlo consistente pero si la superficie magnetica del disco se esta degradando o si por casualidad trabaja en un bloque defectuoso y tiene la suerte de lograr confirmar la operacion, no te dira que encontro un sector defectuoso en el disco.

Para esto ultimo existe el comando badblocks. Este comando se invoca antes de crear un file system pero nunca es invocado por fsck. Por lo tanto, aun no sabes a ciencia cierta si el disco esta sano o no.

Inclusive es recomendable, altamente recomendable, instalar smartmontools y habilitarlo para que monitoree la unidad desde las funciones y tests de S.M.A.R.T. Podes consultar el estado del disco en consola/terminal y/o via alguna interface GUI y/o web (webmin posee esa posibilidad, por ejemplo, y es una aplicacion web que va mas alla del tema del disco).

---

### Post by Vero1 on 2012-10-08
Hola buen día.

Tenía smartmontools instalado, así que acabo de pasar smartctl /dev/sdb (donde está instalado Ubuntu) y salió que el disco no tiene problemas.

Pero sigo con problemas de solo lectura(a veces, no siempre) y cuesta mucho para que "enganche" lectura escritura, que consigo despues de varios reinicios.

Hoy quise pasar desde LiveCD fsck -cfv otra vez pero no pude.
Salió una leyenda donde habla que no pudo abrir el dev y pregunta si puede ser una particion "0" o algo así. No recuerdo exactamente.

En estos momentos funciona como lectura/escritura.

A veces me salen un montón de errores de bloques. 

En fin, si no estuviera cerca la salida de Quetzal me tiraría a reinstalar Pangolin.

Gracias y saludos

---

### Post by hictio on 2012-10-08
Es una laptop? Una PC?
Sinceramente lo que te recomendaría, antes que nada, y mientras todavía puedas, un backup urgente de toda la data.
Segundo, sacaría el disco, pondría uno nuevo y me olvidaría del tema.

No se si es tu máquina de trabajo o que, pero hoy en día no tiene sentido perder tiempo -y ni hablar del riesgo que deje de funcionar en cualquier momento- el bendito disco.

---

### Post by guillermolisi on 2012-10-08
> **hictio said:**
> Es una laptop? Una PC?
Sinceramente lo que te recomendaría, antes que nada, y mientras todavía puedas, un backup urgente de toda la data.
Segundo, sacaría el disco, pondría uno nuevo y me olvidaría del tema.

No se si es tu máquina de trabajo o que, pero hoy en día no tiene sentido perder tiempo -y ni hablar del riesgo que deje de funcionar en cualquier momento- el bendito disco.
Totalmente de acuerdo ... y ademas volves a disfrutar de un sistema confiable que enciende y se apaga bien siempre.

---

### Post by Vero1 on 2012-10-09
Hola,
Contestando la pregunta de hictio, es una PC de escritorio.
No es de trabajo, es de mi casa.

Ayer hice la prueba que me sugirió guillermolisi y el disco no tiene errores.
Pienso que todo se debe a problemas con los archivos.
No tengo data realmente importante.
Lo que me interesa realmente es el Thunderbird y Firefox por los correos y los Bookmarks.
La PC la uso para entretenerme en realidad.
Creo que voy a "tirar" hasta que instale Quetzal, momento en el que se formateará todo menos home. No obstante veo si puedo hacer backup de home. 
Pueden recomendarme qué programa es el mas conveniente a tal fin?

Gracias.

---

### Post by hictio on 2012-10-09
Thunderbird no te sabría decir, uso Evolution hace años.
Firefox los Bookmarks los guardás así:

Ctrl + Shift + o

Click "Import and Backup" > Backup
Una ventana pop-up te pide dónde querés guardar el archivo: bookmarks-2012-10-xx.json.

Para instalarlos de nuevo en la nueva instalación:

Ctrl + Shift + o

Click "Import and Backup" > Restore
Y seleccionás el archivo json del backup ya hecho.

Además, ti tenés passwords guardados, te conviene hacer backup de los archivos:

```

~/.mozilla/firefox/XXXXXXXXXX.default/key3.db
~/.mozilla/firefox/XXXXXXXXXX.default/signons.sqlite

```

Y luego copiarlos a la nueva instalación.

---

### Post by guillermolisi on 2012-10-09
Vero, serias tan amable de mostrar con que opciones corriste badblocks y, si recordas, cuanto tardo en finalizar ?

Thunderbird, en una de mis maquinas, esta en /home/guille/.thunderbird/hwd1ftzb.default/

La ultima parte del path es el nombre que TB le da al perfil de usuario.
Si copias ese directorio tenes todo lo referido al e-mail resguardado. Ojo que tenes que tener vista de los archivos ocultos !

---

### Post by EnriqueK on 2012-10-10
Te recomiendo respaldar toda la carpeta oculta .thunderbird , para ello abre terminal en el directorio donde quieres crear el respaldo y ejecuta
tar -zcvf thun.tar.gz /home/*/.thunderbird
Si solo quieres respaldar los perfiles, ejecuta
tar -zcvf thun-perfil.tar.gz /home/*/.thunderbird/*.default
Para reponerlos abre terminal en el directorio donde tienes los respados y ejecuta
tar -zxvf thun.tar.gz -C /
o sino
tar -zxvf thun-perfil.tar.gz -C /
Lo mismo se aplica para firefox en este caso sería operar sobre la carpeta oculta .mozilla.

---

