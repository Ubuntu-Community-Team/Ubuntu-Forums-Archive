---
title: "Instalar drivers?"
date: 2009-04-27
forum: Hardware
---

### Post by Just64 on 2009-04-27
Instale 9.04 y no tengo los drivers de la placa de video de mi MSI PR200, creo q la paca era una intel x3100 o algo asi, el tema es q en controladores de hardware no me sale nada actualizarlo... asiq estoy sin efectos 3d en la maquina.
¿Como hago para actualizar los drivers de los diferentes componentes de la  notebook? Xq tengo el cd de los drivers pero son para Vista.

---

### Post by luks911 on 2009-04-28
Las placas intel no necesitan drivers aparte como las nvidia o ati, o sea, usan drivers pero son detectadas automáticamente por el sistema que se encarga de instalarlos.
Ahora, hay una serie de "cuestiones" con algunas intel y los drivers que vienen en Jaunty. Pasá por este[0] hilo a ver si te sirve, no estoy seguro de que se trate de la misma placa.

[0] [http://ubuntuforums.org/showthread.php?t=1130135](http://ubuntuforums.org/showthread.php?t=1130135)

---

### Post by guillermolisi on 2009-04-28
Para verificar como detecta tu placa de video y que driver estas usando abri una consola/terminal e ingresa
```
sudo lshw |less
```
Fijate que vas a tener una entrada con la etiqueta "display" con la informacion de la placa de video y el driver.

Mostra esa seccion asi podemos ver de que se trata.

---

### Post by Just64 on 2009-04-28
```
*-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
```
Ahy esta.
 
Tambien tengo problemas con la camara web... :S

```
pato@pato-laptop:~$ lsusb
Bus 002 Device 006: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 004: ID 1221:3234  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 007 Device 002: ID 147e:2016  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by guillermolisi on 2009-04-28
> **Just64 said:**
> ```
*-display:0 UNCLAIMED
             description: **VGA compatible controller**
             product: **Mobile GM965/GL960** Integrated Graphics Controller
             vendor: **Intel Corporation**
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
```Ahy esta.
 
Tambien tengo problemas con la camara web... :S

```
pato@pato-laptop:~$ lsusb
Bus 002 Device 006: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 004: ID 1221:3234  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 007 Device 002: ID 147e:2016  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
Fijate en el siguiente thread que hablan de problemas con placas de video como la que tenes en tu maquina (Intel GM965/GL960)

[http://ubuntuforums.org/showpost.php?p=7110298&postcount=6](http://ubuntuforums.org/showpost.php?p=7110298&postcount=6)

El mensaje de Sajnox tambien te indica unos bugs que no se si a la fecha estan resueltos.

---

