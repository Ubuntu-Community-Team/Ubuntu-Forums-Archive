---
title: "Acer Aspire 3680 con 9.10 sin reconocer altavoces"
date: 2009-12-05
forum: Hardware
---

### Post by sebapugliese on 2009-12-05
Estimados, buenas tardes, les comento mis problemas, hace un tiempo que uso Ubunto, en su version 7.04, si bien tuve siempre el problema que mas tarde mencionare, acabo de mudarme a su version 9.10, es increible su funcionamiento y aspecto grafico, la verdad es un sistima muy bueno. Bueno acerca de mi problema que lo vengo arrastrando desde la version 7.04, el sistema esta instalado en mi Acer Aspire 3680, y siempre he tenido el problema de que no me reconoce los altavoces de la maquina, si enchufo altavoces externo el sonido anda perfecto, asi que me parece que no es problema de placa de sonido o driver. Probe alsamixer y esta todo bien, probe modificar el alsa-base.conf, de todas las maneras habidas y nada. Probe instalando el nuevo driver del que habla este post y nada, al parecer no soy el primero en tener el problema. Este es mi lspci
 
sebastian@sebastian-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
sebastian@sebastian-laptop:~$

Espero que puedan ayudarme. 
Saludos
Sebastian

---

### Post by sebapugliese on 2009-12-07
> **sebapugliese said:**
> Estimados, buenas tardes, les comento mis problemas, hace un tiempo que uso Ubunto, en su version 7.04, si bien tuve siempre el problema que mas tarde mencionare, acabo de mudarme a su version 9.10, es increible su funcionamiento y aspecto grafico, la verdad es un sistima muy bueno. Bueno acerca de mi problema que lo vengo arrastrando desde la version 7.04, el sistema esta instalado en mi Acer Aspire 3680, y siempre he tenido el problema de que no me reconoce los altavoces de la maquina, si enchufo altavoces externo el sonido anda perfecto, asi que me parece que no es problema de placa de sonido o driver. Probe alsamixer y esta todo bien, probe modificar el alsa-base.conf, de todas las maneras habidas y nada. Probe instalando el nuevo driver del que habla este post y nada, al parecer no soy el primero en tener el problema. Este es mi lspci
 
sebastian@sebastian-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
sebastian@sebastian-laptop:~$

Espero que puedan ayudarme. 
Saludos
Sebastian

Alguien me puede dar una mano con esto????

---

### Post by sebapugliese on 2009-12-11
Por favor en ubuntu 9.10, no tengo sonido de ninguna forma ya he probado todo lo que estaba a mi alcance,ayuda.
En el 7.04, el problema solo eran los altavoces de la notebock, pero ahora no tengo sonido de ninguna forma, ya probe con el alsamixer y estaria todo bien, pero el sonido no aparece, ya no se que hacer.
post anterior sin ninguna respuesta
[http://ubuntuforums.org/showthread.php?t=1347083](http://ubuntuforums.org/showthread.php?t=1347083)
Sebastian

---

### Post by Mauro22 on 2009-12-12
Hacer multiposting no va a conseguirte mas respuesta:


5 min en Google:

[http://ubuntuforums.org/showthread.php?t=537676](http://ubuntuforums.org/showthread.php?t=537676)

En resume dice que hay que bootear con el parametro:

acpi=off


Si no sabes como hacerlo, avisá, si no funciona, también

---

### Post by guillermolisi on 2009-12-12
> **sebapugliese said:**
> Por favor en ubuntu 9.10, no tengo sonido de ninguna forma ya he probado todo lo que estaba a mi alcance,ayuda.
En el 7.04, el problema solo eran los altavoces de la notebock, pero ahora no tengo sonido de ninguna forma, ya probe con el alsamixer y estaria todo bien, pero el sonido no aparece, ya no se que hacer.
post anterior sin ninguna respuesta
[http://ubuntuforums.org/showthread.php?t=1347083](http://ubuntuforums.org/showthread.php?t=1347083)
Sebastian
Threads merged.

Si no hay respuestas puede ser que los que puedan ayudar aun no hayan leido el thread.

Para revivir el thread lo que se debe hacer es un bump, es decir, enviar un nuevo post al mismo thread como recordatorio (mas o menos como hiciste con tu segundo mensaje en el hilo original).

Por favor, no abrir nuevos threads por falta de respuestas.
Gracias.

---

### Post by sebapugliese on 2009-12-12
> **guillermolisi said:**
> Threads merged.

Si no hay respuestas puede ser que los que puedan ayudar aun no hayan leido el thread.

Para revivir el thread lo que se debe hacer es un bump, es decir, enviar un nuevo post al mismo thread como recordatorio (mas o menos como hiciste con tu segundo mensaje en el hilo original).

Por favor, no abrir nuevos threads por falta de respuestas.
Gracias.

De cualquier forma muchas gracias

---

### Post by sebapugliese on 2009-12-12
> **Mauro22 said:**
> Hacer multiposting no va a conseguirte mas respuesta:


5 min en Google:

[http://ubuntuforums.org/showthread.php?t=537676](http://ubuntuforums.org/showthread.php?t=537676)

En resume dice que hay que bootear con el parametro:

acpi=off


Si no sabes como hacerlo, avisá, si no funciona, también
Estimado lamento no saber invertir tan bien mis 5 minutos como lo haces vos. Ademas si no lo he hecho es por que quizas no se como hacerlo, al menos en mi ubunto el archivo al que hace mencion dentro del grub no lo puedo encontrar (menu.lst), al igual que el comando kate, no se que es lo que hace y cuando tipeo sudo kate, si bien me pide el pass me dice que desconece dicho comando, te agradeceria si pudieras darme un poco mas de ayuda, ya que esto ya lo habia probado pero no me habia solucionado el problema, tambien he probado modificar alsaconf, agregando la marca y todas esas cosas. Gracias

---

### Post by guillermolisi on 2009-12-12
> **sebapugliese said:**
> Estimado lamento no saber invertir tan bien mis 5 minutos como lo haces vos. Ademas si no lo he hecho es por que quizas no se como hacerlo, al menos en mi ubunto el archivo al que hace mencion dentro del grub no lo puedo encontrar (menu.lst), al igual que el comando kate, no se que es lo que hace y cuando tipeo sudo kate, si bien me pide el pass me dice que desconece dicho comando, te agradeceria si pudieras darme un poco mas de ayuda, ya que esto ya lo habia probado pero no me habia solucionado el problema, tambien he probado modificar alsaconf, agregando la marca y todas esas cosas. Gracias
Kate es un editor de texto plano, equivalente a gEdit o similares, solo que existe en ambientes KDE, no viene con Gnome.

Si no tenes el archivo /boot/grub/menu.lst es porque estas usando la version 1.97 (comunmente llamado 2) de Grub y ahi cambia radicalmente su estructura de archivos.

Podrias mostrar la salida del comando "lsmod" (sin las comillas) ingresado en una consola/terminal ?

Por favor, evitar comentarios ironicos que restan energia en la resolucion del problema.

---

### Post by guillermolisi on 2009-12-12
> **sebapugliese said:**
> Estimados es mas facil ver el error que simplemente contestar una consulta?
De cualquier forma muchas gracias
Es tan facil o tan dificil una cosa como la otra y no son excluyentes entre si.

Hice la observacion en un intento de ayudarte a que aproveches mas y mejor el foro, que tiene sus reglas y estan todas en la primer pagina, como sticky threads, del Argentina LoCo Team subforum.

---

### Post by Mauro22 on 2009-12-12
Antes de andar modificando archivos te conviene probar primero:


Cuando llegas a la pantalla del grub y si no ves el menú apretas ESC. (o si es GRUB2 mantené apretado SHIFT antes de que aparezca)

Una vez en la lista de kernels, elegi el mas reciente (generalmente el primero) y apretas la E para editar la entrada, aparecen varios renglones, con las flechas selecciona la mas larga y apretas E otra vez y al final pones acpi=off

Apretas ESC y despues la B para bootear esa entrada... si tenes audio, postealo aca para hacer ese cambio definitivo.


En el livecd anda el audio?

---

### Post by sebapugliese on 2009-12-13
> **Mauro22 said:**
> Antes de andar modificando archivos te conviene probar primero:


Cuando llegas a la pantalla del grub y si no ves el menú apretas ESC. (o si es GRUB2 mantené apretado SHIFT antes de que aparezca)

Una vez en la lista de kernels, elegi el mas reciente (generalmente el primero) y apretas la E para editar la entrada, aparecen varios renglones, con las flechas selecciona la mas larga y apretas E otra vez y al final pones acpi=off

Apretas ESC y despues la B para bootear esa entrada... si tenes audio, postealo aca para hacer ese cambio definitivo.


En el livecd anda el audio?

Mauro, muchas gracias pero en live cd tampoco funciona, intente lo que me decis pero cundo edito el grub (2), y le agrego al final esa linea no me lo guarda, apreto la e y escribe la e en pantalla, no se si estoy haciendo algo mal o que???, probe modificar el grub.conf, con el gedit no puedo no?. Puedo modificarlo con algun otro editor?
Aguardo comentarios saludos
Me olvidaba en el 7.04 funcionaba el sonido siempre y cuando le conectaras auriculares o parlantes externos, los altavoces de la maquina no andaban, pero tenia sonido ahora ni eso.

---

### Post by sebapugliese on 2009-12-14
Estimados buenos dias ayer instale KDE y al menos cuando inicia el sistema el sonido sale por los altavoces, pero cuando quiero escuchar algun mp3 o ver algun video por el youtub..., se queda nuevamente muda. Mirando por hay vi que Seting... puedo configurar el hardware para reproducir sonidos, me aparacen como si fueran 4 placas de sonido, en la primera que dice Alc883 (Analog), hago clic en test y anda perfecto en las otras tres nada. Como hago para predefinir que el sonida salga por esa placa? Creo que ya estamos cerca.
Saludos
Sebastian

---

### Post by Mauro22 on 2009-12-14
Te da error al querer escuchar mp3 o simplemente hace como que lo reproduce??

Tenés instalado el paquete ubuntu-restricted-extras ?

Para kde es kubuntu-restricted-extras

---

### Post by sebapugliese on 2009-12-14
Mauro buen dia, eso a que te referis es el que restringe los driver??? si es asi si lo tengo instalado al paquete. Y si hace que lo reproduce pero no se escucha nada.

---

### Post by sebapugliese on 2009-12-15
Alguien que pueda ayudarme con esto??? Ademas descubr en KDE que si reproduzco medios o musica desde Amarock se escucha perfecto, pero por ejemplo los videos de youtube o cosas asi no tienen sonido. Ayuda por favor.

---

### Post by sebapugliese on 2009-12-19
Alguna ayuda con esto. Por Favor

---

### Post by LessOne on 2010-03-29
La solucion la podes encontrar por aca...

---

### Post by guillermolisi on 2010-03-29
Y donde queda "aca" ? :)

---

