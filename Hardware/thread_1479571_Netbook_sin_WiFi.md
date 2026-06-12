---
title: "Netbook sin WiFi"
date: 2010-05-10
forum: Hardware
---

### Post by PayasoMalaOnda on 2010-05-10
Hola gente tengo una netbook EXO infinity 2250[ ESPECIFICACIONES]("http://www.google.com.ar/imgres?imgurl=http://www.mosdata.com.ar/web2/components/com_virtuemart/shop_image/product/EXO_SMART_RX850__4a575defab01f.jpg&imgrefurl=http://www.mosdata.com.ar/web2/notebooks/notebook-exo-smart-rx850.html&usg=__D5rabQm00I2UICfXaBkbYi5dFIs=&h=450&w=450&sz=22&hl=es&start=18&sig2=HCt0Cca_pneP_7t_-FxPew&um=1&itbs=1&tbnid=C9bOMcW3hOCFsM:&tbnh=127&tbnw=127&prev=/images%3Fq%3Dexo%2B2250%26um%3D1%26hl%3Des%26client%3Dfirefox-a%26sa%3DG%26rls%3Dorg.mozilla:es-ES:official%26tbs%3Disch:1&ei=4qDoS_7NB4_oMafc1dQJ") la cual anda realmente muy bien y la tengo con el seven que vino de fabrica mas el Lucid y anda muy bien pero con el internet tengo problemas ya que con la ficha de red anda bien pero con el wifi tengo problemas ya que no me puedo conectar:confused:
En el Seven anda bien el bluetoth y el wifi peero Linux no me encuentra la placa wifi ni tampoco el bluetooth ensima no he encontrado en ningun post alguna respuesta asi que los molesto:(

---

### Post by mhoyos on 2010-05-10
hola..

lo que necesitaria saber de ese modelo de netbook, es que placa de red wifi tiene (marca, modelo, etc).

te pediria que ejecutes en una consola/terminal:
```
sudo lspci -v 
```

y el resultado, lo pongas en este foro. con esa info, veremos de como seguimos.

saludos.

---

### Post by guillermolisi on 2010-05-10
Por las dudas que sean placas USB, ejecuta en consola/terminal y mostranos la salida de ```
lsusb
```

---

### Post by PayasoMalaOnda on 2010-05-10
[B]lsusb
[/B] 



Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1700:013a  
Bus 001 Device 002: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




y


[B]
sudo lspci -v
[/B] 




00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Intel Corporation Mobile 945GME Express Memory Controller Hub
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Intel Corporation Mobile 945GME Express Integrated Graphics Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc80 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fea40000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Intel Corporation Device 27ae
    Flags: bus master, fast devsel, latency 0
    Memory at fe980000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Device 1b35:2001
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fea38000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Device 1b35:2001
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Intel Corporation N10/ICH7 Family USB UHCI Controller #1
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fea37c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    Capabilities: [50] Subsystem: Device 1b35:2001

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Device 1b35:2001
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Device 1b35:2001
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Device 1b35:2001
    Flags: medium devsel, IRQ 5
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
    Subsystem: JMicron Technology Corp. SD/MMC Host Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at febffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

01:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80) (prog-if 01)
    Subsystem: JMicron Technology Corp. Standard SD Host Controller
    Flags: fast devsel, IRQ 17
    Memory at febff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel modules: sdhci-pci

01:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
    Subsystem: JMicron Technology Corp. MS Host Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at febff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

01:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
    Subsystem: JMicron Technology Corp. xD Host Controller
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at febff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

01:00.5 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 02)
    Subsystem: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at febf4000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at ec80 [size=128]
    I/O ports at e800 [size=256]
    Capabilities: [68] Power Management version 3
    Capabilities: [50] Express Legacy Endpoint, MSI 00
    Capabilities: [40] MSI-X: Enable- Mask- TabSize=8
    Capabilities: [70] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
    Kernel driver in use: jme
    Kernel modules: jme





Muchachos wifi tiene porque lo uso en el Seven y el bluetooth tambien solo no me andan en el Lucid:(

---

### Post by guillermolisi on 2010-05-11
Definitivamente es una placa WiFi USB de Syntek, el mismo fabricante de las 3DSP que traen las Bangho Fit, que vienen WiFi y Bluetooth. Verifique por el ID code.

Mas info en Ingles en:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9218168](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=9218168)

[http://ubuntuforums.org/showthread.php?t=1234213&page=2](http://ubuntuforums.org/showthread.php?t=1234213&page=2)

Mi mujer tiene una Bangho con esa placa pero miniPCI con 9.10 funcionando.

---

### Post by PayasoMalaOnda on 2010-05-11
Desde las dos de la tarde que estoy tratando y no logro hacerlo andar ya me bajè casi todos los que estan en ese enlace y no aparece nada

---

### Post by PayasoMalaOnda on 2010-05-12
El problema esta en que nunca instalè algo de esta manera:confused: no me maten :(
estoy buscando la forma pero no puedo  porque no vienen en un .deb y listo no:guitar:
desde ya les agradesco si me pueden ayudar que no se para donde disparar y el seven no 

me da confianza para usarlo tyodo el dia y descargar cosas:P

---

### Post by guillermolisi on 2010-05-12
No te desesperes que entre todos lo vamos a sacar funcionando.

Mientras Marco (mhoyos) hace la investigacion profunda del caso (trabaja en Exo) te recomiendo que leas [este thread]("http://ubuntuforums.org/showthread.php?t=1320989") que, si bien es sobre una maquina de diferente marca, usa la misma placa wifi que la tuya.

---

### Post by PayasoMalaOnda on 2010-05-12
UH! Buenisimo ya lo estoy leyendo (espero no perder la garantia jejeje)
Gracias por la ayuda , ya hace años que uso linux y la verdad nunca se deja de aprender:)

2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

---

### Post by guillermolisi on 2010-05-12
> **PayasoMalaOnda said:**
> UH! Buenisimo ya lo estoy leyendo (espero no perder la garantia jejeje)
Gracias por la ayuda , ya hace años que uso linux y la verdad nunca se deja de aprender:)

2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
Ojo que para esa version de kernel aun no salio el driver.

[Ver aqui]("http://www.stk.com.tw/product-01.asp?Product_Type=58") para mas info.

---

### Post by PayasoMalaOnda on 2010-05-12
Ya habia visto eso,quiere decir que ya fue no? no podria usar ni wifi ni el bluetooth en la netbook , que mala leche .

---

### Post by guillermolisi on 2010-05-12
> **PayasoMalaOnda said:**
> Ya habia visto eso,quiere decir que ya fue no? no podria usar ni wifi ni el bluetooth en la netbook , que mala leche .
Por ahora es posible (no lo he probado aun) que cuando compiles te de errores.
Me paso cuando en 9.10 con una actualziacion cambio la version de kernel. Intente compilar el driver anterior sin suerte y ahi baje el nuevo que actualmente esta funcionando.

Como aun no salio el driver para el kernel actual, la note esta sin actualizar a proposito. Apenas lo liberen actualizo y reinstalo el driver.

Es cuestion de poco tiempo para que tengas tu maquina funcionando a full.

Una alternativa que tenes a mano es comprarte un dongle USB, una antena wifi USB externa. Por poco dinero tendrias conexion. No compres nada sofisticado porque en general las mas berretas son las que mejor funcionan con Linux.

---

### Post by PayasoMalaOnda on 2010-05-13
Ok entonces me resigno pero estaré atento a este thread y a la pagina donde se bajan los drivers **diariamente** :P muchas gracias por la ayuda y me pongo a buscar como se "compilan" y como se instalan para ir aprendiendo.
Muchas gracias por la ayuda

---

### Post by guillermolisi on 2010-05-13
> **PayasoMalaOnda said:**
> Ok entonces me resigno pero estaré atento a este thread y a la pagina donde se bajan los drivers **diariamente** :P muchas gracias por la ayuda y me pongo a buscar como se "compilan" y como se instalan para ir aprendiendo.
Muchas gracias por la ayuda
No necesitas buscar como se compilan ya que el script de instalacion que se provee con estos drivers incluye la compilacion previa a su instalacion.

---

### Post by PayasoMalaOnda on 2010-05-13
La pregunta que se me cae de maduro es:puedo bajar el kernel? y me respondo (y corregime)deberia instalar el anterior ubuntu para poder usar el wifi? y si no es el anterior cual serìa?

---

### Post by guillermolisi on 2010-05-13
> **PayasoMalaOnda said:**
> La pregunta que se me cae de maduro es:puedo bajar el kernel? y me respondo (y corregime)deberia instalar el anterior ubuntu para poder usar el wifi? y si no es el anterior cual serìa?
Si realizaste un upgrade desde la version 9.10 y no borraste los kernels anteriores, deberias poder elegirlos desde el menu del Grub (siempre que lo tengas visible) en tiempo de arranque.

Podrias bajarte el kernel vigente de la 9.10 (o el anterior al vigente) e instalarlo. Como nunca tuve ncesidad de semejante operacion, no se que resultados tendra respecto de modulos que tengas instalados (los modulos son drivers que estan fuera del kernel, asociados externamente). Siempre fui hacia la ultima version via actualizaciones y siempre guardo el ultimo kernel anterior en uso por si le pasa algo a la instalacion nueva.

Esta todo en los repositorios.

Me parece que si por (ponele) $ 50.- haces funcionar la maquina con una antena USB, ni me meteria a semejante cosa y disfrutaria a fondo de LL (hasta podrias olvidarte de la 3DSP).

---

### Post by PayasoMalaOnda on 2010-05-14
Por lo de la antena externa no hay problema , es mas la semana pasada tube que tirar dos que tenia rota eso es lo de menos el tema es usar la maquina como está asi que voy a esperar ya que me gusta como deje la maquina , de ultima reinstalo desde cero y listo jeje pero la verdad no tengo ganas de tomarme el trabajo asi que voy a esperar un tiempito y me sigo arreglando con la ficha de red,muchas gracias por la ayuda.

---

### Post by guillermolisi on 2010-05-14
> **PayasoMalaOnda said:**
> Por lo de la antena externa no hay problema , es mas la semana pasada tube que tirar dos que tenia rota eso es lo de menos el tema es usar la maquina como está asi que voy a esperar ya que me gusta como deje la maquina , de ultima reinstalo desde cero y listo jeje pero la verdad no tengo ganas de tomarme el trabajo asi que voy a esperar un tiempito y me sigo arreglando con la ficha de red,muchas gracias por la ayuda.
Aguanta que en cualquier momento los chinos liberan una version para el kernel que estamos usando.

---

### Post by PayasoMalaOnda on 2010-05-31
Bueno al fin jeje despues de esperar unos dias salio mi salvacion 

y ya pude usar el wifi y el bluetoth de mi EXO , pero por lo menos para mi que no se 

nada me costo bastante hacerlo andar y para los que no lo han logrado aca les dejo como hice :guitar:

[http://www.stk.com.tw/product-01.asp?Product_Type=58](http://www.stk.com.tw/product-01.asp?Product_Type=58)  de esta pagina lo bajé (gracias por el dato! ) que es este de esta captura



[IMG]http://i404.photobucket.com/albums/pp129/PayasoMalaOnda/d1afffd6.png[/IMG]



una vez que lo baje lo metì en mi carpeta personal y habrí el README para poder instalarlos

ya que es la primera vez que instalo drivers en Ubuntu hice todo lo que dice el archivo

pero hay que destacar para los que NO saben NADA como yo que las lineas que copiamos

al terminal son sin el numeral que esta por delante ( **#** ) sino no anda el comando los 

que ya saben no se rian eh :P

despues de extraer (como dice el readme)
hace una carpeta llamada  **BlueW-2310U_2.4.1_100527_Ubuntu10.04_withouthotkey** dentro de la carpeta personal pero no me dejaba

instalar entonces copie todo lo que esta dentro de** BlueW-2310U_2.4.1_100527_Ubuntu10.04_withouthotkey** suelto en la carpeta personal

y ahi SI lo instaló correctamente y ya lo estoy usando!!
Pero me surge una duda TODO lo que saque de la carpeta y lo dejé desparramado en la carpeta personal 

es lo mismo que esta dentro de la carpeta de **BlueW-2310U_2.4.1_100527_Ubuntu10.04_withouthotkey**  entonces se puede eliminar ya??

o sino cual debo eliminar? archivos sultos o carpeta:confused:   igualmete seria lo de menos pero es soy muy 

hincha pelotas con el orden y saber que esta la carpeta despelotada me jode jaja gracis de antemano!!
[IMG]http://www.stk.com.tw/product-01.asp?Product_Type=58[/IMG]

---

### Post by guillermolisi on 2010-05-31
Bueno, una alegria despues de solo dos semanas de "dulce espera".

Gracias por tomarte el trabajo de pasarnos toda la informacion y confirmar que con ese nuevo driver funciona.

---

### Post by PayasoMalaOnda on 2010-05-31
En realidad instale el Jaunty y me puse a bajar los drivers y vi que estaban los nuevos asi que tube que instalar otra vez el 

Ultimate y ahi los instalé jaja un par de horas instalando y desinstalando pero bueno el que no tiene cabeza tiene pies .

---

