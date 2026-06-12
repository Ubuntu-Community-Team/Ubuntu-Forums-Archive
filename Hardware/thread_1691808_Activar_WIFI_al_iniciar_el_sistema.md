---
title: "Activar WIFI al iniciar el sistema"
date: 2011-02-20
forum: Hardware
---

### Post by san000 on 2011-02-20
[SIZE=2]Hola,[/SIZE]
 [SIZE=2]¿Hay algún script que haga para activar el wifi del portatil al  inicio de forma automática sin tener que pulsar el botón de activación  en el teclado?[/SIZE]
 [SIZE=2]He intentado utilizar este, [/SIZE][SIZE=2]convirtiéndolo en un archivo de texto .run, y añadiéndolo a aplicaciones al inicio, pero no funciona. 
[/SIZE]
[SIZE=2]
[/SIZE]
 ```
dbus-send --system --type=method_call  --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager  org.freedesktop.DBus.Properties.Set  string:org.freedesktop.NetworkManager string:WirelessEnabled  variant:boolean:true
```
 [SIZE=2]
[/SIZE]
 [SIZE=2]
[/SIZE]
[SIZE=2]gracias[/SIZE]

---

### Post by san000 on 2011-02-21
Up. Necesito ayuda con esto.

---

### Post by alfplayer on 2011-02-21
Podés probar con:

```
sudo ifconfig wlan0 up
```

Aunque no funciona para agregarlo a aplicaciones de inicio porque usa sudo.

---

### Post by guillermolisi on 2011-02-21
No se si lo que se busca lograr es encender la interface o habilitarla logicamente (que seria el ejemplo dado).

---

### Post by san000 on 2011-02-22
Mi intención sería activar la wifi como hardware, no a nivel del sistema operativo. Es decir, un script para evitar la tarea de apretar el botón del teclado que activa la wifi cada vez que reinicio el sistema.

---

### Post by guillermolisi on 2011-02-22
No se de que maquina se trata pero he visto que algunas incluyen en su BIOS una funcion para determinar en que estado, electricamente hablando, se quiere este la interface wifi al encender la notebook.

De hecho uso una Bangho con motherboard Evo y BIOS Phoenix que trae esa funcion (ademas del acceso via teclado).

Si el BIOS permite determinar ese estado en el startup te ahorras el script :)

---

### Post by guillermolisi on 2011-02-23
Buscando las alternativas de iwconfig, encontre esto que podria servir para lo que queres lograr:

Agrega esta linea al archivo /etc/rc.local si la queres apagar (modifica la identificacion de la placa wlan0 por la que corresponda a tu caso) cuando inicias el sistema:
```

/sbin/iwconfig wlan0 txpower off

```
O agrega esta otra si la queres encender al inicio del sistema:
```

/sbin/iwconfig wlan0 txpower on

```
El asunto es que luego tendras que habilitarla logicamente a mano o via script con el siguiente comando, si el adaptador no quedo habilitado (up):
```
sudo /sbin/ifconfig wlan0 up
```

Mas info en [http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm](http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm)
(ver "iwlist power" y "iwlist txpower" para ser mas especifico)

Proba y conta como te fue

---

### Post by san000 on 2011-02-26
Hola, muchas gracias por la respuesta. Comentaros que el laptop estaba recién comprado, y como me estaba ocasionando muchos problemas de compatibilidad con Linux, lo he devuelto y he pedido otro.

Si encuentro el mismo problema para mantener conectada la wireless, aplicaré tu solución. 


un saludo

---

