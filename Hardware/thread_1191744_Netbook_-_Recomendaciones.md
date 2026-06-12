---
title: "Netbook - Recomendaciones"
date: 2009-06-19
forum: Hardware
---

### Post by Eddy_Kine on 2009-06-19
Antes que todo, se que me dirán "Depende de lo que quieras...a tu gusto..etc" o bien "Revisa compatibilidad de hardware..etc.."
Pero lo que busco con este post es que me den su opinion como usuarios, es decir, quienes tienen uno ¿Podrían decirme cual es netbook, sus puntos fuertes y débiles? ¿Cómo es el soporte tecnico, como les ha ido con Ubuntu... etc. ?
Sin perder de vista la compatibilidad y las prestaciones quiero que me orienten para efectuar una buena compra, pues a veces los netbook mas caros no son los mejores.
Desde ya gracias por su ayuda
;)

---

### Post by kamus on 2009-06-19
> **Eddy_Kine said:**
> Antes que todo, se que me dirán "Depende de lo que quieras...a tu gusto..etc" o bien "Revisa compatibilidad de hardware..etc.."
Pero lo que busco con este post es que me den su opinion como usuarios, es decir, quienes tienen uno ¿Podrían decirme cual es netbook, sus puntos fuertes y débiles? ¿Cómo es el soporte tecnico, como les ha ido con Ubuntu... etc. ?
Sin perder de vista la compatibilidad y las prestaciones quiero que me orienten para efectuar una buena compra, pues a veces los netbook mas caros no son los mejores.
Desde ya gracias por su ayuda
;)

Lo mejor es revisar: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

Con respecto al soporte técnico, si tienes contratado con canonical no deberias tener problema ya que tendrás una persona escuchándote en caso que tengas algun problema y también esta la comunidad que te podría ayudar en ciertos casos ;)

Salu2

---

### Post by AlexDDR on 2009-06-19
Despues de leer toda esa lista de fallos el MSI WIND me parece una buena opcion, ademas le encuentro mejor diseño que los otros y el ENTER es grande, habria que ver cuanto tiempo dan de garantia ersus los otros

saludos

---

### Post by vtssrm on 2009-06-19
Yo tengo el HP Mini 1020LA y el HP Mini 1120LA. Los resultados para ambos son:
Ubuntu 8.04: **TODO** bien
Ubuntu 8.10: **TODO** bien
Ubuntu 9.04: **SÓLO** falta el **AUDIO**. Aquí esta la solución: [http://ubuntuforums.org/showthread.php?t=1175223](http://ubuntuforums.org/showthread.php?t=1175223)

Estos modelos tienen en común:
*Bluetooth
*Un teclado GRANDE, este punto es **MUY **interesante
*Una carcasa que tiene estilo y resiste el paso del tiempo
*Usan el procesador ATOM de INTEL
*1GB de RAM, expansible a 2GB
*A la batería le saco 2 horas y media
*La pantalla es de 10,2 pulgadas (1024 x 600)
*WIFI
*Ranura SD
*RJ-45
*La cámara WEB funciona bien, sólo hay que instalar el programa Cheese
*La garantía es de 1 año
*Compiz Fusion funciona a la primera

Puntos en contra:
*Sólo dos USB
*Si no cubres el teclado y el touchpad con un paño es muy posible que estos te rayen la pantalla al momento de cerrar el netbook, me paso sólo con uno y me costo 2 meses de insistencia en Paris para que me cambiaran el producto
*Tiene una salida VGA para conectar un proyector o monitor externo. Pero para esto hay que comprar una adaptador que cuesta 20 dolares en EE.UU., desconozco cuanto saldría la importación, la pagina del cable es esta: [http://www.hp.com/united-states/campaigns/mini1000/accessories6.html](http://www.hp.com/united-states/campaigns/mini1000/accessories6.html)
*Las actualizaciones de la BIOS vienen en .exe (no me atrevo a instalarlas con WINE)

Nota: Si tuviese que elegir uno de los dos, me quedo con el 1120LA porque tiene un disco duro TOSHIBA de 80GB versus un SAMSUNG de 60GB que tiene el 1020LA.

---

### Post by Eddy_Kine on 2009-06-20
Estoy triste. Por cuestiones de dinero y por una promoción elegí un Acer One, muy compatible, según el listado de netbooks, pero el RJ45 no sirve.
Esta muerto, no enciende las luces de conectividad cuando lo conecto, instale Ubuntu 9.04 y corre excelente. Lamentablemente cometi un error al no probar el RJ45 con XP como venia por defecto. 
Lo compre en Ripley, solo ayer, asi es que puedo devolverlo, pero ¿como le hago si ya le instale Ubuntu?
Help

---

### Post by moFeta on 2009-06-21
Yo tambien tengo un Aspire One, el nuevo de 10" y el problema con el RJ45 es conocido, no es problema del hardware, sino de como ubuntu reconoce el hardware. La solucion está en este post: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1141529](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1141529)
Lo probé (leelo completo antes) y funciona bien
Lo medular está en esta parte:
> sso@aspirenova:~/Downloads/linux-files/test$ ls
AR813X-linux-v1.0.0.8.tar.gz
sso@aspirenova:~/Downloads/linux-files/test$ gunzip AR813X-linux-v1.0.0.8.tar.gz 
sso@aspirenova:~/Downloads/linux-files/test$ tar xvf AR813X-linux-v1.0.0.8.tar 
sso@aspirenova:~/Downloads/linux-files/test$ cd src
sso@aspirenova:~/Downloads/linux-files/test/src$ make
sso@aspirenova:~/Downloads/linux-files/test/src$ sudo su
[sudo] password for sso: 
root@aspirenova:/home/sso/Documents/Downloads/linux-files/test/src# make install
root@aspirenova:/home/sso/Documents/Downloads/linux-files/test/src# cd /lib/modules/2.6.28-12-generic/kernel/drivers/net/atl1e/
root@aspirenova:/lib/modules/2.6.28-12-generic/kernel/drivers/net/atl1e# insmod ./arl1e.ko

and thats it it should make the network manager see the network card. I believe that you have to do this each time your kernel updates.. i am guessing until 2.6.30 where i believe this driver will then be supported.

Suerte

---

### Post by Eddy_Kine on 2009-06-21
Pero a ti te paso que ni siquiera los led del RJ45 funcionaban?...:(
 
Otro error mas.... borre la partición Recovery de XP............casi me di de cabezaos
 
Uf... ke mas malo me puede pasar?
 
Amigo moFeta segui el tread del link y la verdad es que llegue ahasta aqui y paff error
 
```
root@aspirenova:/home/sso/Documents/Downloads/linux-files/test/src# cd /lib/modules/2.6.28-12-generic/kernel/drivers/net/atl1e/
```

---

### Post by moFeta on 2009-06-21
Tiene un led?
:)
El led del inalámbrico no funciona. Segun ese foro, se solucionaria instalado los backport-modules, pero realmente no me interesa si enciende o no ese led. ya que es un cambio desde mi anterior Asus EeePC 701, en que estaba permanentemente encendido, ya sea que estuviese activodo o no el wifi.
Acabo de probarlo, y no me funcinó, es más, activar los drivers madwifi, simplemente me dejaron sin wifi.

---

### Post by Eddy_Kine on 2009-06-21
> **moFeta said:**
> Tiene un led?
:)
El led del inalámbrico no funciona. Segun ese foro, se solucionaria instalado los backport-modules, pero realmente no me interesa si enciende o no ese led. ya que es un cambio desde mi anterior Asus EeePC 701, en que estaba permanentemente encendido, ya sea que estuviese activodo o no el wifi.
Acabo de probarlo, y no me funcinó, es más, activar los drivers madwifi, simplemente me dejaron sin wifi.
 
 
Me explico, cuando conecto el RJ45 a mi Netbook Acer One 250, en el modem no papadea la luz de conección del modem, es decir cuando el modem detecta conección con un pc parapdea la luz aunque este apagado. Eso no me pasa con mi RJ45, no funciona el Led del Modem indicando "Hey hay un pc conectado"....por decirlo asi. Eso me lleva a pensar que la conección RJ45 de mi netbook esta muerta, más alla de que ubuntu no la reconozca.
 
Mi WiFi funciona excelente, mi lio es con la internet "alambrica" (si asi se puede llamar), por eso te preguntaba si tu netbook cuando lo conectabas (antes de solucionar el problema) mostraba los led de la RJ45 corriendo o bien si tu modem reconocía que estaba conectado a un pc.
 
Pa rematarla solo me quedan 6 dias para devolver el netbook si es problema de hardware y elimine sin querer el recvovery.
 
SOLUCIONES QUE VEO PARA ELLO (DEVOLUCION)
1.- Conseguir restaurar el sistema , es dificil ya que el recovery lo borré ¿Consulta, puedes hacer un backup de él?.. y obviamente enviarmelo (por pagar y cualquier gasto lo pago yo)
2.- Instalarle vista para ver si reconoce la HD Flash que trae y asi ver tambien si reconoce el RJ45
3.- Ir de frenton y pedir cambio (me van a mandar a volar...por decirlo asi)
4.- Seguir sin conección alambrica... :(
Desde ya, muchisimas gracias, la verdad es que estoy bastante preocupado, sé que no es bueno postear asi pero, ya me he quebrado la cabeza muchas horas tratando de arreglar MI grave error. Saludos :D

---

### Post by moFeta on 2009-06-21
Ok, vamos por partes.
Yo no borré la particion para restablecer el sistema, así que podría hacer un 'respaldo' y enviartela :), es más, solo achiqué la partición XP y lo dejé para usarlo desde una máquina virtual desde ubuntu, pero eso es otro cuento.
No, a mi tampoco me detectaba en el router que el AA1 estuviese conectado a través del cable, en applet del network-manager no me daba la opcion de 'Red Cableada' tampoco.
Voy a ir paso por paso lo que acabo de hacer, hace algunos minutos para hechar a andar la red cableada (antes lo había hecho en el LiveUSB desde donde instalé Ubuntu).
La dirección correcta para descargar el driver es: [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) allí descarga el archivo [459]AR813X-linux-v1.0.0.9.tar.gz.
En una ventana de terminal instala lo siguiente:
sudo apt-get install build-essential linux-headers-$(uname -r)
te cambias al directorio donde descargaste el driver y lo descomprimes
tar -xzvf \[459\]AR813X-linux-v1.0.0.9.tar.gz /* no hagas caso de los errores al descomprimir */
cd src
make /* y lo dejar trabajar, debería terminar sin errores */
sudo su /* porque necesitas ejecutar un par de cosas como root y así es más fácil que estar poniendo sudo a cada rato */
make install /* te va a dar un error al final pero es por el archivo man que parece que no está. No importa */
cd /lib/modules/[tab][tab] y elige el ultimo kernel que tengas, ya que es posible que hayas instalado la reciente actualización. Agregas despues el resto de la ruta: kernel/drivers/net/atl1e/
insmod ./[tab][tab] y te va a seleccionar el archivo correcto, ya que el nombre difiere del que se menciona.

Listo, ya deberías tener tu red funcionando.

Suerte.

---

### Post by Eddy_Kine on 2009-06-21
1.- Gracias por entender mi predicamento, por lo que me señalas, no te detecto nada como a mi... uff un alivio.-
2.- Lo de la partición recovery, te agracedería muchisimo si me dieras una mano con ella. Por lo que lei no es tan facil hacerla ojalá y no te complique y puedas enviarmela cuando tengas tiempo (el de todos es muy valioso y eso lo se)
3.- Seguiré las instrucciones al pie de la letra y cuando termine (ahora estoy en el trabajo) posteare la respuesta (ojalá y sea favorable)
4.- Nuevamente gracias por tu tiempo y disposición :D

---

### Post by Eddy_Kine on 2009-06-21
Legué hasta aquí ¿Qué hice mal?

```
luis@luis-laptop:~$ tar -xzvf \[459\]AR813X-linux-v1.0.0.9.tar.gz
atl1e.7
at_osdep.h
copying
ldistrib.txt
readme
release_note.txt
src/
src/atl1c.h
src/atl1c_ethtool.c
src/atl1c_hw.c
src/atl1c_hw.h
src/atl1c_main.c
src/atl1c_param.c
src/atl1e.h
src/atl1e_ethtool.c
src/atl1e_hw.c
src/atl1e_hw.h
src/atl1e_main.c
src/atl1e_param.c
src/at_common.h
src/at_common_main.c
src/at_osdep.h
src/kcompat.c
src/kcompat.h
src/kcompat_ethtool.c

gzip: stdin: decompression OK, trailing garbage ignored
src/Makefile
src/Module.symvers
src/modules.order
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores
luis@luis-laptop:~$ cd src
luis@luis-laptop:~/src$ make
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/luis/src modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/luis/src/at_common_main.o
  CC [M]  /home/luis/src/atl1e_main.o
  CC [M]  /home/luis/src/atl1c_main.o
  CC [M]  /home/luis/src/atl1c_hw.o
  CC [M]  /home/luis/src/atl1e_hw.o
  CC [M]  /home/luis/src/atl1e_param.o
  CC [M]  /home/luis/src/atl1c_param.o
  CC [M]  /home/luis/src/atl1e_ethtool.o
  CC [M]  /home/luis/src/atl1c_ethtool.o
  CC [M]  /home/luis/src/kcompat.o
  LD [M]  /home/luis/src/atl1e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/luis/src/atl1e.mod.o
  LD [M]  /home/luis/src/atl1e.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-13-generic'
luis@luis-laptop:~/src$ sudo su
root@luis-laptop:/home/luis/src# make install
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/luis/src modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.28-13-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-13-generic'
gzip -c ../atl1e.7 > atl1e.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.28-13-generic -name atl1e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.28-13-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.28-13-generic/kernel/drivers/net/atl1e/atl1e.ko
/sbin/depmod -a || true
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz
man -c -P'cat > /dev/null' atl1e || true
man: 
no se puede escribir en /var/cache/man/cat7/atl1e.7.gz en modo catman.
atl1e.
root@luis-laptop:/home/luis/src# cd /lib/modules
root@luis-laptop:/lib/modules# 
Display all 2017 possibilities? (y or n)


```

---

### Post by moFeta on 2009-06-21
Hola.

Jejejeje... te faltó el "/" al final de la línea:
cd /lib/modules/ <-- ahí presionas [tab] y te va a poner:
cd /lib/modules/2.6.28-1   <-- presionas [tab] una o dos veces más y te va a mostrar las opciones de kernels. le agregas el '3' solamente al final de esa línea ya que vi que tienes esa version del kernel, y prfesonas [tab] una vez más y la va a autocompletar.
cd /lib/modules/2.6.28-13-generic/   <-- aquí sigues con el resto de la ruta
cd /lib/modules/2.6.28-13-generic/kernel/drivers/net/atl1e/   <-- [enter]

Es que yo uso mucho la tecla [tab] para autocompletar tanto la ruta como el nombre de los archivos, le pongo las dos primeras letras, le doy al [tab] y listo, me ahorro tipeo y evito errores.

Vas bien. Animo
Con respecto al disco de restauración... voy a necesitar un grabador de dvd externo, pero de ahí veo como me la arreglo.

---

