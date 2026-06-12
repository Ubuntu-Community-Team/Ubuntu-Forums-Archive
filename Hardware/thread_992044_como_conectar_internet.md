---
title: "como conectar internet"
date: 2008-11-24
forum: Hardware
---

### Post by brianmel on 2008-11-24
jajaja una pregunta muy simple no ?

lo que pasa es que instale ubuntu por primera ves y estoy pensando en primero configurar el ubuntu y luego desinstalar el XP.
pero... no puedo conectarme a internet 

ISP: fibertel

modem: scientific atlanta 
     
la conexion es a traves de ethernet osea LAN 
pero no me conecta y no se como se configura el modem o tal vez tenga que poner las ips y el MAC :confused:

por favor  ayudaaaa

---

### Post by aljama on 2008-11-24
perdon pero no especificas que vesion de ubuntu usas,
para la version 8.04 
abres una terminal (Aplicacciones->Accesorios->terminal) y escribes

$ sudo pppoeconf y presiones ENTER

te va a pedir un password, es el usas para loguearte en el sistema

Despues de password va aparecer una pantalla azul de texto preguntandote el usuario y password de tu conexion a internet, donde no te pregunta el usuario o password conteste que SI/YES

---

### Post by sajnox on 2008-11-24
Bueno, bienvenido!!

Que raro que con una conexion ethernet no funcione, generalmente andan de una.

La placa de red es onboard o la agregaste al mother??

Hace lo siguiente

Con ubuntu andando

1) Por las dudas desenchufa (no apagar, *desenchufa*) el modem de fibertel, esperas unos segundos y le volves a dar corriente

Paso algo?

2) Fijate si donde tenes enchufada la placa de red los leds de la placa indican que hay trafico (titilan)

3) Abri una terminal (alt + f2) y escribis lo siguiente

```
gnome-terminal
```

Se abre una ventana como el viejo DOS y escribis

```
lspci
```

El resultado, lo pegas en la respuesta que nos das aca

---

### Post by brianmel on 2008-11-24
la placa de red es on-board y es buena 
es un mother asus m2npv-vm 
y tambien (creo que por no tener internet no se actualizo el driver)no puedo subir la resolucion a mas de 800x600 ¿?

---

### Post by brianmel on 2008-11-24
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by guillermolisi on 2008-11-24
> **brianmel said:**
> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

Esa motherboard tiene chipset nForce 430 (de nVidia).

La placa de red tiene las siguientes caracteristicas generales:

 Gigbit LAN
NVIDIA Gb LAN controller delivers transfer speeds up to ten times faster than conventional 10/100 Ethernet connections. Gigabit LAN is the networking standard for the early future and is ideal for handling large amounts of data such as video, audio, and voice.

Si es asi, bajate el paquete que esta en 
[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2NPV-VM](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2NPV-VM)

La puesta en marcha de una conexion a Fibertel es de lo mas sencilla. Plug and Play, sin necesidad de nada adicional porque el cablemodem te configura todo lo necesario en la placa (siempre que esta este operativa).

Tambien posiblemente tengas que bajar drivers para video. Es lo haces desde
[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2NPV-VM](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2NPV-VM)

Logicamente vas a tener que usar o una placa discreta agregada a esa PC u otra PC y pasas los archivos por pendrive o algo similar.

Conta como te fue.

---

### Post by brianmel on 2008-11-24
tengo malas noticias, hoy a la tarde se quebro el ISP fibertel y no sabia que era un problema de la cuadra y por miedo (pense que toque algo raro) desinstale el ubuntu :( pero cuando tenga un ratito la instalo de nuevo!!!

---

### Post by guillermolisi on 2008-11-24
> **brianmel said:**
> tengo malas noticias, hoy a la tarde se quebro el ISP fibertel y no sabia que era un problema de la cuadra y por miedo (pense que toque algo raro) desinstale el ubuntu :( pero cuando tenga un ratito la instalo de nuevo!!!
En realidad fuiste vos el que dejo sin servicio a todo el vecindario :)

---

### Post by vagoybostero on 2009-01-04
> **guillermolisi said:**
> Esa motherboard tiene chipset nForce 430 (de nVidia).

Si es asi, bajate el paquete que esta en 
[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2NPV-VM](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2NPV-VM)

La puesta en marcha de una conexion a Fibertel es de lo mas sencilla. Plug and Play, sin necesidad de nada adicional porque el cablemodem te configura todo lo necesario en la placa (siempre que esta este operativa).

Tambien posiblemente tengas que bajar drivers para video. Es lo haces desde
[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2NPV-VM](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2NPV-VM)


Amigo yo tengo esa misma placa y todavia no le pude hacer correr los drivers (como es todo on board, no tengo internet, placa de video, etc).

Ya me habia bajado los drivers de esa pagina q vos pusiste, q son los oficiales de asus, pero no los puedo instalar.

Para instalarlo segui los siguientes pasos:
Abro la consola, me autentico como root, y arrastro el Driver.run y lo instalo.
Luego de pedirme que acepte los terminos y condiciones (y los acepto), me salta el siguiente error:

[B]No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface.

ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package.[/B]

Posteando en el foro, uno me dijo que haga lo siguiente:

```
sudo apt-get install build-essential
```

Lo puse pero me tira el siguiente error:

[B]administrador@pcpatricio:~$ sudo apt-get install build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete build-essential[/B]

Y sigo usando Windows para entrar al foro y ver como hacerlo.. jeje

Si alguien sabe que me falta, q hice mal y/o q debo hacer, le agradeceria que me responda!! :D

---

### Post by guillermolisi on 2009-01-05
> **vagoybostero said:**
> Amigo yo tengo esa misma placa y todavia no le pude hacer correr los drivers (como es todo on board, no tengo internet, placa de video, etc).

Ya me habia bajado los drivers de esa pagina q vos pusiste, q son los oficiales de asus, pero no los puedo instalar.

Para instalarlo segui los siguientes pasos:
Abro la consola, me autentico como root, y arrastro el Driver.run y lo instalo.
Luego de pedirme que acepte los terminos y condiciones (y los acepto), me salta el siguiente error:

[B]No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface.

ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package.[/B]

Posteando en el foro, uno me dijo que haga lo siguiente:

```
sudo apt-get install build-essential
```

Lo puse pero me tira el siguiente error:

[B]administrador@pcpatricio:~$ sudo apt-get install build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete build-essential[/B]

Y sigo usando Windows para entrar al foro y ver como hacerlo.. jeje

Si alguien sabe que me falta, q hice mal y/o q debo hacer, le agradeceria que me responda!! :D

Estas corriendo Ubuntu 8.10 64 bits ?

Podrias pegar en un nuevo mensaje el contenido de tu archivo /etc/apt/sources.list ? Es que algo no me cierra con ese mensaje de que no encuentra el build_essential package.

El primer driver que tenes que actualizar es el de la imagen que adjunto.

---

### Post by luks911 on 2009-01-05
> **guillermolisi said:**
> Estas corriendo Ubuntu 8.10 64 bits ?

Podrias pegar en un nuevo mensaje el contenido de tu archivo /etc/apt/sources.list ? Es que algo no me cierra con ese mensaje de que no encuentra el build_essential package.

El primer driver que tenes que actualizar es el de la imagen que adjunto.

Eso, o querés instalar el paquete y no tenés internet ;) por eso el error. Si este es el caso, bajate los paquetes (en formato .deb) de Ubuntu Packages con wino desde otra máquina, los copias a tu home y los instalás con un doble click. Que alguien me corrija si me equivoco, pero los paquetes que necesitás son estos:

64bits: [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-9.19_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-9.19_amd64.deb)
32bits: [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-9.19_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-9.19_i386.deb)

y 

64bits: [http://mirrors.kernel.org/ubuntu/pool/main/m/make-dfsg/make_3.81-5_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/m/make-dfsg/make_3.81-5_amd64.deb)
32bits: [http://mirrors.kernel.org/ubuntu/pool/main/m/make-dfsg/make_3.81-5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/m/make-dfsg/make_3.81-5_i386.deb)

Lo que sucede es que el build-essential lo que hace al instalarse es llamar a otros paquetes para que se instalen. Los dos que te pasé son algunos de ellos. Es posible que urante la instalación de los drivers te falte algún otro. En ese caso, se busca y se repite el procedimiento.

---

