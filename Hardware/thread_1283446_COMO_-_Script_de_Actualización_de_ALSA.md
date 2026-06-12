---
title: "COMO - Script de Actualización de ALSA"
date: 2009-10-05
forum: Hardware
---

### Post by pablo.s on 2009-10-05
[SIZE=3]**COMO - Script de Actualización de ALSA**[/SIZE]


Escrito por el usuario [soundcheck]("http://ubuntuforums.org/member.php?u=343879") en un [Post original]("http://ubuntuforums.org/showpost.php?p=6589810&postcount=1") en UbuntuForums

[SIZE=2]**CONTEXTO:**[/SIZE]

La idea principal de la actualización de ALSA con el script adjunto
es la de solventar la gran demora (mas de un año) de actualizaciones
suministradas a través de los canales oficiales.
Esta gran demora en mi humilde opinión no es aceptable.
De alguna manera las "autoridades Linux" no se han dado cuenta que
las funciones de audio en un sistema Linux pertenecen a las funciones
más básicas de una computadora, las cuales deben funcionar desde
el primer día.

Al ejecutar la actualización hay una gran probabilidad que su tarjeta de
sonido comience a funcionar debidamente o se resuelvan sus problemas.
Este script le conseguirá la versión estable oficial más reciente de ALSA.
Incluso puede instalar la versión de pruebas más reciente, que está tres
meses más adelante en el desarrollo que la última versión estable.

[SIZE=2]**COMENTARIOS PERSONALES:**[/SIZE]
Algunos comentarios personales acerca de ALSA o audio en Linux y la
falta parcial de soporte en las caracteristicas de las tarjetas de sonido.

El soporte limitado o restringido de ALSA es, antes que nada, un problema
de la industria de las tarjetas de sonido. Muchos fabricantes no hacen disponibles
las descripciones de interface al proyecto ALSA, ni se involucran en el 
desarrollo de drivers.
Comparando las ganancias que están teniendo por el lado del hardware,
el esfuerzo de preparar y mantener un driver tendria que ser obligatorio.
Sabiendo esto, no culpe a Linux o ALSA  si su tarjeta de sonido no funciona
correctamente, dado que lo más probable sea que la culpa no sea de ALSA.
Bastantes problemas son generados por los fabricantes de computadoras,
quienes no escriben BIOS adecuados para integrar debidamente a los chips 
de sonido. Esto desde luego no le facilita las cosas a ALSA.
Cuanta más presión le meta a los fabricantes (solicitando soporte para Linux),
más temprano van a ponerse en acción.
Si quieren mi opinión, los drivers de las tarjetas de sonido deberían ser
gestionados en una manera parecida a la de los drivers de las tarjetas de video,
similar a fglrx de AMD. La variante Open Source usualmente viene con una
funcionalidad limitada y la variante del driver propietario con una funcionalidad
plena. Tengo entendido que hasta Linus Torvalds está en contra de esto, por
muchas razones. Sin embargo, a menos que el problema se comience a solucionar
Linux enfrentará grandes problemas para atraer a una comunidad más grande.
A propósito: Hay una forma de tener instalados ciertos drivers de tarjetas de sonido 
restringidos en Linux. 
Eche un vistazo a OSS (una alternativa a ALSA) de 4-Front-Technologies. Funciona
con un número limitado de tarjetas de sonido (por ejemplo tarjetas Lynx) con
drivers no-propietarios.
Personalmente espero que por la presión del gran número de usuarios Linux, la
situación actual sobre este tema mejore en el futuro.

Hablemos de los problemas de calidad de ALSA. Si, hay bastantes.
Lo que quiero decir, basicamente es que cualquiera está invitado a unirse a las
fuerzas de ALSA para mejorar la performance de ALSA, documentar, etc.
Incluso reportar los problemas en una manera apropiada le hará un contribuyente.
Si todo lo que se hubiera escrito sobre ALSA en este foro (y cientos de otros foros)
se juntara en la página de ALSA en una manera estructurada, supongo que el gran
mundo del audio en Linux sería mucho mejor al día de hoy.

[SIZE=2]**PASEMOS A LA ACTUALIZACION.**[/SIZE]

Paquetes actualizados: Alsa 1.0.21 estable
Bitacora de cambios (changelog): Alsa 1.0.21

DRIVER=alsa-driver-1.0.21
FIRMWARE=alsa-firmware-1.0.20
LIB=alsa-lib-1.0.21
PLUGINS=alsa-plugins-1.0.21
UTILS=alsa-utils-1.0.21
TOOLS=alsa-tools-1.0.21
OSS=alsa-oss-1.0.17

Núcleos soportados: Familia de 2.6.24/26/27/28/29/30/31
(incluyendo al núcleo rt-kernel y el ZEN-rt-kernel que no es de Ubuntu)

Este script no sigue los lineamientos de manejo de paquetes Debian/Ubuntu.
Solamente sobreescribe los archivos existentes. Usted no verá cambios en la
identificación de paquetes de ALSA en Synaptic!
Una función que tiene es la de reconocer problemas graves durante la instalación
y detenerse automaticamente. No debe descomponer su sistema.
Si el script se detiene con un mensaje de error, entonces nada se ha modificado.
En el peor de los casos la opción -r (de restaurar) hace la restauración de su estado
del sistema anterior de la mejor manera posible. Reinstalará el núcleo, los cabezales
del núcleo (kernel-headers) y los paquetes relacionados con ALSA.

Actualizar ubuntu puede sobreescribir esta instalación manual de vez en cuando.
(Por ejemplo durante actualizaciones de versión, actualizaciones de núcleo o de
paquetería de ALSA) En ese caso lo que usted debe hacer es ejecutar nuevamente
el script con la opción -i. Actualizaciones de versión tambien pueden sobreescribir
archivos de configuración importantes, tales como  /etc/modprobe.d/alsa-base.conf.
En ese caso tendrá que restaurar manualmente los archivos de configuración.
SIEMPRE CONSERVE UNA COPIA DE SU ARCHIVO alsa-base.conf  A SALVO!    

[SIZE=2][I]ADVERTENCIA: No me haré cargo de ningún desastre causado por este script (Esto
va por el autor del COMO y por el traductor también). Desde luego que este script
no provoca --siendo bien utilizado y siguiendo las instrucciones correctas-- ningún
desastre. Como siempre, haga un backup antes. Restaurar solo toma cinco minutos
con rsync. Esto puede salvarle horas de solucionar problemas y frustración.[/I][/SIZE]

[SIZE=2]**INSTRUCCIONES DE INSTALACION**[/SIZE]

1. Descargue el script donde lo pueda ejecutar.
2. cd <carpeta-donde-lo-ha-descargado>
3. tar xvf AlsaUpgrade-1.0.21-3.tar
4. sudo ./AlsaUpgrade-1.0.21-4.sh -di
5. sudo shutdown -r 0

> [ATTACH]130878[/ATTACH]


[SIZE=2]**TESTEO Y SOLUCION DE PROBLEMAS**[/SIZE]

Cuando esté de nuevo en sus sistema, abra una terminal y ejecute:

```
cat /proc/asound/version
```Este comando le hará saber si está ejecutando la nueva versión.
La manera mas confiable de verificar si ALSA está funcionando es con
aplay, que es el reproductor de sonido de ALSA. Si aplay no funciona,
nada le va a funcionar.
Asegurese que no tenga canales silenciados y el volumen esté alto!

Escriba en una terminal:

```
aplay -l
```Si su tarjeta de sonido sale listada, ya está en el buen camino.
Para probar su tarjeta por defecto (default-index 0 X=0), escriba:

```
aplay -Dplughw:X,0 -fcd /<su-directorio-con-temas>/<aqui-va-el-nombre-del-tema>.wav
```o
```
speaker-test -Dplughw:X,0 -c2
```Reemplace la X con el indice de su tarjeta de sonido, que se encuentra cuando
usted escribe aplay-l. Fijese en "card X"
Puede probar la salida de multicanales de la siguiente forma:
1. Escriba aplay -L (si, ele mayúscula!) para saber de su dispositivo PCM, por ejemplo
"surround51"
2. Escriba speaker-test -D surround51 -c6
Nota: En caso de que el mapeo de canales sea erroneo deberá ajustarlo en .asoundrc

[B]POR FAVOR: Antes de reportar problemas de "NO TENGO SONIDO!"  fijese si los canales en alsamixer están activados y no silenciados.
[/B]

---

### Post by lady_mcnolium on 2009-10-11
Saludos! buen post... soy nueva en la comunidad, y usando ubuntu tengo pocos años, sucede que hoy en la mañana actualicé unos repos que me propuso el gestor de actualizaciones (de los cuales no me fijé), y desde ese momento estoy sin audio y con algunos cuelgues del sistema que me obligan a apagarlo -porque no me permite hacer más nada-.

El comando aplay -l me lanza lo siguiente:

ariana@ariana-laptop:~$ aplay -l
aplay: device_list:223: no se encontraron tarjetas de sonido...

Gracias de antemano por tu ayuda

---

### Post by pablo.s on 2009-10-11
> **lady_mcnolium said:**
> sucede que hoy en la mañana actualicé unos repos que me propuso el gestor de actualizaciones (de los cuales no me fijé), y desde ese momento estoy sin audio y con algunos cuelgues del sistema que me obligan a apagarlo -porque no me permite hacer más nada-.

Te hago unas preguntas:

1) Qué versión de Ubuntu estás
usando ahora?
2)¿ Tenés la posibilidad de entrar
en modo de recuperación del
sistema (en grub) y ejecutar

```
sudo apt-get update && apt-get upgrade
```

3) En cuanto puedas, posteá la
salida del comando

```
lspci
```

Ah! Bienvenida al foro Ubuntu.

---

### Post by lady_mcnolium on 2009-10-11
Saludos Pablo, estoy usando jaunty, aqui te dejo lo que me lanza el lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
0c:00.0 Network controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Voy a hacer lo del grub y te cuento! 
Gracias por tu bienvenida ^^

---

### Post by lady_mcnolium on 2009-10-11
Bien, ya hice lo del grub y no me aparece nada para actualizar ni instalar.... y sigo sin audio :/

---

### Post by pablo.s on 2009-10-11
Te fijaste si el mezclador
tiene el volumen subido?
Escribí
```
alsamixer
```
y fijate si está alto.

---

### Post by lady_mcnolium on 2009-10-11
sí, está alto... 100 de 100. Y sigo sin sonido :/ tanto los videos de youtube, como todo lo que tenga audio está silenciado. Gracias por tu paciencia!

---

### Post by pablo.s on 2009-10-11
Entonces te recomiendo seguir
el tutorial que está en este post
y ver si se corrige el problema.
Tienes que bajar el archivo
adjunto (está entre la parte de
instrucciones de instalación y
testeo - solución de problemas)
y ejecutarlo.
Mientras se ejecuta te aparecerán
algunas preguntas.
Espero que te sirva.

---

### Post by lady_mcnolium on 2009-10-12
Hola de nuevo che, muchas gracias por la ayuda, he recuperado el sonido :) Sin embargo, cuando intenté hacer el testeo me lanza lo siguiente:

Error de apertura para reproducción: -2,No existe el fichero ó directorio
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM sorround51

Luego cuando trato de solucionarlo con el .asoundrc me lanza 'bash: .asoundrc: orden no encontrada'.... pero bueno, por ahora todo bien, un millón de gracias.

Saludos desde Venezuela.

---

### Post by pablo.s on 2009-10-12
> **lady_mcnolium said:**
> Luego cuando trato de solucionarlo con el .asoundrc me lanza 'bash: .asoundrc: orden no encontrada'.... pero bueno, por ahora todo bien, un millón de gracias.

Saludos desde Venezuela.

Lo que sucede es que .asoundrc
es un archivo de configuración y
los estás llamando como si fuera
un comando. Por eso te dice que 
no lo encuentra.
Puedes probar a editarlo con:

```
nano .asoundrc
```

---

### Post by guillermolisi on 2009-12-05
> **sebapugliese said:**
> Estimados, buenas tardes, les comento mis problemas, hace un tiempo que uso Ubunto, en su version 7.04, si bien tuve siempre el problema que mas tarde mencionare, acabo de mudarme a su version 9.10, es increible su funcionamiento y aspecto grafico, la verdad es un sistima muy bueno. Bueno acerca de mi problema que lo vengo arrastrando desde la version 7.04, el sistema esta instalado en mi Acer Aspire 3680, y siempre he tenido el problema de que no me reconoce los altavoces de la maquina, si enchufo altavoces externo el sonido anda perfecto, asi que me parece que no es problema de placa de sonido o driver. Probe alsamixer y esta todo bien, probe modificar el alsa-base.conf, de todas las maneras habidas y nada. Probe instalando el nuevo driver del que habla este post y nada, al parecer no soy el primero en tener el problema.
Sebastian
Post movido a un nuevo thread en la seccion Hardware

---

### Post by noisecl on 2009-12-10
Gracias, buscando por internet llegué aquí cuando empece desde ayer (10-12-2009) a tener problemas con el sonido justo cuando se actualizó al kernel 2.6.31-16-generic. 
No tengo la remota idea de por qué. Pero este post fue de gran ayuda :KS

---

### Post by infolinuxar on 2010-06-27
Ya estoy en la versión 1.0.23 también me canse de tocar todas las  preferencia de sonido  para que  funcione el micrófono en mi hp  dv4-1212la  con el skype pero no logro hacerlo  funcionar. De todas  manera dejo un  tutorial que traduje al español para actualizar  a la  versión de Alsa 1.0.23 . 
 
Aquí dejo  el link  con la traducción  y  su fuente original.

[En español]("http://www.tobauntu.com.ar/2010/06/27/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

[Original]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")


Saludos

---

### Post by ma_chro on 2010-11-25
Buenas tardes, estoy intentando tener sonido en mi Vaio recién comprada.
Estuve leyendo un poco tu post, y quisiera enviarte unos datos para ver si me podés ayudar:

**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC269 Analog [ALC269 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: HDMI [HDA ATI HDMI], dispositivo 3: ATI HDMI [ATI HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
mario@mario-laptop:~$ speaker-test -Dplughw:X,0 -c2

speaker-test 1.0.22

El dispositivo de reproducción es plughw:X,0
Los parámetros del flujo son 48000Hz, S16_LE, 2 canales
Usando 16 octavas de ruido rosa
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Error de apertura para reproducción: -19,No existe el dispositivo


Como verás la placa está.
Pero no emite ningún sonido.

Desde ya te agradezco cualquier ayuda que pudieras darme.

Saludos para todos.

Mario

---

### Post by ma_chro on 2010-12-06
Finalmente pude solucionar mis problemas de sonido.
Actualicé a 10.10 y listo.

Saludos :)

---

