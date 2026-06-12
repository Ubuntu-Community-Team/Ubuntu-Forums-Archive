---
title: "Inrepid Ibex no detecta placa de audio &amp; no funciona la placa ethernet"
date: 2009-03-23
forum: Hardware
---

### Post by ZeT76 on 2009-03-23
Buenas! Soy nuevo en el foro y tengo ALGO  de experiencia (básica) en Ubuntu. 

Después de bastante tiempo de usar el Win, decidí hacer una nueva prueba con el Ubuntu.Bajé la nueva versión (Intrepid Ibex) y después de instalado el sistema, no me reconoce la placa de audio (hace como si no hubiera hardware) y con la placa de red tengo el problema de que si bien me la detecta, con el pppoeconf no puedo configurar la cta de mi ISP.

Si alguien tiene una idea de cómo puedo hacer apra solucionar estos dos inconvenientes, se los agradezco! Los datos de mi maquina, deberían aparecer en la firma.

Saludos y gracias!

---

### Post by pablo.s on 2009-03-23
Hola: Por favor podrias ser tan amable de tipear en una terminal estos comandos:

**lspci**

**ifconfig**

y después copiar y pegar el texto que te devuelve el comando? Gracias

---

### Post by ZeT76 on 2009-03-23
Hola Pablo, gracias por responder! Olvidé mencionar antes que instalé la version de 64 bits. Instalé también el Kubuntu para ver si se resolvía, pero no fue así. Te copio acá abajo lo que me pediste:

lspci:


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)



ifconfig:


eth0      
Link encap:Ethernet  direcciónHW 00:1b:93:6e:6b:a3  
          
dirección inet6: fe80::21a:92ff:fe6d:6ca3/64 Alcance:Vínculo
          
ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
colisiones:0 txqueuelen:1000         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
Interrupción:22 

lo        
Link encap:Bucle local  
          
inet dirección:127.0.0.1  Máscara:255.0.0.0
          
dirección inet6: ::1/128 Alcance:Anfitrión
          
ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



cuando le doy al pppoeconf:


Lo siento, se consultaron 2 interface(s), pero no respondió el concentrador de acceso de su proveedor.Por favor, verifique sus cables de red y del módem. Otra razón del fallo puede ser también que esté ejecutándose otro proceso pppoe y que éste esté controlando el módem.

Gracias!

---

### Post by pablo.s on 2009-03-23
Ok, lei un pedazo de información en Internet para darte una respuesta 
que te sirva y he llegado a la conclusión que el problema radica en que
el núcleo de la versión 64 bits no se lleva bien con la placa de red.
Le harías una prueba con la versión Desktop de 32 bits, sin instalarla y 
fijarte si de esa forma levanta la placa de red, configura pppoeconf y 
sale sonido de la placa de sonido? Creo que es eso.

---

### Post by ZeT76 on 2009-03-26
Estimado Pablo,

Quería comentarte y comentarle al resto que le interese que tenías razón. Baje e instalé Ubuntu 32 bits y no tuve problema ni de red ni de audio, funciona todo OK!

Mil gracias y un saludo,
:popcorn:

---

### Post by faktorqm on 2009-03-27
si el modem es ethernet pasalo a modo router, se desaconseja el uso de pppoeconf. salu2!

---

### Post by josecuervo86 on 2009-03-28
Es media facilista la solución de pasarse a 32 bits por que no te ande el router o lo que sea. Lo copado seria poder lograr que ande en 64 bits para no desperdiciar el poder de ese procesador.

---

### Post by pablo.s on 2009-03-28
> **josecuervo86 said:**
> Es media facilista la solución de pasarse a 32 bits por que no te ande el router o lo que sea. Lo copado seria poder lograr que ande en 64 bits para no desperdiciar el poder de ese procesador.

Decime dos aplicaciones que utilicen el poder del procesador de
64 bits y del multithreading y yo te digo 200 que no lo hacen.

---

### Post by josecuervo86 on 2009-03-28
> **pablo.s said:**
> Decime dos aplicaciones que utilicen el poder del procesador de
64 bits y del multithreading y yo te digo 200 que no lo hacen.

Claro, porque la computación avanza tan lento que nunca se va a llegar a implementar masivamente no? Qudate con tu Amiga, que en su momento fue lo mas, total :roll:

---

### Post by pablo.s on 2009-03-28
> **josecuervo86 said:**
> Qudate con tu Amiga, que en su momento fue lo mas, total :roll:

No me respondiste la pregunta, sigo esperando...

---

### Post by josecuervo86 on 2009-03-28
> **pablo.s said:**
> No me respondiste la pregunta, sigo esperando...

Aca[0] tenes una lista de las librerias multithread de Gnu. Te va? ;)

[0][http://www.gnu.org/software/pth/related.html]("http://www.gnu.org/software/pth/related.html")

---

### Post by pablo.s on 2009-03-28
Mirá Josecuervo86, veo que no estamos discutiendo de lo mismo y
no quiero tener problemas con Hei Ku, pero evidentemente no te
estás dando cuenta que estamos desbaratando el post (que por otro
lado ya estaba solucionado). Así que por mi parte dejo acá la
discusión, si te place podés abrir un nuevo tema en Comunidad y
todos juntos podemos aclararte el tema de optimizaciones de
procesador y multithreading. Implicar a una noble maquina como la
Amiga que debe estar en alta estima para mucha gente del foro en
una presunción para atacar a alguien, me da muy mala leche.
Saludos.

---

### Post by josecuervo86 on 2009-03-29
Por mi parte tambien lo dejo aca. Pero mala leche, nada. Solo tome un ejemplo de una maquina que fue un icono en su tiempo, para conceptualizar la idea. Queda ahi. Despues uno saca sus concluciones.
Un abrazo

---

