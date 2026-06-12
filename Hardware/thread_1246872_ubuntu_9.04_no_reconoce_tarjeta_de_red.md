---
title: "ubuntu 9.04 no reconoce tarjeta de red"
date: 2009-08-22
forum: Hardware
---

### Post by descriptivo on 2009-08-22
HOla, soy nuevisimo en linux. Me compre un portatil Packard Bell MH45. Instalé el ubuntu 9.04 y todo bien, pero no me detecta la tarjeta de red. Aparentemente es una realtek 8102. El wifi si lo detecta, pero yo necesito conectar con el cable al router.
Después tampoco me funciona la camara web, pero me han dicho que la solucion esta por ahi.
Lo importante es la tarjeta de red para poder conectar a internet. 
Chas gracias.

---

### Post by guillermolisi on 2009-08-22
> **descriptivo said:**
> HOla, soy nuevisimo en linux. Me compre un portatil Packard Bell MH45. Instalé el ubuntu 9.04 y todo bien, pero no me detecta la tarjeta de red. Aparentemente es una realtek 8102. El wifi si lo detecta, pero yo necesito conectar con el cable al router.
Después tampoco me funciona la camara web, pero me han dicho que la solucion esta por ahi.
Lo importante es la tarjeta de red para poder conectar a internet. 
Chas gracias.
Para confirmar marca y modelo de la placa, en una consola/terminal ingresa "lspci" (sin las comillas) y mostranos la salida que te da ese comando.

---

### Post by descriptivo on 2009-08-22
mira, lo que me pone es
[IMG]file:///E:/Documents%20and%20Settings/bart/Escritorio/lspci.png[/IMG][ATTACH]125860[/ATTACH]

---

### Post by gmunioz on 2009-08-22
Hola des....:

Prueba:

a) Ejecuta en consola, conectado a la red por wifi

sudo apt-get install linux-headers-'uname -r' linux-source-'uname -r' bison flex build-essential


b) Descarga desde:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false)

LINUX driver for kernel 2.6.X and 2.4.X (Support x86 and x64)

c) Remueve el modulo r8169:

sudo rmmod 8169


d) Copia y descomprime el archivo descargado a /usr/src ejecutando:

sudo cp /home/tuusuario/r8101-1.012.00.tar.bz2 /usr/src && cd /usr/src && tar xfj r8101-1.012.00.tar.bz2 && cd r8101-1.012.00

e) Estando en el directorio de los archivos fuente, ejecuta:
    
sudo make

sudo make install

sudo depmod -a

sudo modprobe r8101


f) Renombra en /lib/modules/ r8169.ko a r8169.ko.old:

sudo cd /lib/modules/'uname -r'/kernel/drivers/net && mv r8169.ko r8169.ko.old


g) Verifica que se cargo el módulo adecuado r8101

sudo lsmod

h) Si es así activa la tarjeta de red

sudo ifconfig eth0 (ip-address) up


i) Haz los cambios permanentes

sudo mkinitramfs -o /boot/initrd.img-'uname -r'


j) En los reinicios, tendría que continuar funcionando

---

### Post by descriptivo on 2009-08-23
ok, voy a buscar una plaza o algo con wifi y pruebo
ya te digo algo.
gracias

---

### Post by descriptivo on 2009-08-23
bueno, lo primero:
al ejecutar sudo apt-get install linux-headers-'uname -r' linux-source-'uname -r' bison flex build-essential
me sale lo siguiente:
          

nacho@nacho-laptop:~$ sudo apt-get install linux-headers-'uname -r' linux-source-'uname -r' bison flex build-essential  
 [sudo] password for nacho:  
 Leyendo lista de paquetes... Hecho  
 Creando árbol de dependencias        
 Leyendo la información de estado... Hecho  
 E: No se pudo encontrar el paquete linux-headers-uname -r  
 nacho@nacho-laptop:~$ 



De todas maneras, intente conectarme a internet con el wifi y si conecta pero no puedo acceder a ninguna web. Entonces me descargue el driver for kernel... que me dijiste desde la otra compu. E intente seguir con los pasos que me habias marcado, pero al primero, al intentar remover el modulo r 8169 me puso esto:
           

nacho@nacho-laptop:~$ sudo rmmod 8169  
 [sudo] password for nacho:  
 ERROR: Module 8169 does not exist in /proc/modules  
 nacho@nacho-laptop:~$  
 

No se, ¿el modulo 8169 no deberia existir? Acabo de instalar el linux, imagino que todas estas cosas deberian estar ¿no?. Bueno, espero tu respuesta, chas gracias

---

### Post by Hei Ku on 2009-08-23
> **descriptivo said:**
> bueno, lo primero:
al ejecutar sudo apt-get install linux-headers-'uname -r' linux-source-'uname -r' bison flex build-essential
me sale lo siguiente:
          

nacho@nacho-laptop:~$ sudo apt-get install linux-headers-'uname -r' linux-source-'uname -r' bison flex build-essential  
 [sudo] password for nacho:  
 Leyendo lista de paquetes... Hecho  
 Creando árbol de dependencias        
 Leyendo la información de estado... Hecho  
 E: No se pudo encontrar el paquete linux-headers-uname -r  
 nacho@nacho-laptop:~$ 



El comando correcto es:

```

sudo apt-get install linux-headers-$(uname -r) linux-source-$(uname -r) bison flex build-essential

```

> 


De todas maneras, intente conectarme a internet con el wifi y si conecta pero no puedo acceder a ninguna web. Entonces me descargue el driver for kernel... que me dijiste desde la otra compu. E intente seguir con los pasos que me habias marcado, pero al primero, al intentar remover el modulo r 8169 me puso esto:
           

nacho@nacho-laptop:~$ sudo rmmod 8169  
 [sudo] password for nacho:  
 ERROR: Module 8169 does not exist in /proc/modules  
 nacho@nacho-laptop:~$  
 

No se, ¿el modulo 8169 no deberia existir? Acabo de instalar el linux, imagino que todas estas cosas deberian estar ¿no?. Bueno, espero tu respuesta, chas gracias

Lo unico que te dice es que ese modulo no esta cargado en memoria. Lo que puede querer decir que no reconoció una placa para ese modulo, nada más.

Recomendacion, no saques conclusiones hasta familiarizarte cómo funcionan en linux. No se parece a cómo funcionan en el otro SO.

---

### Post by EnriqueK on 2009-08-23
Estos problemas suelen pasar cuando tenés un equipo muy nuevo, hay varias soluciones, una es compilar el kernel , otra es ver si en el CD de instalación tiene el Driver  Lan para Linux, para mi lo mas simple es instalar un nuevo Kernel  desde [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.5/)
son cuatro paquetes .deb

---

### Post by descriptivo on 2009-08-23
hei ku: no saco conclusiones, solo digo lo que me paso, si lo que quiero es quedarme con el linux, y justamente estoy metido en esto para lograr entender el funcionamiento de linux y poder manjearme solo.
Voy a probar con el comando que me estas diciendo.
Tb voy a probar lo que dice enriquek. El aparato es nuevo (relativamente) asi que puede ser que no haya drivers y eso.

---

### Post by Hei Ku on 2009-08-23
Algo que no vi fue que pusieras el resultado de lspci.

Abrí una terminal, ejecuta lspci y posteá lo que te tira. Eso nos va a dar una idea mas fina de qué hardware tenés. Si realmente es realtek no "deberías" tener problemas.

---

### Post by guillermolisi on 2009-08-23
> **Hei Ku said:**
> Algo que no vi fue que pusieras el resultado de lspci.

Abrí una terminal, ejecuta lspci y posteá lo que te tira. Eso nos va a dar una idea mas fina de qué hardware tenés. Si realmente es realtek no "deberías" tener problemas.
Esta entre los primeros posts del thread, en un archivo con la imagen.

Es una Realtek y yo tambien pienso que deberia salir funcionando "a o toque".

---

### Post by descriptivo on 2009-08-24
lo puse mas arriba en un adjunto, pero de todas formas aca va:
 
[FONT=Times New Roman][SIZE=3]nacho@nacho-laptop:~$ lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)[/SIZE][/FONT]
 
Entiendo que si se trata de una realtek. pero sigue sin reconocerla...

---

### Post by descriptivo on 2009-08-24
[quote=Hei Ku;7833647]El comando correcto es:
 
```

sudo apt-get install linux-headers-$(uname -r) linux-source-$(uname -r) bison flex build-essential

```
 
 
lo que me pone con tu comado es 
[FONT=Times New Roman][SIZE=3]nacho@nacho-laptop:~$ sudo apt-get install linux-headers-$(uname -r) linux-source-$(uname -r) bison flex build-essential [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][sudo] password for nacho: [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Leyendo lista de paquetes... Hecho [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Creando árbol de dependencias [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Leyendo la información de estado... Hecho [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]linux-headers-2.6.28-11-generic ya está en su versión más reciente. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]fijado linux-headers-2.6.28-11-generic como instalado manualmente. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]E: No se pudo encontrar el paquete linux-source-2.6.28-11-generic [/SIZE][/FONT]

---

### Post by gmunioz on 2009-08-25
Hola:

Cambia en la orden:

[HTML]sudo apt-get install linux-source-$(uname -r)[/HTML]

por

[HTML]sudo apt-get install linux-source-2.6.28-15-generic bison flex build-essential  [/HTML]

---

