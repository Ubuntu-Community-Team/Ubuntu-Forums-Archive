---
title: "wireless en netbook exo"
date: 2010-11-02
forum: Hardware
---

### Post by infernus92 on 2010-11-02
hola ubunteros
ando con un problemita con una netbook exo que tengo hace muy poco. le puse ubuntu 9.10 netbook remix (no pude levantar 10.10) y no logro hacer andar la red inalambrica. Controladores restringidos no me pide ninguno.
Tiene la luz prendida cono si estuviera activada pero desde el gestor de red no la veo. Tambien supongo que puede ser la tecla de funcion para activarla, la que no me reconoce bien todas las combinaciones
si alguno me puede dar una mano con esto se lo agradezco mucho

saludos

---

### Post by infernus92 on 2010-11-02
otra solucion para esto seria algun comando que me active la placa de red inalambrica. con un script lo podria solucionar facilmente... buscando no encontre nada, alguien no conoce algo asi??

---

### Post by benja22 on 2010-11-02
¿Que tarjeta de red inalambrica es?

tal vez deberias instalar el firmware de tu tarjeta...

---

### Post by infernus92 on 2010-11-02
esto es lo que me devuelve un lspci

```
00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
**07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)**
09:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

```

la placa esta marcada en negrita

---

### Post by benja22 on 2010-11-02
> **infernus92 said:**
> esto es lo que me devuelve un lspci

```
00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
**07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)**
09:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

```

la placa esta marcada en negrita


Esa es la ethernet (la red por cable) sale el nombre de la inalambrica dice Rtl8172 ```
09:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
```

---

### Post by benja22 on 2010-11-02
escribe en el terminal:
```
ifconfig
```
```
iwconfig
```

y escribe lo que muestra

---

### Post by infernus92 on 2010-11-02
tenes razon, marque la otra.
la verdad no creo que sea un problema de drivers. normalmente ubuntu avisa si necesita un controlador adicional a los que trae por defecto
lo que no logro hacer es activarla. cono todas las notebook y netbook trae atajos del teclado con una tecla de funcion, y no me reconoce a casi ninguna de esas funciones. Lo ideal seria conseguir el comando que deberia activar la combinacion de teclas que habilitan la placa de red inalambrica

---

### Post by infernus92 on 2010-11-02
tenes razon, marque la otra.
la verdad no creo que sea un problema de drivers. normalmente ubuntu avisa si necesita un controlador adicional a los que trae por defecto
lo que no logro hacer es activarla. cono todas las notebook y netbook trae atajos del teclado con una tecla de funcion, y no me reconoce a casi ninguna de esas funciones. Lo ideal seria conseguir el comando que deberia activar la combinacion de teclas que habilitan la placa de red inalambrica

---

### Post by benja22 on 2010-11-02
sabes, me ocurre algo parecido con mi una tarjeta rt61,la tarjeta es reconocida por el sistema pero no funciona,como si no viera redes, entonces lo que hago es instalar el firmware de la tarjeta rt61.
¿algo así te sucede?

Si es asi prueba instalar el firmware, creo que es el firmware-realtek


```
sudo aptitude install firmware-realtek
```

Si eso no te funciona, instala tu tarjeta con los drivers de windows:
```
sudo su
```
```
aptitude install ndiswrapper
```
luego vas a la carpeta donde tienes el driver de tu tarjeta(de windows), busca un archivo .inf y escribes (por ejemplo la tienes en /home/juan/driver
```
cd /home/juan/driver 
``` 
```
ndiswrapper -i nombre-de-archivo.inf
```
```
gedit /etc/modules
``` 
ahí agregas al final: ndiswrapper
debes bloquear el otro driver para lo que escribes
```
gedit /etc/modprobe.d/blacklist
``` 
ahí agregas el nombre del driver que tenias instalado (buscas el nombre en gedit /proc/modules  deberia estar ahi)

---

### Post by infernus92 on 2010-11-02
googleando encontre en launchpad (en ingles) a algunos q tenian mi mismo problema. Habia un paquete para instalar que lo solucionaba. Muy simple, se descomprime y desde un terminal ./install y nada mas. Dejo el link de descarga para alguien que tenga mi mismo problema y espero que se les solucione a mi.
Y muchas gracias benja22 por tratar de ayudarme

saludos

[http://https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/+attachment/672240/+files/e1312wlan.tar.gz]("http://https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/+attachment/672240/+files/e1312wlan.tar.gz")

---

### Post by benja22 on 2010-11-02
muy bien!
me alegro de que lo hayas solucionado
suerte para la proxima ;)
saludos

---

