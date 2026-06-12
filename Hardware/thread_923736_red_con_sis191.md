---
title: "red con sis191"
date: 2008-09-18
forum: Hardware
---

### Post by kechonius on 2008-09-18
Alguien ha podido hacer funcionar placas basadas en el sis191 bajo Hardy??
:confused:

---

### Post by faktorqm on 2008-09-19
postea la salida de lspci e ifconfig. salu2!

---

### Post by leo_liet on 2008-09-20
Hola, yo tengo el adaptador de red  SiS191 Ethernet Controller
y no puedo conectarme ni siquiera al router :(, no puede hacerle ni un ping.

---

### Post by gmunioz on 2008-09-20
Hola:
Para resolver el problema es necesario:
Ejecutar en consola para instalar las fuentes del kernel:
sudo apt-get install linux-source-`uname -r`
tar jxvf /usr/src/linux-source-`uname -r`.tar.bz2
Revisar el código-fuente del módulo, ejecutando:

sudo gedit /usr/src/linux-source-`uname -r`/drivers/net/sis190.c

Buscar en el código del módulo hasta hallar algo similar a:

printk(KERN_INFO "%s: Read MAC address from APC\n", net_dev->name);

isa_bridge = pci_find_device(0x1039, 0x0965, isa_bridge);
if (!isa_bridge) {
printk("%s: Can not find ISA bridge\n", net_dev->name);
return 0;
}

Y cambiar por

printk(KERN_INFO "%s: Read MAC address from APC\n", net_dev->name);

isa_bridge = pci_find_device(0x1039, 0x0968, isa_bridge);
if (!isa_bridge) {
printk("%s: Can not find ISA bridge\n", net_dev->name);
return 0;
}

Guardar el archivo, salir de gedit y compilar el nuevo módulo

Para compilar es necesario build-essential, ejecutar

sudo apt-get install build-essential

Ahora cambiar al directorio fuente y compilar el módulo ejecutando:

cd /usr/src/linux-source-`uname -r`
sudo make menuconfig
exit
yes 
sudo make drivers/net/sis190.ko

Una vez compilado ejecutar:

sudo rmmod sis190.ko
sudo cp drivers/net/sis190.ko /lib/modules/`uname -r`/kernel/drivers/net/
sudo  modprobe sis190

Si todo está bien, ya estaría funcionando el módulo.

Saludos.
Gabriel.

---

### Post by kechonius on 2008-09-21
gmunioz: gracias, probaré tu receta.

faktorqm: recien mañana tengo acceso a la sala, si no funciona lo que posteó gmunioz postearé las configuraciones

---

### Post by leo_liet on 2008-09-23
gmunioz muchas gracias por tu respuesta, pero como se supone que pueda bajar el paquete de internet, sino puedo conectarme?  :confused:
si sabes de otra forma que pueda descargarlo (desde windows me conecto sin problemas), te agradeceria que me la dijeras :)

   saludos y gracias   :lolflag:

---

### Post by kechonius on 2008-09-24
tenía la esperanza de que la solución de gmunioz funcionara, sobre todo por el grado de detalle, pero lamentablemente no fue así

aparentemente hay enlace, porque tanto en la placa como en el switch los leds están encendidos. Sin embargo, ni los pings responden.

```
administrador@construcciones:~$ sudo dmesg
[   45.662224] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   45.662241] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   45.662252] 0000:00:04.0: Read MAC address from APC.
[   45.710568] 0000:00:04.0: Unknown PHY transceiver at address 1.
[   46.278265] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at ffffc200004f2c00 (IRQ: 19), 00:1f:c6:ac:34:eb
```

a continuación las salidas de lspci e ifconfig

```
administrador@construcciones:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 671MX [1039:0671]
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:0004]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] [1039:0968] (rev 01)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] SATA Controller / IDE mode [1039:1183] (rev 03)
00:06.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:000a]
00:07.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:000a]
00:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8029(AS) [10ec:8029]
00:0f.0 Audio device [0403]: Silicon Integrated Systems [SiS] Azalia Audio Controller [1039:7502]
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7100 GS [10de:016a] (rev a1)

```

```
administrador@construcciones:~$ ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 00:00:21:43:e6:69  
          inet dirección:192.168.0.205  Difusión:192.168.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::200:21ff:fe43:e669/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:11860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4227 errors:65 dropped:0 overruns:0 carrier:130
          colisiones:1107 txqueuelen:1000
          RX bytes:9237265 (8.8 MB)  TX bytes:435393 (425.1 KB)
          Interrupción:19 Dirección base: 0xd000

eth1      Link encap:Ethernet  direcciónHW 00:1f:c6:ac:34:eb  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:3911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:280997 (274.4 KB)  TX bytes:0 (0.0 B)
          Interrupción:19 Dirección base: 0xdead

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:4042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4042 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0
          RX bytes:203315 (198.5 KB)  TX bytes:203315 (198.5 KB
```

---

### Post by rubioo on 2008-10-01
El problema creo que es del nucleo del SO. Creo que en Fedora no esta este problema, asi que espero que para la proxima version de Ubuntu este problema pueda estar solucionado.(si alguien pudo solucionarlo que postee la solucion)

   Saludos

---

### Post by leo_liet on 2008-10-07
Hola a todos, nadie ha podido hacer funcionar este tipo de placa en Ubuntu?¿
 Porque yo tengo la SiS191, y no puedo conectarme!
 Espero que no tenga que pasarme a Fedora, porque hasta ahora me gusto mucho Ubuntu, pero sino puedo conectarme a internet voy a tener que pasarme :(

       saludos

---

### Post by faktorqm on 2008-10-08
> **kechonius said:**
> eth1      Link encap:Ethernet  direcciónHW 00:1f:c6:ac:34:eb  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:3911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000
          RX bytes:280997 (274.4 KB)  TX bytes:0 (0.0 B)
          Interrupción:19 Dirección base: 0xdead


Hola, la placa de gigabit es esa, imposible que puedas a hacer ping a algun lugar si no le configuraste ninguna direccion IP!!!
Pone este comando en la consola completando los datos, y te pongo los datos de la eth0 para que veas COMO EJEMPLO.

```
sudo ifconfig eth1 direccion_ip netmask mascara_de_subred broadcast direccion_de_broadcast up
```

```
sudo ifconfig eth1 192.168.0.205 netmask 255.255.255.0 broadcast 192.168.0.255 up
```

Salu2!!!

---

### Post by leo_liet on 2008-10-08
Hola, muchas gracias faktorqm !!!
 Ya puedo hacerle un ping al router :D
 Pero no puedo entrar a la configuracion del mismo, es decir, no puedo conectarme con el Firefox al router. Y mucho menos puedo conectarme a internet, ya que no se como :S

   Espero que puedan ayudarme 

              Saludos

---

### Post by faktorqm on 2008-10-08
postea marca y modelo de router. salu2!

---

### Post by leo_liet on 2008-10-08
Es un router HUAWEI SmartAX MT 880, conectado por cable ethernet

---

### Post by faktorqm on 2008-10-08
pero capo! y el search para que esta?

[http://ubuntuforums.org/showthread.php?t=779717&page=2](http://ubuntuforums.org/showthread.php?t=779717&page=2)

---

### Post by leo_liet on 2008-10-09
Gracias capo! pero como hago para confirurar el router desde el Firefox, porque solamente puedo hacerle un ping al router :S

---

### Post by faktorqm on 2008-10-09
che sabes que varios me dicen eso a veces... no se bien que les pasa (a mi nunca me fallo... pero bueno). Postea un ifconfig y el ping al router a ver que pasa. (probaste usando telnet? dice 2 metodos el post) Salu2!

---

