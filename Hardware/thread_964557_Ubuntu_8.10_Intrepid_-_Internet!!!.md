---
title: "Ubuntu 8.10 Intrepid - Internet!!!"
date: 2008-10-31
forum: Hardware
---

### Post by erdosain9 on 2008-10-31
Hola a todos.  Les comento que he hecho la actualizacion de hardy al intrepid y resulta que la maquina se ha quedado sin conexion........... mmmm... lo raro es que figura en el icono de red como @conectado@ e incluso una ip, mascara, etc... pero lo cierto es que no tengo conexion... por que???????????
pueden ayudarme!!!
Saludos y gracias

Por cierto, estoy conectado por Fibertel, modem webstar 2100

---

### Post by hictio on 2008-10-31
- El IP que decis que tenes, de que tipo es? Es publico o de rango privado, o es del rango de [APIPA](http://en.wikipedia.org/wiki/APIPA#Choosing_addresses)
- Probaste de hacer ping a algun sitio?
- Proba tanto con hostname, como con direccion IP.

Estas usando Gnome? Entonces, abri un Terminal, para eso, tipea Alt + F2, escribi:
```

gnome-terminal

```

Dale ENTER y dentro del Terminal, tipea:  ping 64.233.161.83 (ENTER)

Esto es el output de un ping al IP de gmail.com, lo matas con Ctrl + C
```

esteban@tango:~$ ping 64.233.161.83
PING 64.233.161.83 (64.233.161.83) 56(84) bytes of data.
64 bytes from 64.233.161.83: icmp_seq=1 ttl=239 time=154 ms
64 bytes from 64.233.161.83: icmp_seq=2 ttl=239 time=155 ms
64 bytes from 64.233.161.83: icmp_seq=3 ttl=239 time=155 ms
64 bytes from 64.233.161.83: icmp_seq=4 ttl=239 time=156 ms
64 bytes from 64.233.161.83: icmp_seq=5 ttl=239 time=155 ms
64 bytes from 64.233.161.83: icmp_seq=6 ttl=239 time=156 ms

```

Si eso camina, proba re-emplazando la direccion IP, por 'gmail.com', si no camina, puede ser que tengas un problema con el DNS.

---

### Post by sam_award on 2008-10-31
esa es buena pero tambien hay q saber si estabas usando ip estatica y si es eso prueba usando los datos q ya tenias anteas de perder la coneccion , o checate bien las DNS y el rango de busqueda

---

### Post by BlackHero on 2008-10-31
abri una terminal 


sudo ifconfig


y si tenes wireless 

sudo iwconfig


y dame los resultados

---

### Post by erdosain9 on 2008-11-02
Hola, disculpen la tardanza.  Bueno, les comento que lo "solucioné" (odio tener que poner esas comillas).  Bueno, la cosa es que me di cuenta de esto:
si hago click con el botón izquierdo del mouse me saltan las dos placas de red que tengo (grisadas, o sea no las puedo seleccionar (y algo más)):

- Redes cableadas (Asustek computer mcp61 ethernet)
- ifupdown (eth1)
- Red cableada (Realtek RTL-8139/8139C/8139C+)
  el dispositivo no está gestionado

Bueno, así estaban las cosas.  Y la opción seleccionada era "ifupdown (eth1)".  Así no había internet.  Entonces toqué con el botón derecho y cree una nueva conexión a la que le copié la mac del eth0 que es la Asustek... y así está funcionando internet.  

Lo que sucede es que sé que esta no es la manera correcta pues siguen grisadas las opciones de las placas de red... Además cada vez que inicio la máquina se pone en ifupdown... y supongo que tendré problemas con la conexión en red a otra máquina cliente que aún ni siquiera revisé.

Un saludo.  pego la salida a sudo ifconfig

```

eth0      Link encap:Ethernet  direcciónHW 00:22:15:c8:d2:e2  
          inet dirección:190.19.64.91  Difusión:190.19.64.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:576  Métrica:1
          RX packets:262317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18963 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:30123828 (30.1 MB)  TX bytes:1840769 (1.8 MB)
          Interrupción:220 Dirección base: 0x8000 

eth1      Link encap:Ethernet  direcciónHW 00:e0:7d:a8:bf:78  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:11 Dirección base: 0xe800 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:424 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:29216 (29.2 KB)  TX bytes:29216 (29.2 KB)

```

---

### Post by erdosain9 on 2008-11-03
ejm!!! alguna ayuda?

---

### Post by mhoyos on 2008-11-04
> **erdosain9 said:**
> ejm!!! alguna ayuda?


por lo visto, hay 2 configuraciones.. eth0 con IP publica y eth1 con IP interna..

podes probar lo siguiente:

- conecta UNICAMENTE con el cable de red, con la conexion a inet.
- reinicia la red: /etc/init.d/networking restart
- ejecuta este comando: route -n y copialo.
- hace un cat a /etc/resolv.conf y copialo.
- hace un traceroute a google.com y copialo.

en base a esto, veremos que info tenes.

salu2

---

