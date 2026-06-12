---
title: "Problemas con Configuración de Red"
date: 2009-01-29
forum: Hardware
---

### Post by Vero1 on 2009-01-29
Hola,
Tengo un problema con mi Red.
Cuando le doy click a los dos monitorcitos me indica que no hay ninguna conexión activa válida(estoy conectada a Internet por DSL y puedo navegar y usar Evolution tambien), así que no lo entiendo.
Corrí pppoeconf y aparece una conexión, aparte de eth0 que es pan0 que no sé cómo apareció y tampoco sé como eliminarlo.
Aparte, me aparece conexión cableada y yo tengo DSL. No dá posibilidad de que en conexiones figure DSL, si bien lo agregué en ese item.
Todo surgió porque instalé Firestarter pero me dice que No se pudo arrancar pòrque el dispositivo eth0 no está preparado. Sin embargo en pppoeconf aparece y repito que navego por Internet y envío y recibo correo sin problemas.

Alguien puede darme una ayuda?

Gracias.

---

### Post by jkid on 2009-01-29
trata d escribir mas claro o diferent no te entiendo....

---

### Post by sergiom99 on 2009-01-29
postea el resultado del comando ifconfig asi vemos como tenes configuradas las placas y red.
Sergio

---

### Post by guillermolisi on 2009-01-29
> **Vero1 said:**
> Hola,
Tengo un problema con mi Red.
Cuando le doy click a los dos monitorcitos me indica que no hay ninguna conexión activa válida(estoy conectada a Internet por DSL y puedo navegar y usar Evolution tambien), así que no lo entiendo.
Corrí pppoeconf y aparece una conexión, aparte de eth0 que es pan0 que no sé cómo apareció y tampoco sé como eliminarlo.
Aparte, me aparece conexión cableada y yo tengo DSL. No dá posibilidad de que en conexiones figure DSL, si bien lo agregué en ese item.
Todo surgió porque instalé Firestarter pero me dice que No se pudo arrancar pòrque el dispositivo eth0 no está preparado. Sin embargo en pppoeconf aparece y repito que navego por Internet y envío y recibo correo sin problemas.

Alguien puede darme una ayuda?

Gracias.
Si estas usando un modem ADSL, este como se conecta a la PC, via USB o via cable de red (el que tiene unas fichitas parecidas a las de los telefonos, pero algo mas grandes) ?

ADSL *es* conexion cableada. Lo que puede ser inalambrico es la conexion entre tu PC y el modem/router si este posee tal funcionalidad o que tengas conectado al modem ADSL un router inalambrico.

Por que instalaste Firestarter ?

---

### Post by Vero1 on 2009-01-31
Hola,
contesto ahora porque no me llegó el aviso por e-mail.

Gracias por las respuestas, pero ya está solucionado.
Desinstalé el NM e instalé wicd. Con eso funciona todo ok.

Instalé Firestarter para tener cierto control sobre entradas y salidas, pero tambien lo desinstalé porque no me dejaba conectarme a Internet ni al correo.

Posiblemente por una mala configuración por mi parte...

saludos

---

### Post by Vero1 on 2009-02-06
Hola,
Si bien el thread anterior se ha solucionado, ahora tengo otro problema y parece ser que tiene algo que ver con el último kernel instalado.

Mi kernel actual es: 2.6.27-11-generic

De pronto me había quedado sin conexión a Internet.
Corrí el pppoeconf y me detecta dos conexiones.
uno es eth0 y el otro Pan0 que no sé de dónde ha salido porque tengo entendido que es para inalámbrico y yo no lo tengo para nada.

El problema es que cuando quiero utilizar pppoeconf me contesta que no encuentra el concentrador raíz( creo que así se llama) del Pan0. Por supuesto porque no lo tengo. La cosa es que no sé cómo eliminar dicha conexión inexistente.

Agradeceré una orientación.

Saludos

---

### Post by Hei Ku on 2009-02-06
Podes postear tu archivo /etc/network/interfaces?

---

### Post by Vero1 on 2009-02-06
Hola HeiKu

Aquí está:

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0

auto eth0


Gracias

---

### Post by Vero1 on 2009-02-06
HeiKu

Creo de interés esta info de ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:17:31:a8:53:8a  
          inet dirección:192.168.1.3  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::217:31ff:fea8:538a/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:1723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1731 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:624944 (624.9 KB)  TX bytes:245660 (245.6 KB)
          Interrupción:23 Dirección base: 0xc800 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:894 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:44700 (44.7 KB)  TX bytes:44700 (44.7 KB)

pan0      Link encap:Ethernet  direcciónHW e2:36:b3:63:e2:b1  
          dirección inet6: fe80::e036:b3ff:fe63:e2b1/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:190.48.249.43  P-t-P:200.51.241.227  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1492  Métrica:1
          RX packets:1635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1615 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:583634 (583.6 KB)  TX bytes:203522 (203.5 KB)

Gracias

---

### Post by Hei Ku on 2009-02-06
Por lo que leí, la interfaz pan0 es de bluetooth. Lo raro es que la quiera tomar para la conexion ppp.

---

### Post by Vero1 on 2009-02-07
Ésto antes del nuevo kernel no pasaba.
He leído que varias personas tienen problemas con este kernel, sobre todo en relación al driver de nvidia.
Yo no tuve ese problema pero tengo este otro que no sé cómo eliminar el Pan0 de Ethernet.
No puedo usar tampoco pppeconf

Hoy, por ejemplo, al encender el equipo, no podía tener conexión porque se borraron las DNS que estaban puestas ayer y se pone sola la puerta de enlace.

Ya no sé qué hacer con este problema.

Otra cosa. Cuando corro pppoeconf me dice que encuentra dos dispositivos. Uno es eth0 que es correcto y otro Pan0. Me pregunta si ésto es correcto y yo le pongo que no, entonces me dirige a modconf para que yo busque los dispositivos. Claro que yo no sé cuales puedan ser. Están en Controladores de Red pero, repito, no sé qué hacer con ésto.

Gracias por tu tiempo.

Qué puedo hacer entonces, tienes idea?

---

### Post by Vero1 on 2009-02-08
Hola,

Se ha solucionado el problema, destildando en Servicios Bluetooth.

Gracias por vuestro tiempo.

saludos

---

