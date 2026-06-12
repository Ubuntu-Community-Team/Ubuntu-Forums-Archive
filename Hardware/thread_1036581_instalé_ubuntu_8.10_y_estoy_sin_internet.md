---
title: "instalé ubuntu 8.10 y estoy sin internet"
date: 2009-01-11
forum: Hardware
---

### Post by pachecojuancarlos on 2009-01-11
Hola comunidad,nuevamente en la arena, les cuento anteriormente tuve problemas con ubuntu 8.4, pero gracias a la ayuda de Uds. sali estuve practicando bastante pero un colapso en la red que me surte internet me obligo a cambiar hasta la ip, en fin que como supuse no seria dificil porque tengo todo escrito lo repeti pero esta vez instale ubuntu 8.10 y no hay caso me dice que la red esta desconectada recien buteo a windows y estoy escribiendo estas lineas con lo que esta claro que el servicio no es, una cosa anedotica, al sistema windows para que no joda mas le puse deep freezer xp, lo hago notar porque es lo unico que difiere del sistema anterior, de ahi en mas ya probe si reconoce la tarjeta si con el  sudo ifconfig escribiendo las direcciones puedo hacer ping y lo hice y los reconoce (solo en la consola no en el navegador)tambien escrbi el /etc/rc.local,en fin espero ayuda porque esta vez no se que mas probar,muchas gracias

---

### Post by Hei Ku on 2009-01-11
Postea el resultado de ifconfig y el contenido de tu archivo /etc/network/interfaces

---

### Post by pachecojuancarlos on 2009-01-20
> **Hei Ku said:**
> Postea el resultado de ifconfig y el contenido de tu archivo /etc/network/interfaces

Hola Hei Ku, lamento la tardanza recien comienzan mis vacaciones y estuve loco bueno te la hago corta,te mando el ifconfig pero el /etc/network/interfaces esta en blanco y no de porque en fin espero ayuda saludos y gracias

carlos@carlos-desktop:~$ ifconfig eth0
          Link encap:Ethernet  direcciónHW 00:22:15:c7:ce:11  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:3 errors:0 dropped:133927394 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0  colisiones:0 txqueuelen:1000 
          RX bytes:180 (180.0 B)  TX bytes:2943 (2.9 KB)      Interrupción:221 lo 
          Link encap:Bucle local   inet dirección:127.0.0.1  Máscara:255.0.0.0
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:368 (368.0 B)  TX bytes:368 (368.0 B) wlan0    
          Link encap:Ethernet  direcciónHW 00:18:e7:48:cb:0e  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  wmaster0 
          Link encap:UNSPEC  direcciónHW 00-18-E7-48-CB-0E-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
carlos@carlos-desktop:~$

---

### Post by guillermolisi on 2009-01-20
> **pachecojuancarlos said:**
> Hola Hei Ku, lamento la tardanza recien comienzan mis vacaciones y estuve loco bueno te la hago corta,te mando el ifconfig pero el /etc/network/interfaces esta en blanco y no de porque en fin espero ayuda saludos y gracias

carlos@carlos-desktop:~$ ifconfig eth0
          Link encap:Ethernet  direcciónHW 00:22:15:c7:ce:11  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:3 errors:0 dropped:133927394 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0  colisiones:0 txqueuelen:1000 
          RX bytes:180 (180.0 B)  TX bytes:2943 (2.9 KB)      Interrupción:221 lo 
          Link encap:Bucle local   inet dirección:127.0.0.1  Máscara:255.0.0.0
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:368 (368.0 B)  TX bytes:368 (368.0 B) wlan0    
          Link encap:Ethernet  direcciónHW 00:18:e7:48:cb:0e  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  wmaster0 
          Link encap:UNSPEC  direcciónHW 00-18-E7-48-CB-0E-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
carlos@carlos-desktop:~$

Si el problema es que no tenes conexion a Internet y efectivamente el archivo /etc/network/interfaces esta vacio, editalo y agregale las siguientes lineas si tu ISP te provee de una IP dinamica (ADSL/cable):
```
iface eth0 inet dhcp
auto eth0
```

La otra forma es configurar la interface alambrica mediante el Networkmanager.

Que clase de conexion tenes contratada para Internet ?

Ahora si el problema es con las interfaces inalambricas, con el Networkmanager no deberias tener mayores problemas bajo 8.10 para configurarlas y hacerlas funcionar (veo que tenes dos inalambricas o una que tambien funciona como access point)

---

### Post by pachecojuancarlos on 2009-01-20
hola guillermo, gracias por el aguante, te cuento ya anduve bien con ubuntu 8.4 pero como buen curioso tenia que migrar a 8.10, bien la cuestion es que tengo dos placa de red una es placa comun y otra es inalambrica, el tema al parecer es que al ser el servicio de internet inhalambrico este se quiere comunicar solo y yo no tengo datos porque como el servicio es de mi vecino este no me vende el servicio de internet pero me puso un cable para evitar comprar la antena, asi que lo que uso es la placa comun con ip estaticas, estas me las cambio hace quince dias por arreglos en la linea yo antes tenia 51 ahora tengo 132, pero esto no me jodio en el otro ubuntu, como sea te cuento las ip quedan 192.168.0.132 la mascara como siempre y gateway 192.168.0.1, espero que te sirva quedo a la espera gracias de nuevo.

---

### Post by pachecojuancarlos on 2009-01-20
Guillermo, me apresuro a aclararte que quise decir no me vendio la antena, pero el servicio lo pago como los demas asociados, pero  no tengo antena, por la cercania tengo un cable que va a la placa comun, bueno ahora si esta mas claro adios.

---

### Post by guillermolisi on 2009-01-21
> **pachecojuancarlos said:**
> hola guillermo, gracias por el aguante, te cuento ya anduve bien con ubuntu 8.4 pero como buen curioso tenia que migrar a 8.10, bien la cuestion es que tengo dos placa de red una es placa comun y otra es inalambrica, el tema al parecer es que al ser el servicio de internet inhalambrico este se quiere comunicar solo y yo no tengo datos porque como el servicio es de mi vecino este no me vende el servicio de internet pero me puso un cable para evitar comprar la antena, asi que lo que uso es la placa comun con ip estaticas, estas me las cambio hace quince dias por arreglos en la linea yo antes tenia 51 ahora tengo 132, pero esto no me jodio en el otro ubuntu, como sea te cuento las ip quedan 192.168.0.132 la mascara como siempre y gateway 192.168.0.1, espero que te sirva quedo a la espera gracias de nuevo.
Todo bien y si pagas o no el servicio es problema tuyo y es totalmente off topic para el caso :).

Si vas por cable, edita el /etc/network/interfaces y configura la eth0 de la siguiente forma con los datos que tenes:
```
iface eth0 inet static
address 192.168.0.132
netmask 255.255.255.0
gateway 192.168.0.1
auto eth1
```

Reinicia los servicios de red
```
sudo /etc/init.d/networking restart
```
y conta como te fue.

---

### Post by pachecojuancarlos on 2009-01-21
Use gksudo para escribir en el archivo interfaces
iface eth0 inet static
adress 192.168.0.132
netmask 255.255.255. 0
gateway 192.168.0.1
auto eth1

luego

carlos@carlos-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... 
  Ignoring unknown interface eth1=eth1.                                                         [ OK ]       
carlos@carlos-desktop:~$

finalmente reseteo el sistema y lo unico que se logro es que desaparazca el icono de red, pero no pude coseguir conectarme con firefox a ninguna pagina , pero si hago ping a algunas ip me responde bien , es como si tuviera nternet pero no puedo ver las paginas , bueno te dejo hasta la proxima

---

### Post by guillermolisi on 2009-01-21
> **pachecojuancarlos said:**
> Use gksudo para escribir en el archivo interfaces
iface eth0 inet static
adress 192.168.0.132
netmask 255.255.255. 0
gateway 192.168.0.1
auto eth1

luego

carlos@carlos-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... 
  Ignoring unknown interface eth1=eth1.                                                         [ OK ]       
carlos@carlos-desktop:~$

finalmente reseteo el sistema y lo unico que se logro es que desaparazca el icono de red, pero no pude coseguir conectarme con firefox a ninguna pagina , pero si hago ping a algunas ip me responde bien , es como si tuviera nternet pero no puedo ver las paginas , bueno te dejo hasta la proxima
Tenes un error al final de lo que pegaste como resultado de la edicion.

Debe decir auto eth0 y dice eth1.
Ademas esa mal la linea donde asignas la IP, dice adress y lo correcto es address.

Luego para que te resuelva los nombres/URLs tenes que agregarle al mismo archivo
```
dns-nameservers 192.168.0.1
```Le puse la misma IP que el gateway pero nada impide que le pongas la que corresponda a los DNS de tu proveedor de Internet.

El archivo en cuestion deberia quedarte asi
```
iface eth0 inet static
address 192.168.0.132
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 <- aqui ponele la IP del DNS de tu ISP o del router que intermedia en la conexion
auto eth0
```Reinicia los servicios de red y proba navegar una pagina web por su nombre y si no funciona proba con su IP.

Para saber la IP de un website tenes que ingresar en una consola
```
nslookup www.clarin.com.ar
```por ejemplo

---

