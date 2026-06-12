---
title: "red inalambrica"
date: 2010-01-31
forum: Hardware
---

### Post by lucazaux on 2010-01-31
necesito controladores para una antena inalàmbrica externa y configurar la red alguien puede guiarne, tengo ubuntu recièn desdee hoy, gracias

---

### Post by guillermolisi on 2010-02-01
> **lucazaux said:**
> necesito controladores para una antena inalàmbrica externa y configurar la red alguien puede guiarne, tengo ubuntu recièn desdee hoy, gracias
Vayamos por partes.

Primero que modelo de placa wifi estas usando ?
Si no sabes su marca y modelo, copia y pega en tu respuesta la salida de los comandos de consola /terminal "lspci" y "lsusb" (sin las comillas). Con esto podremos poner en marcha la red wifi para luego configurarla.

---

### Post by lucazaux on 2010-02-03
> **guillermolisi said:**
> Vayamos por partes.

Primero que modelo de placa wifi estas usando ?
Si no sabes su marca y modelo, copia y pega en tu respuesta la salida de los comandos de consola /terminal "lspci" y "lsusb" (sin las comillas). Con esto podremos poner en marcha la red wifi para luego configurarla.

estoy usando una antena externa porque la interna no funciona, es tipo pendrive.y su nombre es eusso. gracias desde ya

---

### Post by guillermolisi on 2010-02-03
> **lucazaux said:**
> estoy usando una antena externa porque la interna no funciona, es tipo pendrive.y su nombre es eusso. gracias desde ya
Lo que importa es la marca y modelo del chip de la antena, no la marca del dongle, por eso lo de los reportes de esos comandos (para este caso "lsusb" con la antena conectada a la PC usando Ubuntu).

---

### Post by lucazaux on 2010-02-03
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




es lo que aparece, gracias

---

### Post by lucazaux on 2010-02-04
p00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
ara el otro caso lo que me aparece es esto

---

### Post by luks911 on 2010-02-05
Probá con lo que dice este post[0], eos sí me parece que los tres comandos los tenés que hacer con sudo delante, o sea
```
sudo cp /lib/firmware/zd1211 /lib/firmware/`uname -r`/zd1211
sudo modprobe zd1211rw
```
y 
```
sudo echo zd1211rw >> /etc/modules

```
La placa debería funcionar luego del segundo, el tercero es para que se cargue el módulo/driver en cada inicio.

[0] [http://ubuntuforums.org/showpost.php?p=7648435&postcount=22](http://ubuntuforums.org/showpost.php?p=7648435&postcount=22)

---

