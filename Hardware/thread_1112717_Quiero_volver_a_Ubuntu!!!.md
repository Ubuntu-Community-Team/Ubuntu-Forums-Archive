---
title: "Quiero volver a Ubuntu!!!"
date: 2009-03-31
forum: Hardware
---

### Post by Gpafundi on 2009-03-31
A ver che quien me puede dar una mano en esto... Les pido por favor que sean claros al explicar lo que tengo que hacer porque soy novato en esto. Hace como 2 meses que dejé de usar mi Ubuntu porque un día se me ocurrió reinstalarlo y nunca más pude hacerlo andar correctamente.


Mi problema es el siguiente:

Yo solía usar el Ubuntu 8.04 (64-Bits) hasta que salió el Intrepid. Lo bajé y decidí instalarlo desde cero. Cuando estoy instalándolo, la pantalla se reinicia como 6 veces y me tira un error. La verdad es que nunca supe que hacer con ese error ya que ni siquiera pude terminar de instalarlo y no puedo acceder a nada.

Lo que después hice fue instalar el viejo Ubuntu 8.04. Luego instalarle la placa de video (nVidia Geforce 9600GT) y después actualizarlo al Intrepid. Hacer eso me funcionó bien.

Luego tuve un inconveniente con Windows y formateé toda la PC. Acá viene el problema. Intenté instalar el Intrepid otra vez y sigue pasando lo mismo. A si que vuelvo a instalar el Ubuntu 8.04.02 para luego actualizarlo al Intrepid. Y ahora al instalar la placa de video no me funciona (se me ve todo grande como en una baja resolución). No se si estaré haciendo mal algún paso para instalar la placa de video pero siempre hice lo mismo y nunca me falló la instalación del controlador.

Primero instale el BUILD-ESSENTIAl.

Despues ALT + CTRL + F1

sudo /etc/init.d/gdm stop

cd Escritorio (que es donde lo tengo bajado)

sudo sh NVIDIA-Linux-x86_64-177.80-pkg2.run

le doy a todo que si y después

sudo nano /etc/default/linux-restricted-modules-common

y buscas la linea que dice disabled_modules=""

dentro pones nv de tal forma que queda así:

Disabled_modules="nv"

guardas con control+0

y sales con control+x

sudo /etc/init.d/gdm start

Si alguien me ayuda les agradezco mucho. Ya que extraño el Ubuntu.

---

### Post by josecuervo86 on 2009-04-01
Hola Gpafundi
1ro: Revisaste que el disco de Intrepid no tuviese errores?
2do: Porque no instalas los drivers de nVidia desde Sistema - Adminidtracion - Controladores de Hardware? Es mucho mas facil

---

### Post by gmunioz on 2009-04-01
Hola gpa....:

Segun lo que posteas, que dicho sea de paso, carece de toda información necesaria y útil como para tener clara idea al respecto del problema que te aqueja:

".... tuve un inconveniente con Windows y formateé toda la PC......Cuando estoy instalándolo, la pantalla se reinicia como 6 veces y me tira un error.....Luego instalarle la placa de video (nVidia Geforce 9600GT)..."

Se puede inferir, que:

1- Usas arranque dual Windows - Ubuntu
2- Tienes una tarjeta gráfica nvidia.
3- Intentas instalar Intrepid ¿con un live-cd quizás?

Sugerencia: si lo inferido es correcto, mi sugerencia es:

a- Pon a resguardo todos tus datos, fuera del ordenador.

b- Ejecuta desde Windows defrag y chkdsk /f, luego deja espacio libre para instalar Ubuntu, y ejecuta nuevamente chkdsk /f

c- Descarga, verifica la iso y graba la versión alternate-cd de Intrepid.

d- Inicia la instalación con el alternate-cd de Intrepid, al llegar a particionamiento elige manual.

e- Borra todas las particiones linux existentes e instala en las siguientes:

Una primaria, activa, sistema de archivos etx3, de 384 megas, punto de montaje /boot

Una lógica, sistema de archivos intercambio, de 1 giga, punto de montaje por defecto.

Una lógica, sistema de archivos reiserfs ó ext3, de entre 8 y 15 gigas, punto de montaje /

Una lógica, sistema de archivos reiserfs ó ext3, del resto de los gigas disponibles, punto de montaje /home

Al finalizar el Grub en el mbr por defecto.

Al iniciar Ubuntu pulsando: 

Sistema - Administración - Controladores de hardware podrás instalar los drivers privativos de nvidia.

Desde la versión 8.04 Ubuntu trae dkms, un desarrollo conjunto con Dell que con cada actualización del kernel, si los drivers privativos se instalaron con controladores de hardware, no es necesario reinstalarlos, como lo es con el antiguo procedimiento que estas utilizando, que ya es obsoleto e inapropiado.

Instalando desde synaptic disk-manager, podras pulsando:

Sistema - Administración - Administrador de disco
Montar tus particiones Windows sin problemas.

Notas: 

Esto es válido si el Windows XP es original, si se trata de alguna versión "mejorada", pueden ocurrir contratiempos severos con su instalación.  

Si la instalación del alternate da error, debes elegir con las teclas de funcion alguna de las opciones, como safe de gráficas.

Saludos.

Gabriel.

---

### Post by Gpafundi on 2009-04-05
Disculpen mi resignación pero voy a esperar a la nueva versión de Ubuntu a ver si con esa no tengo inconvenientes. Es que me resulta complicado esto...

---

### Post by josecuervo86 on 2009-04-05
No te resignes loco! lo mas probable es que la imagen tenga un error. Pero si queres esperar, espera nomas. Lo mismo voy a hacer yo :D

---

### Post by Gpafundi on 2009-04-24
Instalé el Ubuntu 9.04 sin problemas. Que bueno. Ya extrañaba este sistema operativo. Parece mucho mejor a las anteriores versiones... Igual, gracias a los que intentaron solucionar mi problema.

---

