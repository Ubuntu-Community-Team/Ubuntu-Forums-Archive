---
title: "Problemas con Live CD Ubuntu 8.04.1"
date: 2008-10-04
forum: Hardware
---

### Post by milonga on 2008-10-04
Luego de recibir la famosa carta documento que está enviando la Asociación Civil Software Legal, me decidí definitivamente a pasarme a Linux, y me recomendaron Ubuntu, ya que soy un ignorante TOTAL en esta materia.

Descargué las versiones de 64 y 32 bit con Live CD pero ninguna me funciona para probarlo.

Mi PC es una Pentium D de 3.5 Mhz sobre Mother MSI Platinum, 2 GB de RAM, placa de video ATI Radeon X1300 256 Mb PCI Express y disco Maxtor SATA 190 Gb. Lo peor es que en la de mi viejo, una Intel Dual Core de 1 Gb RAM comprada en Garbarino (las Commodore truchas que viene con el RXart de SO) funciona bien, por lo menos entra ... aunque a veces se cuelga y hay que resetear.

Quisiera saber si alguien sabe porqué no me funca a mí ... el Memtest me dió bárbaro.

Inserto el CD, bootea, elijo el idioma y luego selecciono probar desde el CD ... empieza a bailar la barrita y después lentamente se empieza a llenar; antes de llegar al último cuadradito, se cuelga. En la versión de 64 bit se para definitivamente y en la de 32 bit se autoreinicia constantemente ... solo una vez de las tantas pruebas en la versión de 64 bit pasó a una pantalla negra con las letras blancas y el tildado de OK en cada verificación, pero se paró al llegar al dinal de la pantalla.

Si me pueden ayudar les agradecería, porque no me gustaría particionar mi disco para intentar instalar el Ubuntu y que después no funcione o se me cuelgue a cada rato.

Muchas gracias a todos de antemano ...

---

### Post by gmunioz on 2008-10-04
hola mil...:
En principio debes tener en cuenta que Linux no es Windows, y es aconsejable que leas un poco al respecto, lee el foro y la documentación.
Respecto de tu problema parece que se debe a tu tarjeta de video, las ATI son problemáticas, problemáticas, no imposibles.
Te sugiero, ya que debes eliminar tu software ilegal e instalar si ó si uno legal, que:
1) Bajes el cd de la versión alternate 32 bits, debes marcar el recuadro debajo del boton start download del sitio de descarga.
Esta versión tiene más opciones de instalación, menos problemas con las gráficas y es tan simle de instalar como la version live, y de 32 bits porque la diferencia con la de 64 en redimiento es despreciable y los problemas con las aplicaciones deficientes o inexistentes son mayores.
2) La instalación la hagas con el siguiente procidimiento:
Inicia con el cd alternate y eliges la primer opción del menu, cuando llegues a particionamiento elige manual, elimina todas las particiones e instala en:
Una partición primaria, activa,sistema de archivos ext3, de 384 megas, punto de montaje /boot
Una partición lógica, sistema de archivos reiserfs, de 15 gigas, punto de montaje /
Una partición lógica, sistema de archivos de intercambio de 1 giga, punto de montaje automático para swap
Una partición lógica, sistema de archivos reiserfs, de 15 gigas, punto de montaje /home
Una partición lógica, sistema de archivos reiserfs, del resto del disco, punto de montaje /home/tusuario/datos
El grub por defecto en el mbr
Cuando inicies, luego de terminada la instalación, deberás ejecutar en consola ( Aplicaciones - Accesorios - Terminal) la orden
sudo chmod -Rf 777 /home/tuusuario/datos
para poder leer y escribir en esa partición.
Y luego desde synaptic instalar envy-ng para instalar los drivers de tu tarjeta, sin problemas.
3) Para el caso de que tengas problemas de instalación por tu tarjeta, elige en el menu la tercer opción, es el sistema solo linea de comandos, los instalas igual, solo que al iniciar lo harás en consola, entonces ejecutando:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu desktop
Tendrás instalado el sistema gráfico completo.
Saludos. Gabriel.
Solo doy soporte para Ubuntu - 6666 - Más malo que el diablo.

---

### Post by faktorqm on 2008-10-04
Hola, podrias llegar a probar instalar con un cd que se llama alternate cd, que es lo mismo que el grafico pero en texto con ventanas dibujadas. Lo descargas de la pagina oficial de ubuntu y antes de apretar download te buscas la opcion que esta al lado del boton que te dice "quiero el alternate cd". 

Tambien podes probar apretar exactamente luego de elegir el idioma la opcion "opciones de arranque" y escribir al final de la linea "noapic" sin comillas. Tambien podes probar con "nolapic" o con las dos juntas. 
Contanos como te fue. Salu2!

---

### Post by milonga on 2008-10-04
Les agardezco la pronta respuesta a ambos ... en realidad quería probarlo antes de instalarlo, pero si no queda otra lo voy a instalar como me dicen ustedes, pero voy a tardar unos días porque quiero comprar otro rígido para dedicarlo exclusivamente a Linux.

Ya me bajé unos tutoriales y manuales de Ubuntu, pero como no lo podía usar con el Live CD, ni me calenté en leerlo.

Gracias por el dato de las ATI y Linux ... saludos

---

### Post by Hei Ku on 2008-10-04
lo de las ATI no es tan asi. Ciertos modelos de ATI son dificiles, nada mas.
Lo mismo pasa con Nvidia, para el caso.

---

