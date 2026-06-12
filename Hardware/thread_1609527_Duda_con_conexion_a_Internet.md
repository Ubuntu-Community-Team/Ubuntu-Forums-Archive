---
title: "Duda con conexion a Internet"
date: 2010-10-30
forum: Hardware
---

### Post by Maicmoon on 2010-10-30
[B]Hola me llamo Miguel y hace tres meses estoy usando ubuntu 10.04en reemplazo total de windows.Estoy mas que contento con linux y por fin estoy todo legal!!!!!

2) compre un router TP-Limk  wireless N modelo TL-WR941 ND ver. 3.1 y cuando lo conecto al modem de telefonica ( huawei SmartAX MT880) no me conecta directamente con el IP si  conecto directo  la pc con el cable de red se conecta solo a internet.Alguien sabe si tengo que configurar algo o hay que instalar algun driver? algun tutorial
gracias por su ayuda:confused::confused:
[/B]

---

### Post by guillermolisi on 2010-10-30
Como tratamos de que cada post mantenga un hilo tematico, de este que abriste se derivan dos.

Sobre los origenes de software esta [en un nuevo thread]("http://ubuntuforums.org/showthread.php?t=1609831").

El otro tema sigue este hilo pero en la seccion hardware.

---

### Post by gmunioz on 2010-11-01
Conecta el equipo al router mediante un cable de red. 

En el navegador preferido (firefox) y pones: 

[http://192.168.1.1](http://192.168.1.1) 

Ingresaras a la pagina web de configuración te pedirá:

Usuario: admin 
Contraseña: admin 

En esta página debes configurar el router.

Aqui un tutorial y review completo:

[http://www.redeszone.net/routers/tp-link-tl-wr941nd-review-y-manual-de-este-router-neutro-con-wifi-n-a-300mbps/](http://www.redeszone.net/routers/tp-link-tl-wr941nd-review-y-manual-de-este-router-neutro-con-wifi-n-a-300mbps/)

---

### Post by biale on 2010-11-01
Habría dos opciones de vida.

La primera sería enseñarle al modem de Telefónica a enrutar, dhcp, firewall/NAT y en ese caso se conecta al router TP-Link como si fuera una PC mas (un port LAN). El modem queda como def gateway para la LAN. El único detalle sería que las dirs de IP del Huawey y la dir de IP de TP-link no se superpongan entre si.

La segunda opción sería configurar la zona WAN del TP-link para que organice el logín a Telefónica. Y el equipo del ISP solo hace una adaptación mas menos grotesca al par telefónico: el port de conexión será el port WAN. Toda la juguetería de red queda a cargo del TP-Link.

Yo encuentro ventajas con la primera opción, pero a la larga es cuestión de gustos. El tutorial parece muy bueno...

---

### Post by Maicmoon on 2010-11-01
Estimados GMUNIOZ y BIALE garcias por tomarse el trabajo de leer el post y responderlo amablemente voy a leer el tutorial e intentar la coneccion y les cuento GRACIAS

---

