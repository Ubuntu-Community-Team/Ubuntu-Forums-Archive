---
title: "Ubuntu Remix no me reconoce ninguna placa de red"
date: 2009-10-03
forum: Hardware
---

### Post by chompi99 on 2009-10-03
Hola a todos. Soy nuevo con Ubuntu. Decidí cambiarme por que el Windows me tenía cansado. Pero cometí el grave error de borrar windows completamente. 
Ahora, lo que me pasó es lo siguiente: instalé el nuevo ubuntu remix para netbooks. Se instaló sin ningún problema, pero no me permite conectarme a internet. No hay vuelta que darle. Estuve leyendo un poco en la web y me enteré que a los que tenían la acer one les pasaba lo mismo. Mi maquina es una toshiba nb205 y tiene placa wifi Atheros. 
Sepan que no entiendo prácticamente nada de como manejar la consola.
Cualquier ayuda será muy agradecida. 

Saludos

---

### Post by josecuervo86 on 2009-10-03
Hola Chompi, Bienvenido!

Como primer paso para acercarnos a la solución anda **Aplicaciones** > **Accesorios** > **Terminal** y escribi lo siguiente:

```
lspci
```

Y pega el resultado.

---

### Post by chompi99 on 2009-10-03
Muchas gracias por tan pronta respuesta. Tardo un poco en copiar los resultados de la terminal por que tengo que pasar todo de una computadora a la otra. 

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by guillermolisi on 2009-10-03
> **chompi99 said:**
> Muchas gracias por tan pronta respuesta. Tardo un poco en copiar los resultados de la terminal por que tengo que pasar todo de una computadora a la otra. 

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
Encontre esto en el foro de Networking & Wireless, por eso esta en Ingles:
> 
Your problem is that your kernel is not new enough. The ath9k driver which handles the AR9285 chipset is standard in kernel 2.6.29 and greater.

[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k) supported chipsets include AR9285 (>= 2.6.29) 

    
You can upgrade the wireless parts of the kernel only which can be found here: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

although I'd be quite careful as you're playing with the kernel now. The compat-wireless tools seem to be the way to go and the above link contains a method for installing them.

Edit 1: For ubuntu jaunty you can run the following command:
```

     sudo apt-get install linux-backports-modules-jaunty 

```
Si no entendes lo que se dice, avisa e intentamos una traduccion.
Al que hizo la consulta le funciono. [El thread original es este]("http://ubuntuforums.org/showthread.php?t=1179951&highlight=AR9285").

---

### Post by chompi99 on 2009-10-03
Se ve que quien había posteado el mismo problema que yo la tenía más clara que yo. No entiendo a donde tengo que bajar esos archivos, como instalarlos, va, no entendí nada. Perdón por mi tan vergonzosa ignorancia.

---

### Post by guillermolisi on 2009-10-03
> **chompi99 said:**
> Se ve que quien había posteado el mismo problema que yo la tenía más clara que yo. No entiendo a donde tengo que bajar esos archivos, como instalarlos, va, no entendí nada. Perdón por mi tan vergonzosa ignorancia.
Ok. Vamos por partes.

Primero, que version de Ubuntu Remix estas usando ?
La 8.04, la 8.10, la 9.04 o alguna otra version ?

---

### Post by chompi99 on 2009-10-03
9.04

---

### Post by guillermolisi on 2009-10-03
> **chompi99 said:**
> 9.04
Abri una terminal/consola e ingresa
```
sudo apt-get install linux-backports-modules-jaunty
```
La orden sudo hara que se te pida de nuevo tu contraseña y cuando la escribas veras que nada se escribe en pantalla por cuestiones de seguridad.

Ingresada la contraseña, le das enter y se instalara el driver adecuado.
Reinicia y fijate si te reconoce la wifi.

Todo esto es porque el driver viene incluido a partir del kernel 2.6.29, o sea que para la nueva version que esta por salir deberia funcionarte diez puntos.

Proba y comentanos como te fue.

---

### Post by chompi99 on 2009-10-03
Me dice que "No se pudo encontrar el paquete linux-backports-modules-jaunty"

---

### Post by pablo.s on 2009-10-03
Tenés que activar en Synaptic
el repositorio de backports.
Acá muestro cómo activarlos.

[IMG]http://a.imagehost.org/0502/1_74.png[/IMG]

[IMG]http://a.imagehost.org/0461/2_20.png[/IMG]

---

### Post by chompi99 on 2009-10-03
Me siguie tirando el mismo error, "no se pudo encontrar el paquete linux-backports-modules-jaunty"

---

### Post by guillermolisi on 2009-10-03
> **chompi99 said:**
> Me siguie tirando el mismo error, "no se pudo encontrar el paquete linux-backports-modules-jaunty"
Despues de activar el repositorio nuevo tenes que presionar el boton "check" para que baje los encabezados de los paquetes. Luego podes llevar a cabo la instalacion recomendada.

---

### Post by chompi99 on 2009-10-03
Perdoname, pero no encuentro ningún botón que diga check o algo parecido.

---

### Post by guillermolisi on 2009-10-03
> **chompi99 said:**
> Perdoname, pero no encuentro ningún botón que diga check o algo parecido.
El boton "check" (o su equivalente en Español) esta en Software Update (gestor de actualizacion de software).

Para el caso de la solucion via consola/terminal es equivalente a
```
sudo apt-get update
```
y despues la linea de comando que instala el paquete indicado antes.

---

### Post by pablo.s on 2009-10-03
Va por pasos:

Primero lo que puse antes.

Luego esto:
[IMG]http://a.imagehost.org/0116/1_92.png[/IMG]

Y esto:
[IMG]http://a.imagehost.org/0782/2_16.png[/IMG]

Entonces esto más:
[IMG]http://a.imagehost.org/0673/3_16.png[/IMG]

Y por último:
[IMG]http://a.imagehost.org/0529/4_7.png[/IMG]

Peeeeero yo estoy utilizando Karmic,
asi que fijate que lo tuyo tiene que decir
Jaunty, eh!

---

### Post by chompi99 on 2009-10-03
Cuando ejecuto "sudo apt-get update" me devuelve lo siguiente:

juan@juan-laptop:~$ sudo apt-get update 
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg 
  No pude resolver 'security.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty Release.gpg 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/main Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/restricted Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/universe Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-es 
  No pude resolver 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-es 
  No pude resolver 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-es 
  No pude resolver 'security.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-es 
  No pude resolver 'security.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty/multiverse Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates Release.gpg 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/main Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/restricted Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/universe Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-updates/multiverse Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-backports Release.gpg 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-backports/main Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-backports/restricted Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-backports/universe Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) jaunty-backports/multiverse Translation-es 
  No pude resolver 'ar.archive.ubuntu.com' 
Leyendo lista de paquetes... Hecho 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-es.bz2](http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-es.bz2)  No pude resolver 'ar.archive.ubuntu.com' 
 
W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  No pude resolver 'security.ubuntu.com' 
 
W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com' 
 
W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com' 
 
W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com' 
 
W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com' 
 
W: Algunos archivos de índice no se han podido descargar, se han ignorado, 
o se ha utilizado unos antiguos en su lugar. 
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas 

Si estás cansado y querés parar no hay drama. Muchas Gracias por la ayuda!

---

### Post by guillermolisi on 2009-10-03
O tenes la maquina desconectada de Internet o los servidores estan colapsados (cosa que viene pasando desde que salio la beta de KK).

---

### Post by pablo.s on 2009-10-03
> **chompi99 said:**
> Si estás cansado y querés parar no hay drama. Muchas Gracias por la ayuda!

Vos no me conocés a mi...
Fijate en Synaptic, la parte de
"Repositorios", cambiale el
servidor patánico de Argentina
por el servidor Principal.
Asi:
[IMG]http://a.imagehost.org/0815/aa.png[/IMG]

---

### Post by chompi99 on 2009-10-03
Pensé que se había entendido, no tengo forma de conectarme a internet. No es solo wi fi, si la conecto directamente al cable de red tampoco pasa nada.

---

### Post by guillermolisi on 2009-10-03
> **chompi99 said:**
> Pensé que se había entendido, no tengo forma de conectarme a internet. No es solo wi fi, si la conecto directamente al cable de red tampoco pasa nada.
Raro que no conecte con cable porque esa placa de red es super standard y no conozco equipo en la que no funcione con Ubuntu.

---

### Post by pablo.s on 2009-10-03
OK. Con lo que sea que estés
respondiendo en el foro, bajá estos
dos paquetes:

-[Backports Jaunty generic]("http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/linux-backports-modules-2.6.28-15-generic_2.6.28-15.17_i386.deb")
-[URL="http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-jaunty_2.6.28.15.20_i386.deb"]Backports Jaunty modules

[/URL]  y luego lo pasás con un pendrive
a la maquina con Ubuntu, reiniciás
y teoricamente tendria que funcionar.

---

### Post by chompi99 on 2009-10-03
Y donde los cargo en la maquina con ubuntu. Digo, una vez que ya están en el pendrive en dicha máquina, ¿que hago?

---

### Post by pablo.s on 2009-10-03
Primero le das doble click al
paquete que dice modules y
se va a abrir un programa para
instalar paquetes. Te va a pedir
la contraseña y se instala. Luego
hacés lo mismo con el otro.
Reiniciás la maquina y vemos.

---

### Post by chompi99 on 2009-10-03
Se abre el instalador de paquetes, y me dice "Error: La dependencia no se puede satisfacer: linux-image-2.6.28-15-generic"

En la descripción del error me dice:

Ubuntu supplied Linux modules for version 2.6.28 on x86/x86_64

This package contains moudles supplied by Ubuntu for Linux kernel 2.6.28 on x86/x86_64.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed.


Esto me pasa con cualquiera de los dos archivos.

---

### Post by pablo.s on 2009-10-04
Si conectás el cable de red
a la máquina y en una terminal
escribis

```
ifconfig
```

¿que te devuelve?

---

### Post by chompi99 on 2009-10-04
Te lo copio a continuación:

eth0      Link encap:Ethernet  direcciónHW 00:23:5a:f9:12:d6   
          dirección inet6: fe80::223:5aff:fef9:12d6/64 Alcance:Vínculo 
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1 
          RX packets:451 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:1000  
          RX bytes:27354 (27.3 KB)  TX bytes:1494 (1.4 KB) 
          Interrupción:250 Dirección base: 0xc000  
 
lo        Link encap:Bucle local   
          inet dirección:127.0.0.1  Máscara:255.0.0.0 
          dirección inet6: ::1/128 Alcance:Anfitrión 
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1 
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:0  
          RX bytes:2800 (2.8 KB)  TX bytes:2800 (2.8 KB)

---

### Post by guillermolisi on 2009-10-04
> **chompi99 said:**
> Te lo copio a continuación:

eth0      Link encap:Ethernet  direcciónHW 00:23:5a:f9:12:d6   
          dirección inet6: fe80::223:5aff:fef9:12d6/64 Alcance:Vínculo 
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1 
          RX packets:451 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:1000  
          RX bytes:27354 (27.3 KB)  TX bytes:1494 (1.4 KB) 
          Interrupción:250 Dirección base: 0xc000  
 
lo        Link encap:Bucle local   
          inet dirección:127.0.0.1  Máscara:255.0.0.0 
          dirección inet6: ::1/128 Alcance:Anfitrión 
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1 
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:0  
          RX bytes:2800 (2.8 KB)  TX bytes:2800 (2.8 KB)
O el cable esta mal o donde lo estas conectando no hay asignacion de IP, del otro extremo al que va la PC.

La placa esta activa pero sin asignacion de IP (por lo menos para IPv4).

Se podria probar asignandole una IP fija, pero primero seria muy util saber a donde conectas ese cable que conectas a la notebook.

---

### Post by chompi99 on 2009-10-04
El cable está conectado a un modem motorola que me provee fibertel. Por lo general está conectado a un rooter inalambrico, como ahora. Y con mi otra máquina te escribo los mensajes.

---

### Post by guillermolisi on 2009-10-04
> **chompi99 said:**
> El cable está conectado a un modem motorola que me provee fibertel. Por lo general está conectado a un rooter inalambrico, como ahora. Y con mi otra máquina te escribo los mensajes.
Ese router posee luz de actividad de red para cada boca de conexion ?
Si es asi, cuando conectas la maquina con Ubuntu se enciende indicando que hay portadora ?

Que pasa si probas con el cable de la otra PC que sabes funciona bien ?

Cuando tenias Windows en esa maquina la red funcionaba con ese cable conectado al router ?

---

### Post by chompi99 on 2009-10-04
Yo tengo un solo cable de red, que sale del modem motorola de fibertel. Desde ese modem va un cable de red, que se puede conectar a la computadora, al router inalambrico.  Ahora te estoy escribiendo desde otra máquina, que está conectada a la red wifi de mi casa. El cable por lo visto anda bien. Lo que en este momento no puedo saber es si la placa ethernet de mi toshiba está funcionando o no. 
Por lo que estoy leyendo, parece que muchos tuvieron problemas parecidos con la misma máquina. 
Pero lo solucionaron con los pasos que ya probamos ayer.

---

### Post by guillermolisi on 2009-10-04
> **chompi99 said:**
> Yo tengo un solo cable de red, que sale del modem motorola de fibertel. Desde ese modem va un cable de red, que se puede conectar a la computadora, al router inalambrico.  Ahora te estoy escribiendo desde otra máquina, que está conectada a la red wifi de mi casa. El cable por lo visto anda bien. Lo que en este momento no puedo saber es si la placa ethernet de mi toshiba está funcionando o no. 
Por lo que estoy leyendo, parece que muchos tuvieron problemas parecidos con la misma máquina. 
Pero lo solucionaron con los pasos que ya probamos ayer.
Lo cual indica que hay algun otro factor que esta incidiendo.

De hecho vuelvo al principio preguntandote como sabes que tu placa alambrica no funciona ? Por que la conectaste directamente al cablemodem y no anduvo ? 

Si es esto, para hacer correctamente esa prueba tenes que apagar el cablemodem, conectar la notebook, encender el cablemodem y luego la maquina. Asi, al detectar que cambio la identificacion MAC de la placa de red la registran y te asignan una nueva IP.

Si lo haces "en caliente", on the fly, no se va a conectar aunque la placa de red funcione bien.

---

### Post by chompi99 on 2009-10-04
No pasa nada, hice todo lo que me dijiste, pero me sigue diciendo que no hay conexión cableada.

---

### Post by guillermolisi on 2009-10-04
> **chompi99 said:**
> No pasa nada, hice todo lo que me dijiste, pero me sigue diciendo que no hay conexión cableada.
Podrias mostrarnos como es el contenido del archivo /etc/network/interfaces ?

---

### Post by chompi99 on 2009-10-04
todo lo que dice ese archivo es:

auto lo
iface lo inet loopback

---

### Post by chompi99 on 2009-10-04
Mirá, me acabo de dar cuenta de que el sonido tampoco funciona. 
Asi que quedate tranquilo, por que me parece que mañana se la voy a llevar a un técnico para que me vuelva a instalar windows. Espero que se pueda, por que yo lo borré completamente. 

Muchisimas gracias por tu apoyo. Pero el problema no desaparece y necesito trabajar mañana con la compu. 
De nuevo, Muchas Gracias!!!!

---

### Post by guillermolisi on 2009-10-04
> **chompi99 said:**
> todo lo que dice ese archivo es:

auto lo
iface lo inet loopback
Editalo con nano o algunotro editor grafico que tengas a mano y te guste y agregale lo siguiente:
```
sudo nano /etc/network/interfaces
```

Agregale lo que marco con color
```
auto lo
iface lo inet loopback

[COLOR=Blue]auto eth0
iface eth0 inet dhcp[/COLOR]
```
Salva/guarda la edicion, reinicia la maquina y proba si ahora funciona la conexion de red por cable.

Esa configuracion espera que un servidor DHCP, como podria ser el de Fibertel, le asigne una IP y el resto de la informacion necesaria para poder navegar y usar servicios de Internet.

Si esto funciona, pasamos al thread sobre el audio.

---

### Post by chompi99 on 2009-10-04
Nada!

---

### Post by guillermolisi on 2009-10-04
> **chompi99 said:**
> Nada!
Algo me dice que no es hardware.

Podrias probar esa maquina conectada a Internet con un LiveCD y ver si funciona la placa de red cableada ?

---

### Post by donmatas on 2009-10-04
> **guillermolisi said:**
> Abri una terminal/consola e ingresa
```
sudo apt-get install linux-backports-modules-jaunty
```
La orden sudo hara que se te pida de nuevo tu contraseña y cuando la escribas veras que nada se escribe en pantalla por cuestiones de seguridad.

Ingresada la contraseña, le das enter y se instalara el driver adecuado.
Reinicia y fijate si te reconoce la wifi.

Todo esto es porque el driver viene incluido a partir del kernel 2.6.29, o sea que para la nueva version que esta por salir deberia funcionarte diez puntos.

Proba y comentanos como te fue.

Compa:

estoy instalando Ubuntu 9.04 en un Toshiba NB 200 que tiene esta bendita tarjeta wi fi Atheros AR9285. ya hice lo que señalaban de instalar linux-backports-modules-jaunty, reinicié pero no funciona. Si escribo en el terminal echo ath9k / sudo tee -a /etc/modules , me devuelve ath9k. Intenté encender la antena (fn+f8) pero permanece apagada... ¿tienen alguna solución?

---

### Post by pablo.s on 2009-10-04
> **donmatas said:**
> Compa:

estoy instalando Ubuntu 9.04 en un Toshiba NB 200 que tiene esta bendita tarjeta wi fi Atheros AR9285. ya hice lo que señalaban de instalar linux-backports-modules-jaunty, reinicié pero no funciona.

¿A ti te funciona la red cableada?
¿Hiciste alguna modificación?

---

