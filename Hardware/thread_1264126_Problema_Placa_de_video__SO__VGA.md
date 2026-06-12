---
title: "Problema Placa de video / SO / VGA"
date: 2009-09-11
forum: Hardware
---

### Post by PabloGNU/LINUX on 2009-09-11
Tengo un problema pero no pude identificar si es HARDWARE o SOFT

Datos sistema:
 Mother: Pcchips M909g V 5.0a
 S.O.: Ubuntu 9.02
 Placa de video: Nvidia Gforce x4 5200 128mb
 
Bueno.. la cuestion es que yo instale ubuntu pero sin la placa de video conectada, entonces cuando termino la instalacion me pidio retirar el CD y apretar "ENTER". Se reinicio y la apague, Instalo la placa de video la prendo pero no inicia el SO, queda cargando antes de inciar Ubuntu en el grafico de la barra. 
Conectando el monitor a la entrada VGA onboard arranca el SO.
 Y la placa de video en Windows XP si funciona entonces descarto que sea problema de hardware no?..

En conclusion:
[LEFT]       
         - No arranca el SO Ubuntu con mi placa de video, pero con VGA onboard si.
         - La placa de video si funciona, cuando la corro bajo windows. 
         - Cuando tenia Ubuntu 8.04 el SO arrancaba. 
- La placa se sobre calienta con ubuntu.

Si alguien puede ayudarme, muchas gracias. 
[/LEFT]

---

### Post by Hei Ku on 2009-09-11
Postea el resultado de correr lspci en una terminal, por favor.

---

### Post by PabloGNU/LINUX on 2009-09-11
Informe de lspci:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Lindo informe :) 
No sabia sobre esto,  de a poco se aprende.

---

### Post by Hei Ku on 2009-09-12
Ahi no figura la nvidia. Seria bueno tener el resultado del comando, pero con la placa conectada.

Por otro lado, por que instalaste con la placa desconectada?

---

### Post by PabloGNU/LINUX on 2009-09-12
No se como poner para que inicie teniendo la VGA como primaria, si lo sabes por favor explicamè. 
Y no la pongo la Nvidia por esa razon. No incia el SO y la tengo puesta como primaria. 
Entonces la retire para podes usar Ubuntu. 

Es la pc de un clente, solo retire la Nvidia para instalar Windows y dejar listo el HDD. 
Son 2 HDD diferentes, en uno instale Windows y en el otro que es mio instale Ubuntu ( no tengo maquina propia) 
Instale windows lo deje perfecto y reinicie y puse master el mio e instale Ubuntu, mientras instalaba recorde que habia retirado la Nvidia por eso hise ese procedimiento despues.

Tengo otro incomveniente :S
Yo pense que al instalar Windows y Ubuntu antes de comenzar me dejaba elegir en que sistema operativo deseaba trabajar. 
Como realizo eso?. para seleccionar el SO.

En que posicion tiene que estar los HDD? (Master/Slave).

Al intentar poner los 2 discos, solo iniciaba con Ubuntu y cuando solo deje el HDD de windows Master salta un mensaje diciendo "Error para cargar el sistema operativo".

Muchas gracias

---

### Post by Hei Ku on 2009-09-12
Si queres arreglar tu problema del doble boot, por favor abri otro thread.

---

### Post by PabloGNU/LINUX on 2009-09-12
Esta bien, abrire otro.
 
Traje un informe de Nvidia desde Windows:
[]("http://driveragent.com?ref=59") 
  [ NVIDIA GeForce FX 5200  (Microsoft Corporation) ]
    Propiedades de la tarjeta gráfica:
      Descripción del dispositivo                       NVIDIA GeForce FX 5200  (Microsoft Corporation)
      identificación de la tarjeta                      GeForce FX 5200
      Identificación de la BIOS                         Version 4.34.20.87.00
      Tipo de circuito                                  GeForce FX 5200
      Tipo de DAC                                       Integrated RAMDAC
      Controladores instalados                          nv4_disp (6.14.10.5673 - nVIDIA ForceWare 56.73)
      Tamaño de la memoria                              128 MB
    Fabricante de la tarjeta gráfica:
      Nombre de la empresa                              NVIDIA Corporation
      Información sobre el producto                     [http://www.nvidia.com/page/products.html](http://www.nvidia.com/page/products.html)
      Descargar el controlador                          [http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)
      Driver Update                                     [http://driveragent.com?ref=59](http://driveragent.com?ref=59)

--------[ Video PCI/AGP ]-----------------------------------------------------------------------------------------------
    Intel Extreme Graphics                                                            Tarjeta gráfica
    nVIDIA GeForce FX 5200 (Gigabyte GV-N52)                                          Tarjeta gráfica
    Intel Extreme Graphics                                                            Acelerador 3D
    nVIDIA GeForce FX 5200                                                            Acelerador 3D
---------------------------------------------------------------------------------------------------
 
Gracias por tu tiempo.

---

### Post by staar on 2009-09-12
como tenés configurado el tema de las placas en la BIOS? cual está como primaria? en algunas mother pcchips había que desactivar manualmente la placa onboard para que levante una agp...

saludos

---

### Post by PabloGNU/LINUX on 2009-09-12
> **staar said:**
> como tenés configurado el tema de las placas en la BIOS? cual está como primaria? en algunas mother pcchips había que desactivar manualmente la placa onboard para que levante una agp...

saludos

Gracias, pero el problema radica en que no puedo iniciar Ubuntu con Nvidia, pero con windows si. La unica manera de que arranque desde ubuntu es retirando la placa de video y por logica VGA queda como primaria. Es automatico. 

Gracias de todos modos.

---

### Post by gmunioz on 2009-09-12
Hola pab....:

Instala la tarjeta nvidia.

Desactiva la tarjeta onboard

Cuando inicia Ubuntu pulsa escape.

```
En el menu del Grub

Elige recovery mode

En el submenu emergente

Elige netroot
```

En la consola que se abre luego

de iniciar en modo texto ejecuta:

```
apt-get update
apt-get upgrade
apt-get install envyng-core envyng-gtk
envyng
```

y sigue las indicaciones para instalar los drivers

de tu tarjeta, completada la instalación, reinicia

normalmente.

---

### Post by PabloGNU/LINUX on 2009-09-12
No, no me funciono =(

Gracias.

---

