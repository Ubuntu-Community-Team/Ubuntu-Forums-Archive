---
title: "[SOLUCIONADO] Ubuntu se me pega"
date: 2009-06-01
forum: Hardware
---

### Post by radixs on 2009-06-01
Tengo un laptop Packcard Bell EasyNote B3221. Con Ubuntu 9,04 y Win xp

Hola bueno les comento Ubuntu se pega, puedo estar trabajando en el o no estar ejecutando nada y simplemente se pega. hay algo que me llama la atención cuando este pega, el led indicador de mayúsculas y minúsculas se queda parpadeando.

Si sirve de algo dejo mi lspci

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

---

### Post by pagondel on 2009-06-01
el contra-ataque de [[COLOR="DarkRed"]Tickless en Jaunty[/COLOR]](http://foros.ubuntu-cl.org/viewtopic.php?t=5869)???? :S

---

### Post by felipeleven on 2009-06-01
> **pagondel said:**
> el contra-ataque de [[COLOR=DarkRed]Tickless en Jaunty[/COLOR]]("http://foros.ubuntu-cl.org/viewtopic.php?t=5869")???? :S
jajaja

:S, ojalá que no, estoy usando jaunty y no tiene ese problema que si tenía hardy.

Radixs:
Por favor, si pudieras describir el tipo de cuelgue, si acaso es total o no (si acaso se mueve el mouse etc). También puede probar apretando la siguiente combinación de teclas en el momento que se cuelgue tu computador:

ctrl+alt+imp pnt+REISUB

es decir, mantener el "ctrl", "alt", "imp pnt" oprimidos y manteniéndolos así comenzar a teclear de a uno R, E, I, S, U y B, al hacer esto tu computador debería reiniciarse de forma segura, en caso de que no funcionará estariamos hablando de un cuelgue total.

Saludos

---

### Post by moreback on 2009-06-04
Que el indicador de Mayúsculas parpadee puede ser signo de algo raro, ¿leiste el manual de tu notebook? ¿qué dice respecto a las formas de parpadear de los leds?

---

### Post by radixs on 2009-06-05
> **moreback said:**
> Que el indicador de Mayúsculas parpadee puede ser signo de algo raro, ¿leiste el manual de tu notebook? ¿qué dice respecto a las formas de parpadear de los leds?

Uff me pides algo que debe de estar quisas donde ya que el note, tiene mas de 4 años... lo buscare el pagina del fabricante, gracias..

---

### Post by Patriciologico on 2009-06-07
A mi me sucedia un cuelgue alrededor de cinco minutos iniciados el sistema, parpadeando las luces Bloq Mayus (en mi caso se soluciono desintalando network-manager) para dar con el error lei los mensajes del visor de sucesos del sistema. Vi si ahi te aparece algun error.

Saludos

---

### Post by guillermolisi on 2009-06-07
Para poder seguir administrando la interface WiFi al haber desinstalado el Network Manager se puede instalar Wicd que a mucha gente le ha dado muy buenos resultados y evita tener que admnistrar a mano las conexiones inalambricas.

---

### Post by javierll on 2009-06-09
Pues a mie pasa lo mismo, si se me mueve la flecal del raton y si funciona lo de Ctrl-Alt.....etc pero no me parpadea nada...

---

### Post by Carlos C on 2009-06-09
> **javierll said:**
> Pues a mie pasa lo mismo, si se me mueve la flecal del raton y si funciona lo de Ctrl-Alt.....etc pero no me parpadea nada...
Como ya iniciaste un thread para ese tema te propongo que sigamos la conversación allí:

[http://ubuntuforums.org/showthread.php?t=1182870](http://ubuntuforums.org/showthread.php?t=1182870)

Evita por favor postear más de una vez presentando tu problema, de esa manera evitamos desorden y es más fácil establecer tu situación actual y tratar de ayudarte.
Saludos.

---

### Post by radixs on 2009-06-09
> **guillermolisi said:**
> Para poder seguir administrando la interface WiFi al haber desinstalado el Network Manager se puede instalar Wicd que a mucha gente le ha dado muy buenos resultados y evita tener que admnistrar a mano las conexiones inalambricas.


Listom, solo vasto con quitar Network Manager y se soluciono el problema. gracias xD

---

