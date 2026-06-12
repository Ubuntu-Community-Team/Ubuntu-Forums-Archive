---
title: "Problemas con wireless Atheros"
date: 2009-06-16
forum: Hardware
---

### Post by ALEXEX on 2009-06-16
Hola.
 
Ya pude instalar el ubuntu en mi netbook gracias a los compañeros de la comunidad ;), pero me enfrento a un nuevo problema, jajaja, que es como configurar el wireless en UBUNTU 9.04, mi netbook es una ASUS 1000HA.
 
Les comento lo que e realizado:
 
**En controladores de hardware me aparece: Se estan usando controladores privativos para que este equipo funcione correctamente. Me aparece que el controlador Atheros <<madwifi>> alternativo esta activado y se esta usando.
 
**En la terminal al momento de poner: sudo lshw -C network me aparece:
 
[SIZE=3][FONT=Times New Roman]*-network               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Ethernet interface [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       product: L1e Gigabit Ethernet Adapter [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       vendor: Attansic Technology Corp. [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:03:00.0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       logical name: eth0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       version: b0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       serial: 00:24:8c:27:96:ec [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capacity: 100MB/s [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       width: 64 bits [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no module=atl1e multicast=yes port=twisted pair [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  *-network UNCLAIMED [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Ethernet controller [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       product: AR242x 802.11abg Wireless PCI Express Adapter [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       vendor: Atheros Communications Inc. [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:01:00.0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       version: 01 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       width: 64 bits [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: pm msi pciexpress msix cap_list [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: latency=0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  *-network DISABLED [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Ethernet interface [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 1 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       logical name: pan0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       serial: 1a:4a:2b:5b:82:5d [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: ethernet physical [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes [/FONT][/SIZE]
 
 
Ya tengo el driver de la wireless para xp. Espero sus respuestas.

---

### Post by pablo.s on 2009-06-16
OK. Si está madwifi funcionando
quiere decir que tienes la placa
operativa. No te detecta ninguna red?

EDIT:
Ahora que veo que utilizas Kubuntu
me viene la interrogante:
¿no te aparece Network Manager?

---

### Post by ALEXEX on 2009-06-16
> **pablo.s said:**
> OK. Si está madwifi funcionando
quiere decir que tienes la placa
operativa. No te detecta ninguna red?
 
EDIT:
Ahora que veo que utilizas Kubuntu
me viene la interrogante:
¿no te aparece Network Manager?
 
 
hola pablo, me equivoque al configurar mi perfil, utlizo ubuntu 9.04, el kubuntu lo tengo en la pc de mi casa.
 
Mira al momento de entrar a Sistema >Preferencias > Conexiones de red
En la pestaña de Inalambrica no me parece ninguna conexion, ni me aparece que me puedo conectar (como Win2), que sera?

---

### Post by pablo.s on 2009-06-16
Mejor entonces.
Pregunta tonta aunque
un poco obligatoria:
¿Hay una red WiFi en las
cercanias, verdad?

---

### Post by ALEXEX on 2009-06-16
> **pablo.s said:**
> Mejor entonces.
Pregunta tonta aunque
un poco obligatoria:
¿Hay una red WiFi en las
cercanias, verdad?
 
si, efectivamente hay muchas, osea si buscas con Win2 te detecta como 3 aqui en la zona, pero en realidad voy a utilizarla del trabajo ya que tengo la clave y el password.

---

### Post by pablo.s on 2009-06-16
En el panel, te debe aparecer
un icono con dos computadoras
pequeñitas. Si haces clic ahi, te
debería mostrar alguna red que
esté en el alcance.
Figura alguna ahi?

---

### Post by ALEXEX on 2009-06-16
No me aparece nada, pero con otra laptop de aqui del trabajo que iene Win2 si aparecen tres conexiones.
 
Me dice un compañero que quizas no este funcionando correctamente la tarjeta de red, que puedo hacer S.O.S. S.O.S. S.O.S.

---

### Post by pablo.s on 2009-06-16
En una terminal escribe:

**[COLOR=DarkGreen]ifconfig[/COLOR]**

luego copia y pega en 
un post nuevo lo que
salga.

---

### Post by ALEXEX on 2009-06-16
alex@XploitR3:~$ ifconfig 
eth0 Link encap:Ethernet direcciónHW 00:24:8c:27:96:ec 
inet dirección:XXX.XXX.X.XX Difusión:XXX.XX.X.XXX Máscara:255.255.255.0 
dirección inet6: fe80::224:8cff:fe27:96ec/64 Alcnce:Vínculo 
ARRIBA DIFUSIÓN CORRIENDO MULTICAST MTU:1492 Métrica:1 
RX packets:8891 errors:0 dropped:0 overruns:0 frame:0 
TX packets:4618 errors:0 dropped:0 overruns:0 carrier:3 
colisiones:0 txqueuelen:1000 
RX bytes:12216122 (12.2 MB) TX bytes:326956 (326.9 KB) 
Interrupción:252 

lo Link encap:Bucle local 
inet dirección:XXX.X.X.X Máscara:255.0.0.0 
dirección inet6: ::1/128 Alcance:Anfitrión 
ARRIBA LOOPBACK CORRIENDO MTU:16436 Métrica:1 
RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
colisiones:0 txqueuelen:0 
RX bytes:1436 (1.4 KB) TX bytes:1436 (1.4 KB) 
 
 
 
ahorita estoy conectado via lan, con cable.

---

### Post by clasificado on 2009-06-16
yo tengo una asus aspire one, y tuve problemas con el driver PRIVATIVO.

Me decia que estaba funcionando, pero no encontraba nada.

Desactivé el driver privativo (osea, me quedé con el libre) y anduvo de 10.

clasificado

---

### Post by guillermolisi on 2009-06-16
Una pregunta absurda pero necesaria, la tarjeta de red de la notebook esta encendida (en ON) ?

---

### Post by ducksun43 on 2009-06-16
hello, maybe this [http://sunoano.name/ws/public_xhtml/ggm.html#wifi_and_debian](http://sunoano.name/ws/public_xhtml/ggm.html#wifi_and_debian) might help you

---

### Post by luks911 on 2009-06-17
Como decía clasificado más arriba, es un tema de drivers. El Madwifi que tenés habilitado, que instala por defecto Ubuntu, no sirve para esa placa. En Controladores de Hardware deberías tener la opción de habilitar uno cuyo módulo se llama ath5k. 
De hecho a mí me funcionó directamente desde el LiveCD.

---

