---
title: "Broadcom version 4321AG 802.11 a/b/g/n ayuda para instalarlo"
date: 2008-07-23
forum: Hardware
---

### Post by caparral on 2008-07-23
*Hola que tal, soy un usuario nuevo en Ubuntu, lo acabo de instalar apenas ayer (Ubuntu 8.04.1 Hardy Heron), he logrado configurar prácticamente todos los drivers de mi laptop (HP Pavilion DV6646us) a excepción de uno, que es el driver de la Wireless Card Broadcom version 4321AG 802.11 a/b/g/n, para ello me he leido diversos manuales y tutoriales pero aún no he podido instalar esa Wireless Card. He visto este tutorial [http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321](http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321) y hecho lo que ahí me marca y no he logrado instalar la Wireless Card Broadcom, quizás este fallando en alguno de los pasos, por eso pido ayuda a ustedes para ver si me pueden orientar, de antemano gracias!!!*

---

### Post by sergiom99 on 2008-07-23
seguro que tenes ese modelo de placa?
postea la salida de: lspci

Yo tengo la misma laptop y la placa es BCM 4328.
Siguiendo ese tutorial la pude instalar perfecto (primero en Kubuntu 7.10 y despues 8.04)

Te da algun error o algo? o solo no tenes conexion? si le pones cable tenes red?

---

### Post by caparral on 2008-07-23
Si le pongo el cable de red (ethernet) funciona bien, pero lo que no me funka es la tarjeta de red Wireless, hice los pasos que ahi me marca, no me sale ningún error pero tampoco puedo navegar por internet con la Wi-Fi,  [http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321](http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321) las instrucciones que dan en este link las he seguido en su equivalente del SO en español, ya que el tutorial se desarrolla en base a un OS en inglés, por eso no sé si lo este desarrollando bien. En relación a lo que me dices de que postie la salida "lspci" y "dmesg |tail" la verdad no comprendo, recuerda que soy usuario nuevo, conforme vaya avanzando en este SO entenderé más el lenguaje, ojalá puedas explicarme y ayudarme, saludos!!!

---

### Post by lega on 2008-07-23
lo que te pide sergiom99 es que en una terminal tipees ese comando

lspci y pegues acá lo que te dice.

Saludos

---

### Post by caparral on 2008-07-23
Ohh jeje, entiendo, gracias Lega, se escucha más complicado de lo que es xD!! entonces eso haré, escribo desde XP, pero falta poco para migrarme completamente a Ubuntu.

---

### Post by caparral on 2008-07-24
Bueno ya me puse a leer y ya capté un poco más acerca de mi fallo, resulta que en los pasos que dan en este [tutorial]("http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321") en la parte que dice "Mientras nosotros estamos aquí vamos a desbloquear todos nuestros repositorios" (esa parte es una de las que no me cuadra) ¿no se supone que solo se necesita activar ndiswrapper y sus utilidades? en fin, lo que hice fue activar las 3 casillas de ndiswrapper nada más, ¿tengo que activar forzosamente todas las casillas de los repositorios? bueno, después seguí con lo que marca ahí, en Gestor de paquetes synaptic fui a configuración y seleccione todas las casillas de la primera página excepto la de CD y todo lo demás lo hice tal cual.

He instalado estos repositorios en torno a ndiswrapper: ndisgtk,ndiswrapper-common, ndiswrapper-utils-1.9

Aqui esta lo del lspci 

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)


Este es el error que me sale:

carlos@carlos-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
[sudo] password for carlos: 
couldn't open bcmwl5.inf: No existe el fichero ó directorio at /usr/sbin/ndiswrapper-1.9 line 219.

Al parecer todo marcha en relación a la incompleta instalación de ndiswrapper la cual yo la hago desde el gestor de paquetes synaptic. Asi es que este es el problema que en estos momentos estoy teniendo. Ojalá puedan ayudarme

---

### Post by sergiom99 on 2008-07-25
creo que se porque es:
el comando ese lo tenes que hacer parado en el directorio en donde descargaste y descomprimiste los drivers que dice el tutorial original.
>  Navigate to where you saved the drivers I had you download and extract. Now run the following
Si los drivers los descargaste en /home/carlos/wifi haces:
```
cd ~/wifi
sudo ndiswrapper -i bcmwl5.inf

``` y así continua...

(lamentablemente no me acuerdo el comando de consola para descomprimir. ahora estoy en el laburo con Win$! Pero desde Gnome, podes extraer los drivers que bajaste haciendo clic derecho y después te pasas a ese directorio en consola.)
Suerte!

---

### Post by caparral on 2008-07-25
Perfecto voy a probarlo, lo único que no entiendo muy bien es el detalle de la localización del directorio donde bajé el driver, es decir, porque ponen esto

```
cd ~/wifi
sudo ndiswrapper -i bcmwl5.inf
```

en vez de poner esto

```
/home/carlos/wifi
sudo ndiswrapper -i bcmwl5.inf
```

FUNCIONÓ DE MARAVILLA!!! Muchas gracias sergiom99, ese era el paso que me estaba faltando, no era porque no entendiera el inglés, sino porque no sabía de que manera ubicar en la terminal el sitio donde estaba el archivo .inf, ahora te escribo desde la wireless card, pero me sale esto después de activar la red inalambrica:

**Introduzca la contraseña para desbloquear el anillo predeterminado**

"la aplicación 'nm-applet' (/usr/bin/nm-applet) quiere acceder al anillo de claves predeterminado, pero esta bloqueado" y me pone que escriba una contraseña pero no se cuál, porque le pongo la de usuario principal y nada, pongo la contraseña de la Wi-Fi y tampoco, además de que cuando suspendo la laptop (cierro la tapa) al volver abrirla y entrar a desktop me pide de nuevo la contraseña Wep de la Wi-Fi, ¿habrá manera de configurarlo para que la arranque automáticamente como en windows?

---

### Post by sergiom99 on 2008-07-25
yo uso Kubuntu y hay algunas cosas que son distintas. Pero creo que 'nm-applet' debe ser el Network Manager. Y la contraseña que te pide debe ser la del gestor de claves de Gnome. (algo como el KdeWallet).
En Kubuntu lo tengo seteado para que el wifi arranque solo y no pida clave. se le puede poner que la clave la guarde por fuera de KDEWallet, asi no pide la clave para desbloquearlo.
En esto vamos a tener que esperar alguno con mas manejo de Gnome.
Pero me alegro que tengas la placa andando!

---

