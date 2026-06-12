---
title: "Sin audio en audifonos"
date: 2009-07-16
forum: Hardware
---

### Post by patolin on 2009-07-16
Caballeros,
Primero que nada gracias por mantener este foro. Es mi primer post luego de casi 2 meses con Ubuntu 9.04 instalado, sin partición en mi notebook Packarbell PB85.

Todo anda de maravilla, al principio los ripios propios de alguien que no domina en absoluto el tema del código libre. Pero no me arrepiento, nunca mas con Window$

Tengo solo un problema que me rompe el mate. al conectar mis audífonos o parlantes externos a mi notebook no tengo sonido, los parlantes del pc no suenan, pero tampoco los audífonos.

Ví el alsamixer en Terminal y no tengo la opción de audífonos o headphones para subir el volumen o nada. Además vi en preferencias con el boton derecho en el "parlante" o en control de volumen y no logro resolver el tema.

Alguién podrá ayudarme?
Que información debo colocar para hacer mas facil su ayuda?

Gracias

---

### Post by moreback on 2009-07-16
Hola: un **lspci** entrega información del hardware que tienes, y un **aplay -l** indica que dispositivos tienes reconocidos con ALSA. Ejecuta estos comandos en un terminal y nos posteas la salida.

PD: esto debiste haberlo posteado en Hardware, te recomiendo que tengas más cuidado para la próxima y que leas los mensajes que estan adheridos en cada sub-foro y que te acostumbres a usar la búsqueda, por que es probable que tu problema ya tenga solución en el foro.

Saludos.

---

### Post by Carlos C on 2009-07-16
Movido al subforo "Hardware".

---

### Post by moFeta on 2009-07-27
Lo solucionaste?
Porque si no, simplemente tienes que activar la salida de audio por los audífonos. Click en el ícono de Control de Volumen, abres el control de volumen haciendo click en el botón que lo señala, en la pestaña "Conmutadores" tienes que activar la salida de audífonos y listo. Si no tienes la pestaña conmutadores, click en Preferencias, y ahí seleccionas Headphones y te debería aparecer la pestaña.

Suerte.

---

### Post by volodia1984 on 2009-09-06
Hola:
Tengo el mismo problema con la salida de sonido por los audifonos. Ya realice los pasos que se indican para solucionar el problema, a través del control de volumen, pero no pude solucionarlo por que no tenía la opción de audifonos.
Utilice los comandos y obtuve lo siguiente:
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC861VD Analog [ALC861VD Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
Porfavor, si pudieran darme una solución.
Llevo muy poco tiempo utilizando ubuntu 9.04

Gracias.

---

### Post by CdK1 on 2009-09-07
Eso es porque NO tienes configurado el sonido... intenta con alsa, sudo apt-get install alsa-oss alsa-base alsa-utils
luego sudo alsaconf y reboot...

---

### Post by volodia1984 on 2009-09-07
Hola:

Aplique los comandos que me enviaron, pero los dos últimos no los pude ejecutar.
Ahora, la cosa esta peor, no tengo salida de audio por los parlantes.
Agradeceria mucho si pudieran ayudarme a solucionar el problema.
Aqui va la información que me entrega el terminal cuando ejecuto los comandos.

edmundo@edmundo:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
edmundo@edmundo:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC861VD Analog [ALC861VD Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
edmundo@edmundo:~$ alsa
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
edmundo@edmundo:~$ sudo apt-get install alsa-oss alsa-base alsa-utils
[sudo] password for edmundo: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
alsa-oss ya está en su versión más reciente.
alsa-base ya está en su versión más reciente.
alsa-utils ya está en su versión más reciente.
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  ttf-wqy-zenhei linux-headers-2.6.28-11 java-common
  linux-headers-2.6.28-11-generic
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
edmundo@edmundo:~$ sudo alsaconf
sudo: alsaconf: command not found
edmundo@edmundo:~$ reboot
reboot: Es necesario ser superusuario

Muchas gracias.

---

### Post by gmo2009 on 2009-09-12
Hola.
Yo tenia el mismo problema buscando encontré lo siguiente:
abre una ventana Terminal
escribes: "sudo gedit /etc/modprobe.d/alsa-base.conf"
se abrirá el editor y te preguntará la password la ingresas, cargará el archivo "alsa-base.conf", al final le escribes lo siguiente: 

options snd-hda-intel model=auto

luego guardas, y reinicias el equipo.
(me di cuenta que tenemos el mismo modelo intel 861vd), cuando puse ese comando se activó el plug de los audifonos.
Espero te sirva la información.

---

### Post by andrestes7 on 2012-10-04
resulta que tengo un asus n46sv y le acabo de instalar ubuntu 12.04 y el parlante externo que tiene el computador ya no me funciona (la entrada del parlante es diferente a la de los audifonos)

---

