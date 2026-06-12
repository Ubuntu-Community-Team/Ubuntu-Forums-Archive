---
title: "ASUS M50vc de Vista a UBUNTU"
date: 2009-04-13
forum: Hardware
---

### Post by sackm on 2009-04-13
Hola ):P bueno, parto saludando a toda la comunidad, como podran ver es mi primer tema en el foro :p les escribo para pedirles ayuda. Con el timpo lei sobre ubuntu y me parecio buenisimo (vista es una ******) y decidi hacer el gran cambio ajaja :D bueno instale ubuntu y me tope con que no me tomaba los drivers de casi nada (wifi, video,sonido, etc.) Instale la version 8.04. El primer gran problema es que sin internet no puedo hacer nada... 

Alguien que pueda ayudarme a buscar los drivers para volver a aplicar Ubuntu porfavor :) saludos :guitar:

---

### Post by pablo.s on 2009-04-13
Hola: Abri una terminal. 
(Aplicaciones - Accesorios -Terminal)

Escribi:

lspci

Copiá lo que te devuelva y pegalo en
un mensaje nuevo.

Saludos.

---

### Post by Mauro22 on 2009-04-13
La verdad que es raro que a esta altura no te reconozca casi nada... :mad:

Ni bien puedas postea el resultado de lspci como te dijo pablo para ver que hardware tenes.

Acordate que podes hacer:

lspci > mihardware.txt 

O el nombre que quieras con o sin extension para que te quede en un archivo, por si te lo vuelven a pedir o para verlo mas comodo...

---

### Post by sackm on 2009-04-13
Trate de hace el Ispci en ubuntu y no me arrojo nada ... les sirve si le doy la informacion de mi hardware atraves de Everest por vista ?

---

### Post by luks911 on 2009-04-13
> **sackm said:**
> Trate de hace el Ispci en ubuntu y no me arrojo nada ... les sirve si le doy la informacion de mi hardware atraves de Everest por vista ?
 Lo que psas es que el comando es 
```
lpci
```

la primera es una L. Probá así que te va adar un resultado.

PD: también podés copiar y pegar en la terminal. Para pegar es Ctrl+Shift+V. Esas combinaciones en la terminal son las usuales Ctrl+(letra) pero se le suma el Shift antes de la letra.

---

### Post by pablo.s on 2009-04-13
> **luks911 said:**
> Lo que psas es que el comando es 
```
lpci
``` 

Oy Vey, el comando es

lspci ====> l s p c i

no lpci. Si lo vas a ayudar fijate
de no mandar fruta.

---

### Post by luks911 on 2009-04-13
> **pablo.s said:**
> Oy Vey, el comando es

lspci ====> l s p c i

no lpci. Si lo vas a ayudar fijate
de no mandar fruta.

Qué salame soy. Eso me pasa por escribir rápido y no mirar... y cuando debería estar trabajando :-P

Gracias por la corrección

---

### Post by sackm on 2009-04-13
Bueno lo saque con everest en windows al final y me dio esto 

[http://www.megaupload.com/?d=QKK6Q9MZ](http://www.megaupload.com/?d=QKK6Q9MZ) no supe subirlo de otra forma u.u

---

### Post by Mauro22 on 2009-04-13
Pegó lo que me pareció importante:

Video: NVIDIA GeForce 9300M GS  (512 MB)
Sonido: Realtek ALC663 @ Intel 82801IB ICH9
Red:  Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)
         Intel Shirley Peak (Shiloh) 1x2 MC Wireless WiFi Adapter


Otra cosa no encontre... hay demaciado...


No lo puedo adjuntar porque supera el limite del foro.


```

--------[ EVEREST Ultimate Edition ]------------------------------------------------------------------------------------ 
 
    Versión                                           EVEREST v4.60.1500/es 
    Benchmark Module                                  2.3.237.0 
    Sitio Web                                         http://www.lavalys.com/ 
    Tipo de informe                                   Asistente de informes [ TRIAL VERSION ] 
    Ordenador                                         SADOCMONSALVE1 
    Generador                                         Sadoc Monsalve 
    Sistema operativo                                 Microsoft Windows Vista Home Premium 6.0.6001 (Vista Retail) 
    Fecha                                             2009-04-13 
    Hora                                              17:48 
 
 
--------[ Resumen ]----------------------------------------------------------------------------------------------------- 
 
    Ordenador: 
      Tipo de ordenador                                 Equipo basado en ACPI x86  (Mobile) 
      Sistema operativo                                 Microsoft Windows Vista Home Premium 
      Service Pack del Sistema Operativo                [ TRIAL VERSION ] 
      Internet Explorer                                 7.0.6001.18000 
      DirectX                                           DirectX 10.0 
      Nombre del sistema                                SADOCMONSALVE1 
      Nombre de usuario                                 Sadoc Monsalve 
      Nombre de dominio                                 [ TRIAL VERSION ] 
      Fecha / Hora                                      2009-04-13 / 17:48 
 
    Placa base: 
      Tipo de procesador                                Mobile DualCore Intel Core 2 Duo P8400, 2250 MHz (8.5 x 265) 
      Nombre de la Placa Base                           Asus M50Vc Series Notebook 
      Chipset de la Placa Base                          Intel Cantiga PM45 
      Memoria del Sistema                               [ TRIAL VERSION ] 
      Tipo de BIOS                                      AMI (08/11/08) 
 
    Monitor: 
      Tarjeta gráfica                                   NVIDIA GeForce 9300M GS  (512 MB) 
      Tarjeta gráfica                                   NVIDIA GeForce 9300M GS  (512 MB) 
      Acelerador 3D                                     nVIDIA GeForce 9300M GS 
      Monitor                                           Chunghwa CLAA154WP05A   [15.4" LCD] 
 
    Multimedia: 
      Tarjeta de sonido                                 nVIDIA HDMI @ Intel 82801IB ICH9 - High Definition Audio Controller 
      Tarjeta de sonido                                 Realtek ALC663 @ Intel 82801IB ICH9 - High Definition Audio Controller 
 
    Almacenamiento: 
      Controlador IDE                                   Intel(R) ICH9M-E/M SATA AHCI Controller 
      Controlador IDE                                   Ricoh Memory Stick Controller 
      Controlador IDE                                   Ricoh xD-Picture Card Controller 
      Storage Controller                                Iniciador iSCSI de Microsoft 
      Disco duro                                        FUJITSU MHX2300BT  (300 GB, 4200 RPM, SATA) 
      Disco duro                                        SONY WALKMAN USB Device  (941 MB, USB) 
      Lector óptico                                     HL-DT-ST DVDRAM GSA-T50N 
      Estado de los discos duros SMART                  OK 
 
    Particiones: 
      C: (NTFS)                                         [ TRIAL VERSION ] 
      Tamaño total                                      [ TRIAL VERSION ] 
 
    Dispositivos de entrada: 
      Teclado                                           Keyboard Device Filter 
      Teclado                                           Teclado Microsoft eHome MCIR 
      Teclado                                           Teclado Microsoft eHome MCIR 109 
      Teclado                                           Teclas del Teclado de control remoto Microsoft eHome 
      Ratón                                             Mouse compatible con HID 
      Ratón                                             Mouse compatible con HID 
      Ratón                                             Synaptics PS/2 Port TouchPad 
 
    Red: 
      Dirección IP principal                            [ TRIAL VERSION ] 
       Dirección MAC principal                          00-16-EA-98-41-E4 
      Tarjeta de Red                                    Intel(R) WiFi Link 5100  (192. [ TRIAL VERSION ]) 
      Tarjeta de Red                                    Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) 
      Modem                                             Agere Systems HDA Modem 
 
    Dispositivos: 
      Impresora                                         Microsoft XPS Document Writer 
      Controlador FireWire                              Ricoh RL5C832 IEEE1394 Controller (PHY: Ricoh RL5C832) 
      Controlador infrarojo                             ITECIR Infrared Receiver (EC) 
      Controlador USB1                                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Controlador USB1                                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Controlador USB1                                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Controlador USB1                                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Controlador USB1                                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Controlador USB1                                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Controlador USB2                                  Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
      Controlador USB2                                  Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
      Dispositivos USB                                  AuthenTec Inc. AES1610 
      Dispositivos USB                                  BT-253 
      Dispositivos USB                                  Dispositivo compuesto USB 
      Dispositivos USB                                  Dispositivo de almacenamiento USB 
      Dispositivos USB                                  Dispositivo de interfaz humana USB 
      Dispositivos USB                                  USB2.0 1.3M UVC WebCam 
      Batería                                           Adaptador de CA de Microsoft 
      Batería                                           Batería con método de control compatible con ACPI de Microsoft 
 
    DMI: 
      DMI Distribuidor de la BIOS                       American Megatrends Inc. 
      DMI Versión de la BIOS                            207 
      DMI Fabricante del Sistema                        ASUSTeK Computer Inc. 
      DMI Nombre del Sistema                            M50Vc 
      DMI Versión del sistema                           1.0 
      DMI Número de serie del Sistema                   [ TRIAL VERSION ] 
      DMI UUID del Sistema                              [ TRIAL VERSION ] 
      DMI Fabricante de la Placa Base                   ASUSTeK Computer Inc. 
      DMI Nombre de la Placa Base                       M50Vc 
      DMI Versión de la Placa Base                      1.0 
      DMI Número de serie de la Placa Base              [ TRIAL VERSION ] 
      DMI Fabricante del chasis                         ASUSTeK Computer Inc. 
      DMI Versión del chasis                            1.0 
      DMI Número de serie del chasis                    [ TRIAL VERSION ] 
      DMI Identificador del chasis                      [ TRIAL VERSION ] 
      DMI Tipo de chasis                                Notebook 
 
 
--------[ DMI ]--------------------------------------------------------------------------------------------------------- 
 
  [ BIOS ] 
 
    Propiedades de la BIOS: 
      Vendedor                                          American Megatrends Inc. 
      Versión                                           207 
      Fecha de salida                                   08/11/2008 
      Tamaño                                            1024 KB 
      Dispositivos de arranque                          Floppy Disk, Hard Disk, CD-ROM 
      Funciones disponibles                             Flash BIOS, Shadow BIOS, Selectable Boot, EDD, BBS, Smart Battery 
      Standards soportados                              DMI, ACPI, ESCD, PnP 
      Posibilidades de expansión                        ISA, PCI, USB 
 
  [ Sistema ] 
 
    Propiedades del Sistema: 
      Fabricante                                        ASUSTeK Computer Inc. 
      Producto                                          M50Vc 
      Versión                                           1.0 
      Número de serie                                   [ TRIAL VERSION ] 
      Identificador único universal                     [ TRIAL VERSION ] 
      Tipo de arranque                                  Botón marcha/parada 
 
  [ Placa base ] 
 
    Propiedades de la Placa Base: 
      Fabricante                                        ASUSTeK Computer Inc. 
      Producto                                          M50Vc 
      Versión                                           1.0 
      Número de serie                                   [ TRIAL VERSION ] 
 
  [ Chasis ] 
 
    Propiedades del chasis: 
      Fabricante                                        ASUSTeK Computer Inc. 
      Versión                                           1.0 
      Número de serie                                   [ TRIAL VERSION ] 
      Etiqueta                                          [ TRIAL VERSION ] 
      Tipo de chasis                                    Notebook 
      Estado del arranque                               Seguro 
      Estado de la alimentación                         Seguro 
 
  [ Procesadores / Intel(R) Core(TM)2 Duo CPU P8400 @ 2.26GHz ] 
 
    Propiedades del procesador: 
      Fabricante                                        Intel 
      Versión                                           Intel(R) Core(TM)2 Duo CPU P8400 @ 2.26GHz 
      Número de serie                                   PSN12345678901234567 
      Etiqueta                                          PATN1234567890123456 
      Número del tipo de componentes                    PPN12345678901234567 
      Reloj externo                                     267 MHz 
      Velocidad de reloj máxima                         2266 MHz 
      Velocidad de reloj actual                         2266 MHz 
      Tipo                                              Central Processor 
      Voltaje                                           1.0 V 
      Estado                                            Activado 
      Actualizar                                        Socket 478 
      Identificación del socket                         Socket 478 
      Unidades HTT / CMP                                1 / 2 
 
  [ Cachés / L1-Cache ] 
 
    Propiedades del caché: 
      Tipo                                              Interna 
      Estado                                            Activado 
      Modo de operación                                 Write-Back 
      Asociatividad                                     8-way Set-Associative 
      Tamaño máximo                                     64 KB 
      Tamaño instalado                                  64 KB 
      Corrección de errores                             Single-bit ECC 
      Identificación del socket                         L1-Cache 
 
  [ Cachés / L1-Cache ] 
 
    Propiedades del caché: 
      Tipo                                              Interna 
      Estado                                            Activado 
      Modo de operación                                 Write-Back 
      Asociatividad                                     8-way Set-Associative 
      Tamaño máximo                                     64 KB 
      Tamaño instalado                                  64 KB 
      Corrección de errores                             Single-bit ECC 
      Identificación del socket                         L1-Cache 
 
  [ Cachés / L2-Cache ] 
 
    Propiedades del caché: 
      Tipo                                              Interna 
      Estado                                            Activado 
      Modo de operación                                 Write-Back 
      Tamaño máximo                                     3072 KB 
      Tamaño instalado                                  3072 KB 
      Corrección de errores                             Single-bit ECC 
      Identificación del socket                         L2-Cache 
 
  [ Periféricos de memoria / SODIMM0 ] 
 
    Propiedades del dispositivo de memoria: 
      Forma                                             SODIMM 
      Tipo                                              DDR2 
      Tipo detallado                                    Synchronous 
      Tamaño                                            2048 MB 
      Velocidad                                         800 MHz 
      Tamaño total                                      64 bits 
      Ancho de datos                                    64 bits 
      Emplazamiento del dispositivo                     SODIMM0 
      Número del Banco                                  BANK0 
      Fabricante                                        N/A 
      Número de serie                                   N/A 
      Etiqueta                                          N/A 
      Número del tipo de componentes                    N/A 
 
  [ Periféricos de memoria / SODIMM1 ] 
 
    Propiedades del dispositivo de memoria: 
      Forma                                             SODIMM 
      Tipo                                              DDR2 
      Tipo detallado                                    Synchronous 
      Tamaño                                            2048 MB 
      Velocidad                                         800 MHz 
      Tamaño total                                      64 bits 
      Ancho de datos                                    64 bits 
      Emplazamiento del dispositivo                     SODIMM1 
      Número del Banco                                  BANK1 
      Fabricante                                        N/A 
      Número de serie                                   N/A 
      Etiqueta                                          N/A 
      Número del tipo de componentes                    N/A 
 
  [ Slots del sistema / PEG ] 
 
    Propiedades del sistema de slot: 
      Identificador del slot                            PEG 
      Tipo                                              PCI-E x1 
      Uso                                               En uso 
      Ancho del Bus de datos                            x16 
      Longitud                                          Corto 
 
  [ Slots del sistema / PCIE1 ] 
 
    Propiedades del sistema de slot: 
      Identificador del slot                            PCIE1 
      Tipo                                              PCI-E x1 
      Uso                                               En uso 
      Ancho del Bus de datos                            64-bit 
      Longitud                                          Corto 
 
  [ Slots del sistema / PCIE2 ] 
 
    Propiedades del sistema de slot: 
      Identificador del slot                            PCIE2 
      Tipo                                              PCI-E x1 
      Uso                                               Vacío 
      Ancho del Bus de datos                            x1 
      Longitud                                          Corto 
 
  [ Slots del sistema / PCIE3 ] 
 
    Propiedades del sistema de slot: 
      Identificador del slot                            PCIE3 
      Tipo                                              PCI-E x1 
      Uso                                               Vacío 
      Ancho del Bus de datos                            x1 
      Longitud                                          Corto 
 
  [ Slots del sistema / PCIE4 ] 
 
    Propiedades del sistema de slot: 
      Identificador del slot                            PCIE4 
      Tipo                                              PCI-E x1 
      Uso                                               Vacío 
      Ancho del Bus de datos                            x1 
      Longitud                                          Corto 
 
  [ Conectores de puertos / LAN ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    Network Port 
      Diseño del conector interno                       J3401 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       LAN 
      Tipo de conector externo                          RJ-45 
 
  [ Conectores de puertos / VGA ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    Video Port 
      Diseño del conector interno                       J4501 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       VGA 
      Tipo de conector externo                          DB-15 pin female 
 
  [ Conectores de puertos / USB1 ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    USB 
      Diseño del conector interno                       J5202 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       USB1 
      Tipo de conector externo                          USB 
 
  [ Conectores de puertos / USB2 ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    USB 
      Diseño del conector interno                       J5202 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       USB2 
      Tipo de conector externo                          USB 
 
  [ Conectores de puertos / HDMI ] 
 
    Propiedades del conector del puerto: 
      Diseño del conector interno                       J4800 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       HDMI 
 
  [ Conectores de puertos / SATA 1 ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    SATA 
      Diseño del conector interno                       J5101 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       SATA 1 
      Tipo de conector externo                          SATA/SAS Plug Receptacle 
 
  [ Conectores de puertos / FlashCard ] 
 
    Propiedades del conector del puerto: 
      Diseño del conector interno                       J4202 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       FlashCard 
 
  [ Conectores de puertos / ExpressCard ] 
 
    Propiedades del conector del puerto: 
      Diseño del conector interno                       J4301 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       ExpressCard 
 
  [ Conectores de puertos / eSATA ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    SATA 
      Diseño del conector interno                       J6601 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       eSATA 
      Tipo de conector externo                          SATA/SAS Plug Receptacle 
 
  [ Conectores de puertos / Audio Out ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    Audio Port 
      Diseño del conector interno                       J3703 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       Audio Out 
      Tipo de conector externo                          Mini-jack (headphones) 
 
  [ Conectores de puertos / Mic In ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    Audio Port 
      Diseño del conector interno                       J3801 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       Mic In 
      Tipo de conector externo                          Mini-jack (headphones) 
 
  [ Conectores de puertos / USB3 ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    USB 
      Diseño del conector interno                       J5202 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       USB3 
      Tipo de conector externo                          USB 
 
  [ Conectores de puertos / 1394 ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    FireWire (IEEE P1394) 
      Diseño del conector interno                       J4203 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       1394 
      Tipo de conector externo                          1394 
 
  [ Conectores de puertos / USB4 ] 
 
    Propiedades del conector del puerto: 
      Tipo de puerto                                    USB 
      Diseño del conector interno                       J5202 
      Tipo de conector interno                          Ninguno 
      Diseño del conector externo                       USB4 
      Tipo de conector externo                          USB 
 
  [ Dispositivos integrados / Gfx Card ] 
 
    Propiedades del dispositivo integrado: 
      Descripción                                       Gfx Card 
      Tipo                                              Video 
      Estado                                            Activado 
 
  [ Dispositivos integrados / NIC ] 
 
    Propiedades del dispositivo integrado: 
      Descripción                                       NIC 
      Tipo                                              Ethernet 
      Estado                                            Activado 
 
  [ Dispositivos integrados / Audio Codec ] 
 
    Propiedades del dispositivo integrado: 
      Descripción                                       Audio Codec 
      Tipo                                              Sound 
      Estado                                            Activado 
 
  [ Dispositivos integrados / SATA Controller ] 
 
    Propiedades del dispositivo integrado: 
      Descripción                                       SATA Controller 
      Tipo                                              SATA Controller 
      Estado                                            Activado 
 
  [ Dispositivos integrados / 1394/FlashCardReader ] 
 
    Propiedades del dispositivo integrado: 
      Descripción                                       1394/FlashCardReader 
      Estado                                            Activado 
 
 
--------[ Overclock ]--------------------------------------------------------------------------------------------------- 
 
    Propiedades de la CPU: 
      Tipo de procesador                                Mobile DualCore Intel Core 2 Duo P8400 
      Alias de la CPU                                   Penryn-3M 
      Escalonamiento de la CPU                          C0/M0 
      Engineering Sample                                No 
      (CPUID) Nombre de la CPU                          Intel(R) Core(TM)2 Duo CPU P8400 @ 2.26GHz 
      (CPUID) Revisión                                  00010676h 
      CPU VID                                           1.0375 V 
 
    Velocidad del CPU: 
      Velocidad de reloj del procesador                 2310.7 MHz  (original: [ TRIAL VERSION ] MHz) 
      Multiplicador de la CPU                           8.5x 
      FSB de la CPU                                     271.8 MHz  (original: 266 MHz, overclock: 2%) 
 
    Caché del CPU: 
      Código de caché L1                                32 KB per core 
      Datos de caché L1                                 [ TRIAL VERSION ] 
      Caché L2                                          3 MB  (On-Die, ECC, ASC, Full-Speed) 
 
    Propiedades de la Placa Base: 
      Identificación de la Placa Base                   64-0100-000001-00101111-081108-Cantiga$M50V0206_BIOS DATE: 08/11/08 VER: 207 
      Nombre de la Placa Base                           Asus M50Vc Series Notebook 
 
    Propiedades del chipset: 
      Chipset de la Placa Base                          Intel Cantiga PM45 
      Tiempos de Memoria                                6-6-6-18  (CL-RCD-RP-RAS) 
 
    Propiedades de la BIOS: 
      Fecha de la BIOS del sistema                      08/11/08 
      Fecha de la BIOS de video                         06/18/08 
      DMI Versión de la BIOS                            207 
 
    Propiedades del procesador gráfico: 
      Tarjeta gráfica                                   nVIDIA GeForce 9300M GS (Asus) 
      Número de código                                  G98M  (PCI Express 2.0 x16 10DE / 06E9, Rev A1) 
      Velocidad de reloj (Geometric Domain)             182 MHz 
      Velocidad de reloj (Shader Domain)                364 MHz 
      Reloj de la memoria                               100 MHz 
 
 
--------[ Gestión de la energía ]--------------------------------------------------------------------------------------- 
 
    Propiedades de la Gestión de Ahorro de Energía: 
      Fuente de potencia actual                         Línea AC 
      Estado de la batería                              99 % (Nivel alto) 
      Tiempo de uso de batería llena                    Desconocido 
      Tiempo de uso restante                            Desconocido 
 
    Battery Properties: 
      Nombre del dispositivo                            M50--24 
      Fabricante                                        ASUSTEK 
      Unique ID                                         ASUSTEKM50--24 
      Battery Type                                      Rechargeable Li-Ion 
      Designed Capacity                                 51260 mWh 
      Fully Charged Capacity                            48004 mWh 
      Current Capacity                                  47652 mWh  (99 %) 
      Voltaje                                           12466 mV 
      Wear Level                                        6 % 
      Power State                                       Línea AC 
 
 
--------[ Portable Computer ]------------------------------------------------------------------------------------------- 
 
    Centrino (Carmel) Platform Compliancy: 
      Procesador: Intel Pentium M (Banias/Dothan)       No  (Mobile DualCore Intel Core 2 Duo P8400) 
      Chipset: Intel i855GM/PM                          No  (Intel Cantiga PM45) 
      WLAN: Intel PRO/Wireless                          No 
      Sistema: Centrino Compliant                       No 
 
    Centrino (Sonoma) Platform Compliancy: 
      Procesador: Intel Pentium M (Dothan)              No  (Mobile DualCore Intel Core 2 Duo P8400) 
      Chipset: Intel i915GM/PM                          No  (Intel Cantiga PM45) 
      WLAN: Intel PRO/Wireless                          No 
      Sistema: Centrino Compliant                       No 
 
    Centrino (Napa) Platform Compliancy: 
      Procesador: Intel Core (Yonah) / Core 2 (Merom)   No  (Mobile DualCore Intel Core 2 Duo P8400) 
      Chipset: Intel i945GM/PM                          No  (Intel Cantiga PM45) 
      WLAN: Intel PRO/Wireless 3945ABG                  No 
      Sistema: Centrino Compliant                       No 
 
    Centrino (Santa Rosa) Platform Compliancy: 
      Procesador: Intel Core 2 (Merom/Penryn)           Sí  (Mobile DualCore Intel Core 2 Duo P8400) 
      Chipset: Intel GM965/PM965                        No  (Intel Cantiga PM45) 
      WLAN: Intel Wireless WiFi Link 4965AGN            No 
      Sistema: Centrino Compliant                       No 
 
    Centrino (Montevina) Platform Compliancy: 
      Procesador: Intel Core 2 (Penryn)                 Sí  (Mobile DualCore Intel Core 2 Duo P8400) 
      Chipset: Intel GM45/GS45/PM45                     Sí  (Intel Cantiga PM45) 
      WLAN: Intel Shirley Peak                          Sí 
      Sistema: Centrino Compliant                       Sí 
 
    Mobile PC Physical Info: 
      Fabricante                                        Asus 
      System Type                                       [ TRIAL VERSION ] 
      Tipo de procesador                                Intel Core 2 Duo 
      Chipset de la Placa Base                          Intel PM45 
      Memory Sockets                                    2 DDR2 
      Max. Memory Size                                  4 GB 
      Hard Disk Type                                    SATA 
      LCD Size                                          [ TRIAL VERSION ] 
      GPU Type                                          nVIDIA GeForce 9300M GS 
      Tarjeta de Red                                    Gigabit 
      WLAN Network Adapter                              802.11a/b/g/n 
      Bluetooth Adapter                                 Optional 
      USB Ports                                         4 USB 2.0 
      FireWire Ports                                    1 
      Video Outputs                                     DSub, TV, HDMI 
      Battery Type                                      53 / 80 Wh Li-Ion 
      Dimensiones físicas                               375 x 269 x 44 mm 
      Peso máximo                                       [ TRIAL VERSION ] 
 
 
--------[ Sensor ]------------------------------------------------------------------------------------------------------ 
 
    Propiedades del sensor: 
      Tipo de sensor                                    CPU, HDD, Asus NB ACPI 
      Tipo de Sensor GPU                                Diode  (NV-Diode) 
 
    Temperaturas: 
      Procesador                                        58 °C  (136 °F) 
      CPU Nº 1 / núcleo Nº 1                            48 °C  (118 °F) 
      CPU Nº 1 / núcleo Nº 2                            49 °C  (120 °F) 
      GPU Diode                                         54 °C  (129 °F) 
      FUJITSU MHX2300BT                                 [ TRIAL VERSION ] 
 
    Valores de voltaje: 
      Núcleo CPU                                        1.04 V 
 
 
--------[ Procesador ]-------------------------------------------------------------------------------------------------- 
 
    Propiedades de la CPU: 
      Tipo de procesador                                Mobile DualCore Intel Core 2 Duo P8400, 2250 MHz (8.5 x 265) 
      Alias de la CPU                                   Penryn-3M 
      Escalonamiento de la CPU                          C0/M0 
      Juego de instrucciones                            x86, x86-64, MMX, SSE, SSE2, SSE3, SSSE3, SSE4.1 
      Velocidad de reloj original                       [ TRIAL VERSION ] 
      Multiplicador de la CPU Min / Max                 6x / 9x 
      Engineering Sample                                No 
      Código de caché L1                                32 KB per core 
      Datos de caché L1                                 [ TRIAL VERSION ] 
      Caché L2                                          3 MB  (On-Die, ECC, ASC, Full-Speed) 
 
    Multi CPU: 
      Identificación de la Placa Base                   ASUSTeK Montevina 
      CPU #1                                            Intel(R) Core(TM)2 Duo CPU P8400 @ 2.26GHz, 2261 MHz 
      CPU #2                                            Intel(R) Core(TM)2 Duo CPU P8400 @ 2.26GHz, 2261 MHz 
 
    Fabricante del procesador: 
      Nombre de la empresa                              Intel Corporation 
      Información sobre el producto                     http://www.intel.com/products/processor 
 
    Uso de la CPU: 
      CPU Nº 1 / núcleo Nº 1                            0 % 
      CPU Nº 1 / núcleo Nº 2                            0 % 
 
 
--------[ CPUID ]------------------------------------------------------------------------------------------------------- 
 
    (CPUID) Propiedades: 
      (CPUID) Fabricante                                GenuineIntel 
      (CPUID) Nombre de la CPU                          Intel(R) Core(TM)2 Duo CPU P8400 @ 2.26GHz 
      (CPUID) Revisión                                  00010676h 
      (IA) Identificador de la marca                    00h  (Desconocido) 
      Identificador de la plataforma                    20h / MC 80h  (Socket 479) 
      Microcode Update Revision                         60C 
      Unidades HTT / CMP                                0 / 2 
      Tjmax Temperature                                 105 °C  (221 °F) 
 
    Juego de instrucciones: 
      Extensión de 64 bitsx86 (AMD64, Intel64)          Soportado 
      AMD 3DNow!                                        No soportado 
      AMD 3DNow! Professional                           No soportado 
      AMD 3DNowPrefetch                                 No soportado 
      AMD Enhanced 3DNow!                               No soportado 
      AMD Extended MMX                                  No soportado 
      AMD MisAligned SSE                                No soportado 
      AMD SSE4A                                         No soportado 
      AMD SSE5                                          No soportado 
      Cyrix Extended MMX                                No soportado 
      IA-64                                             No soportado 
      IA MMX                                            Soportado 
      IA SSE                                            Soportado 
      IA SSE 2                                          Soportado 
      IA SSE 3                                          Soportado 
      IA Supplemental SSE 3                             Soportado 
      IA SSE 4.1                                        Soportado 
      IA SSE 4.2                                        No soportado 
      IA AVX                                            No soportado 
      IA FMA                                            No soportado 
      IA AES Extensions                                 No soportado 
      VIA Alternate Instruction Set                     No soportado 
      Instrucción CLFLUSH                               Soportado 
      Instrucción CMPXCHG8B                             Soportado 
      Instrucción CMPXCHG16B                            Soportado 
      Instrucción Conditional Move                      Soportado 
      Instrucción LZCNT                                 No soportado 
      Instrucción MONITOR / MWAIT                       Soportado 
      Instrucción MOVBE                                 No soportado 
      Instrucción PCLMULQDQ                             No soportado 
      Instrucción POPCNT                                No soportado 
      Instrucción RDTSCP                                No soportado 
      Instrucción SYSCALL / SYSRET                      No soportado 
      Instrucción SYSENTER / SYSEXIT                    Soportado 
      Instrucción VIA FEMMS                             No soportado 
 
    Funciones de seguridad: 
      Advanced Cryptography Engine (ACE)                No soportado 
      Advanced Cryptography Engine 2 (ACE2)             No soportado 
      Prevención de ejecución de datos (DEP, NX, EDB)   Soportado 
      Hardware Random Number Generator (RNG)            No soportado 
      PadLock Hash Engine (PHE)                         No soportado 
      PadLock Montgomery Multiplier (PMM)               No soportado 
      Processor Serial Number (PSN)                     No soportado 
 
    Funciones de la gestión de ahorro de energía: 
      Automatic Clock Control                           Soportado 
      Digital Thermometer                               Soportado 
      Dynamic FSB Frequency Switching                   Soportado, Activado 
      Enhanced Halt State (C1E)                         Soportado, Desactivado 
      Enhanced SpeedStep Technology (EIST, ESS)         Soportado, Activado 
      Frequency ID Control                              No soportado 
      Hardware P-State Control                          No soportado 
      LongRun                                           No soportado 
      LongRun Table Interface                           No soportado 
      PowerSaver 1.0                                    No soportado 
      PowerSaver 2.0                                    No soportado 
      PowerSaver 3.0                                    No soportado 
      Processor Duty Cycle Control                      Soportado 
      Software Thermal Control                          No soportado 
      Temperature Sensing Diode                         No soportado 
      Thermal Monitor 1                                 Soportado 
      Thermal Monitor 2                                 Soportado 
      Thermal Monitoring                                No soportado 
      Thermal Trip                                      No soportado 
      Turbo Mode                                        No soportado 
      Voltage ID Control                                No soportado 
 
    (CPUID) Funciones: 
      1 GB Page Size                                    No soportado 
      36-bit Page Size Extension                        Soportado 
      Address Region Registers (ARR)                    No soportado 
      CPL Qualified Debug Store                         Soportado 
      Debug Trace Store                                 Soportado 
      Debugging Extension                               Soportado 
      Direct Cache Access                               No soportado 
      Dynamic Acceleration Technology (IDA)             Soportado, Activado 
      Fast Save & Restore                               Soportado 
      Hyper-Threading Technology (HTT)                  No soportado 
      Invariant Time Stamp Counter                      Soportado 
      L1 Context ID                                     No soportado 
      Local APIC On Chip                                Soportado 
      Machine Check Architecture (MCA)                  Soportado 
      Machine Check Exception (MCE)                     Soportado 
      Memory Configuration Registers (MCR)              No soportado 
      Memory Type Range Registers (MTRR)                Soportado 
      Model Specific Registers (MSR)                    Soportado 
      Nested Paging                                     No soportado 
      Page Attribute Table (PAT)                        Soportado 
      Page Global Extension                             Soportado 
      Page Size Extension (PSE)                         Soportado 
      Pending Break Event                               Soportado 
      Physical Address Extension (PAE)                  Soportado 
      Safer Mode Extensions (SMX)                       Soportado 
      Secure Virtual Machine Extensions (Pacifica)      No soportado 
      Self-Snoop                                        Soportado 
      Time Stamp Counter (TSC)                          Soportado 
      Virtual Machine Extensions (Vanderpool)           Soportado 
      Virtual Mode Extension                            Soportado 
      x2APIC                                            No soportado 
      XSAVE / XRSTOR Extended States                    No soportado 
 
    CPUID Registers (CPU #1): 
      CPUID 00000000                                    0000000A-756E6547-6C65746E-49656E69 
      CPUID 00000001                                    00010676-00020800-0008E3FD-BFEBFBFF 
      CPUID 00000002                                    05B0B101-005657F0-00000000-2CB43048 
      CPUID 00000003                                    00000000-00000000-00000000-00000000 
      CPUID 00000004                                    04000121-01C0003F-0000003F-00000001 
      CPUID 00000004                                    04000122-01C0003F-0000003F-00000001 
      CPUID 00000004                                    04004143-02C0003F-00000FFF-00000001 
      CPUID 00000005                                    00000040-00000040-00000003-03122220 
      CPUID 00000006                                    00000001-00000002-00000001-00000000 
      CPUID 00000007                                    00000000-00000000-00000000-00000000 
      CPUID 00000008                                    00000400-00000000-00000000-00000000 
      CPUID 00000009                                    00000000-00000000-00000000-00000000 
      CPUID 0000000A                                    07280202-00000000-00000000-00000503 
      CPUID 80000000                                    80000008-00000000-00000000-00000000 
      CPUID 80000001                                    00000000-00000000-00000001-20100000 
      CPUID 80000002                                    65746E49-2952286C-726F4320-4D542865 
      CPUID 80000003                                    44203229-43206F75-20205550-50202020 
      CPUID 80000004                                    30303438-20402020-36322E32-007A4847 
      CPUID 80000005                                    00000000-00000000-00000000-00000000 
      CPUID 80000006                                    00000000-00000000-0C006040-00000000 
      CPUID 80000007                                    00000000-00000000-00000000-00000000 
      CPUID 80000008                                    00003024-00000000-00000000-00000000 
 
    CPUID Registers (CPU #2): 
      CPUID 00000000                                    0000000A-756E6547-6C65746E-49656E69 
      CPUID 00000001                                    00010676-01020800-0008E3FD-BFEBFBFF 
      CPUID 00000002                                    05B0B101-005657F0-00000000-2CB43048 
      CPUID 00000003                                    00000000-00000000-00000000-00000000 
      CPUID 00000004                                    04000121-01C0003F-0000003F-00000001 
      CPUID 00000004                                    04000122-01C0003F-0000003F-00000001 
      CPUID 00000004                                    04004143-02C0003F-00000FFF-00000001 
      CPUID 00000005                                    00000040-00000040-00000003-03122220 
      CPUID 00000006                                    00000001-00000002-00000001-00000000 
      CPUID 00000007                                    00000000-00000000-00000000-00000000 
      CPUID 00000008                                    00000400-00000000-00000000-00000000 
      CPUID 00000009                                    00000000-00000000-00000000-00000000 
      CPUID 0000000A                                    07280202-00000000-00000000-00000503 
      CPUID 80000000                                    80000008-00000000-00000000-00000000 
      CPUID 80000001                                    00000000-00000000-00000001-20100000 
      CPUID 80000002                                    65746E49-2952286C-726F4320-4D542865 
      CPUID 80000003                                    44203229-43206F75-20205550-50202020 
      CPUID 80000004                                    30303438-20402020-36322E32-007A4847 
      CPUID 80000005                                    00000000-00000000-00000000-00000000 
      CPUID 80000006                                    00000000-00000000-0C006040-00000000 
      CPUID 80000007                                    00000000-00000000-00000000-00000000 
      CPUID 80000008                                    00003024-00000000-00000000-00000000 
 
    MSR Registers: 
      MSR 00000017                                      001C-0000-B9F4-C81A [PlatID = 7] 
      MSR 0000002A                                      0000-0000-4248-0800 
      MSR 0000008B                                      0000-060C-0000-0000 
      MSR 000000CD                                      0000-0000-0000-01E0 
      MSR 000000CE                                      8017-0923-4345-060F 
      MSR 000000E7                                      0000-00F0-D41F-7EA4 
      MSR 000000E8                                      0000-0000-701B-D21B 
      MSR 000000EE                                      0000-0000-9EB9-1000 
      MSR 0000011E                                      0000-0000-7470-2119 
      MSR 00000198                                      0617-0923-0600-0923 
      MSR 00000199                                      0000-0000-0000-0923 
      MSR 0000019A                                      0000-0000-0000-0002 
      MSR 0000019B                                      0000-0000-00E4-9900 
      MSR 0000019C                                      0000-0000-8834-0100 
      MSR 0000019D                                      0000-0000-0000-0617 
      MSR 000001A0                                      0000-0013-6497-2489 
 
 
--------[ Placa base ]-------------------------------------------------------------------------------------------------- 
 
    Propiedades de la Placa Base: 
      Identificación de la Placa Base                   64-0100-000001-00101111-081108-Cantiga$M50V0206_BIOS DATE: 08/11/08 VER: 207 
      Nombre de la Placa Base                           Asus M50Vc Series Notebook 
 
    Propiedades del Bus principal: 
      Tipo de Bus                                       Intel AGTL+ 
      Ancho de bus                                      64 bits 
      Reloj real                                        265 MHz (QDR) 
      Reloj efectivo                                    1059 MHz 
      Banda pasante                                     8471 MB/s 
 
    Propiedades de la memoria del Bus: 
      Tipo de Bus                                       Dual DDR2 SDRAM 
      Ancho de bus                                      128 bits 
 
    Propiedades del chipset del Bus: 
      Tipo de Bus                                       Intel Direct Media Interface 
 
    Fabricante de la Placa Base: 
      Nombre de la empresa                              ASUSTeK Computer Inc. 
      Información sobre el producto                     http://www.asus.com/products.aspx?l1=3 
      Descarga de la BIOS                               http://support.asus.com/download/download.aspx?SLanguage=en-us 
 
 
--------[ Memoria ]----------------------------------------------------------------------------------------------------- 
 
    Memoria física: 
      Total                                             [ TRIAL VERSION ] 
      Usada                                             [ TRIAL VERSION ] 
      Disponible                                        1891 MB 
      Uso                                               [ TRIAL VERSION ] 
 
    Archivo de intercambio: 
      Total                                             6341 MB 
      Usada                                             1323 MB 
      Disponible                                        5017 MB 
      Uso                                               21 % 
 
    Memoria virtual: 
      Total                                             9411 MB 
      Usada                                             2502 MB 
      Disponible                                        6908 MB 
      Uso                                               27 % 
 
    Paging File: 
      Paging File                                       C:\pagefile.sys 
      Current Size                                      3370 MB 
      Current / Peak Usage                              55 MB / 63 MB 
      Uso                                               2 % 
 
    Physical Address Extension (PAE): 
      Soportado por el sistema operativo                Sí 
      Soportado por la CPU                              Sí 
      Activo                                            Sí 
 
 
--------[ Chipset ]----------------------------------------------------------------------------------------------------- 
 
  [ Puente Norte: Intel Cantiga PM45 ] 
 
    Propiedades del puente Norte: 
      Puente Norte                                      Intel Cantiga PM45 
      Intel Platform                                    Montevina 
      Supported FSB Speeds                              FSB533, FSB667, FSB800 
      Maximum Memory Amount                             8 GB 
      Revisión / Stepping                               07 / B3 
      Forma del componente                              1329 Pin FC-BGA 
      Tamaño del componente                             3.4 cm x 3.4 cm 
      voltaje del núcleo                                1.05 V 
      In-Order Queue Depth                              12 
 
    Controlador de memoria: 
      Tipo                                              Dual Channel  (128 bits) 
      Modo Activo                                       Dual Channel  (128 bits) 
 
    Tiempos de Memoria: 
      CAS Latency (CL)                                  6T 
      RAS To CAS Delay (tRCD)                           6T 
      RAS Precharge (tRP)                               6T 
      RAS Active Time (tRAS)                            18T 
      Row Refresh Cycle Time (tRFC)                     51T 
      RAS To RAS Delay (tRRD)                           3T 
      Read To Precharge Delay (tRTP)                    5T 
      Four Activate Window Delay (tFAW)                 15T 
      Write CAS Latency (tWCL)                          5T 
      Refresh Period (tREF)                             7.8 us 
 
    Corrección de errores: 
      ECC                                               No soportado 
      ChipKill ECC                                      No soportado 
      RAID                                              No soportado 
      ECC Scrubbing                                     No soportado 
 
    Slots de memoria: 
      Slot DRAM nº1                                     2 GB  (DDR2 SDRAM) 
      Slot DRAM nº2                                     2 GB  (DDR2 SDRAM) 
 
    Controlador PCI Express: 
      PCI-E 1.0 x16 port #2                             En uso @ x1  (nVIDIA GeForce 9300M GS (Asus) Video Adapter) 
 
    Fabricante del chipset: 
      Nombre de la empresa                              Intel Corporation 
      Información sobre el producto                     http://www.intel.com/products/chipsets 
      Descargar el controlador                          http://support.intel.com/support/chipsets 
      Driver Update                                     http://driveragent.com?ref=59 
 
  [ Puente Sur: [ TRIAL VERSION ] ] 
 
    Propiedades del puente Sur: 
      Puente Sur                                        [ TRIAL VERSION ] 
      Intel Platform                                    Montevina 
      Revisión                                          93 
      Forma del componente                              676 Pin mBGA 
      Tamaño del componente                             3.1 cm x 3.1 cm 
      voltaje del núcleo                                1.05 V 
 
    High Definition Audio: 
      Nombre del Codec                                  Realtek ALC663 
      Identificación del Codec                          10EC0663h / 10431893h 
      Codec Revision                                    00100001h 
      Codec Type                                        Audio 
      Supported Sound Formats                           44 kHz, 48 kHz, 96 kHz, 192 kHz, 16 bits, 20 bits, 24 bits 
 
    High Definition Audio: 
      Nombre del Codec                                  Agere Si3054 
      Identificación del Codec                          11C11040h / 10431636h 
      Codec Revision                                    00100200h 
      Codec Type                                        Modem 
 
    High Definition Audio: 
      Nombre del Codec                                  nVIDIA HDMI 
      Identificación del Codec                          10DE0003h / 10DE0101h 
      Codec Revision                                    00100000h 
      Codec Type                                        Audio 
 
    Controlador PCI Express: 
      PCI-E 1.0 x1 port #1                              Vacío 
      PCI-E 1.0 x1 port #2                              En uso @ x1  (Intel Shirley Peak (Shiloh) 1x2 MC Wireless WiFi Adapter) 
      PCI-E 1.0 x1 port #3                              Vacío 
      PCI-E 1.0 x1 port #4                              Vacío 
      PCI-E 1.0 x1 port #5                              Vacío 
      PCI-E 1.0 x1 port #6                              En uso @ x1  (Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter) 
 
    Fabricante del chipset: 
      Nombre de la empresa                              Intel Corporation 
      Información sobre el producto                     http://www.intel.com/products/chipsets 
      Descargar el controlador                          http://support.intel.com/support/chipsets 
      Driver Update                                     http://driveragent.com?ref=59 
 
 
--------[ BIOS ]-------------------------------------------------------------------------------------------------------- 
 
    Propiedades de la BIOS: 
      Tipo de BIOS                                      AMI 
      BIOS Version                                      207 
      Fecha de la BIOS del sistema                      08/11/08 
      Fecha de la BIOS de video                         06/18/08 
 
    Fabricante de la BIOS: 
      Nombre de la empresa                              American Megatrends Inc. 
      Información sobre el producto                     http://www.ami.com/amibios 
      Actualizaciones del BIOS                          http://www.esupport.com/biosagent/index.cfm?refererid=40 
 
 
--------[ ACPI ]-------------------------------------------------------------------------------------------------------- 
 
  [ APIC: Multiple APIC Description Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    APIC 
      Table Description                                 Multiple APIC Description Table 
      Memory Address                                    BFF80390h 
      Table Length                                      92 bytes 
      OEM ID                                            081108 
      OEM Table ID                                      APIC2148 
      Creator ID                                        MSFT 
 
  [ ATKG: Unknown ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    ATKG 
      Table Description                                 Desconocido 
      Memory Address                                    BFF8EAC0h 
      Table Length                                      32804 bytes 
      OEM ID                                            022008 
      OEM Table ID                                      OEMATKG 
      Creator ID                                        MSFT 
 
  [ BOOT: Simple Boot Flag Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    BOOT 
      Table Description                                 Simple Boot Flag Table 
      Memory Address                                    BFF805F0h 
      Table Length                                      40 bytes 
      OEM ID                                            081108 
      OEM Table ID                                      BOOT2148 
      Creator ID                                        MSFT 
 
  [ DBGP: Debug Port Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    DBGP 
      Table Description                                 Debug Port Table 
      Memory Address                                    BFF803F0h 
      Table Length                                      52 bytes 
      OEM ID                                            081108 
      OEM Table ID                                      DBGP2148 
      Creator ID                                        MSFT 
 
  [ DSDT: Differentiated System Description Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    DSDT 
      Table Description                                 Differentiated System Description Table 
      Memory Address                                    BFF80680h 
      Table Length                                      48672 bytes 
      OEM ID                                            M50V0 
      OEM Table ID                                      M50V0206 
      Creator ID                                        INTL 
 
  [ ECDT: Embedded Controller Boot Resources Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    ECDT 
      Table Description                                 Embedded Controller Boot Resources Table 
      Memory Address                                    BFF80620h 
      Table Length                                      84 bytes 
      OEM ID                                            081108 
      OEM Table ID                                      OEMECDT 
      Creator ID                                        MSFT 
 
  [ FACP: Fixed ACPI Description Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    FACP 
      Table Description                                 Fixed ACPI Description Table 
      Memory Address                                    BFF80200h 
      Table Length                                      132 bytes 
      OEM ID                                            081108 
      OEM Table ID                                      FACP2148 
      Creator ID                                        MSFT 
      SMI Command Port                                  000000B2h 
      PM Timer                                          00000808h 
 
  [ FACS: Firmware ACPI Control Structure ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    FACS 
      Table Description                                 Firmware ACPI Control Structure 
      Memory Address                                    BFF8E800h 
      Table Length                                      64 bytes 
 
  [ HPET: IA-PC High Precision Event Timer Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    HPET 
      Table Description                                 IA-PC High Precision Event Timer Table 
      Memory Address                                    BFF8C4A0h 
      Table Length                                      56 bytes 
      OEM ID                                            081108 
      OEM Table ID                                      OEMHPET 
      Creator ID                                        MSFT 
 
  [ MCFG: Memory Mapped Configuration Space Base Address Description Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    MCFG 
      Table Description                                 Memory Mapped Configuration Space Base Address Description Table 
      Memory Address                                    BFF80430h 
      Table Length                                      60 bytes 
      OEM ID                                            081108 
      OEM Table ID                                      OEMMCFG 
      Creator ID                                        MSFT 
 
  [ OEMB: OEM Specific Information Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    OEMB 
      Table Description                                 OEM Specific Information Table 
      Memory Address                                    BFF8E840h 
      Table Length                                      113 bytes 
      OEM ID                                            081108 
      OEM Table ID                                      OEMB2148 
      Creator ID                                        MSFT 
 
  [ RSD PTR: Root System Description Pointer ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    RSD PTR 
      Table Description                                 Root System Description Pointer 
      Memory Address                                    000F9370h 
      Table Length                                      36 bytes 
      OEM ID                                            ACPIAM 
 
  [ RSDT: Root System Description Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    RSDT 
      Table Description                                 Root System Description Table 
      Memory Address                                    BFF80000h 
      Table Length                                      80 bytes 
      OEM ID                                            _ASUS_ 
      OEM Table ID                                      Notebook 
      Creator ID                                        MSFT 
 
  [ SLIC: Software Licensing Description Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    SLIC 
      Table Description                                 Software Licensing Description Table 
      Memory Address                                    BFF80470h 
      Table Length                                      374 bytes 
      OEM ID                                            _ASUS_ 
      OEM Table ID                                      Notebook 
      Creator ID                                        MSFT 
 
  [ SSDT: Secondary System Description Table ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    SSDT 
      Table Description                                 Secondary System Description Table 
      Memory Address                                    BFF97610h 
      Table Length                                      1264 bytes 
      OEM ID                                            PmRef 
      OEM Table ID                                      CpuPm 
      Creator ID                                        INTL 
 
  [ XSDT: Extended System Description Table  (Emulated) ] 
 
    ACPI Table Properties: 
      ACPI Signature                                    XSDT 
      Table Description                                 Extended System Description Table 
      Memory Address                                    Emulated 
      Table Length                                      124 bytes 
      OEM ID                                            _ASUS_ 
      OEM Table ID                                      Notebook 
      Creator ID                                        MSFT 
 
 
--------[ Video Windows ]----------------------------------------------------------------------------------------------- 
 
  [ NVIDIA GeForce 9300M GS ] 
 
    Propiedades de la tarjeta gráfica: 
      Descripción del dispositivo                       NVIDIA GeForce 9300M GS 
      identificación de la tarjeta                      GeForce 9300M GS 
      Identificación de la BIOS                         Version 62.98.39.0.18 
      Tipo de circuito                                  GeForce 9300M GS 
      Tipo de DAC                                       Integrated RAMDAC 
      Fecha del controlador                             08/06/2008 
      Versión del controlador                           7.15.11.7597 - nVIDIA ForceWare 175.97 
      Proveedor del controlador                         NVIDIA 
      Tamaño de la memoria                              512 MB 
 
    Controladores instalados: 
      nvd3dum                                           7.15.11.7597 - nVIDIA ForceWare 175.97 
      nvwgf2um                                          7.15.11.7597 
 
    Fabricante de la tarjeta gráfica: 
      Nombre de la empresa                              NVIDIA Corporation 
      Información sobre el producto                     http://www.nvidia.com/page/products.html 
      Descargar el controlador                          http://www.nvidia.com/content/drivers/drivers.asp 
      Driver Update                                     http://driveragent.com?ref=59 
 
  [ NVIDIA GeForce 9300M GS ] 
 
    Propiedades de la tarjeta gráfica: 
      Descripción del dispositivo                       NVIDIA GeForce 9300M GS 
      identificación de la tarjeta                      GeForce 9300M GS 
      Identificación de la BIOS                         Version 62.98.39.0.18 
      Tipo de circuito                                  GeForce 9300M GS 
      Tipo de DAC                                       Integrated RAMDAC 
      Fecha del controlador                             08/06/2008 
      Versión del controlador                           7.15.11.7597 - nVIDIA ForceWare 175.97 
      Proveedor del controlador                         NVIDIA 
      Tamaño de la memoria                              512 MB 
 
    Controladores instalados: 
      nvd3dum                                           7.15.11.7597 - nVIDIA ForceWare 175.97 
      nvwgf2um                                          7.15.11.7597 
 
    Fabricante de la tarjeta gráfica: 
      Nombre de la empresa                              NVIDIA Corporation 
      Información sobre el producto                     http://www.nvidia.com/page/products.html 
      Descargar el controlador                          http://www.nvidia.com/content/drivers/drivers.asp 
      Driver Update                                     http://driveragent.com?ref=59 
 
 
--------[ Video PCI/AGP ]----------------------------------------------------------------------------------------------- 
 
    nVIDIA GeForce 9300M GS                                                           Tarjeta gráfica 
    nVIDIA GeForce 9300M GS                                                           Acelerador 3D 
 
 
--------[ GPU ]--------------------------------------------------------------------------------------------------------- 
 
  [ PCI Express 2.0 x16: nVIDIA GeForce 9300M GS (Asus) ] 
 
    Propiedades del procesador gráfico: 
      Tarjeta gráfica                                   nVIDIA GeForce 9300M GS (Asus) 
      Número de código                                  G98M 
      Dispositivos PCI                                  10DE-06E9 / 1043-19B2  (Rev A1) 
      Tecnología utilizada                              65 nm 
      Tipo de Bus                                       PCI Express 2.0 x16 @ x1 
      Tamaño de la memoria                              512 MB  (TurboCache: 1792 MB) 
      Velocidad de reloj (Geometric Domain)             182 MHz 
      Velocidad de reloj (Shader Domain)                364 MHz 
      Reloj RAMDAC                                      400 MHz 
      Pipelines Pixel                                   4 
      Pipeline TMU Per                                  1 
      Unified Shaders                                   16  (v4.0) 
      Soporte de Hardware DirectX                       DirectX v10 
      Pixel Fillrate                                    728 MPixel/s 
      Texel Fillrate                                    [ TRIAL VERSION ] 
 
    Propiedades de la memoria del Bus: 
      Tipo de Bus                                       DDR2 
      Ancho de bus                                      64 bits 
      Reloj real                                        100 MHz (DDR) 
      Reloj efectivo                                    200 MHz 
      Banda pasante                                     [ TRIAL VERSION ] 
 
    nVIDIA ForceWare Clocks: 
      Level #1                                          GPU: 169 MHz, Shader: 338 MHz, Memoria: 100 MHz 
      Level #2                                          GPU: 275 MHz, Shader: 550 MHz, Memoria: 250 MHz 
      Level #3                                          GPU: 500 MHz, Shader: 1000 MHz, Memoria: 400 MHz 
      Level #4                                          GPU: 580 MHz, Shader: 1450 MHz, Memoria: 400 MHz 
 
    Fabricante del procesador gráfico: 
      Nombre de la empresa                              NVIDIA Corporation 
      Información sobre el producto                     http://www.nvidia.com/page/products.html 
      Descargar el controlador                          http://www.nvidia.com/content/drivers/drivers.asp 
      Driver Update                                     http://driveragent.com?ref=59 
 
    nVIDIA GPU Registers: 
      nv-000000                                         298480A2 
      nv-0010F0                                         00000000 
      nv-001218                                         00000000 
      nv-001540                                         F1010001 
      nv-0015F4                                         00000000 
      nv-0015F8                                         00000000 
      nv-0015FC                                         00000000 
      nv-001600                                         00000000 
      nv-001850                                         00000000 
      nv-004000                                         00000000 
      nv-004004                                         00000000 
      nv-004008                                         10082200 
      nv-00400C                                         00002504 
      nv-004018                                         00000000 
      nv-00401C                                         00000000 
      nv-004020                                         00010000 
      nv-004024                                         00000C01 
      nv-004028                                         80120000 
      nv-00402C                                         00001B04 
      nv-00C040                                         2E80D0A3 
      nv-00E114                                         00000001 
      nv-00E118                                         00000000 
      nv-00E11C                                         00000001 
      nv-00E120                                         00000000 
      nv-020008                                         C0083753 
      nv-020014                                         FE500389 
      nv-020400                                         00000036 
      nv-100000                                         00000042 
      nv-100200                                         00000800 
      nv-10020C                                         20000000 
      nv-100214                                         00000003 
      nv-100474                                         00000000 
      nv-100714                                         00000101 
      nv-100914                                         00000000 
      nv-101000                                         8F44A400 
 
 
--------[ Monitor ]----------------------------------------------------------------------------------------------------- 
 
  [ Chunghwa CLAA154WP05A  ] 
 
    Propiedades del monitor: 
      Nombre del monitor                                Chunghwa CLAA154WP05A  
      Identificación del monitor                        CPT1465 
      Fabricante                                        CLAA154WP05A  
      Tipo de monitor                                   15.4" LCD (WXGA+) 
      Fecha de fabricación                              Semana 24 / 2008 
      Número de serie                                   Ninguno 
      Tamaño de visión máximo                           33 cm x 21 cm (15.4") 
      Ratio de aspecto de la imagen                     16:10 
      Resolución máxima                                 1440 x 900 
      Gamma                                             2.20 
      Gestión del modo DPMS                             Ninguno 
 
 
--------[ Escritorio ]-------------------------------------------------------------------------------------------------- 
 
    Propiedades del Escritorio: 
      Tecnología utilizada                              Mostrar Raster 
      Resolución                                        1440 x 900 
      Profundidad de colores                            32 bits 
      Planos de color                                   1 
      Resolución de las fuentes                         96 dpi 
      Altura/longitud en píxeles                        36 / 36 
      Diagonal en píxeles                               51 
      Velocidad de refreco vertical                     60 Hz 
      Imagen de fondo del escritorio                    c:\Windows\ASUS\wallpapers\ASUS.jpg 
 
    Efectos gráficos: 
      Animación de combo-box                            Activado 
      Efecto de sombra decreciente                      Activado 
      Efecto de menú plano                              Activado 
      Alisado de fuentes                                Activado 
      ClearType                                         Activado 
      Diseño de ventana durante los desplazamientos de ratónActivado 
      Gradiente en las barras de título                 Activado 
      Ocultar el menú de acceso al teclado              Activado 
      Efecto de relieve con el ratón                    Activado 
      Envoltura de los títulos de iconos                Activado 
      Desplazamiento suave de las listas                Activado 
      Animación de menú                                 Activado 
      Efecto de desvanecimiento de menú                 Activado 
      Animación en minimizar/restaurar                  Activado 
      Sombra del puntero del ratón                      Activado 
      Efecto de desvanecimiento de la selección         Activado 
      Uso de sonidos visuales (ShowSounds)              Desactivado 
      Animación de consejos de ayuda                    Activado 
      Desvanecimiento de consejos de ayuda              Activado 
      Windows Aero                                      Activado 
      Extensión Windows Plus!                           Desactivado 
 
 
--------[ Monitores múltiples ]----------------------------------------------------------------------------------------- 
 
    \\.\DISPLAY1        Sí   (0,0)          (1440,900) 
 
 
--------[ Modos de video ]---------------------------------------------------------------------------------------------- 
 
    640 x 480          8 bits  60 Hz 
    640 x 480          8 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    640 x 480         16 bits  60 Hz 
    640 x 480         16 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    640 x 480         32 bits  60 Hz 
    640 x 480         32 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    720 x 480          8 bits  60 Hz 
    720 x 480          8 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    720 x 480         16 bits  60 Hz 
    720 x 480         16 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    720 x 480         32 bits  60 Hz 
    720 x 480         32 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    720 x 576          8 bits  60 Hz 
    720 x 576          8 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    720 x 576         16 bits  60 Hz 
    720 x 576         16 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    720 x 576         32 bits  60 Hz 
    720 x 576         32 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    800 x 600          8 bits  60 Hz 
    800 x 600          8 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    800 x 600         16 bits  60 Hz 
    800 x 600         16 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    800 x 600         32 bits  60 Hz 
    800 x 600         32 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    1024 x 768         8 bits  60 Hz 
    1024 x 768         8 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    1024 x 768        16 bits  60 Hz 
    1024 x 768        16 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    1024 x 768        32 bits  60 Hz 
    1024 x 768        32 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    1280 x 720         8 bits  60 Hz 
    1280 x 720         8 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    1280 x 720        16 bits  60 Hz 
    1280 x 720        16 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    1280 x 720        32 bits  60 Hz 
    1280 x 720        32 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    1440 x 900         8 bits  60 Hz 
    1440 x 900        16 bits  60 Hz 
    [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
 
 
--------[ OpenGL ]------------------------------------------------------------------------------------------------------ 
 
    Propiedades del OpenGL: 
      Vendedor                                          NVIDIA Corporation 
      Renderer                                          GeForce 9300M GS/PCI/SSE2 
      Versión                                           2.1.2 
      Shading Language Version                          1.20 NVIDIA via Cg compiler 
      OpenGL DLL                                        6.0.6000.16386(vista_rtm.061101-2205) 
      Multitexture Texture Units                        4 
      Occlusion Query Counter Bits                      32 
      Sub-Pixel Precision                               8 bits 
      Max Viewport Size                                 8192 x 8192 
      Max Cube Map Texture Size                         8192 x 8192 
      Max Rectangle Texture Size                        8192 x 8192 
      Max 3D Texture Size                               2048 x 2048 x 2048 
      Max Anisotropy                                    16 
      Max Draw Buffers                                  8 
      Max General Register Combiners                    8 
      Max Texture LOD Bias                              15 
      Max Vertex Array Range Element Size               1048575 
 
    Draw Range Elements: 
      Max Index Count                                   1048576 
      Max Vertex Count                                  1048576 
 
    Extended Lighting Parameters: 
      Max Shininess                                     128 
      Max Spot Exponent                                 128 
 
    Framebuffer Object: 
      Max Color Attachments                             8 
      Max Render Buffer Size                            8192 x 8192 
 
    Imaging: 
      Max Color Matrix Stack Depth                      2 
      Max Convolution Width / Height                    11 / 11 
 
    Vertex Shader: 
      Max Uniform Vertex Components                     4096 
      Max Varying Floats                                60 
      Max Vertex Texture Image Units                    32 
      Max Combined Texture Image Units                  32 
 
    Fragment Shader: 
      Max Uniform Fragment Components                   2048 
 
    Vertex Program: 
      Max Local Parameters                              1024 
      Max Environment Parameters                        256 
      Max Program Matrices                              8 
      Max Program Stack Depth                           1 
      Max Vertex Attributes                             16 
      Max Instructions                                  16384 
      Max Native Instructions                           16384 
      Max Temporaries                                   4096 
      Max Native Temporaries                            4096 
      Max Parameters                                    1024 
      Max Native Parameters                             1024 
      Max Attributes                                    16 
      Max Native Attributes                             16 
      Max Address Registers                             2 
      Max Native Address Registers                      2 
 
    Fragment Program: 
      Max Local Parameters                              512 
      Max Environment Parameters                        256 
      Max Texture Coordinates                           8 
      Max Texture Image Units                           32 
      Max Instructions                                  16384 
      Max Native Instructions                           16384 
      Max Temporaries                                   4096 
      Max Native Temporaries                            4096 
      Max Parameters                                    1024 
      Max Native Parameters                             1024 
      Max Attributes                                    16 
      Max Native Attributes                             16 
      Max Address Registers                             1 
      Max Native Address Registers                      1 
      Max ALU Instructions                              16384 
      Max Native ALU Instructions                       16384 
      Max Texture Instructions                          16384 
      Max Native Texture Instructions                   16384 
      Max Texture Indirections                          16384 
      Max Native Texture Indirections                   16384 
      Max Execution Instructions                        16777216 
      Max Call Stack Depth                              32 
      Max If Statement Depth                            64 
      Max Loop Depth                                    64 
      Max Loop Count                                    16777216 
 
    OpenGL Extensions: 
      GL_3DFX_multisample                               No soportado 
      GL_3DFX_texture_compression_FXT1                  No soportado 
      GL_3DL_direct_texture_access2                     No soportado 
      GL_3Dlabs_multisample_transparency_id             No soportado 
      GL_3Dlabs_multisample_transparency_range          No soportado 
      GL_AMD_performance_monitor                        No soportado 
      GL_AMDX_vertex_shader_tessellator                 No soportado 
      GL_APPLE_aux_depth_stencil                        No soportado 
      GL_APPLE_client_storage                           No soportado 
      GL_APPLE_element_array                            No soportado 
      GL_APPLE_fence                                    No soportado 
      GL_APPLE_float_pixels                             No soportado 
      GL_APPLE_flush_buffer_range                       No soportado 
      GL_APPLE_flush_render                             No soportado 
      GL_APPLE_packed_pixel                             No soportado 
      GL_APPLE_packed_pixels                            No soportado 
      GL_APPLE_pixel_buffer                             No soportado 
      GL_APPLE_specular_vector                          No soportado 
      GL_APPLE_texture_range                            No soportado 
      GL_APPLE_transform_hint                           No soportado 
      GL_APPLE_vertex_array_object                      No soportado 
      GL_APPLE_vertex_array_range                       No soportado 
      GL_APPLE_vertex_program_evaluators                No soportado 
      GL_APPLE_ycbcr_422                                No soportado 
      GL_ARB_color_buffer_float                         Soportado 
      GL_ARB_depth_texture                              Soportado 
      GL_ARB_draw_buffers                               Soportado 
      GL_ARB_fragment_program                           Soportado 
      GL_ARB_fragment_program_shadow                    Soportado 
      GL_ARB_fragment_shader                            Soportado 
      GL_ARB_half_float_pixel                           Soportado 
      GL_ARB_imaging                                    Soportado 
      GL_ARB_multisample                                Soportado 
      GL_ARB_multitexture                               Soportado 
      GL_ARB_occlusion_query                            Soportado 
      GL_ARB_pixel_buffer_object                        Soportado 
      GL_ARB_point_parameters                           Soportado 
      GL_ARB_point_sprite                               Soportado 
      GL_ARB_shader_objects                             Soportado 
      GL_ARB_shader_texture_lod                         No soportado 
      GL_ARB_shading_language_100                       Soportado 
      GL_ARB_shadow                                     Soportado 
      GL_ARB_shadow_ambient                             No soportado 
      GL_ARB_texture_border_clamp                       Soportado 
      GL_ARB_texture_compression                        Soportado 
      GL_ARB_texture_cube_map                           Soportado 
      GL_ARB_texture_env_add                            Soportado 
      GL_ARB_texture_env_combine                        Soportado 
      GL_ARB_texture_env_crossbar                       No soportado 
      GL_ARB_texture_env_dot3                           Soportado 
      GL_ARB_texture_float                              Soportado 
      GL_ARB_texture_mirrored_repeat                    Soportado 
      GL_ARB_texture_non_power_of_two                   Soportado 
      GL_ARB_texture_rectangle                          Soportado 
      GL_ARB_transpose_matrix                           Soportado 
      GL_ARB_vertex_blend                               No soportado 
      GL_ARB_vertex_buffer_object                       Soportado 
      GL_ARB_vertex_program                             Soportado 
      GL_ARB_vertex_shader                              Soportado 
      GL_ARB_window_pos                                 Soportado 
      GL_ATI_array_rev_comps_in_4_bytes                 No soportado 
      GL_ATI_blend_equation_separate                    No soportado 
      GL_ATI_blend_weighted_minmax                      No soportado 
      GL_ATI_draw_buffers                               Soportado 
      GL_ATI_element_array                              No soportado 
      GL_ATI_envmap_bumpmap                             No soportado 
      GL_ATI_fragment_shader                            No soportado 
      GL_ATI_lock_texture                               No soportado 
      GL_ATI_map_object_buffer                          No soportado 
      GL_ATI_meminfo                                    No soportado 
      GL_ATI_pixel_format_float                         No soportado 
      GL_ATI_pn_triangles                               No soportado 
      GL_ATI_point_cull_mode                            No soportado 
      GL_ATI_separate_stencil                           No soportado 
      GL_ATI_shader_texture_lod                         No soportado 
      GL_ATI_text_fragment_shader                       No soportado 
      GL_ATI_texture_compression_3dc                    No soportado 
      GL_ATI_texture_env_combine3                       No soportado 
      GL_ATI_texture_float                              Soportado 
      GL_ATI_texture_mirror_once                        Soportado 
      GL_ATI_vertex_array_object                        No soportado 
      GL_ATI_vertex_attrib_array_object                 No soportado 
      GL_ATI_vertex_blend                               No soportado 
      GL_ATI_vertex_shader                              No soportado 
      GL_ATI_vertex_streams                             No soportado 
      GL_ATIX_pn_triangles                              No soportado 
      GL_ATIX_texture_env_combine3                      No soportado 
      GL_ATIX_texture_env_route                         No soportado 
      GL_ATIX_vertex_shader_output_point_size           No soportado 
      GL_Autodesk_facet_normal                          No soportado 
      GL_Autodesk_valid_back_buffer_hint                No soportado 
      GL_DIMD_YUV                                       No soportado 
      GL_EXT_422_pixels                                 No soportado 
      GL_EXT_abgr                                       Soportado 
      GL_EXT_bgra                                       Soportado 
      GL_EXT_bindable_uniform                           Soportado 
      GL_EXT_blend_color                                Soportado 
      GL_EXT_blend_equation_separate                    Soportado 
      GL_EXT_blend_func_separate                        Soportado 
      GL_EXT_blend_logic_op                             No soportado 
      GL_EXT_blend_minmax                               Soportado 
      GL_EXT_blend_subtract                             Soportado 
      GL_EXT_Cg_shader                                  Soportado 
      GL_EXT_clip_volume_hint                           No soportado 
      GL_EXT_color_matrix                               No soportado 
      GL_EXT_color_subtable                             No soportado 
      GL_EXT_color_table                                No soportado 
      GL_EXT_compiled_vertex_array                      Soportado 
      GL_EXT_convolution                                No soportado 
      GL_EXT_convolution_border_modes                   No soportado 
      GL_EXT_copy_texture                               No soportado 
      GL_EXT_cull_vertex                                No soportado 
      GL_EXT_depth_bounds_test                          Soportado 
      GL_EXT_draw_buffers2                              Soportado 
      GL_EXT_draw_instanced                             Soportado 
      GL_EXT_draw_range_elements                        Soportado 
      GL_EXT_fog_coord                                  Soportado 
      GL_EXT_fog_function                               No soportado 
      GL_EXT_fog_offset                                 No soportado 
      GL_EXT_framebuffer_blit                           Soportado 
      GL_EXT_framebuffer_multisample                    Soportado 
      GL_EXT_framebuffer_object                         Soportado 
      GL_EXT_framebuffer_sRGB                           Soportado 
      GL_EXT_generate_mipmap                            No soportado 
      GL_EXT_geometry_shader4                           Soportado 
      GL_EXT_gpu_program_parameters                     Soportado 
      GL_EXT_gpu_shader4                                Soportado 
      GL_EXT_histogram                                  No soportado 
      GL_EXT_interlace                                  No soportado 
      GL_EXT_multi_draw_arrays                          Soportado 
      GL_EXT_multisample                                No soportado 
      GL_EXT_packed_depth_stencil                       Soportado 
      GL_EXT_packed_float                               Soportado 
      GL_EXT_packed_pixels                              Soportado 
      GL_EXT_packed_pixels_12                           No soportado 
      GL_EXT_paletted_texture                           No soportado 
      GL_EXT_pixel_buffer_object                        Soportado 
      GL_EXT_pixel_format                               No soportado 
      GL_EXT_pixel_texture                              No soportado 
      GL_EXT_point_parameters                           Soportado 
      GL_EXT_polygon_offset                             No soportado 
      GL_EXT_rescale_normal                             Soportado 
      GL_EXT_secondary_color                            Soportado 
      GL_EXT_separate_specular_color                    Soportado 
      GL_EXT_shadow_funcs                               Soportado 
      GL_EXT_stencil_clear_tag                          No soportado 
      GL_EXT_stencil_two_side                           Soportado 
      GL_EXT_stencil_wrap                               Soportado 
      GL_EXT_subtexture                                 No soportado 
      GL_EXT_swap_control                               No soportado 
      GL_EXT_texgen_reflection                          No soportado 
      GL_EXT_texture                                    No soportado 
      GL_EXT_texture_array                              Soportado 
      GL_EXT_texture_border_clamp                       No soportado 
      GL_EXT_texture_buffer_object                      Soportado 
      GL_EXT_texture_color_table                        No soportado 
      GL_EXT_texture_compression_dxt1                   No soportado 
      GL_EXT_texture_compression_latc                   Soportado 
      GL_EXT_texture_compression_rgtc                   Soportado 
      GL_EXT_texture_compression_s3tc                   Soportado 
      GL_EXT_texture_cube_map                           Soportado 
      GL_EXT_texture_edge_clamp                         Soportado 
      GL_EXT_texture_env_add                            Soportado 
      GL_EXT_texture_env_combine                        Soportado 
      GL_EXT_texture_env_dot3                           Soportado 
      GL_EXT_texture_filter_anisotropic                 Soportado 
      GL_EXT_texture_integer                            Soportado 
      GL_EXT_texture_lod                                Soportado 
      GL_EXT_texture_lod_bias                           Soportado 
      GL_EXT_texture_mirror_clamp                       Soportado 
      GL_EXT_texture_object                             Soportado 
      GL_EXT_texture_rectangle                          No soportado 
      GL_EXT_texture_shared_exponent                    Soportado 
      GL_EXT_texture_sRGB                               Soportado 
      GL_EXT_texture3D                                  Soportado 
      GL_EXT_texture4D                                  No soportado 
      GL_EXT_timer_query                                Soportado 
      GL_EXT_transform_feedback                         No soportado 
      GL_EXT_vertex_array                               Soportado 
      GL_EXT_vertex_shader                              No soportado 
      GL_EXT_vertex_weighting                           No soportado 
      GL_EXTX_framebuffer_mixed_formats                 Soportado 
      GL_EXTX_packed_depth_stencil                      No soportado 
      GL_FGL_lock_texture                               No soportado 
      GL_GL2_geometry_shader                            No soportado 
      GL_HP_occlusion_test                              No soportado 
      GL_I3D_argb                                       No soportado 
      GL_I3D_color_clamp                                No soportado 
      GL_I3D_interlace_read                             No soportado 
      GL_IBM_clip_check                                 No soportado 
      GL_IBM_cull_vertex                                No soportado 
      GL_IBM_load_named_matrix                          No soportado 
      GL_IBM_multi_draw_arrays                          No soportado 
      GL_IBM_multimode_draw_arrays                      No soportado 
      GL_IBM_occlusion_cull                             No soportado 
      GL_IBM_pixel_filter_hint                          No soportado 
      GL_IBM_rasterpos_clip                             Soportado 
      GL_IBM_rescale_normal                             No soportado 
      GL_IBM_texture_clamp_nodraw                       No soportado 
      GL_IBM_texture_mirrored_repeat                    Soportado 
      GL_IBM_vertex_array_lists                         No soportado 
      GL_IBM_YCbCr                                      No soportado 
      GL_INGR_blend_func_separate                       No soportado 
      GL_INGR_multiple_palette                          No soportado 
      GL_KTX_buffer_region                              Soportado 
      GL_MTX_fragment_shader                            No soportado 
      GL_MTX_precision_dpi                              No soportado 
      GL_NV_blend_square                                Soportado 
      GL_NV_centroid_sample                             No soportado 
      GL_NV_conditional_render                          Soportado 
      GL_NV_copy_depth_to_color                         Soportado 
      GL_NV_depth_buffer_float                          Soportado 
      GL_NV_depth_clamp                                 Soportado 
      GL_NV_evaluators                                  No soportado 
      GL_NV_fence                                       Soportado 
      GL_NV_float_buffer                                Soportado 
      GL_NV_fog_distance                                Soportado 
      GL_NV_fragment_program                            Soportado 
      GL_NV_fragment_program_option                     Soportado 
      GL_NV_fragment_program2                           Soportado 
      GL_NV_framebuffer_multisample_coverage            Soportado 
      GL_NV_framebuffer_multisample_ex                  No soportado 
      GL_NV_geometry_shader4                            Soportado 
      GL_NV_gpu_program4                                Soportado 
      GL_NV_half_float                                  Soportado 
      GL_NV_light_max_exponent                          Soportado 
      GL_NV_multisample_coverage                        Soportado 
      GL_NV_multisample_filter_hint                     Soportado 
      GL_NV_occlusion_query                             Soportado 
      GL_NV_packed_depth_stencil                        Soportado 
      GL_NV_parameter_buffer_object                     Soportado 
      GL_NV_pixel_buffer_object                         No soportado 
      GL_NV_pixel_data_range                            Soportado 
      GL_NV_point_sprite                                Soportado 
      GL_NV_primitive_restart                           Soportado 
      GL_NV_register_combiners                          Soportado 
      GL_NV_register_combiners2                         Soportado 
      GL_NV_texgen_emboss                               No soportado 
      GL_NV_texgen_reflection                           Soportado 
      GL_NV_texture_compression_latc                    No soportado 
      GL_NV_texture_compression_vtc                     Soportado 
      GL_NV_texture_env_combine4                        Soportado 
      GL_NV_texture_expand_normal                       Soportado 
      GL_NV_texture_rectangle                           Soportado 
      GL_NV_texture_shader                              Soportado 
      GL_NV_texture_shader2                             Soportado 
      GL_NV_texture_shader3                             Soportado 
      GL_NV_timer_query                                 No soportado 
      GL_NV_transform_feedback                          Soportado 
      GL_NV_vertex_array_range                          Soportado 
      GL_NV_vertex_array_range2                         Soportado 
      GL_NV_vertex_program                              Soportado 
      GL_NV_vertex_program1_1                           Soportado 
      GL_NV_vertex_program2                             Soportado 
      GL_NV_vertex_program2_option                      Soportado 
      GL_NV_vertex_program3                             Soportado 
      GL_NVX_conditional_render                         Soportado 
      GL_NVX_flush_hold                                 No soportado 
      GL_NVX_ycrcb                                      No soportado 
      GL_OML_interlace                                  No soportado 
      GL_OML_resample                                   No soportado 
      GL_OML_subsample                                  No soportado 
      GL_S3_s3tc                                        Soportado 
      GL_SGI_color_matrix                               No soportado 
      GL_SGI_color_table                                No soportado 
      GL_SGI_compiled_vertex_array                      No soportado 
      GL_SGI_cull_vertex                                No soportado 
      GL_SGI_index_array_formats                        No soportado 
      GL_SGI_index_func                                 No soportado 
      GL_SGI_index_material                             No soportado 
      GL_SGI_index_texture                              No soportado 
      GL_SGI_make_current_read                          No soportado 
      GL_SGI_texture_add_env                            No soportado 
      GL_SGI_texture_color_table                        No soportado 
      GL_SGI_texture_edge_clamp                         No soportado 
      GL_SGI_texture_lod                                No soportado 
      GL_SGIS_fog_function                              No soportado 
      GL_SGIS_generate_mipmap                           Soportado 
      GL_SGIS_multisample                               No soportado 
      GL_SGIS_multitexture                              No soportado 
      GL_SGIS_pixel_texture                             No soportado 
      GL_SGIS_texture_border_clamp                      No soportado 
      GL_SGIS_texture_color_mask                        No soportado 
      GL_SGIS_texture_edge_clamp                        No soportado 
      GL_SGIS_texture_lod                               Soportado 
      GL_SGIS_texture4D                                 No soportado 
      GL_SGIX_depth_pass_instrument                     No soportado 
      GL_SGIX_depth_texture                             Soportado 
      GL_SGIX_fog_offset                                No soportado 
      GL_SGIX_instruments                               No soportado 
      GL_SGIX_interlace                                 No soportado 
      GL_SGIX_pbuffer                                   No soportado 
      GL_SGIX_pixel_texture                             No soportado 
      GL_SGIX_shadow                                    Soportado 
      GL_SGIX_shadow_ambient                            No soportado 
      GL_SGIX_subsample                                 No soportado 
      GL_SGIX_ycrcb_subsample                           No soportado 
      GL_SUN_multi_draw_arrays                          No soportado 
      GL_SUN_slice_accum                                Soportado 
      GL_SUN_vertex                                     No soportado 
      GL_WGL_ARB_extensions_string                      No soportado 
      GL_WGL_EXT_extensions_string                      No soportado 
      GL_WGL_EXT_swap_control                           No soportado 
      GL_WIN_swap_hint                                  Soportado 
      GLX_ARB_fbconfig_float                            No soportado 
      GLX_SUN_video_resize                              No soportado 
      WGL_3DFX_gamma_control                            No soportado 
      WGL_3DFX_multisample                              No soportado 
      WGL_ARB_buffer_region                             Soportado 
      WGL_ARB_extensions_string                         Soportado 
      WGL_ARB_make_current_read                         Soportado 
      WGL_ARB_multisample                               Soportado 
      WGL_ARB_pbuffer                                   Soportado 
      WGL_ARB_pixel_format                              Soportado 
      WGL_ARB_pixel_format_float                        Soportado 
      WGL_ARB_render_texture                            Soportado 
      WGL_ATI_pbuffer_memory_hint                       No soportado 
      WGL_ATI_pixel_format_float                        Soportado 
      WGL_ATI_render_texture_rectangle                  No soportado 
      WGL_EXT_buffer_region                             No soportado 
      WGL_EXT_extensions_string                         Soportado 
      WGL_EXT_framebuffer_sRGB                          Soportado 
      WGL_EXT_gamma_control                             No soportado 
      WGL_EXT_make_current_read                         No soportado 
      WGL_EXT_multisample                               No soportado 
      WGL_EXT_pbuffer                                   No soportado 
      WGL_EXT_pixel_format                              No soportado 
      WGL_EXT_pixel_format_packed_float                 Soportado 
      WGL_EXT_render_texture                            No soportado 
      WGL_EXT_swap_control                              Soportado 
      WGL_EXT_swap_interval                             No soportado 
      WGL_I3D_digital_video_control                     No soportado 
      WGL_I3D_gamma                                     No soportado 
      WGL_I3D_genlock                                   No soportado 
      WGL_I3D_image_buffer                              No soportado 
      WGL_I3D_swap_frame_lock                           No soportado 
      WGL_I3D_swap_frame_usage                          No soportado 
      WGL_MTX_video_preview                             No soportado 
      WGL_NV_float_buffer                               Soportado 
      WGL_NV_multisample_coverage                       Soportado 
      WGL_NV_render_depth_texture                       Soportado 
      WGL_NV_render_texture_rectangle                   Soportado 
      WGL_NV_swap_group                                 No soportado 
 
    Supported Compressed Texture Formats: 
      RGB DXT1                                          Soportado 
      RGBA DXT1                                         No soportado 
      RGBA DXT3                                         Soportado 
      RGBA DXT5                                         Soportado 
      RGB FXT1                                          No soportado 
      RGBA FXT1                                         No soportado 
      3Dc                                               No soportado 
 
 
--------[ Audio de Windows ]-------------------------------------------------------------------------------------------- 
 
    midi-out.0   0001 001B  Microsoft GS Wavetable Synth 
    mixer.0      0001 0068  Altavoces (Realtek High Definit 
    mixer.1      0001 0068  Realtek Digital Output (Realtek 
    mixer.2      0001 0068  Micrófono (Realtek High Definit 
    wave-in.0    0001 0065  Micrófono (Realtek High Definit 
    wave-in.1    0001 0050  Línea #0 del módem 
    wave-out.0   0001 0064  Altavoces (Realtek High Definit 
    wave-out.1   0001 0051  Línea #0 del módem 
    wave-out.2   0001 0064  Realtek Digital Output (Realtek 
 
 
--------[ Audio PCI/PnP ]----------------------------------------------------------------------------------------------- 
 
    nVIDIA HDMI @ Intel 82801IB ICH9 - High Definition Audio Controller               PCI 
    Realtek ALC663 @ Intel 82801IB ICH9 - High Definition Audio Controller            PCI 
 
 
--------[ Almacenamiento de Windows ]----------------------------------------------------------------------------------- 
 
  [ FUJITSU MHX2300BT ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       FUJITSU MHX2300BT 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       disk.inf 
 
    Información física sobre el dispositivo disco: 
      Fabricante                                        Fujitsu 
      Forma                                             2.5" 
      Capacidad después del formateo                    300 GB 
      Discos                                            3 
      Superficies de grabación                          6 
      Dimensiones físicas                               100 x 70 x 12.5 mm 
      Peso máximo                                       135 g 
      Latencia media de rotación                        7.14 ms 
      Velocidad de rotación                             4200 RPM 
      Tiempo de búsqueda medio                          12 ms 
      Búsqueda pista a pista                            1.5 ms 
      Búsqueda completa                                 22 ms 
      Interfaz                                          SATA 
      Tasa de transferencia de buffer hacia host        150 MB/s 
      Tamaño del buffer                                 8 MB 
 
    Fabricante del dispositivo: 
      Nombre de la empresa                              Fujitsu Computer Products of America, Inc. 
      Información sobre el producto                     http://www.fcpa.fujitsu.com/products/hard-drives 
 
  [ SONY WALKMAN USB Device ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SONY WALKMAN USB Device 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       disk.inf 
 
  [ HL-DT-ST DVDRAM GSA-T50N ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       HL-DT-ST DVDRAM GSA-T50N 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       cdrom.inf 
 
    Fabricante del dispositivo: 
      Nombre de la empresa                              LG Electronics 
      Información sobre el producto                     http://www.lge.com/products/category/list/computer%20product_optical%20storage.jhtml 
      Firmware Download                                 http://www.lge.com/support/software.jsp 
 
  [ Intel(R) ICH9M-E/M SATA AHCI Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) ICH9M-E/M SATA AHCI Controller 
      Fecha del controlador                             07/05/2008 
      Versión del controlador                           8.2.0.1001 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem7.inf 
 
    Recursos de los dispositivos: 
      IRQ                                               19 
      Memoria                                           F7FFF000-F7FFF7FF 
      Puerto                                            A480-A49F 
      Puerto                                            A800-A803 
      Puerto                                            A880-A887 
      Puerto                                            AC00-AC03 
      Puerto                                            B000-B007 
 
  [ Ricoh Memory Stick Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Ricoh Memory Stick Controller 
      Fecha del controlador                             30/07/2007 
      Versión del controlador                           6.0.1.11 
      Proveedor del controlador                         Ricoh Company 
      Archivo INF                                       oem15.inf 
 
    Recursos de los dispositivos: 
      IRQ                                               17 
      Memoria                                           FDFFF000-FDFFF0FF 
 
  [ Ricoh xD-Picture Card Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Ricoh xD-Picture Card Controller 
      Fecha del controlador                             30/07/2007 
      Versión del controlador                           6.0.1.13 
      Proveedor del controlador                         Ricoh Company 
      Archivo INF                                       oem14.inf 
 
    Recursos de los dispositivos: 
      IRQ                                               17 
      Memoria                                           FDFFEC00-FDFFECFF 
 
  [ Iniciador iSCSI de Microsoft ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Microsoft iSCSI Initiator 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       iscsi.inf 
 
 
--------[ Discos lógicos ]---------------------------------------------------------------------------------------------- 
 
    [ TRIAL VERSION ]                         Disco local         NTFS      [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ]  [ TRIAL VERSION ] 
    D:                                        Lector óptico                                                                            
    E:                                        Disco removible     FAT32           938 MB        905 MB         33 MB    4 %  3A1F-BAC7 
 
 
--------[ Discos físicos ]---------------------------------------------------------------------------------------------- 
 
  [ Disco nº1 - FUJITSU MHX2300BT (279 GB) ] 
 
    #1 (Activo)      NTFS             C: (VistaOS)                                    1 MB   286166 MB 
 
  [ Disco nº2 - SONY    WALKMAN (941 MB) ] 
 
    #1 (Activo)      FAT32            E:                                              0 MB      942 MB 
  
      Descripción del dispositivo                       HL-DT-ST DVDRAM GSA-T50N 
      Número de serie                                   K0088522150 
      Firmware Revision                                 RR04 
      Firmware Date                                     28/03/2008 
      Tamaño del buffer                                 2 MB 
      Region Code                                       Ninguno 
      Remaining User Changes                            5 
      Remaining Vendor Changes                          4 
 
    Supported Disk Types: 
      BD-ROM                                            No soportado 
      BD-R                                              No soportado 
      BD-RE                                             No soportado 
      HD DVD-ROM                                        No soportado 
      HD DVD-R                                          No soportado 
      HD DVD-RW                                         No soportado 
      DVD-ROM                                           Read 
      DVD+R9 Dual Layer                                 Read + Write 
      DVD+R                                             Read + Write 
      DVD+RW                                            Read + Write 
      DVD-R9 Dual Layer                                 Read + Write 
      DVD-R                                             Read + Write 
      DVD-RW                                            Read + Write 
      DVD-RAM                                           Read + Write 
      CD-ROM                                            Read 
      CD-R                                              Read + Write 
      CD-RW                                             Read + Write 
 
    Optical Drive Features: 
      Buffer Underrun Protection                        Soportado 
      C2 Error Pointers                                 Soportado 
      CD+G                                              No soportado 
      CD-Text                                           Soportado 
      Hybrid Disc                                       No soportado 
      JustLink                                          No soportado 
      LabelFlash                                        No soportado 
      Layer-Jump Recording                              Soportado 
      LightScribe                                       No soportado 
      Mount Rainier                                     No soportado 
      SMART                                             Soportado 
      CSS                                               Soportado 
      CPRM                                              Soportado 
      AACS                                              No soportado 
      VCPS                                              No soportado 
      BD CPS                                            No soportado 
 
 
--------[ ASPI ]-------------------------------------------------------------------------------------------------------- 
 
    00  00  00  Disco duro               FUJITSU   MHX2300BT                
    00  01  00  Lector óptico            HL-DT-ST  DVDRAM GSA-T50N          
    00  07  00  Adaptador Host           iaStor                             
 
 
--------[ ATA ]--------------------------------------------------------------------------------------------------------- 
 
  [ FUJITSU MHX2300BT (K201T7A26Y17) ] 
 
    Propiedades del dispositivo ATA: 
      Identificador del modelo                          FUJITSU MHX2300BT 
      Número de serie                                   K201T7A26Y17 
      Revisión                                          0000000B 
      World Wide Name                                   5-00000E-0410D2A1E 
      Tipo de dispositivo                               SATA 
      Parámetros                                        581421 cilinfros, 16 cabezas, 63 sectores por pista, 512 bytes por sector 
      Sectores LBA                                      586072368 
      Memoria de almacenamiento temporal (buffer)       8 MB (Dual Ported, Read Ahead) 
      Sectores múltiples                                16 
      Bytes ECC                                         0 
      Capacidad de no-formateo                          286168 MB 
 
    Funciones del dispositivo ATA: 
      48-bit LBA                                        Soportado 
      Gestión de ahorro de energía APM                  Soportado, Activado 
      Automatic Acoustic Management                     Soportado, Activado 
      Device Configuration Overlay                      Soportado 
      DMA Setup Auto-Activate                           Soportado, Activado 
      General Purpose Logging                           Soportado 
      Host Protected Area                               Soportado, Activado 
      In-Order Data Delivery                            No soportado 
      Native Command Queuing                            Soportado 
      Phy Event Counters                                Soportado 
      Gestión de la energía                             Soportado, Activado 
      Power-Up In Standby                               No soportado 
      Read Look-Ahead                                   Soportado, Activado 
      Release Interrupt                                 No soportado 
      Modo de seguridad                                 Soportado, Desactivado 
      SMART                                             Soportado, Activado 
      SMART Error Logging                               Soportado 
      SMART Self-Test                                   Soportado 
      Software Settings Preservation                    Soportado, Activado 
      Streaming                                         No soportado 
      Tagged Command Queuing                            No soportado 
      Caché en escritura                                Soportado, Activado 
 
    Información física sobre el dispositivo ATA: 
      Fabricante                                        Fujitsu 
      Forma                                             2.5" 
      Capacidad después del formateo                    300 GB 
      Discos                                            3 
      Superficies de grabación                          6 
      Dimensiones físicas                               100 x 70 x 12.5 mm 
      Peso máximo                                       135 g 
      Latencia media de rotación                        7.14 ms 
      Velocidad de rotación                             4200 RPM 
      Tiempo de búsqueda medio                          12 ms 
      Búsqueda pista a pista                            1.5 ms 
      Búsqueda completa                                 22 ms 
      Interfaz                                          SATA 
      Tasa de transferencia de buffer hacia host        150 MB/s 
      Tamaño del buffer                                 8 MB 
 
    Fabricante del dispositivo ATA: 
      Nombre de la empresa                              Fujitsu Computer Products of America, Inc. 
      Información sobre el producto                     http://www.fcpa.fujitsu.com/products/hard-drives 
 
  [ HL-DT-ST DVDRAM GSA-T50N ] 
 
 
    Fabricante del dispositivo: 
      Nombre de la empresa                              LG Electronics 
      Información sobre el producto                     http://www.lge.com/products/category/list/computer%20product_optical%20storage.jhtml 
      Firmware Download                                 http://www.lge.com/support/software.jsp 
 
 
--------[ SMART ]------------------------------------------------------------------------------------------------------- 
 
  [ FUJITSU MHX2300BT (K201T7A26Y17) ] 
 
    01  Raw Read Error Rate                  46   100  100       87287  OK (el valor es normal) 
    02  Throughput Performance               30   100  100    90177536  OK (el valor es normal) 
    03  Spinup Time                          25   100  100           1  OK (el valor es normal) 
    04  Start/Stop Count                     0    99   99          415  OK (siempre funcionará) 
    05  Reallocated Sector Count             24   100  100           0  OK (el valor es normal) 
    07  Seek Error Rate                      47   100  100        3942  OK (el valor es normal) 
    08  Seek Time Performance                19   100  100           0  OK (el valor es normal) 
    09  Power-On Time Count                  0    98   98         1164  OK (siempre funcionará) 
    0A  Spinup Retry Count                   20   100  100           0  OK (el valor es normal) 
    0C  Power Cycle Count                    0    100  100         372  OK (siempre funcionará) 
    C0  Power-Off Retract Count              0    100  100           7  OK (siempre funcionará) 
    C1  Load/Unload Cycle Count              0    100  100        5490  OK (siempre funcionará) 
    C2  Temperature                          0    100  100      20, 42  OK (siempre funcionará) 
    C3  Hardware ECC Recovered               0    100  100         393  OK (siempre funcionará) 
    C4  Reallocation Event Count             0    100  100   410648576  OK (siempre funcionará) 
    C5  Current Pending Sector Count         0    100  100           0  OK (siempre funcionará) 
    C6  Offline Uncorrectable Sector Count   0    100  100           0  OK (siempre funcionará) 
    C7  Ultra ATA CRC Error Rate             0    200  200           0  OK (siempre funcionará) 
    C8  Write Error Rate                     60   100  100        1058  OK (el valor es normal) 
    CB  Run Out Cancel                       0    100  100  4248240898  OK (siempre funcionará) 
    F0  Head Flying Hours                    0    200  200           0  OK (siempre funcionará) 
 
 
--------[ Red de Windows ]---------------------------------------------------------------------------------------------- 
 
  [ Intel(R) WiFi Link 5100 ] 
 
    Propiedades de la tarjeta de Red: 
      Tarjeta de Red                                    Intel(R) WiFi Link 5100 
      Tipo de interfaz                                  Desconocido 
      Dirección material                                00-16-EA-98-41-E4 
      Nombre de la conexión                             Conexión de red inalámbrica 
      Velocidad de la conexión                          24 Mbps 
      MTU                                               1500 bytes 
      Concesión DHCP obtenida                           13/04/2009 05:31:36 p.m. 
      La concesión DHCP caduca                          16/04/2009 05:31:36 p.m. 
      Bytes recibidos                                   30101700 (28.7 MB) 
      Bytes enviados                                    1951668 (1.9 MB) 
 
    Direcciones de Red: 
      Máscara de subred                                 [ TRIAL VERSION ] 
      Puerta de enlace predeterminada                   [ TRIAL VERSION ] 
      DHCP                                              [ TRIAL VERSION ] 
      DNS                                               [ TRIAL VERSION ] 
      DNS                                               [ TRIAL VERSION ] 
 
    Fabricante de la tarjeta de Red: 
      Nombre de la empresa                              Intel Corporation 
      Información sobre el producto                     http://www.intel.com/design/network/products/ethernet/linecard_ec.htm 
      Descargar el controlador                          http://support.intel.com/support/network 
      Driver Update                                     http://driveragent.com?ref=59 
 
  [ Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) ] 
 
    Propiedades de la tarjeta de Red: 
      Tarjeta de Red                                    Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) 
      Tipo de interfaz                                  Gigabit Ethernet 
      Dirección material                                00-22-15-B0-70-DB 
      Nombre de la conexión                             Conexión de área local 
      Velocidad de la conexión                          4294967295 bps 
      MTU                                               1500 bytes 
      Bytes recibidos                                   0 
      Bytes enviados                                    0 
 
    Fabricante de la tarjeta de Red: 
      Nombre de la empresa                              Realtek Semiconductor Corp. 
      Información sobre el producto                     http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=7&PFid=10&Level=3&Conn=2 
      Descargar el controlador                          http://www.realtek.com.tw/downloads 
      Driver Update                                     http://driveragent.com?ref=59 
 
 
--------[ Red PCI/PnP ]------------------------------------------------------------------------------------------------- 
 
    Intel Shirley Peak (Shiloh) 1x2 MC Wireless WiFi Adapter                          PCI 
    Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter (PHY: Realtek RTL8211/8212)   PCI 
 
 
--------[ Video DirectX ]----------------------------------------------------------------------------------------------- 
 
  [ Controlador de pantalla primaria ] 
 
    Propiedades del dispositivo DirectDraw: 
      Nombre del controlador DirectDraw                 display 
      Descripción del controlador DirectDraw            Controlador de pantalla primaria 
      Controlador de hardware                           nvd3dum.dll (7.15.11.7597 - nVIDIA ForceWare 175.97) 
      Descripción de hardware                           NVIDIA GeForce 9300M GS 
 
    Propiedades del dispositivo Direct3D: 
      Profundidad de bites de llegada                   16, 32 
      Profundidad de bits Z-Buffer                      16, 24, 32 
      Tamaño mínimo de la textura                       1 x 1 
      Tamaño máximo de la textura                       8192 x 8192 
      Versión de Vertex Shader                          3.0 
      Versión de Pixel Shader                           3.0 
 
    Funciones del dispositivo Direct3D: 
      Additive Texture Blending                         Soportado 
      AGP Texturing                                     Soportado 
      Anisotropic Filtering                             Soportado 
      Bilinear Filtering                                Soportado 
      Cubic Environment Mapping                         Soportado 
      Cubic Filtering                                   No soportado 
      Decal-Alpha Texture Blending                      Soportado 
      Decal Texture Blending                            Soportado 
      DirectX Texture Compression                       No soportado 
      DirectX Volumetric Texture Compression            No soportado 
      Dithering                                         Soportado 
      Dot3 Texture Blending                             Soportado 
      Dynamic Textures                                  Soportado 
      Edge Antialiasing                                 Soportado 
      Environmental Bump Mapping                        Soportado 
      Environmental Bump Mapping + Luminance            Soportado 
      Factor Alpha Blending                             Soportado 
      Geometric Hidden-Surface Removal                  No soportado 
      Guard Band                                        Soportado 
      Hardware Scene Rasterization                      Soportado 
      Hardware Transform & Lighting                     Soportado 
      Legacy Depth Bias                                 Soportado 
      Mipmap LOD Bias Adjustments                       Soportado 
      Mipmapped Cube Textures                           Soportado 
      Mipmapped Volume Textures                         Soportado 
      Modulate-Alpha Texture Blending                   Soportado 
      Modulate Texture Blending                         Soportado 
      Non-Square Textures                               Soportado 
      N-Patches                                         No soportado 
      Perspective Texture Correction                    Soportado 
      Point Sampling                                    Soportado 
      Projective Textures                               Soportado 
      Quintic Bezier Curves & B-Splines                 No soportado 
      Range-Based Fog                                   Soportado 
      Rectangular & Triangular Patches                  No soportado 
      Rendering In Windowed Mode                        Soportado 
      Scissor Test                                      Soportado 
      Slope-Scale Based Depth Bias                      Soportado 
      Specular Flat Shading                             Soportado 
      Specular Gouraud Shading                          Soportado 
      Specular Phong Shading                            No soportado 
      Spherical Mapping                                 Soportado 
      Stencil Buffers                                   Soportado 
      Sub-Pixel Accuracy                                Soportado 
      Table Fog                                         Soportado 
      Texture Alpha Blending                            Soportado 
      Texture Clamping                                  Soportado 
      Texture Mirroring                                 Soportado 
      Texture Transparency                              Soportado 
      Texture Wrapping                                  Soportado 
      Triangle Culling                                  No soportado 
      Trilinear Filtering                               Soportado 
      Two-Sided Stencil Test                            Soportado 
      Vertex Alpha Blending                             Soportado 
      Vertex Fog                                        Soportado 
      Vertex Tweening                                   No soportado 
      Volume Textures                                   Soportado 
      W-Based Fog                                       Soportado 
      W-Buffering                                       No soportado 
      Z-Based Fog                                       Soportado 
      Z-Bias                                            Soportado 
      Z-Test                                            Soportado 
 
    Códigos FourCC reconocidos: 
      3x16                                              Soportado 
      AI44                                              Soportado 
      AIP8                                              Soportado 
      ATOC                                              Soportado 
      AV12                                              Soportado 
      AYUV                                              Soportado 
      NV12                                              Soportado 
      NV24                                              Soportado 
      NVDB                                              Soportado 
      NVDP                                              Soportado 
      NVMD                                              Soportado 
      PLFF                                              Soportado 
      SSAA                                              Soportado 
      UYVY                                              Soportado 
      YUY2                                              Soportado 
      YV12                                              Soportado 
 
 
--------[ Sonido DirectX ]---------------------------------------------------------------------------------------------- 
 
  [ Controlador primario de sonido ] 
 
    Propiedades del dispositivo DirectSound: 
      Descripción del dispositivo                       Controlador primario de sonido 
      Módulo del controlador                             
      Buffers principales                               1 
      Tamaño de muestra min/máx de los buffers secundarios100 / 200000 Hz 
      Formatos de sonido de los buffers principales     8 bits, 16 bits, Mono, Estereo 
      Fomatos de sonido de los buffers secundarios      8 bits, 16 bits, Mono, Estereo 
      Buffers de sonido (total/libres)                  1 / 0 
      Buffers de sonido estáticos (total/libres)        1 / 0 
      Buffers de sonido fluidos (total/libres)          1 / 0 
      Buffers de sonido 3D (total/libres)               0 / 0 
      Bufers de sonido 3D estáticos (total/libres)      0 / 0 
      Buffers de sonido 3D fluidos (total/libres)       0 / 0 
 
    Funciones del dispositivo DirectSound: 
      Controlador certificado                           No 
      Dispositivo emulado                               No 
      Tamaño de muestra preciso                         Soportado 
      DirectSound3D                                     No soportado 
      Creative EAX 1.0                                  No soportado 
      Creative EAX 2.0                                  No soportado 
      Creative EAX 3.0                                  No soportado 
      Creative EAX 4.0                                  No soportado 
      Creative EAX 5.0                                  No soportado 
      I3DL2                                             No soportado 
      Sensaura ZoomFX                                   No soportado 
 
  [ Altavoces (Realtek High Definition Audio) ] 
 
    Propiedades del dispositivo DirectSound: 
      Descripción del dispositivo                       Altavoces (Realtek High Definition Audio) 
      Módulo del controlador                            {0.0.0.00000000}.{f44d606d-6837-49d8-87dc-05672f1ad2d8} 
      Buffers principales                               1 
      Tamaño de muestra min/máx de los buffers secundarios100 / 200000 Hz 
      Formatos de sonido de los buffers principales     8 bits, 16 bits, Mono, Estereo 
      Fomatos de sonido de los buffers secundarios      8 bits, 16 bits, Mono, Estereo 
      Buffers de sonido (total/libres)                  1 / 0 
      Buffers de sonido estáticos (total/libres)        1 / 0 
      Buffers de sonido fluidos (total/libres)          1 / 0 
      Buffers de sonido 3D (total/libres)               0 / 0 
      Bufers de sonido 3D estáticos (total/libres)      0 / 0 
      Buffers de sonido 3D fluidos (total/libres)       0 / 0 
 
    Funciones del dispositivo DirectSound: 
      Controlador certificado                           No 
      Dispositivo emulado                               No 
      Tamaño de muestra preciso                         Soportado 
      DirectSound3D                                     No soportado 
      Creative EAX 1.0                                  No soportado 
      Creative EAX 2.0                                  No soportado 
      Creative EAX 3.0                                  No soportado 
      Creative EAX 4.0                                  No soportado 
      Creative EAX 5.0                                  No soportado 
      I3DL2                                             No soportado 
      Sensaura ZoomFX                                   No soportado 
 
  [ Realtek Digital Output (Realtek High Definition Audio) ] 
 
    Propiedades del dispositivo DirectSound: 
      Descripción del dispositivo                       Realtek Digital Output (Realtek High Definition Audio) 
      Módulo del controlador                            {0.0.0.00000000}.{77d458d4-6e63-4ef9-981d-d3662fa03a9b} 
      Buffers principales                               1 
      Tamaño de muestra min/máx de los buffers secundarios100 / 200000 Hz 
      Formatos de sonido de los buffers principales     8 bits, 16 bits, Mono, Estereo 
      Fomatos de sonido de los buffers secundarios      8 bits, 16 bits, Mono, Estereo 
      Buffers de sonido (total/libres)                  1 / 0 
      Buffers de sonido estáticos (total/libres)        1 / 0 
      Buffers de sonido fluidos (total/libres)          1 / 0 
      Buffers de sonido 3D (total/libres)               0 / 0 
      Bufers de sonido 3D estáticos (total/libres)      0 / 0 
      Buffers de sonido 3D fluidos (total/libres)       0 / 0 
 
    Funciones del dispositivo DirectSound: 
      Controlador certificado                           No 
      Dispositivo emulado                               No 
      Tamaño de muestra preciso                         Soportado 
      DirectSound3D                                     No soportado 
      Creative EAX 1.0                                  No soportado 
      Creative EAX 2.0                                  No soportado 
      Creative EAX 3.0                                  No soportado 
      Creative EAX 4.0                                  No soportado 
      Creative EAX 5.0                                  No soportado 
      I3DL2                                             No soportado 
      Sensaura ZoomFX                                   No soportado 
 
 
--------[ Música DirectX ]---------------------------------------------------------------------------------------------- 
 
  [ Microsoft MIDI Mapper [Emulado] ] 
 
    Propiedades del dispositivo DirectMusic: 
      Descripción del dispositivo                       Microsoft MIDI Mapper [Emulado] 
      Tipo de sintetizador                              Hardware 
      Clase de dispositivo                              Puerta de salida 
      Tipo de dispositivo                               Windows Multimedia 
      Canales MIDI                                      16 
 
    Funciones del dispositivo DirectMusic: 
      Juego de instrumentos GP integrados               No 
      Juego de sonidos Roland GS integrados             No 
      DirectSound                                       No soportado 
      Colección de ejemplos DLS L1                      No soportado 
      Colección de ejemplos DLS L2                      No soportado 
      Puerto externo MIDI                               No 
      Tamaño de la memoria DLS adosada                  No 
      Puerto compartido                                 Soportado 
      Efecto Coro                                       No soportado 
      Efecto Retraso                                    No soportado 
      Efecto Reverberación                              No soportado 
 
  [ Microsoft GS Wavetable Synth [Emulado] ] 
 
    Propiedades del dispositivo DirectMusic: 
      Descripción del dispositivo                       Microsoft GS Wavetable Synth [Emulado] 
      Tipo de sintetizador                              Hardware 
      Clase de dispositivo                              Puerta de salida 
      Tipo de dispositivo                               Windows Multimedia 
      Canales MIDI                                      16 
 
    Funciones del dispositivo DirectMusic: 
      Juego de instrumentos GP integrados               No 
      Juego de sonidos Roland GS integrados             No 
      DirectSound                                       No soportado 
      Colección de ejemplos DLS L1                      No soportado 
      Colección de ejemplos DLS L2                      No soportado 
      Puerto externo MIDI                               No 
      Tamaño de la memoria DLS adosada                  No 
      Puerto compartido                                 Soportado 
      Efecto Coro                                       No soportado 
      Efecto Retraso                                    No soportado 
      Efecto Reverberación                              No soportado 
 
  [ Microsoft Synthesizer ] 
 
    Propiedades del dispositivo DirectMusic: 
      Descripción del dispositivo                       Microsoft Synthesizer 
      Tipo de sintetizador                              Programas 
      Clase de dispositivo                              Puerta de salida 
      Tipo de dispositivo                               User-Mode Synthesizer 
      Canales de audio                                  2 
      Canales MIDI                                      16000 
      Voces                                             1000 
      Memoria disponible                                Memoria del Sistema 
 
    Funciones del dispositivo DirectMusic: 
      Juego de instrumentos GP integrados               No 
      Juego de sonidos Roland GS integrados             No 
      DirectSound                                       Soportado 
      Colección de ejemplos DLS L1                      Soportado 
      Colección de ejemplos DLS L2                      Soportado 
      Puerto externo MIDI                               No 
      Tamaño de la memoria DLS adosada                  No 
      Puerto compartido                                 No soportado 
      Efecto Coro                                       No soportado 
      Efecto Retraso                                    No soportado 
      Efecto Reverberación                              Soportado 
 
 
--------[ Entradas DirectX ]-------------------------------------------------------------------------------------------- 
 
  [ Ratón ] 
 
    Propiedades del dispositivo DirectInput: 
      Descripción del dispositivo                       Ratón 
      Tipo de dispositivo                               Desconocido 
      Sub-tipo de dispositivo                           Desconocido 
      Axes                                              3 
      Botones/teclas                                    8 
 
    Funciones del dispositivo DirectInput: 
      Dispositivo emulado                               Sí 
      Alias Device                                      No 
      Polled Device                                     No 
      Polled Data Format                                No 
      Attack Force Feedback                             No soportado 
      Deadband Force Feedback                           No soportado 
      Fade Force Feedback                               No soportado 
      Force Feedback                                    No soportado 
      Saturation Force Feedback                         No soportado 
      +/- Force Feedback Coefficients                   No soportado 
      +/- Force Feedback Saturation                     No soportado 
 
  [ Teclado ] 
 
    Propiedades del dispositivo DirectInput: 
      Descripción del dispositivo                       Teclado 
      Tipo de dispositivo                               Desconocido 
      Sub-tipo de dispositivo                           Desconocido 
      Botones/teclas                                    109 
 
    Funciones del dispositivo DirectInput: 
      Dispositivo emulado                               Sí 
      Alias Device                                      No 
      Polled Device                                     No 
      Polled Data Format                                No 
      Attack Force Feedback                             No soportado 
      Deadband Force Feedback                           No soportado 
      Fade Force Feedback                               No soportado 
      Force Feedback                                    No soportado 
      Saturation Force Feedback                         No soportado 
      +/- Force Feedback Coefficients                   No soportado 
      +/- Force Feedback Saturation                     No soportado 
 
  [ Transceptor de infrarrojos eHome de Microsoft ] 
 
    Propiedades del dispositivo DirectInput: 
      Descripción del dispositivo                       Transceptor de infrarrojos eHome de Microsoft 
      Tipo de dispositivo                               Desconocido 
      Sub-tipo de dispositivo                           Desconocido 
 
    Funciones del dispositivo DirectInput: 
      Dispositivo emulado                               Sí 
      Alias Device                                      No 
      Polled Device                                     No 
      Polled Data Format                                No 
      Attack Force Feedback                             No soportado 
      Deadband Force Feedback                           No soportado 
      Fade Force Feedback                               No soportado 
      Force Feedback                                    No soportado 
      Saturation Force Feedback                         No soportado 
      +/- Force Feedback Coefficients                   No soportado 
      +/- Force Feedback Saturation                     No soportado 
 
  [ Transceptor de infrarrojos eHome de Microsoft ] 
 
    Propiedades del dispositivo DirectInput: 
      Descripción del dispositivo                       Transceptor de infrarrojos eHome de Microsoft 
      Tipo de dispositivo                               Desconocido 
      Sub-tipo de dispositivo                           Desconocido 
      Botones/teclas                                    573 
 
    Funciones del dispositivo DirectInput: 
      Dispositivo emulado                               Sí 
      Alias Device                                      No 
      Polled Device                                     No 
      Polled Data Format                                No 
      Attack Force Feedback                             No soportado 
      Deadband Force Feedback                           No soportado 
      Fade Force Feedback                               No soportado 
      Force Feedback                                    No soportado 
      Saturation Force Feedback                         No soportado 
      +/- Force Feedback Coefficients                   No soportado 
      +/- Force Feedback Saturation                     No soportado 
 
  [ Transceptor de infrarrojos eHome de Microsoft ] 
 
    Propiedades del dispositivo DirectInput: 
      Descripción del dispositivo                       Transceptor de infrarrojos eHome de Microsoft 
      Tipo de dispositivo                               Desconocido 
      Sub-tipo de dispositivo                           Desconocido 
 
    Funciones del dispositivo DirectInput: 
      Dispositivo emulado                               Sí 
      Alias Device                                      No 
      Polled Device                                     No 
      Polled Data Format                                No 
      Attack Force Feedback                             No soportado 
      Deadband Force Feedback                           No soportado 
      Fade Force Feedback                               No soportado 
      Force Feedback                                    No soportado 
      Saturation Force Feedback                         No soportado 
      +/- Force Feedback Coefficients                   No soportado 
      +/- Force Feedback Saturation                     No soportado 
 
  [ Transceptor de infrarrojos eHome de Microsoft ] 
 
    Propiedades del dispositivo DirectInput: 
      Descripción del dispositivo                       Transceptor de infrarrojos eHome de Microsoft 
      Tipo de dispositivo                               Desconocido 
      Sub-tipo de dispositivo                           Desconocido 
      Botones/teclas                                    3 
 
    Funciones del dispositivo DirectInput: 
      Dispositivo emulado                               Sí 
      Alias Device                                      No 
      Polled Device                                     No 
      Polled Data Format                                No 
      Attack Force Feedback                             No soportado 
      Deadband Force Feedback                           No soportado 
      Fade Force Feedback                               No soportado 
      Force Feedback                                    No soportado 
      Saturation Force Feedback                         No soportado 
      +/- Force Feedback Coefficients                   No soportado 
      +/- Force Feedback Saturation                     No soportado 
 
 
--------[ Dispositivos Windows ]---------------------------------------------------------------------------------------- 
 
  [ Dispositivos de hardware ] 
 
    Adaptadores de pantalla: 
      NVIDIA GeForce 9300M GS                           7.15.11.7597 
 
    Adaptadores de red: 
      Intel(R) WiFi Link 5100                           12.0.0.78 
      isatap.{D1292219-B3AF-4B62-B7A8-A8EA49D149F4}     6.0.6000.16386 
      isatap.{F6E406B0-F6C6-4F2F-BD36-9A4DA581BFC1}     6.0.6000.16386 
      Minipuerto WAN (IP)                               6.0.6001.18000 
      Minipuerto WAN (IPv6)                             6.0.6001.18000 
      Minipuerto WAN (L2TP)                             6.0.6001.18000 
      Minipuerto WAN (Monitor de red)                   6.0.6001.18000 
      Minipuerto WAN (PPPOE)                            6.0.6001.18000 
      Minipuerto WAN (PPTP)                             6.0.6001.18000 
      Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)6.203.214.2008 
      WAN Miniport (SSTP)                               6.0.6001.18000 
 
    Adaptadores host SD: 
      Controladora de host SD compatible con el estándar SDA6.0.6001.18000 
 
    Baterías: 
      Adaptador de CA de Microsoft                      6.0.6001.18000 
      Batería con método de control compatible con ACPI de Microsoft6.0.6001.18000 
 
    Controladoras de almacenamiento: 
      Iniciador iSCSI de Microsoft                      6.0.6001.18000 
 
    Controladoras de bus serie universal: 
      Concentrador raíz USB                             6.0.6001.22183 
      Concentrador raíz USB                             6.0.6001.22183 
      Concentrador raíz USB                             6.0.6001.22183 
      Concentrador raíz USB                             6.0.6001.22183 
      Concentrador raíz USB                             6.0.6001.22183 
      Concentrador raíz USB                             6.0.6001.22183 
      Concentrador raíz USB                             6.0.6001.22183 
      Concentrador raíz USB                             6.0.6001.22183 
      Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293A6.0.6001.22183 
      Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293C6.0.6001.22183 
      Controlador de host universal USB de la familia Intel(R) ICH8 - 29346.0.6001.22183 
      Controlador de host universal USB de la familia Intel(R) ICH9 - 29356.0.6001.22183 
      Controlador de host universal USB de la familia Intel(R) ICH9 - 29366.0.6001.22183 
      Controlador de host universal USB de la familia Intel(R) ICH9 - 29376.0.6001.22183 
      Controlador de host universal USB de la familia Intel(R) ICH9 - 29386.0.6001.22183 
      Controlador de host universal USB de la familia Intel(R) ICH9 - 29396.0.6001.22183 
      Dispositivo compuesto USB                         6.0.6001.22183 
      Dispositivo de almacenamiento USB                 6.0.6001.18000 
 
    Controladoras host de bus IEEE 1394: 
      Controladora de host RICOH OHCI compatible con IEEE 13946.0.6001.18000 
 
    Controladores ATA/ATAPI IDE: 
      Intel(R) ICH9M-E/M SATA AHCI Controller           8.2.0.1001 
      Ricoh Memory Stick Controller                     6.0.1.11 
      Ricoh xD-Picture Card Controller                  6.0.1.13 
 
    Controladores que no son Plug and Play: 
      Ancilliary Function Driver for Winsock             
      ASMMAP                                             
      ASUS Process Creation/Termination Observer         
      Beep                                               
      CO_Mon                                             
      COH_Mon                                            
      Common Log (CLFS)                                  
      Controlador de autorización de Firewall de Windows 
      Controlador de protocolo TCP/IP                    
      Controlador de soporte TDI heredado NetIO          
      Crcdisk Filter Driver                              
      Dynamic Volume Manager                             
      EraserUtilRebootDrv                                
      ghaio                                              
      HTTP                                               
      IDE Channel                                        
      ISA/EISA Class Driver                              
      Kernel Mode Driver Frameworks service              
      KSecDD                                             
      LDDM Graphics Subsystem                            
      Link-Layer Topology Discovery Mapper I/O Driver    
      Link-Layer Topology Discovery Responder            
      Mount Point Manager                                
      msahci                                             
      NativeWiFi Filter                                  
      NAVENG                                             
      NAVEX15                                            
      NDIS System Driver                                 
      NDIS Usermode I/O Protocol                         
      NDProxy                                            
      NETBT                                              
      NSI proxy service                                  
      Null                                               
      PEAUTH                                             
      Programador de paquetes QoS                        
      Protocolo TCP/IP y TCP/IPv6 orientado a mensajes (sesión SMB) 
      RDP Encoder Mirror Driver                          
      RDPCDD                                             
      Remote Access Auto Connection Driver               
      Remote Access IPv6 ARP Driver                      
      Security Driver                                    
      Security Processor Loader Driver                   
      SPBBCDrv                                           
      SRTSPX                                             
      Storage volumes                                    
      Symantec Eraser Control driver                     
      Symantec Intrusion Prevention Driver               
      Symantec Network Security Intermediate Filter Driver 
      SYMDNS                                             
      SymEvent                                           
      SYMFW                                              
      SYMNDISV                                           
      SYMREDRV                                           
      SYMTDI                                             
      TCP/IP Registry Compatibility                      
      VgaSave                                            
 
    Dispositivos de imagen: 
      USB2.0 1.3M UVC WebCam                            61.5.33.30 
 
    Dispositivos de interfaz de usuario (HID): 
      Dispositivo compatible con HID                    6.1.6001.22000 
      Dispositivo compatible con HID                    6.1.6001.22000 
      Dispositivo compatible con HID                    6.1.6001.22000 
      Dispositivo de control del consumidor compatible con HID6.0.6000.16386 
      Dispositivo de interfaz humana USB                6.1.6001.22000 
      ITECIR Infrared Receiver (EC)                     5.0.4.6 
      Transceptor de infrarrojos eHome de Microsoft     6.1.6001.22000 
 
    Dispositivos de sonido, vídeo y juegos: 
      Dispositivo de audio dúplex completo Unimodem     6.0.6001.18000 
      NVIDIA HDMI Audio                                 1.0.0.28 
      Realtek High Definition Audio                     6.0.1.5643 
 
    Dispositivos del sistema: 
      Administrador de volúmenes                        6.0.6001.18000 
      Altavoz del sistema                               6.0.6001.18000 
      ATK0100 ACPI UTILITY                              1043.2.31.100 
      Batería compuesta de Microsoft                    6.0.6001.18000 
      Botón de característica fija ACPI                 6.0.6001.18000 
      Botón de suspensión ACPI                          6.0.6001.18000 
      Bus PCI                                           6.0.6001.18000 
      Controlador BIOS de Microsoft System Management   6.0.6001.18000 
      Controlador de mouse de Terminal Server           6.0.6001.18000 
      Controlador de teclado de Terminal Server         6.0.6001.18000 
      Controladora de acceso directo a memoria          6.0.6001.18000 
      Controladora de High Definition Audio             6.0.6001.18000 
      Controladora integrada compatible con Microsoft ACPI6.0.6001.18000 
      Controladora programable de interrupciones        6.0.6001.18000 
      Cronómetro del sistema                            6.0.6001.18000 
      Dispositivos IR de consumo                        6.0.6001.18000 
      Enumerador de bus raíz de UMBus                   6.0.6001.18000 
      Enumerador de dispositivos de software Plug and Play6.0.6001.18000 
      Enumerador de UMBus                               6.0.6001.18000 
      Enumerador de UMBus                               6.0.6001.18000 
      Intel(R) ICH9 Family PCI Express Root Port 1 - 29408.6.1.1002 
      Intel(R) ICH9 Family PCI Express Root Port 2 - 29428.6.1.1002 
      Intel(R) ICH9 Family PCI Express Root Port 3 - 29448.6.1.1002 
      Intel(R) ICH9 Family PCI Express Root Port 4 - 29468.6.1.1002 
      Intel(R) ICH9 Family PCI Express Root Port 5 - 29488.6.1.1002 
      Intel(R) ICH9 Family PCI Express Root Port 6 - 294A8.6.1.1002 
      Intel(R) ICH9M LPC Interface Controller - 2919    8.6.1.1002 
      Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A418.7.0.1007 
      Mobile Intel(R) 45 Express Chipset Series Processor to DRAM Controller - 2A408.7.0.1007 
      Procesador de datos numéricos                     6.0.6001.18000 
      Puente PCI Intel(R) 82801 - 2448                  6.0.6001.18000 
      Recursos de la placa base                         6.0.6001.18000 
      Recursos de la placa base                         6.0.6001.18000 
      Recursos de la placa base                         6.0.6001.18000 
      Recursos de la placa base                         6.0.6001.18000 
      Recursos de la placa base                         6.0.6001.18000 
      Recursos de la placa base                         6.0.6001.18000 
      Sistema CMOS/reloj en tiempo real                 6.0.6001.18000 
      Sistema Microsoft compatible con ACPI             6.0.6001.18000 
      Tapa ACPI                                         6.0.6001.18000 
      Tarjeta de sistema                                6.0.6001.18000 
      Temporizador de eventos de alta precisión         6.0.6001.18000 
      Zona térmica ACPI                                 6.0.6001.18000 
 
    Dispositivos portátiles: 
      WALKMAN                                           6.0.6001.18000 
 
    Equipo: 
      Equipo basado en ACPI x86                         6.0.6001.18000 
 
    Instantáneas de volumen de almacenamiento: 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
      Instantánea de volumen genérico                   6.0.6000.16386 
 
    Módems: 
      Agere Systems HDA Modem                           2.1.88.0 
 
    Monitores: 
      Monitor PnP genérico                              6.0.6001.18000 
 
    Mouse y otros dispositivos señaladores: 
      Mouse compatible con HID                          6.0.6001.18000 
      Mouse compatible con HID                          6.0.6001.18000 
      Synaptics PS/2 Port TouchPad                      10.1.6.0 
 
    Personal identification devices: 
      AuthenTec Inc. AES1610                            7.8.1.7 
 
    Procesador: 
      Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz   6.0.6001.18000 
      Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz   6.0.6001.18000 
 
    Radios Bluetooth: 
      BT-253                                            6.0.6001.18000 
 
    Teclados: 
      Keyboard Device Filter                            1.0.0.0 
      Teclado Microsoft eHome MCIR 109                  6.0.6001.18000 
      Teclado Microsoft eHome MCIR                      6.0.6001.18000 
      Teclas del Teclado de control remoto Microsoft eHome6.0.6001.18000 
 
    Unidades de disco: 
      FUJITSU MHX2300BT                                 6.0.6001.18000 
      SONY WALKMAN USB Device                           6.0.6001.18000 
 
    Unidades de DVD o CD-ROM: 
      HL-DT-ST DVDRAM GSA-T50N                          6.0.6001.18000 
 
    Volúmenes de almacenamiento: 
      Volumen genérico                                  6.0.6001.18000 
      Volumen genérico                                  6.0.6001.18000 
 
  [ Adaptadores de pantalla / NVIDIA GeForce 9300M GS ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NVIDIA GeForce 9300M GS 
      Fecha del controlador                             09/06/2008 
      Versión del controlador                           7.15.11.7597 
      Proveedor del controlador                         NVIDIA 
      Archivo INF                                       oem28.inf 
      Identificación del material                       PCI\VEN_10DE&DEV_06E9&SUBSYS_19B21043&REV_A1 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(1,0,0) 
      Dispositivos PCI                                  nVIDIA GeForce 9300M GS (Asus) Video Adapter 
 
    Recursos de los dispositivos: 
      IRQ                                               16 
      Memoria                                           000A0000-000BFFFF 
      Memoria                                           D0000000-DFFFFFFF 
      Memoria                                           F8000000-F9FFFFFF 
      Memoria                                           FB000000-FBFFFFFF 
      Puerto                                            03B0-03BB 
      Puerto                                            03C0-03DF 
      Puerto                                            CC00-CC7F 
 
  [ Adaptadores de red / Intel(R) WiFi Link 5100 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) WiFi Link 5100 
      Fecha del controlador                             21/05/2008 
      Versión del controlador                           12.0.0.78 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem12.inf 
      Identificación del material                       PCI\VEN_8086&DEV_4232&SUBSYS_12018086&REV_00 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(3,0,0) 
      Dispositivos PCI                                  Intel Shirley Peak (Shiloh) 1x2 MC Wireless WiFi Adapter 
 
    Recursos de los dispositivos: 
      IRQ                                               65536 
      Memoria                                           FCFFE000-FCFFFFFF 
 
  [ Adaptadores de red / isatap.{D1292219-B3AF-4B62-B7A8-A8EA49D149F4} ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       isatap.{D1292219-B3AF-4B62-B7A8-A8EA49D149F4} 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       nettun.inf 
      Identificación del material                       *ISATAP 
 
  [ Adaptadores de red / isatap.{F6E406B0-F6C6-4F2F-BD36-9A4DA581BFC1} ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       isatap.{F6E406B0-F6C6-4F2F-BD36-9A4DA581BFC1} 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       nettun.inf 
      Identificación del material                       *ISATAP 
 
  [ Adaptadores de red / Minipuerto WAN (IP) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       WAN Miniport (IP) 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       netrasa.inf 
      Identificación del material                       ms_ndiswanip 
 
  [ Adaptadores de red / Minipuerto WAN (IPv6) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       WAN Miniport (IPv6) 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       netrasa.inf 
      Identificación del material                       ms_ndiswanipv6 
 
  [ Adaptadores de red / Minipuerto WAN (L2TP) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       WAN Miniport (L2TP) 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       netrasa.inf 
      Identificación del material                       ms_l2tpminiport 
 
  [ Adaptadores de red / Minipuerto WAN (Monitor de red) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       WAN Miniport (Network Monitor) 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       netrasa.inf 
      Identificación del material                       ms_ndiswanbh 
 
  [ Adaptadores de red / Minipuerto WAN (PPPOE) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       WAN Miniport (PPPOE) 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       netrasa.inf 
      Identificación del material                       ms_pppoeminiport 
 
  [ Adaptadores de red / Minipuerto WAN (PPTP) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       WAN Miniport (PPTP) 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       netrasa.inf 
      Identificación del material                       ms_pptpminiport 
 
  [ Adaptadores de red / Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) 
      Fecha del controlador                             14/02/2008 
      Versión del controlador                           6.203.214.2008 
      Proveedor del controlador                         Realtek 
      Archivo INF                                       oem9.inf 
      Identificación del material                       PCI\VEN_10EC&DEV_8168&SUBSYS_16D51043&REV_02 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(8,0,0) 
      Dispositivos PCI                                  Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter 
 
    Recursos de los dispositivos: 
      IRQ                                               17 
      Memoria                                           F6FE0000-F6FEFFFF 
      Memoria                                           F6FFF000-F6FFFFFF 
      Puerto                                            E800-E8FF 
 
  [ Adaptadores de red / WAN Miniport (SSTP) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       WAN Miniport (SSTP) 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       netsstpa.inf 
      Identificación del material                       ms_sstpminiport 
 
  [ Adaptadores host SD / Controladora de host SD compatible con el estándar SDA ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SDA Standard Compliant SD Host Controller 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       sdbus.inf 
      Identificación del material                       PCI\VEN_1180&DEV_0822&SUBSYS_18971043&REV_22 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(9,1,1) 
      Dispositivos PCI                                  Ricoh RL5C822 SD Bus Host Adapter 
 
    Recursos de los dispositivos: 
      IRQ                                               17 
      Memoria                                           FDFFF400-FDFFF4FF 
 
  [ Baterías / Adaptador de CA de Microsoft ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Microsoft AC Adapter 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       battery.inf 
      Identificación del material                       ACPI\ACPI0003 
      Dispositivos PnP                                  Microsoft AC Adapter 
 
  [ Baterías / Batería con método de control compatible con ACPI de Microsoft ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Microsoft ACPI-Compliant Control Method Battery 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       battery.inf 
      Identificación del material                       ACPI\PNP0C0A 
      Dispositivos PnP                                  Control Method Battery 
 
  [ Controladoras de almacenamiento / Iniciador iSCSI de Microsoft ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Microsoft iSCSI Initiator 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       iscsi.inf 
      Identificación del material                       ROOT\iSCSIPrt 
 
  [ Controladoras de bus serie universal / Concentrador raíz USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Concentrador raíz USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       USB\ROOT_HUB&VID8086&PID2936&REV0003 
 
  [ Controladoras de bus serie universal / Concentrador raíz USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Concentrador raíz USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       USB\ROOT_HUB&VID8086&PID2937&REV0003 
 
  [ Controladoras de bus serie universal / Concentrador raíz USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Concentrador raíz USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       USB\ROOT_HUB&VID8086&PID2938&REV0003 
 
  [ Controladoras de bus serie universal / Concentrador raíz USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Concentrador raíz USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       USB\ROOT_HUB&VID8086&PID2934&REV0003 
 
  [ Controladoras de bus serie universal / Concentrador raíz USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Concentrador raíz USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       USB\ROOT_HUB&VID8086&PID2935&REV0003 
 
  [ Controladoras de bus serie universal / Concentrador raíz USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Concentrador raíz USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       USB\ROOT_HUB&VID8086&PID2939&REV0003 
 
  [ Controladoras de bus serie universal / Concentrador raíz USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Concentrador raíz USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       USB\ROOT_HUB20&VID8086&PID293A&REV0003 
 
  [ Controladoras de bus serie universal / Concentrador raíz USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Concentrador raíz USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       USB\ROOT_HUB20&VID8086&PID293C&REV0003 
 
  [ Controladoras de bus serie universal / Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293A ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293A 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       PCI\VEN_8086&DEV_293A&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,29,7) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               23 
      Memoria                                           F7FFF800-F7FFFBFF 
 
  [ Controladoras de bus serie universal / Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293C ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293C 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       PCI\VEN_8086&DEV_293C&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,26,7) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               18 
      Memoria                                           F7FFFC00-F7FFFFFF 
 
  [ Controladoras de bus serie universal / Controlador de host universal USB de la familia Intel(R) ICH8 - 2934 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de host universal USB de la familia Intel(R) ICH8 - 2934 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2934&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,29,0) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - USB Universal Host Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               23 
      Puerto                                            B480-B49F 
 
  [ Controladoras de bus serie universal / Controlador de host universal USB de la familia Intel(R) ICH9 - 2935 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de host universal USB de la familia Intel(R) ICH9 - 2935 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2935&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,29,1) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - USB Universal Host Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               19 
      Puerto                                            B400-B41F 
 
  [ Controladoras de bus serie universal / Controlador de host universal USB de la familia Intel(R) ICH9 - 2936 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de host universal USB de la familia Intel(R) ICH9 - 2936 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2936&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,29,2) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - USB Universal Host Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               18 
      Puerto                                            B080-B09F 
 
  [ Controladoras de bus serie universal / Controlador de host universal USB de la familia Intel(R) ICH9 - 2937 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de host universal USB de la familia Intel(R) ICH9 - 2937 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2937&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,26,0) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - USB Universal Host Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               16 
      Puerto                                            BC00-BC1F 
 
  [ Controladoras de bus serie universal / Controlador de host universal USB de la familia Intel(R) ICH9 - 2938 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de host universal USB de la familia Intel(R) ICH9 - 2938 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2938&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,26,1) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - USB Universal Host Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               21 
      Puerto                                            B880-B89F 
 
  [ Controladoras de bus serie universal / Controlador de host universal USB de la familia Intel(R) ICH9 - 2939 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de host universal USB de la familia Intel(R) ICH9 - 2939 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbport.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2939&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,26,2) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - USB Universal Host Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               19 
      Puerto                                            B800-B81F 
 
  [ Controladoras de bus serie universal / Dispositivo compuesto USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dispositivo compuesto USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.22183 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usb.inf 
      Identificación del material                       USB\VID_04F2&PID_B033&REV_6012 
      Location Information                              Port_#0005.Hub_#0008 
 
  [ Controladoras de bus serie universal / Dispositivo de almacenamiento USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dispositivo de almacenamiento USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       usbstor.inf 
      Identificación del material                       USB\VID_054C&PID_031A&REV_0001 
      Location Information                              Port_#0004.Hub_#0008 
 
  [ Controladoras host de bus IEEE 1394 / Controladora de host RICOH OHCI compatible con IEEE 1394 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       RICOH OHCI Compliant IEEE 1394 Host Controller 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       1394.inf 
      Identificación del material                       PCI\VEN_1180&DEV_0832&SUBSYS_18971043&REV_05 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(9,1,0) 
      Dispositivos PCI                                  Ricoh RL5C832 IEEE1394 Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               16 
      Memoria                                           FDFFF800-FDFFFFFF 
 
  [ Controladores ATA/ATAPI IDE / Intel(R) ICH9M-E/M SATA AHCI Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) ICH9M-E/M SATA AHCI Controller 
      Fecha del controlador                             07/05/2008 
      Versión del controlador                           8.2.0.1001 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem7.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2929&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,31,2) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - 4-port SATA AHCI Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               19 
      Memoria                                           F7FFF000-F7FFF7FF 
      Puerto                                            A480-A49F 
      Puerto                                            A800-A803 
      Puerto                                            A880-A887 
      Puerto                                            AC00-AC03 
      Puerto                                            B000-B007 
 
  [ Controladores ATA/ATAPI IDE / Ricoh Memory Stick Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Ricoh Memory Stick Controller 
      Fecha del controlador                             30/07/2007 
      Versión del controlador                           6.0.1.11 
      Proveedor del controlador                         Ricoh Company 
      Archivo INF                                       oem15.inf 
      Identificación del material                       PCI\VEN_1180&DEV_0592&SUBSYS_18971043&REV_12 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(9,1,2) 
      Dispositivos PCI                                  Ricoh RL5C592 Memory Stick Bus Host Adapter 
 
    Recursos de los dispositivos: 
      IRQ                                               17 
      Memoria                                           FDFFF000-FDFFF0FF 
 
  [ Controladores ATA/ATAPI IDE / Ricoh xD-Picture Card Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Ricoh xD-Picture Card Controller 
      Fecha del controlador                             30/07/2007 
      Versión del controlador                           6.0.1.13 
      Proveedor del controlador                         Ricoh Company 
      Archivo INF                                       oem14.inf 
      Identificación del material                       PCI\VEN_1180&DEV_0852&SUBSYS_18971043&REV_12 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(9,1,3) 
      Dispositivos PCI                                  Ricoh RL5C852 xD-Picture Card Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               17 
      Memoria                                           FDFFEC00-FDFFECFF 
 
  [ Controladores que no son Plug and Play / Ancilliary Function Driver for Winsock ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Ancilliary Function Driver for Winsock 
 
  [ Controladores que no son Plug and Play / ASMMAP ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ASMMAP 
 
  [ Controladores que no son Plug and Play / ASUS Process Creation/Termination Observer ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ASUS Process Creation/Termination Observer 
 
  [ Controladores que no son Plug and Play / Beep ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Beep 
 
  [ Controladores que no son Plug and Play / CO_Mon ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       CO_Mon 
 
  [ Controladores que no son Plug and Play / COH_Mon ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       COH_Mon 
 
  [ Controladores que no son Plug and Play / Common Log (CLFS) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Common Log (CLFS) 
 
  [ Controladores que no son Plug and Play / Controlador de autorización de Firewall de Windows ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de autorización de Firewall de Windows 
 
  [ Controladores que no son Plug and Play / Controlador de protocolo TCP/IP ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de protocolo TCP/IP 
 
  [ Controladores que no son Plug and Play / Controlador de soporte TDI heredado NetIO ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de soporte TDI heredado NetIO 
 
  [ Controladores que no son Plug and Play / Crcdisk Filter Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Crcdisk Filter Driver 
 
  [ Controladores que no son Plug and Play / Dynamic Volume Manager ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dynamic Volume Manager 
 
  [ Controladores que no son Plug and Play / EraserUtilRebootDrv ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       EraserUtilRebootDrv 
 
  [ Controladores que no son Plug and Play / ghaio ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ghaio 
 
  [ Controladores que no son Plug and Play / HTTP ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       HTTP 
 
  [ Controladores que no son Plug and Play / IDE Channel ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       IDE Channel 
 
  [ Controladores que no son Plug and Play / ISA/EISA Class Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ISA/EISA Class Driver 
 
  [ Controladores que no son Plug and Play / Kernel Mode Driver Frameworks service ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Kernel Mode Driver Frameworks service 
 
  [ Controladores que no son Plug and Play / KSecDD ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       KSecDD 
 
  [ Controladores que no son Plug and Play / LDDM Graphics Subsystem ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       LDDM Graphics Subsystem 
 
  [ Controladores que no son Plug and Play / Link-Layer Topology Discovery Mapper I/O Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Link-Layer Topology Discovery Mapper I/O Driver 
 
  [ Controladores que no son Plug and Play / Link-Layer Topology Discovery Responder ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Link-Layer Topology Discovery Responder 
 
  [ Controladores que no son Plug and Play / Mount Point Manager ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Mount Point Manager 
 
  [ Controladores que no son Plug and Play / msahci ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       msahci 
 
  [ Controladores que no son Plug and Play / NativeWiFi Filter ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NativeWiFi Filter 
 
  [ Controladores que no son Plug and Play / NAVENG ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NAVENG 
 
  [ Controladores que no son Plug and Play / NAVEX15 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NAVEX15 
 
  [ Controladores que no son Plug and Play / NDIS System Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NDIS System Driver 
 
  [ Controladores que no son Plug and Play / NDIS Usermode I/O Protocol ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NDIS Usermode I/O Protocol 
 
  [ Controladores que no son Plug and Play / NDProxy ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NDProxy 
 
  [ Controladores que no son Plug and Play / NETBT ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NETBT 
 
  [ Controladores que no son Plug and Play / NSI proxy service ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NSI proxy service 
 
  [ Controladores que no son Plug and Play / Null ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Null 
 
  [ Controladores que no son Plug and Play / PEAUTH ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       PEAUTH 
 
  [ Controladores que no son Plug and Play / Programador de paquetes QoS ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Programador de paquetes QoS 
 
  [ Controladores que no son Plug and Play / Protocolo TCP/IP y TCP/IPv6 orientado a mensajes (sesión SMB) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Protocolo TCP/IP y TCP/IPv6 orientado a mensajes (sesión SMB) 
 
  [ Controladores que no son Plug and Play / RDP Encoder Mirror Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       RDP Encoder Mirror Driver 
 
  [ Controladores que no son Plug and Play / RDPCDD ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       RDPCDD 
 
  [ Controladores que no son Plug and Play / Remote Access Auto Connection Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Remote Access Auto Connection Driver 
 
  [ Controladores que no son Plug and Play / Remote Access IPv6 ARP Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Remote Access IPv6 ARP Driver 
 
  [ Controladores que no son Plug and Play / Security Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Security Driver 
 
  [ Controladores que no son Plug and Play / Security Processor Loader Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Security Processor Loader Driver 
 
  [ Controladores que no son Plug and Play / SPBBCDrv ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SPBBCDrv 
 
  [ Controladores que no son Plug and Play / SRTSPX ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SRTSPX 
 
  [ Controladores que no son Plug and Play / Storage volumes ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Storage volumes 
 
  [ Controladores que no son Plug and Play / Symantec Eraser Control driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Symantec Eraser Control driver 
 
  [ Controladores que no son Plug and Play / Symantec Intrusion Prevention Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Symantec Intrusion Prevention Driver 
 
  [ Controladores que no son Plug and Play / Symantec Network Security Intermediate Filter Driver ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Symantec Network Security Intermediate Filter Driver 
 
  [ Controladores que no son Plug and Play / SYMDNS ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SYMDNS 
 
  [ Controladores que no son Plug and Play / SymEvent ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SymEvent 
 
  [ Controladores que no son Plug and Play / SYMFW ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SYMFW 
 
  [ Controladores que no son Plug and Play / SYMNDISV ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SYMNDISV 
 
  [ Controladores que no son Plug and Play / SYMREDRV ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SYMREDRV 
 
  [ Controladores que no son Plug and Play / SYMTDI ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SYMTDI 
 
  [ Controladores que no son Plug and Play / TCP/IP Registry Compatibility ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       TCP/IP Registry Compatibility 
 
  [ Controladores que no son Plug and Play / VgaSave ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       VgaSave 
 
  [ Dispositivos de imagen / USB2.0 1.3M UVC WebCam ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       USB2.0 1.3M UVC WebCam 
      Fecha del controlador                             15/10/2007 
      Versión del controlador                           61.5.33.30 
      Proveedor del controlador                         Chicony,(EM2760) 
      Archivo INF                                       oem17.inf 
      Identificación del material                       USB\VID_04F2&PID_B033&REV_6012&MI_00 
      Location Information                              0000.001d.0007.005.000.000.000.000.000 
 
  [ Dispositivos de interfaz de usuario (HID) / Dispositivo compatible con HID ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dispositivo compatible con HID 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.1.6001.22000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       input.inf 
      Identificación del material                       HID\IrDevice&Col01 
 
  [ Dispositivos de interfaz de usuario (HID) / Dispositivo compatible con HID ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dispositivo compatible con HID 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.1.6001.22000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       input.inf 
      Identificación del material                       HID\IrDevice&Col03 
 
  [ Dispositivos de interfaz de usuario (HID) / Dispositivo compatible con HID ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dispositivo compatible con HID 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.1.6001.22000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       input.inf 
      Identificación del material                       HID\IrDevice&Col04 
 
  [ Dispositivos de interfaz de usuario (HID) / Dispositivo de control del consumidor compatible con HID ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dispositivo de control del consumidor compatible con HID 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       hidserv.inf 
      Identificación del material                       HID\IrDevice&Col02 
 
  [ Dispositivos de interfaz de usuario (HID) / Dispositivo de interfaz humana USB ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dispositivo de interfaz humana USB 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.1.6001.22000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       input.inf 
      Identificación del material                       USB\VID_046D&PID_C019&REV_4301 
      Location Information                              Port_#0001.Hub_#0006 
 
  [ Dispositivos de interfaz de usuario (HID) / ITECIR Infrared Receiver (EC) ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ITECIR Infrared Receiver (EC) 
      Fecha del controlador                             18/12/2007 
      Versión del controlador                           5.0.4.6 
      Proveedor del controlador                         ITE Tech.Inc. 
      Archivo INF                                       oem16.inf 
      Identificación del material                       ACPI\ITE8708 
      Dispositivos PnP                                  ITE CIR Infrared Receiver 
 
    Recursos de los dispositivos: 
      IRQ                                               04 
      Puerto                                            0300-0307 
 
  [ Dispositivos de interfaz de usuario (HID) / Transceptor de infrarrojos eHome de Microsoft ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Transceptor de infrarrojos eHome de Microsoft 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.1.6001.22000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       input.inf 
      Identificación del material                       CIRCLASS\IrDevice 
 
  [ Dispositivos de sonido, vídeo y juegos / Dispositivo de audio dúplex completo Unimodem ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dispositivo de audio dúplex completo Unimodem 
      Fecha del controlador                             26/01/1999 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       modemcsa.inf 
      Identificación del material                       MODEMWAVE\FULLDUPLEX 
 
  [ Dispositivos de sonido, vídeo y juegos / NVIDIA HDMI Audio ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       NVIDIA HDMI Audio 
      Fecha del controlador                             22/05/2008 
      Versión del controlador                           1.0.0.28 
      Proveedor del controlador                         NVIDIA Corporation 
      Archivo INF                                       oem8.inf 
      Identificación del material                       HDAUDIO\FUNC_01&VEN_10DE&DEV_0003&SUBSYS_10DE0101&REV_1000 
      Location Information                              Internal High Definition Audio Bus 
 
  [ Dispositivos de sonido, vídeo y juegos / Realtek High Definition Audio ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Realtek High Definition Audio 
      Fecha del controlador                             13/06/2008 
      Versión del controlador                           6.0.1.5643 
      Proveedor del controlador                         Realtek Semiconductor Corp. 
      Archivo INF                                       oem11.inf 
      Identificación del material                       HDAUDIO\FUNC_01&VEN_10EC&DEV_0663&SUBSYS_10431893&REV_1000 
      Location Information                              Internal High Definition Audio Bus 
 
  [ Dispositivos del sistema / Administrador de volúmenes ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Volume Manager 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ROOT\VOLMGR 
 
  [ Dispositivos del sistema / Altavoz del sistema ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       System speaker 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0800 
      Dispositivos PnP                                  PC Speaker 
 
    Recursos de los dispositivos: 
      Puerto                                            0061-0061 
 
  [ Dispositivos del sistema / ATK0100 ACPI UTILITY ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ATK0100 ACPI UTILITY 
      Fecha del controlador                             14/12/2006 
      Versión del controlador                           1043.2.31.100 
      Proveedor del controlador                         ATK 
      Archivo INF                                       oem2.inf 
      Identificación del material                       ACPI\ATK0100 
      Dispositivos PnP                                  Asus ATK-100 ACPI Utility 
 
  [ Dispositivos del sistema / Batería compuesta de Microsoft ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Microsoft Composite Battery 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       acpi.inf 
      Identificación del material                       COMPOSITE_BATTERY 
 
  [ Dispositivos del sistema / Botón de característica fija ACPI ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ACPI Fixed Feature Button 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\FixedButton 
 
  [ Dispositivos del sistema / Botón de suspensión ACPI ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ACPI Sleep Button 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C0E 
      Dispositivos PnP                                  Sleep Button 
 
  [ Dispositivos del sistema / Bus PCI ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       PCI bus 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0A08 
      Dispositivos PnP                                  ACPI Three-wire Device Bus 
 
    Recursos de los dispositivos: 
      Memoria                                           000A0000-000BFFFF 
      Memoria                                           000D0000-000DFFFF 
      Memoria                                           C0000000-FFFFFFFF 
      Puerto                                            0000-0CF7 
      Puerto                                            0D00-FFFF 
 
  [ Dispositivos del sistema / Controlador BIOS de Microsoft System Management ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Microsoft System Management BIOS Driver 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       root\mssmbios 
 
  [ Dispositivos del sistema / Controlador de mouse de Terminal Server ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Controlador de mouse de Terminal Server 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ROOT\RDP_MOU 
 
  [ Dispositivos del sistema / Controlador de teclado de Terminal Server ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Terminal Server Keyboard Driver 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ROOT\RDP_KBD 
 
  [ Dispositivos del sistema / Controladora de acceso directo a memoria ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Direct memory access controller 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0200 
      Dispositivos PnP                                  DMA Controller 
 
    Recursos de los dispositivos: 
      DMA                                               04 
      Puerto                                            0000-000F 
      Puerto                                            0081-0083 
      Puerto                                            0087-0087 
      Puerto                                            0089-008B 
      Puerto                                            008F-008F 
      Puerto                                            00C0-00DF 
 
  [ Dispositivos del sistema / Controladora de High Definition Audio ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       High Definition Audio Controller 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       hdaudbus.inf 
      Identificación del material                       PCI\VEN_8086&DEV_293E&SUBSYS_18931043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,27,0) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - High Definition Audio Controller 
 
    Recursos de los dispositivos: 
      IRQ                                               22 
      Memoria                                           F7FF8000-F7FFBFFF 
 
  [ Dispositivos del sistema / Controladora integrada compatible con Microsoft ACPI ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Microsoft ACPI-Compliant Embedded Controller 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C09 
      Dispositivos PnP                                  Embedded Controller Device 
 
    Recursos de los dispositivos: 
      Puerto                                            0062-0062 
      Puerto                                            0066-0066 
 
  [ Dispositivos del sistema / Controladora programable de interrupciones ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Programmable interrupt controller 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0000 
      Dispositivos PnP                                  Programmable Interrupt Controller 
 
    Recursos de los dispositivos: 
      Puerto                                            0020-0021 
      Puerto                                            00A0-00A1 
 
  [ Dispositivos del sistema / Cronómetro del sistema ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       System timer 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0100 
      Dispositivos PnP                                  System Timer 
 
    Recursos de los dispositivos: 
      IRQ                                               00 
      Puerto                                            0040-0043 
 
  [ Dispositivos del sistema / Dispositivos IR de consumo ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Dispositivos IR de consumo 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       circlass.inf 
      Identificación del material                       ROOT\CIRClass 
 
  [ Dispositivos del sistema / Enumerador de bus raíz de UMBus ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       UMBus Root Bus Enumerator 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       umbus.inf 
      Identificación del material                       root\umbus 
 
  [ Dispositivos del sistema / Enumerador de dispositivos de software Plug and Play ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Plug and Play Software Device Enumerator 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       root\swenum 
 
  [ Dispositivos del sistema / Enumerador de UMBus ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       UMBus Enumerator 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       umbus.inf 
      Identificación del material                       UMB\UMBUS 
 
  [ Dispositivos del sistema / Enumerador de UMBus ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Enumerador de UMBus 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       umbus.inf 
      Identificación del material                       UMB\UMBUS 
 
  [ Dispositivos del sistema / Intel(R) ICH9 Family PCI Express Root Port 1 - 2940 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) ICH9 Family PCI Express Root Port 1 - 2940 
      Fecha del controlador                             20/02/2008 
      Versión del controlador                           8.6.1.1002 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem5.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2940&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,28,0) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - PCI Express Root Port 1 
 
    Recursos de los dispositivos: 
      IRQ                                               65536 
 
  [ Dispositivos del sistema / Intel(R) ICH9 Family PCI Express Root Port 2 - 2942 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) ICH9 Family PCI Express Root Port 2 - 2942 
      Fecha del controlador                             20/02/2008 
      Versión del controlador                           8.6.1.1002 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem5.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2942&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,28,1) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - PCI Express Root Port 2 
 
    Recursos de los dispositivos: 
      IRQ                                               65536 
      Memoria                                           FCF00000-FCFFFFFF 
 
  [ Dispositivos del sistema / Intel(R) ICH9 Family PCI Express Root Port 3 - 2944 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) ICH9 Family PCI Express Root Port 3 - 2944 
      Fecha del controlador                             20/02/2008 
      Versión del controlador                           8.6.1.1002 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem5.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2944&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,28,2) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - PCI Express Root Port 3 
 
    Recursos de los dispositivos: 
      IRQ                                               65536 
      Memoria                                           F4000000-F6EFFFFF 
      Memoria                                           FD000000-FDDFFFFF 
      Puerto                                            D000-DFFF 
 
  [ Dispositivos del sistema / Intel(R) ICH9 Family PCI Express Root Port 4 - 2946 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) ICH9 Family PCI Express Root Port 4 - 2946 
      Fecha del controlador                             20/02/2008 
      Versión del controlador                           8.6.1.1002 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem5.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2946&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,28,3) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - PCI Express Root Port 4 
 
    Recursos de los dispositivos: 
      IRQ                                               65536 
 
  [ Dispositivos del sistema / Intel(R) ICH9 Family PCI Express Root Port 5 - 2948 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) ICH9 Family PCI Express Root Port 5 - 2948 
      Fecha del controlador                             20/02/2008 
      Versión del controlador                           8.6.1.1002 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem5.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2948&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,28,4) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - PCI Express Root Port 5 
 
    Recursos de los dispositivos: 
      IRQ                                               65536 
 
  [ Dispositivos del sistema / Intel(R) ICH9 Family PCI Express Root Port 6 - 294A ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) ICH9 Family PCI Express Root Port 6 - 294A 
      Fecha del controlador                             20/02/2008 
      Versión del controlador                           8.6.1.1002 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem5.inf 
      Identificación del material                       PCI\VEN_8086&DEV_294A&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,28,5) 
      Dispositivos PCI                                  Intel 82801IB ICH9 - PCI Express Root Port 6 
 
    Recursos de los dispositivos: 
      IRQ                                               65536 
      Memoria                                           F6F00000-F6FFFFFF 
      Memoria                                           FDE00000-FDEFFFFF 
      Puerto                                            E000-EFFF 
 
  [ Dispositivos del sistema / Intel(R) ICH9M LPC Interface Controller - 2919 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) ICH9M LPC Interface Controller - 2919 
      Fecha del controlador                             20/02/2008 
      Versión del controlador                           8.6.1.1002 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem5.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2919&SUBSYS_18971043&REV_03 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,31,0) 
      Dispositivos PCI                                  Intel 82801IM ICH9-M - LPC Bridge 
 
  [ Dispositivos del sistema / Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A41 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A41 
      Fecha del controlador                             20/02/2008 
      Versión del controlador                           8.7.0.1007 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem6.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2A41&SUBSYS_18971043&REV_07 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,1,0) 
      Dispositivos PCI                                  Intel GL40/GM45/GS45/PM45 Chipset - PCI Express Graphics Root Port [B-3] 
 
    Recursos de los dispositivos: 
      IRQ                                               65536 
      Memoria                                           000A0000-000BFFFF 
      Memoria                                           D0000000-DFFFFFFF 
      Memoria                                           F8000000-FBFFFFFF 
      Puerto                                            03B0-03BB 
      Puerto                                            03C0-03DF 
      Puerto                                            C000-CFFF 
 
  [ Dispositivos del sistema / Mobile Intel(R) 45 Express Chipset Series Processor to DRAM Controller - 2A40 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Mobile Intel(R) 45 Express Chipset Series Processor to DRAM Controller - 2A40 
      Fecha del controlador                             20/02/2008 
      Versión del controlador                           8.7.0.1007 
      Proveedor del controlador                         Intel 
      Archivo INF                                       oem6.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2A40&SUBSYS_18971043&REV_07 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,0,0) 
      Dispositivos PCI                                  Intel GL40/GM45/GS45/PM45 Chipset - Memory Controller Hub [B-3] 
 
  [ Dispositivos del sistema / Procesador de datos numéricos ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Numeric data processor 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C04 
      Dispositivos PnP                                  Numeric Data Processor 
 
    Recursos de los dispositivos: 
      IRQ                                               13 
      Puerto                                            00F0-00FF 
 
  [ Dispositivos del sistema / Puente PCI Intel(R) 82801 - 2448 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) 82801 PCI Bridge - 2448 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       PCI\VEN_8086&DEV_2448&SUBSYS_18971043&REV_93 
      Location Information                              @system32\drivers\pci.sys,#65536;PCI bus %1, device %2, function %3;(0,30,0) 
      Dispositivos PCI                                  Intel 82801IBM/JBM I/O Controller Hub 9/10 (ICH9M/10M) 
 
    Recursos de los dispositivos: 
      Memoria                                           FDF00000-FDFFFFFF 
 
  [ Dispositivos del sistema / Recursos de la placa base ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Motherboard resources 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C02 
      Dispositivos PnP                                  Motherboard Resources 
 
    Recursos de los dispositivos: 
      Memoria                                           E0000000-EFFFFFFF 
 
  [ Dispositivos del sistema / Recursos de la placa base ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Motherboard resources 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C02 
      Dispositivos PnP                                  Motherboard Resources 
 
    Recursos de los dispositivos: 
      Memoria                                           FED10000-FED19FFF 
 
  [ Dispositivos del sistema / Recursos de la placa base ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Motherboard resources 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C02 
      Dispositivos PnP                                  Motherboard Resources 
 
    Recursos de los dispositivos: 
      Memoria                                           FEC00000-FEC00FFF 
      Memoria                                           FEC10000-FEC17FFF 
      Memoria                                           FEC18000-FEC1FFFF 
      Memoria                                           FEC20000-FEC27FFF 
      Memoria                                           FEC28000-FEC2FFFF 
      Memoria                                           FEC30000-FEC37FFF 
      Memoria                                           FEC38000-FEC3FFFF 
      Memoria                                           FEE00000-FEE00FFF 
      Puerto                                            0250-0253 
      Puerto                                            0256-025F 
 
  [ Dispositivos del sistema / Recursos de la placa base ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Motherboard resources 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C02 
      Dispositivos PnP                                  Motherboard Resources 
 
    Recursos de los dispositivos: 
      Memoria                                           F7FFEC00-F7FFECFF 
      Memoria                                           FED1C000-FED1FFFF 
      Memoria                                           FED20000-FED3FFFF 
      Memoria                                           FED45000-FED89FFF 
      Memoria                                           FED90000-FED90FFF 
      Memoria                                           FED91000-FED91FFF 
      Memoria                                           FED92000-FED92FFF 
      Memoria                                           FED93000-FED93FFF 
      Memoria                                           FFB00000-FFBFFFFF 
      Memoria                                           FFF00000-FFFFFFFF 
      Puerto                                            0010-001F 
      Puerto                                            0022-003F 
      Puerto                                            0044-005F 
      Puerto                                            0063-0063 
      Puerto                                            0065-0065 
      Puerto                                            0067-006F 
      Puerto                                            0072-007F 
      Puerto                                            0080-0080 
      Puerto                                            0084-0086 
      Puerto                                            0088-0088 
      Puerto                                            008C-008E 
      Puerto                                            0090-009F 
      Puerto                                            00A2-00BF 
      Puerto                                            00E0-00EF 
      Puerto                                            0400-041F 
      Puerto                                            04D0-04D1 
      Puerto                                            0500-057F 
      Puerto                                            0800-087F 
 
  [ Dispositivos del sistema / Recursos de la placa base ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Motherboard resources 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C02 
      Dispositivos PnP                                  Motherboard Resources 
 
    Recursos de los dispositivos: 
      Memoria                                           FFA00000-FFBFFFFF 
      Memoria                                           FFE00000-FFFFFFFF 
 
  [ Dispositivos del sistema / Recursos de la placa base ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Motherboard resources 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C02 
      Dispositivos PnP                                  Motherboard Resources 
 
    Recursos de los dispositivos: 
      Memoria                                           FFC00000-FFDFFFFF 
 
  [ Dispositivos del sistema / Sistema CMOS/reloj en tiempo real ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       System CMOS/real time clock 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0B00 
      Dispositivos PnP                                  Real-Time Clock 
 
    Recursos de los dispositivos: 
      IRQ                                               08 
      Puerto                                            0070-0071 
 
  [ Dispositivos del sistema / Sistema Microsoft compatible con ACPI ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Microsoft ACPI-Compliant System 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       acpi.inf 
      Identificación del material                       ACPI_HAL\PNP0C08 
      Dispositivos PnP                                  ACPI Driver/BIOS 
 
    Recursos de los dispositivos: 
      IRQ                                               100 
      IRQ                                               101 
      IRQ                                               102 
      IRQ                                               103 
      IRQ                                               104 
      IRQ                                               105 
      IRQ                                               106 
      IRQ                                               107 
      IRQ                                               108 
      IRQ                                               109 
      IRQ                                               110 
      IRQ                                               111 
      IRQ                                               112 
      IRQ                                               113 
      IRQ                                               114 
      IRQ                                               115 
      IRQ                                               116 
      IRQ                                               117 
      IRQ                                               118 
      IRQ                                               119 
      IRQ                                               120 
      IRQ                                               121 
      IRQ                                               122 
      IRQ                                               123 
      IRQ                                               124 
      IRQ                                               125 
      IRQ                                               126 
      IRQ                                               127 
      IRQ                                               128 
      IRQ                                               129 
      IRQ                                               130 
      IRQ                                               131 
      IRQ                                               132 
      IRQ                                               133 
      IRQ                                               134 
      IRQ                                               135 
      IRQ                                               136 
      IRQ                                               137 
      IRQ                                               138 
      IRQ                                               139 
      IRQ                                               140 
      IRQ                                               141 
      IRQ                                               142 
      IRQ                                               143 
      IRQ                                               144 
      IRQ                                               145 
      IRQ                                               146 
      IRQ                                               147 
      IRQ                                               148 
      IRQ                                               149 
      IRQ                                               150 
      IRQ                                               151 
      IRQ                                               152 
      IRQ                                               153 
      IRQ                                               154 
      IRQ                                               155 
      IRQ                                               156 
      IRQ                                               157 
      IRQ                                               158 
      IRQ                                               159 
      IRQ                                               160 
      IRQ                                               161 
      IRQ                                               162 
      IRQ                                               163 
      IRQ                                               164 
      IRQ                                               165 
      IRQ                                               166 
      IRQ                                               167 
      IRQ                                               168 
      IRQ                                               169 
      IRQ                                               170 
      IRQ                                               171 
      IRQ                                               172 
      IRQ                                               173 
      IRQ                                               174 
      IRQ                                               175 
      IRQ                                               176 
      IRQ                                               177 
      IRQ                                               178 
      IRQ                                               179 
      IRQ                                               180 
      IRQ                                               181 
      IRQ                                               182 
      IRQ                                               183 
      IRQ                                               184 
      IRQ                                               185 
      IRQ                                               186 
      IRQ                                               187 
      IRQ                                               188 
      IRQ                                               189 
      IRQ                                               190 
      IRQ                                               81 
      IRQ                                               82 
      IRQ                                               83 
      IRQ                                               84 
      IRQ                                               85 
      IRQ                                               86 
      IRQ                                               87 
      IRQ                                               88 
      IRQ                                               89 
      IRQ                                               90 
      IRQ                                               91 
      IRQ                                               92 
      IRQ                                               93 
      IRQ                                               94 
      IRQ                                               95 
      IRQ                                               96 
      IRQ                                               97 
      IRQ                                               98 
      IRQ                                               99 
 
  [ Dispositivos del sistema / Tapa ACPI ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ACPI Lid 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C0D 
      Dispositivos PnP                                  Lid 
 
  [ Dispositivos del sistema / Tarjeta de sistema ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       System board 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0C01 
      Dispositivos PnP                                  System Board Extension 
 
    Recursos de los dispositivos: 
      Memoria                                           00000000-0009FFFF 
      Memoria                                           000C0000-000CFFFF 
      Memoria                                           000E0000-000FFFFF 
      Memoria                                           00100000-BFFFFFFF 
 
  [ Dispositivos del sistema / Temporizador de eventos de alta precisión ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       High precision event timer 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\PNP0103 
      Dispositivos PnP                                  High Precision Event Timer 
 
    Recursos de los dispositivos: 
      Memoria                                           FED00000-FED003FF 
 
  [ Dispositivos del sistema / Zona térmica ACPI ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ACPI Thermal Zone 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       machine.inf 
      Identificación del material                       ACPI\ThermalZone 
 
  [ Dispositivos portátiles / WALKMAN ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       WALKMAN 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       wpdfs.inf 
 
  [ Equipo / Equipo basado en ACPI x86 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       ACPI x86-based PC 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       hal.inf 
      Identificación del material                       acpiapic 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Generic volume shadow copy 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Generic volume shadow copy 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Instantáneas de volumen de almacenamiento / Instantánea de volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Instantánea de volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6000.16386 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volsnap.inf 
      Identificación del material                       STORAGE\VolumeSnapshot 
 
  [ Módems / Agere Systems HDA Modem ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Agere Systems HDA Modem 
      Fecha del controlador                             21/03/2008 
      Versión del controlador                           2.1.88.0 
      Proveedor del controlador                         Agere 
      Archivo INF                                       oem10.inf 
      Identificación del material                       HDAUDIO\FUNC_02&VEN_11C1&DEV_1040&SUBSYS_10431636&REV_1002 
      Location Information                              Internal High Definition Audio Bus 
 
  [ Monitores / Monitor PnP genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Monitor PnP genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       monitor.inf 
      Identificación del material                       MONITOR\CPT1465 
      Monitor                                           Chunghwa CLAA154WP05A  
 
  [ Mouse y otros dispositivos señaladores / Mouse compatible con HID ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Mouse compatible con HID 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       msmouse.inf 
      Identificación del material                       HID\VID_046D&PID_C019&REV_4301 
 
  [ Mouse y otros dispositivos señaladores / Mouse compatible con HID ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Mouse compatible con HID 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       msmouse.inf 
      Identificación del material                       HID\IrDevice&Col08 
 
  [ Mouse y otros dispositivos señaladores / Synaptics PS/2 Port TouchPad ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Synaptics PS/2 Port TouchPad 
      Fecha del controlador                             16/11/2007 
      Versión del controlador                           10.1.6.0 
      Proveedor del controlador                         Synaptics 
      Archivo INF                                       oem20.inf 
      Identificación del material                       ACPI\SYN0A0F 
      Dispositivos PnP                                  Synaptics PS/2 Port TouchPad 
 
    Recursos de los dispositivos: 
      IRQ                                               12 
 
  [ Personal identification devices / AuthenTec Inc. AES1610 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       AuthenTec Inc. AES1610 
      Fecha del controlador                             16/06/2007 
      Versión del controlador                           7.8.1.7 
      Proveedor del controlador                         AuthenTec, Inc. 
      Archivo INF                                       oem18.inf 
      Identificación del material                       USB\VID_08FF&PID_1600&REV_0<10 
      Location Information                              Port_#0002.Hub_#0003 
 
  [ Procesador / Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       cpu.inf 
      Identificación del material                       ACPI\GenuineIntel_-_x86_Family_6_Model_23 
 
  [ Procesador / Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       cpu.inf 
      Identificación del material                       ACPI\GenuineIntel_-_x86_Family_6_Model_23 
 
  [ Radios Bluetooth / BT-253 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       BT-253 
      Fecha del controlador                             25/03/2008 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Broadcom 
      Archivo INF                                       oem21.inf 
      Identificación del material                       USB\VID_0B05&PID_1751&REV_0235 
      Location Information                              Port_#0001.Hub_#0003 
 
  [ Teclados / Keyboard Device Filter ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Keyboard Device Filter 
      Fecha del controlador                             24/01/2007 
      Versión del controlador                           1.0.0.0 
      Proveedor del controlador                         ATK 
      Archivo INF                                       oem3.inf 
      Identificación del material                       ACPI\PNP0303 
      Dispositivos PnP                                  101/102-Key or MS Natural Keyboard 
 
    Recursos de los dispositivos: 
      IRQ                                               01 
      Puerto                                            0060-0060 
      Puerto                                            0064-0064 
 
  [ Teclados / Teclado Microsoft eHome MCIR 109 ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Teclado Microsoft eHome MCIR 109 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       keyboard.inf 
      Identificación del material                       HID\IrDevice&Col07 
 
  [ Teclados / Teclado Microsoft eHome MCIR ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Teclado Microsoft eHome MCIR 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       keyboard.inf 
      Identificación del material                       HID\IrDevice&Col06 
 
  [ Teclados / Teclas del Teclado de control remoto Microsoft eHome ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Teclas del Teclado de control remoto Microsoft eHome 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       keyboard.inf 
      Identificación del material                       HID\IrDevice&Col05 
 
  [ Unidades de disco / FUJITSU MHX2300BT ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       FUJITSU MHX2300BT 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       disk.inf 
      Identificación del material                       IDE\DiskFUJITSU_MHX2300BT_______________________0000000B 
      Location Information                              0 
 
  [ Unidades de disco / SONY WALKMAN USB Device ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       SONY WALKMAN USB Device 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       disk.inf 
      Identificación del material                       USBSTOR\DiskSONY____WALKMAN_________0100 
 
  [ Unidades de DVD o CD-ROM / HL-DT-ST DVDRAM GSA-T50N ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       HL-DT-ST DVDRAM GSA-T50N 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       cdrom.inf 
      Identificación del material                       IDE\CdRomHL-DT-ST_DVDRAM_GSA-T50N________________RR04____ 
      Location Information                              1 
 
  [ Volúmenes de almacenamiento / Volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Generic volume 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volume.inf 
      Identificación del material                       STORAGE\Volume 
 
  [ Volúmenes de almacenamiento / Volumen genérico ] 
 
    Propiedades del dispositivo: 
      Descripción del controlador                       Volumen genérico 
      Fecha del controlador                             21/06/2006 
      Versión del controlador                           6.0.6001.18000 
      Proveedor del controlador                         Microsoft 
      Archivo INF                                       volume.inf 
      Identificación del material                       STORAGE\Volume 
 
 
--------[ Dispositivos físicos ]---------------------------------------------------------------------------------------- 
 
    Dispositivos PCI: 
      Bus 0, Dispositivo 31, función 2                  Intel 82801IB ICH9 - 4-port SATA AHCI Controller 
      Bus 0, Dispositivo 27, función 0                  Intel 82801IB ICH9 - High Definition Audio Controller 
      Bus 0, Dispositivo 28, función 0                  Intel 82801IB ICH9 - PCI Express Root Port 1 
      Bus 0, Dispositivo 28, función 1                  Intel 82801IB ICH9 - PCI Express Root Port 2 
      Bus 0, Dispositivo 28, función 2                  Intel 82801IB ICH9 - PCI Express Root Port 3 
      Bus 0, Dispositivo 28, función 3                  Intel 82801IB ICH9 - PCI Express Root Port 4 
      Bus 0, Dispositivo 28, función 4                  Intel 82801IB ICH9 - PCI Express Root Port 5 
      Bus 0, Dispositivo 28, función 5                  Intel 82801IB ICH9 - PCI Express Root Port 6 
      Bus 0, Dispositivo 26, función 0                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Bus 0, Dispositivo 26, función 1                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Bus 0, Dispositivo 26, función 2                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Bus 0, Dispositivo 29, función 0                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Bus 0, Dispositivo 29, función 1                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Bus 0, Dispositivo 29, función 2                  Intel 82801IB ICH9 - USB Universal Host Controller 
      Bus 0, Dispositivo 26, función 7                  Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
      Bus 0, Dispositivo 29, función 7                  Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
      Bus 0, Dispositivo 30, función 0                  Intel 82801IBM/JBM I/O Controller Hub 9/10 (ICH9M/10M) 
      Bus 0, Dispositivo 31, función 0                  Intel 82801IM ICH9-M - LPC Bridge 
      Bus 0, Dispositivo 0, función 0                   Intel GL40/GM45/GS45/PM45 Chipset - Memory Controller Hub [B-3] 
      Bus 0, Dispositivo 1, función 0                   Intel GL40/GM45/GS45/PM45 Chipset - PCI Express Graphics Root Port [B-3] 
      Bus 3, Dispositivo 0, función 0                   Intel Shirley Peak (Shiloh) 1x2 MC Wireless WiFi Adapter 
      Bus 1, Dispositivo 0, función 0                   nVIDIA GeForce 9300M GS (Asus) Video Adapter 
      Bus 8, Dispositivo 0, función 0                   Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter 
      Bus 9, Dispositivo 1, función 2                   Ricoh RL5C592 Memory Stick Bus Host Adapter 
      Bus 9, Dispositivo 1, función 1                   Ricoh RL5C822 SD Bus Host Adapter 
      Bus 9, Dispositivo 1, función 0                   Ricoh RL5C832 IEEE1394 Controller 
      Bus 9, Dispositivo 1, función 3                   Ricoh RL5C852 xD-Picture Card Controller 
 
    Dispositivos PnP: 
      PNP0303                                           101/102-Key or MS Natural Keyboard 
      PNP0C08                                           ACPI Driver/BIOS 
      PNP0A08                                           ACPI Three-wire Device Bus 
      ATK0100                                           Asus ATK-100 ACPI Utility 
      FIXEDBUTTON                                       Botón de característica fija ACPI 
      PNP0C0A                                           Control Method Battery 
      PNP0200                                           DMA Controller 
      PNP0C09                                           Embedded Controller Device 
      PNP0103                                           High Precision Event Timer 
      GENUINEINTEL_-_X86_FAMILY_6_MODEL_23              Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz 
      GENUINEINTEL_-_X86_FAMILY_6_MODEL_23              Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz 
      ISATAP                                            isatap.{D1292219-B3AF-4B62-B7A8-A8EA49D149F4} 
      ISATAP                                            isatap.{F6E406B0-F6C6-4F2F-BD36-9A4DA581BFC1} 
      ITE8708                                           ITE CIR Infrared Receiver 
      PNP0C0D                                           Lid 
      ACPI0003                                          Microsoft AC Adapter 
      PNP0C02                                           Motherboard Resources 
      PNP0C02                                           Motherboard Resources 
      PNP0C02                                           Motherboard Resources 
      PNP0C02                                           Motherboard Resources 
      PNP0C02                                           Motherboard Resources 
      PNP0C02                                           Motherboard Resources 
      PNP0C04                                           Numeric Data Processor 
      PNP0800                                           PC Speaker 
      PNP0000                                           Programmable Interrupt Controller 
      PNP0B00                                           Real-Time Clock 
      PNP0C0E                                           Sleep Button 
      SYN0A0F                                           Synaptics PS/2 Port TouchPad 
      PNP0C01                                           System Board Extension 
      PNP0100                                           System Timer 
      THERMALZONE                                       Zona térmica ACPI 
 
    Dispositivos USB: 
      08FF 1600                                         AuthenTec Inc. AES1610 
      0B05 1751                                         BT-253 
      04F2 B033                                         Dispositivo compuesto USB 
      054C 031A                                         Dispositivo de almacenamiento USB 
      046D C019                                         Dispositivo de interfaz humana USB 
      04F2 B033                                         USB2.0 1.3M UVC WebCam 
 
 
--------[ Dispositivos PCI ]-------------------------------------------------------------------------------------------- 
 
  [ Intel 82801IB ICH9 - 4-port SATA AHCI Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - 4-port SATA AHCI Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 31 / 2 
      Identificador del dispositivo                     8086-2929 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0106 (SATA Controller) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    Soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - High Definition Audio Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - High Definition Audio Controller 
      Tipo de Bus                                       PCI Express 1.0 
      Bus / Dispositivo / Función                       0 / 27 / 0 
      Identificador del dispositivo                     8086-293E 
      N° del Sub-sistema                                1043-1893 
      Clase de dispositivo                              0403 (High Definition Audio) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - PCI Express Root Port 1 ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - PCI Express Root Port 1 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 28 / 0 
      Identificador del dispositivo                     8086-2940 
      N° del Sub-sistema                                0000-0000 
      Clase de dispositivo                              0604 (PCI/PCI Bridge) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - PCI Express Root Port 2 ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - PCI Express Root Port 2 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 28 / 1 
      Identificador del dispositivo                     8086-2942 
      N° del Sub-sistema                                0000-0000 
      Clase de dispositivo                              0604 (PCI/PCI Bridge) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - PCI Express Root Port 3 ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - PCI Express Root Port 3 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 28 / 2 
      Identificador del dispositivo                     8086-2944 
      N° del Sub-sistema                                0000-0000 
      Clase de dispositivo                              0604 (PCI/PCI Bridge) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - PCI Express Root Port 4 ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - PCI Express Root Port 4 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 28 / 3 
      Identificador del dispositivo                     8086-2946 
      N° del Sub-sistema                                0000-0000 
      Clase de dispositivo                              0604 (PCI/PCI Bridge) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - PCI Express Root Port 5 ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - PCI Express Root Port 5 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 28 / 4 
      Identificador del dispositivo                     8086-2948 
      N° del Sub-sistema                                0000-0000 
      Clase de dispositivo                              0604 (PCI/PCI Bridge) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - PCI Express Root Port 6 ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - PCI Express Root Port 6 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 28 / 5 
      Identificador del dispositivo                     8086-294A 
      N° del Sub-sistema                                0000-0000 
      Clase de dispositivo                              0604 (PCI/PCI Bridge) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - USB Universal Host Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - USB Universal Host Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 26 / 0 
      Identificador del dispositivo                     8086-2937 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0C03 (USB Controller) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - USB Universal Host Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - USB Universal Host Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 26 / 1 
      Identificador del dispositivo                     8086-2938 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0C03 (USB Controller) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - USB Universal Host Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - USB Universal Host Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 26 / 2 
      Identificador del dispositivo                     8086-2939 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0C03 (USB Controller) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - USB Universal Host Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - USB Universal Host Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 29 / 0 
      Identificador del dispositivo                     8086-2934 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0C03 (USB Controller) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - USB Universal Host Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - USB Universal Host Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 29 / 1 
      Identificador del dispositivo                     8086-2935 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0C03 (USB Controller) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - USB Universal Host Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - USB Universal Host Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 29 / 2 
      Identificador del dispositivo                     8086-2936 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0C03 (USB Controller) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - USB2 Enhanced Host Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 26 / 7 
      Identificador del dispositivo                     8086-293C 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0C03 (USB Controller) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IB ICH9 - USB2 Enhanced Host Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 29 / 7 
      Identificador del dispositivo                     8086-293A 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0C03 (USB Controller) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IBM/JBM I/O Controller Hub 9/10 (ICH9M/10M) ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IBM/JBM I/O Controller Hub 9/10 (ICH9M/10M) 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 30 / 0 
      Identificador del dispositivo                     8086-2448 
      N° del Sub-sistema                                0000-0000 
      Clase de dispositivo                              0604 (PCI/PCI Bridge) 
      Revisión                                          93 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel 82801IM ICH9-M - LPC Bridge ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel 82801IM ICH9-M - LPC Bridge 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 31 / 0 
      Identificador del dispositivo                     8086-2919 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0601 (PCI/ISA Bridge) 
      Revisión                                          03 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel GL40/GM45/GS45/PM45 Chipset - Memory Controller Hub [B-3] ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel GL40/GM45/GS45/PM45 Chipset - Memory Controller Hub [B-3] 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 0 / 0 
      Identificador del dispositivo                     8086-2A40 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0600 (Host/PCI Bridge) 
      Revisión                                          07 
      Fast Back-to-Back Transactions                    Soportado, Desactivado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel GL40/GM45/GS45/PM45 Chipset - PCI Express Graphics Root Port [B-3] ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel GL40/GM45/GS45/PM45 Chipset - PCI Express Graphics Root Port [B-3] 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       0 / 1 / 0 
      Identificador del dispositivo                     8086-2A41 
      N° del Sub-sistema                                0000-0000 
      Clase de dispositivo                              0604 (PCI/PCI Bridge) 
      Revisión                                          07 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Intel Shirley Peak (Shiloh) 1x2 MC Wireless WiFi Adapter ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Intel Shirley Peak (Shiloh) 1x2 MC Wireless WiFi Adapter 
      Tipo de Bus                                       PCI Express 1.0 x1 
      Bus / Dispositivo / Función                       3 / 0 / 0 
      Identificador del dispositivo                     8086-4232 
      N° del Sub-sistema                                8086-1201 
      Clase de dispositivo                              0280 (Network Controller) 
      Revisión                                          00 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ nVIDIA GeForce 9300M GS (Asus) Video Adapter ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       nVIDIA GeForce 9300M GS (Asus) Video Adapter 
      Tipo de Bus                                       PCI Express 2.0 x16 
      Bus / Dispositivo / Función                       1 / 0 / 0 
      Identificador del dispositivo                     10DE-06E9 
      N° del Sub-sistema                                1043-19B2 
      Clase de dispositivo                              0300 (VGA Display Controller) 
      Revisión                                          A1 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter 
      Tipo de Bus                                       PCI Express 1.0 x1 
      Bus / Dispositivo / Función                       8 / 0 / 0 
      Identificador del dispositivo                     10EC-8168 
      N° del Sub-sistema                                1043-16D5 
      Clase de dispositivo                              0200 (Ethernet Controller) 
      Revisión                                          02 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Ricoh RL5C592 Memory Stick Bus Host Adapter ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Ricoh RL5C592 Memory Stick Bus Host Adapter 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       9 / 1 / 2 
      Identificador del dispositivo                     1180-0592 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0880 (Base System Peripheral) 
      Revisión                                          12 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Ricoh RL5C822 SD Bus Host Adapter ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Ricoh RL5C822 SD Bus Host Adapter 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       9 / 1 / 1 
      Identificador del dispositivo                     1180-0822 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0805 (SD Host Controller) 
      Revisión                                          22 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Ricoh RL5C832 IEEE1394 Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Ricoh RL5C832 IEEE1394 Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       9 / 1 / 0 
      Identificador del dispositivo                     1180-0832 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0C00 (FireWire Controller) 
      Revisión                                          05 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
  [ Ricoh RL5C852 xD-Picture Card Controller ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Ricoh RL5C852 xD-Picture Card Controller 
      Tipo de Bus                                       PCI 
      Bus / Dispositivo / Función                       9 / 1 / 3 
      Identificador del dispositivo                     1180-0852 
      N° del Sub-sistema                                1043-1897 
      Clase de dispositivo                              0880 (Base System Peripheral) 
      Revisión                                          12 
      Fast Back-to-Back Transactions                    No soportado 
 
    Funcionalidades del dispositivo: 
      Opera a 66 MHz                                    No soportado 
      Bus Mastering                                     Activado 
 
 
--------[ Dispositivos USB ]-------------------------------------------------------------------------------------------- 
 
  [ Dispositivo de interfaz humana USB (USB Optical Mouse) ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Dispositivo de interfaz humana USB 
      Identificador del dispositivo                     046D-C019 
      Clase de dispositivo                              03 / 01 (Human Interface Device) 
      Device Protocol                                   02 
      Fabricante                                        Logitech 
      Producto                                          USB Optical Mouse 
      Supported USB Version                             2.00 
      Current Speed                                     Low  (USB 1.1) 
 
  [ BT-253 ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       BT-253 
      Identificador del dispositivo                     0B05-1751 
      Clase de dispositivo                              E0 / 01 (Bluetooth) 
      Device Protocol                                   01 
      Supported USB Version                             2.00 
      Current Speed                                     Full  (USB 1.1) 
 
  [ AuthenTec Inc. AES1610 ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       AuthenTec Inc. AES1610 
      Identificador del dispositivo                     08FF-1600 
      Clase de dispositivo                              FF / FF 
      Device Protocol                                   FF 
      Supported USB Version                             1.10 
      Current Speed                                     Full  (USB 1.1) 
 
  [ Dispositivo de almacenamiento USB (WALKMAN) ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Dispositivo de almacenamiento USB 
      Identificador del dispositivo                     054C-031A 
      Clase de dispositivo                              08 / 06 (Mass Storage) 
      Device Protocol                                   50 
      Fabricante                                        Sony 
      Producto                                          WALKMAN 
      Número de serie                                   4002FF7764A98BCD4002FF7764AC498A 
      Supported USB Version                             2.00 
      Current Speed                                     High  (USB 2.0) 
 
  [ Dispositivo compuesto USB ] 
 
    Propiedades del dispositivo: 
      Descripción del dispositivo                       Dispositivo compuesto USB 
      Identificador del dispositivo                     04F2-B033 
      Clase de dispositivo                              EF / 02 (Interface Association Descriptor) 
      Device Protocol                                   01 
      Supported USB Version                             2.00 
      Current Speed                                     High  (USB 2.0) 
 
 
--------[ Recursos de los dispositivos ]-------------------------------------------------------------------------------- 
 
    DMA 04                       Exclusivo             Controladora de acceso directo a memoria 
    IRQ 00                       Exclusivo             Cronómetro del sistema 
    IRQ 01                       Exclusivo             Keyboard Device Filter 
    IRQ 04                       Exclusivo             ITECIR Infrared Receiver (EC) 
    IRQ 08                       Exclusivo             Sistema CMOS/reloj en tiempo real 
    IRQ 100                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 101                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 102                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 103                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 104                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 105                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 106                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 107                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 108                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 109                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 110                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 111                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 112                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 113                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 114                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 115                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 116                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 117                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 118                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 119                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 12                       Exclusivo             Synaptics PS/2 Port TouchPad 
    IRQ 120                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 121                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 122                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 123                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 124                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 125                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 126                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 127                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 128                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 129                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 13                       Exclusivo             Procesador de datos numéricos 
    IRQ 130                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 131                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 132                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 133                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 134                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 135                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 136                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 137                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 138                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 139                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 140                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 141                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 142                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 143                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 144                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 145                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 146                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 147                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 148                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 149                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 150                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 151                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 152                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 153                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 154                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 155                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 156                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 157                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 158                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 159                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 16                       Compartido            Controlador de host universal USB de la familia Intel(R) ICH9 - 2937 
    IRQ 16                       Compartido            NVIDIA GeForce 9300M GS 
    IRQ 16                       Compartido            Controladora de host RICOH OHCI compatible con IEEE 1394 
    IRQ 160                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 161                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 162                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 163                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 164                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 165                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 166                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 167                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 168                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 169                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 17                       Compartido            Controladora de host SD compatible con el estándar SDA 
    IRQ 17                       Compartido            Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) 
    IRQ 17                       Compartido            Ricoh Memory Stick Controller 
    IRQ 17                       Compartido            Ricoh xD-Picture Card Controller 
    IRQ 170                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 171                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 172                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 173                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 174                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 175                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 176                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 177                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 178                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 179                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 18                       Compartido            Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293C 
    IRQ 18                       Compartido            Controlador de host universal USB de la familia Intel(R) ICH9 - 2936 
    IRQ 180                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 181                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 182                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 183                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 184                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 185                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 186                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 187                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 188                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 189                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 19                       Compartido            Controlador de host universal USB de la familia Intel(R) ICH9 - 2935 
    IRQ 19                       Compartido            Controlador de host universal USB de la familia Intel(R) ICH9 - 2939 
    IRQ 19                       Compartido            Intel(R) ICH9M-E/M SATA AHCI Controller 
    IRQ 190                      Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 21                       Compartido            Controlador de host universal USB de la familia Intel(R) ICH9 - 2938 
    IRQ 22                       Compartido            Controladora de High Definition Audio 
    IRQ 23                       Compartido            Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293A 
    IRQ 23                       Compartido            Controlador de host universal USB de la familia Intel(R) ICH8 - 2934 
    IRQ 65536                    Exclusivo             Intel(R) WiFi Link 5100 
    IRQ 65536                    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 1 - 2940 
    IRQ 65536                    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 2 - 2942 
    IRQ 65536                    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 3 - 2944 
    IRQ 65536                    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 4 - 2946 
    IRQ 65536                    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 5 - 2948 
    IRQ 65536                    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 6 - 294A 
    IRQ 65536                    Exclusivo             Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A41 
    IRQ 81                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 82                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 83                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 84                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 85                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 86                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 87                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 88                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 89                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 90                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 91                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 92                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 93                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 94                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 95                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 96                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 97                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 98                       Exclusivo             Sistema Microsoft compatible con ACPI 
    IRQ 99                       Exclusivo             Sistema Microsoft compatible con ACPI 
    Memoria 00000000-0009FFFF    Exclusivo             Tarjeta de sistema 
    Memoria 000A0000-000BFFFF    Compartido            Bus PCI 
    Memoria 000A0000-000BFFFF    Compartido            NVIDIA GeForce 9300M GS 
    Memoria 000A0000-000BFFFF    Indeterminado         Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A41 
    Memoria 000C0000-000CFFFF    Exclusivo             Tarjeta de sistema 
    Memoria 000D0000-000DFFFF    Compartido            Bus PCI 
    Memoria 000E0000-000FFFFF    Exclusivo             Tarjeta de sistema 
    Memoria 00100000-BFFFFFFF    Exclusivo             Tarjeta de sistema 
    Memoria C0000000-FFFFFFFF    Compartido            Bus PCI 
    Memoria D0000000-DFFFFFFF    Exclusivo             Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A41 
    Memoria D0000000-DFFFFFFF    Exclusivo             NVIDIA GeForce 9300M GS 
    Memoria E0000000-EFFFFFFF    Exclusivo             Recursos de la placa base 
    Memoria F4000000-F6EFFFFF    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 3 - 2944 
    Memoria F6F00000-F6FFFFFF    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 6 - 294A 
    Memoria F6FE0000-F6FEFFFF    Exclusivo             Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) 
    Memoria F6FFF000-F6FFFFFF    Exclusivo             Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) 
    Memoria F7FF8000-F7FFBFFF    Exclusivo             Controladora de High Definition Audio 
    Memoria F7FFEC00-F7FFECFF    Compartido            Recursos de la placa base 
    Memoria F7FFF000-F7FFF7FF    Exclusivo             Intel(R) ICH9M-E/M SATA AHCI Controller 
    Memoria F7FFF800-F7FFFBFF    Exclusivo             Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293A 
    Memoria F7FFFC00-F7FFFFFF    Exclusivo             Controlador de host mejorado USB2 de la familia Intel(R) ICH9 - 293C 
    Memoria F8000000-F9FFFFFF    Exclusivo             NVIDIA GeForce 9300M GS 
    Memoria F8000000-FBFFFFFF    Exclusivo             Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A41 
    Memoria FB000000-FBFFFFFF    Exclusivo             NVIDIA GeForce 9300M GS 
    Memoria FCF00000-FCFFFFFF    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 2 - 2942 
    Memoria FCFFE000-FCFFFFFF    Exclusivo             Intel(R) WiFi Link 5100 
    Memoria FD000000-FDDFFFFF    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 3 - 2944 
    Memoria FDE00000-FDEFFFFF    Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 6 - 294A 
    Memoria FDF00000-FDFFFFFF    Exclusivo             Puente PCI Intel(R) 82801 - 2448 
    Memoria FDFFEC00-FDFFECFF    Exclusivo             Ricoh xD-Picture Card Controller 
    Memoria FDFFF000-FDFFF0FF    Exclusivo             Ricoh Memory Stick Controller 
    Memoria FDFFF400-FDFFF4FF    Exclusivo             Controladora de host SD compatible con el estándar SDA 
    Memoria FDFFF800-FDFFFFFF    Exclusivo             Controladora de host RICOH OHCI compatible con IEEE 1394 
    Memoria FEC00000-FEC00FFF    Exclusivo             Recursos de la placa base 
    Memoria FEC10000-FEC17FFF    Exclusivo             Recursos de la placa base 
    Memoria FEC18000-FEC1FFFF    Exclusivo             Recursos de la placa base 
    Memoria FEC20000-FEC27FFF    Exclusivo             Recursos de la placa base 
    Memoria FEC28000-FEC2FFFF    Exclusivo             Recursos de la placa base 
    Memoria FEC30000-FEC37FFF    Exclusivo             Recursos de la placa base 
    Memoria FEC38000-FEC3FFFF    Exclusivo             Recursos de la placa base 
    Memoria FED00000-FED003FF    Exclusivo             Temporizador de eventos de alta precisión 
    Memoria FED10000-FED19FFF    Exclusivo             Recursos de la placa base 
    Memoria FED1C000-FED1FFFF    Exclusivo             Recursos de la placa base 
    Memoria FED20000-FED3FFFF    Exclusivo             Recursos de la placa base 
    Memoria FED45000-FED89FFF    Exclusivo             Recursos de la placa base 
    Memoria FED90000-FED90FFF    Exclusivo             Recursos de la placa base 
    Memoria FED91000-FED91FFF    Exclusivo             Recursos de la placa base 
    Memoria FED92000-FED92FFF    Exclusivo             Recursos de la placa base 
    Memoria FED93000-FED93FFF    Exclusivo             Recursos de la placa base 
    Memoria FEE00000-FEE00FFF    Exclusivo             Recursos de la placa base 
    Memoria FFA00000-FFBFFFFF    Exclusivo             Recursos de la placa base 
    Memoria FFB00000-FFBFFFFF    Exclusivo             Recursos de la placa base 
    Memoria FFC00000-FFDFFFFF    Exclusivo             Recursos de la placa base 
    Memoria FFE00000-FFFFFFFF    Exclusivo             Recursos de la placa base 
    Memoria FFF00000-FFFFFFFF    Exclusivo             Recursos de la placa base 
    Puerto 0000-000F             Exclusivo             Controladora de acceso directo a memoria 
    Puerto 0000-0CF7             Compartido            Bus PCI 
    Puerto 0010-001F             Exclusivo             Recursos de la placa base 
    Puerto 0020-0021             Exclusivo             Controladora programable de interrupciones 
    Puerto 0022-003F             Exclusivo             Recursos de la placa base 
    Puerto 0040-0043             Exclusivo             Cronómetro del sistema 
    Puerto 0044-005F             Exclusivo             Recursos de la placa base 
    Puerto 0060-0060             Exclusivo             Keyboard Device Filter 
    Puerto 0061-0061             Exclusivo             Altavoz del sistema 
    Puerto 0062-0062             Exclusivo             Controladora integrada compatible con Microsoft ACPI 
    Puerto 0063-0063             Exclusivo             Recursos de la placa base 
    Puerto 0064-0064             Exclusivo             Keyboard Device Filter 
    Puerto 0065-0065             Exclusivo             Recursos de la placa base 
    Puerto 0066-0066             Exclusivo             Controladora integrada compatible con Microsoft ACPI 
    Puerto 0067-006F             Exclusivo             Recursos de la placa base 
    Puerto 0070-0071             Exclusivo             Sistema CMOS/reloj en tiempo real 
    Puerto 0072-007F             Exclusivo             Recursos de la placa base 
    Puerto 0080-0080             Exclusivo             Recursos de la placa base 
    Puerto 0081-0083             Exclusivo             Controladora de acceso directo a memoria 
    Puerto 0084-0086             Exclusivo             Recursos de la placa base 
    Puerto 0087-0087             Exclusivo             Controladora de acceso directo a memoria 
    Puerto 0088-0088             Exclusivo             Recursos de la placa base 
    Puerto 0089-008B             Exclusivo             Controladora de acceso directo a memoria 
    Puerto 008C-008E             Exclusivo             Recursos de la placa base 
    Puerto 008F-008F             Exclusivo             Controladora de acceso directo a memoria 
    Puerto 0090-009F             Exclusivo             Recursos de la placa base 
    Puerto 00A0-00A1             Exclusivo             Controladora programable de interrupciones 
    Puerto 00A2-00BF             Exclusivo             Recursos de la placa base 
    Puerto 00C0-00DF             Exclusivo             Controladora de acceso directo a memoria 
    Puerto 00E0-00EF             Exclusivo             Recursos de la placa base 
    Puerto 00F0-00FF             Exclusivo             Procesador de datos numéricos 
    Puerto 0250-0253             Exclusivo             Recursos de la placa base 
    Puerto 0256-025F             Exclusivo             Recursos de la placa base 
    Puerto 0300-0307             Exclusivo             ITECIR Infrared Receiver (EC) 
    Puerto 03B0-03BB             Compartido            NVIDIA GeForce 9300M GS 
    Puerto 03B0-03BB             Indeterminado         Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A41 
    Puerto 03C0-03DF             Compartido            NVIDIA GeForce 9300M GS 
    Puerto 03C0-03DF             Indeterminado         Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A41 
    Puerto 0400-041F             Exclusivo             Recursos de la placa base 
    Puerto 04D0-04D1             Exclusivo             Recursos de la placa base 
    Puerto 0500-057F             Exclusivo             Recursos de la placa base 
    Puerto 0800-087F             Exclusivo             Recursos de la placa base 
    Puerto 0D00-FFFF             Compartido            Bus PCI 
    Puerto A480-A49F             Exclusivo             Intel(R) ICH9M-E/M SATA AHCI Controller 
    Puerto A800-A803             Exclusivo             Intel(R) ICH9M-E/M SATA AHCI Controller 
    Puerto A880-A887             Exclusivo             Intel(R) ICH9M-E/M SATA AHCI Controller 
    Puerto AC00-AC03             Exclusivo             Intel(R) ICH9M-E/M SATA AHCI Controller 
    Puerto B000-B007             Exclusivo             Intel(R) ICH9M-E/M SATA AHCI Controller 
    Puerto B080-B09F             Exclusivo             Controlador de host universal USB de la familia Intel(R) ICH9 - 2936 
    Puerto B400-B41F             Exclusivo             Controlador de host universal USB de la familia Intel(R) ICH9 - 2935 
    Puerto B480-B49F             Exclusivo             Controlador de host universal USB de la familia Intel(R) ICH8 - 2934 
    Puerto B800-B81F             Exclusivo             Controlador de host universal USB de la familia Intel(R) ICH9 - 2939 
    Puerto B880-B89F             Exclusivo             Controlador de host universal USB de la familia Intel(R) ICH9 - 2938 
    Puerto BC00-BC1F             Exclusivo             Controlador de host universal USB de la familia Intel(R) ICH9 - 2937 
    Puerto C000-CFFF             Exclusivo             Mobile Intel(R) 45 Express Chipset Series PCI Express Root Port - 2A41 
    Puerto CC00-CC7F             Exclusivo             NVIDIA GeForce 9300M GS 
    Puerto D000-DFFF             Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 3 - 2944 
    Puerto E000-EFFF             Exclusivo             Intel(R) ICH9 Family PCI Express Root Port 6 - 294A 
    Puerto E800-E8FF             Exclusivo             Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0) 
 
 
--------[ Dispositivos de entrada ]------------------------------------------------------------------------------------- 
 
  [ Keyboard Device Filter ] 
 
    Propiedades del teclado: 
      Nombre del teclado                                Keyboard Device Filter 
      Tipo de teclado                                   Japanese keyboard 
      Disposición del teclado                           Latin American 
      Página de códigos ANSI                            1252 - @%SystemRoot%\system32\mlang.dll,-4612 
      Página de códigos OEM                             850 
      Retraso de repetición                             1 
      Frecuencia de repetición                          31 
 
  [ Mouse compatible con HID ] 
 
    Propiedades del ratón: 
      Nombre del ratón                                  Mouse compatible con HID 
      Número de botones                                 8 
      Localización                                      Derecha 
      Velocidad del puntero                             1 
      Retraso al hacer doble click                      500 msec 
      Sensibilidad X/Y                                  6 / 10 
      Líneas de desplazamiento de la rueda del ratón    3 
 
    Funciones del ratón: 
      Rastreo automático de una ventana                 Desactivado 
      ClickLock                                         Desactivado 
      Ocultar el puntero del ratón mientras se escribe  Activado 
      Rueda del ratón                                   Presente 
      Volver a poner el puntero sobre el ratón por defectoDesactivado 
      Dejar rastro con el puntero                       Desactivado 
      Sonar                                             Desactivado 
 
 
--------[ Impresoras ]-------------------------------------------------------------------------------------------------- 
 
  [ Microsoft XPS Document Writer (Por defecto) ] 
 
    Propiedades de la impresora: 
      Nombre de la impresora                            Microsoft XPS Document Writer 
      Impresora predeterminada                          Sí 
      Punto compartido                                  No compartido 
      Puerto de impresión                               XPSPort: 
      Controlador de impresora                          Microsoft XPS Document Writer (v6.00) 
      Nombre del dispositivo                            Microsoft XPS Document Writer 
      Procesador de impresora                           WinPrint 
      Página de separación                              Ninguno 
      Disponibilidad                                    Siempre 
      Prioridad                                         1 
      Trabajos de impresión en cola                     0 
      Estado                                            Desconocido 
 
    Propiedades del papel: 
      Tamaño del papel                                  Letter, 8.5 x 11 in 
      Orientación                                       Foto 
      Calidad de impresión                              600 x 600 dpi Color 
 
 
--------[ Debug - PCI ]------------------------------------------------------------------------------------------------- 
 
    B00 D00 F00:  Intel GL40/GM45/GS45/PM45 Chipset - Memory Controller Hub [B-3] 
                   
      Offset 000:  86 80 40 2A  06 00 90 20  07 00 00 06  00 00 00 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  E0 00 00 00  00 00 00 00  00 00 00 00  
      Offset 040:  01 90 D1 FE  00 00 00 00  01 00 D1 FE  00 00 00 00  
      Offset 050:  00 00 02 00  03 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  01 00 00 E0  00 00 00 00  01 80 D1 FE  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  01 08 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  10 11 11 00  00 33 33 00  40 00 4F 00  00 1A 38 00  
      Offset 0A0:  20 00 00 14  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 C0 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 20 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  60 01 00 00  
      Offset 0E0:  09 00 0A 11  86 7C 40 1C  01 90 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  A0 0F 07 00  00 00 00 00  
 
    B00 D01 F00:  Intel GL40/GM45/GS45/PM45 Chipset - PCI Express Graphics Root Port [B-3] 
                   
      Offset 000:  86 80 41 2A  07 05 10 00  07 00 04 06  08 00 01 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 01 01 00  C0 C0 00 00  
      Offset 020:  00 F8 F0 FB  01 D0 F1 DF  00 00 00 00  00 00 00 00  
      Offset 030:  00 00 00 00  88 00 00 00  00 00 00 00  00 01 1A 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 02  
      Offset 080:  01 90 03 C8  00 00 00 00  0D 80 00 00  43 10 97 18  
      Offset 090:  05 A0 01 00  0C 30 E0 FE  B0 49 00 00  00 00 00 00  
      Offset 0A0:  10 00 41 01  00 80 00 00  00 00 01 00  01 2D 01 02  
      Offset 0B0:  43 00 11 10  C0 25 84 00  E8 01 40 00  08 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 01 07  04 00 00 A0  A0 0F 07 00  13 40 00 00  
 
    B00 D1A F00:  Intel 82801IB ICH9 - USB Universal Host Controller 
                   
      Offset 000:  86 80 37 29  05 00 90 02  03 00 03 0C  00 00 80 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  01 BC 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  10 01 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  13 00 06 03  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  10 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 2F 00 00  00 00 00 00  00 00 01 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1A F01:  Intel 82801IB ICH9 - USB Universal Host Controller 
                   
      Offset 000:  86 80 38 29  05 00 90 02  03 00 03 0C  00 00 00 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  81 B8 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  15 02 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  13 00 06 03  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  10 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 2F 00 00  00 00 00 00  00 00 01 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1A F02:  Intel 82801IB ICH9 - USB Universal Host Controller 
                   
      Offset 000:  86 80 39 29  05 00 90 02  03 00 03 0C  00 00 00 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  01 B8 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  13 04 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  13 00 06 03  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  10 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 2F 00 00  00 00 00 00  00 00 01 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1A F07:  Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
                   
      Offset 000:  86 80 3C 29  06 00 90 02  03 20 03 0C  00 00 00 00  
      Offset 010:  00 FC FF F7  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  12 03 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  01 58 C2 C9  00 00 00 00  0A 98 A0 20  00 00 00 00  
      Offset 060:  20 20 FF 01  00 00 00 00  01 00 00 00  00 20 00 C0  
      Offset 070:  00 00 DF 0F  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  11 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  13 00 06 03  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 AA FF 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  88 85 40 00  86 0F 03 00  0A 17 02 20  
 
    B00 D1B F00:  Intel 82801IB ICH9 - High Definition Audio Controller 
                   
      Offset 000:  86 80 3E 29  06 00 10 00  03 00 03 04  08 00 00 00  
      Offset 010:  04 80 FF F7  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 93 18  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  16 01 00 00  
      Offset 040:  01 00 00 07  07 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  01 60 42 C8  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  05 70 80 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  10 00 91 00  00 00 00 10  00 00 10 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 04 00 01  00 00 00 00  31 00 A3 02  00 00 00 00  
      Offset 0D0:  61 00 A3 02  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1C F00:  Intel 82801IB ICH9 - PCI Express Root Port 1 
                   
      Offset 000:  86 80 40 29  04 05 10 00  03 00 04 06  08 00 81 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 02 02 00  F0 00 00 20  
      Offset 020:  F0 FF 00 00  F1 FF 01 00  00 00 00 00  00 00 00 00  
      Offset 030:  00 00 00 00  40 00 00 00  00 00 00 00  00 01 02 00  
      Offset 040:  10 80 41 00  00 80 00 00  00 00 10 00  11 2C 11 01  
      Offset 050:  40 00 01 10  60 05 00 00  00 00 40 00  08 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  05 90 01 00  0C 30 E0 FE  70 49 00 00  00 00 00 00  
      Offset 090:  0D A0 00 00  43 10 97 18  00 00 00 00  00 00 00 00  
      Offset 0A0:  01 00 02 C8  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  80 00 11 08  00 00 00 00  
      Offset 0E0:  00 0F C7 00  06 07 08 00  30 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1C F01:  Intel 82801IB ICH9 - PCI Express Root Port 2 
                   
      Offset 000:  86 80 42 29  06 05 10 00  03 00 04 06  08 00 81 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 03 03 00  F0 00 00 00  
      Offset 020:  F0 FC F0 FC  F1 FF 01 00  00 00 00 00  00 00 00 00  
      Offset 030:  00 00 00 00  40 00 00 00  00 00 00 00  00 02 02 00  
      Offset 040:  10 80 41 00  00 80 00 00  00 00 11 00  11 2C 11 02  
      Offset 050:  43 00 11 30  60 05 00 00  00 00 48 01  08 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  05 90 01 00  0C 30 E0 FE  A0 49 00 00  00 00 00 00  
      Offset 090:  0D A0 00 00  43 10 97 18  00 00 00 00  00 00 00 00  
      Offset 0A0:  01 00 02 C8  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  80 00 11 08  00 00 00 00  
      Offset 0E0:  00 0F C7 00  06 07 08 00  30 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1C F02:  Intel 82801IB ICH9 - PCI Express Root Port 3 
                   
      Offset 000:  86 80 44 29  07 05 10 00  03 00 04 06  08 00 81 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 04 05 00  D0 D0 00 20  
      Offset 020:  00 FD D0 FD  01 F4 E1 F6  00 00 00 00  00 00 00 00  
      Offset 030:  00 00 00 00  40 00 00 00  00 00 00 00  00 03 02 00  
      Offset 040:  10 80 41 01  00 80 00 00  00 00 10 00  11 2C 11 03  
      Offset 050:  40 00 01 10  60 05 00 00  3A 10 00 00  08 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  05 90 01 00  0C 30 E0 FE  90 49 00 00  00 00 00 00  
      Offset 090:  0D A0 00 00  43 10 97 18  00 00 00 00  00 00 00 00  
      Offset 0A0:  01 00 02 C8  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  80 00 11 08  00 00 00 00  
      Offset 0E0:  00 0F C7 00  06 07 08 00  30 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1C F03:  Intel 82801IB ICH9 - PCI Express Root Port 4 
                   
      Offset 000:  86 80 46 29  04 05 10 00  03 00 04 06  08 00 81 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 06 06 00  F0 00 00 20  
      Offset 020:  F0 FF 00 00  F1 FF 01 00  00 00 00 00  00 00 00 00  
      Offset 030:  00 00 00 00  40 00 00 00  00 00 00 00  00 04 02 00  
      Offset 040:  10 80 41 01  00 80 00 00  00 00 10 00  11 2C 11 04  
      Offset 050:  40 00 01 10  60 05 00 00  3A 10 00 00  08 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  05 90 01 00  0C 30 E0 FE  60 49 00 00  00 00 00 00  
      Offset 090:  0D A0 00 00  43 10 97 18  00 00 00 00  00 00 00 00  
      Offset 0A0:  01 00 02 C8  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  80 00 11 08  00 00 00 00  
      Offset 0E0:  00 0F C7 00  06 07 08 00  30 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1C F04:  Intel 82801IB ICH9 - PCI Express Root Port 5 
                   
      Offset 000:  86 80 48 29  04 05 10 00  03 00 04 06  08 00 81 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 07 07 00  F0 00 00 20  
      Offset 020:  F0 FF 00 00  F1 FF 01 00  00 00 00 00  00 00 00 00  
      Offset 030:  00 00 00 00  40 00 00 00  00 00 00 00  00 01 02 00  
      Offset 040:  10 80 41 00  00 80 00 00  00 00 10 00  11 2C 11 05  
      Offset 050:  40 00 01 10  60 05 00 00  00 00 40 00  08 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  05 90 01 00  0C 30 E0 FE  51 49 00 00  00 00 00 00  
      Offset 090:  0D A0 00 00  43 10 97 18  00 00 00 00  00 00 00 00  
      Offset 0A0:  01 00 02 C8  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 11 08  00 00 00 00  
      Offset 0E0:  00 0F C7 00  06 07 08 00  30 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1C F05:  Intel 82801IB ICH9 - PCI Express Root Port 6 
                   
      Offset 000:  86 80 4A 29  07 05 10 00  03 00 04 06  08 00 81 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 08 08 00  E0 E0 00 00  
      Offset 020:  E0 FD E0 FD  F1 F6 F1 F6  00 00 00 00  00 00 00 00  
      Offset 030:  00 00 00 00  40 00 00 00  00 00 00 00  00 02 02 00  
      Offset 040:  10 80 41 00  00 80 00 00  00 00 10 00  11 2C 11 06  
      Offset 050:  41 00 11 30  60 05 00 00  00 00 48 01  08 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  05 90 01 00  0C 30 E0 FE  80 49 00 00  00 00 00 00  
      Offset 090:  0D A0 00 00  43 10 97 18  00 00 00 00  00 00 00 00  
      Offset 0A0:  01 00 02 C8  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  80 00 11 08  00 00 00 00  
      Offset 0E0:  00 0F C7 00  06 07 08 00  30 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1D F00:  Intel 82801IB ICH9 - USB Universal Host Controller 
                   
      Offset 000:  86 80 34 29  05 00 90 02  03 00 03 0C  00 00 80 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  81 B4 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  17 01 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  13 00 06 03  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  10 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 2F 00 00  00 00 00 00  00 00 01 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1D F01:  Intel 82801IB ICH9 - USB Universal Host Controller 
                   
      Offset 000:  86 80 35 29  05 00 90 02  03 00 03 0C  00 00 00 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  01 B4 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  13 02 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  13 00 06 03  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  10 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 2F 00 00  00 00 00 00  00 00 01 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1D F02:  Intel 82801IB ICH9 - USB Universal Host Controller 
                   
      Offset 000:  86 80 36 29  05 00 90 02  03 00 03 0C  00 00 00 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  81 B0 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  12 03 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  13 00 06 03  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  10 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 2F 00 00  00 00 00 00  00 00 01 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1D F07:  Intel 82801IB ICH9 - USB2 Enhanced Host Controller 
                   
      Offset 000:  86 80 3A 29  06 01 90 02  03 20 03 0C  00 00 00 00  
      Offset 010:  00 F8 FF F7  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  17 01 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  01 58 C2 C9  00 00 00 00  0A 98 A0 20  00 00 00 00  
      Offset 060:  20 20 FF 01  00 00 00 00  01 00 00 00  00 20 00 C0  
      Offset 070:  00 00 DF 0F  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  11 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  13 00 06 03  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 AA FF 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  88 85 40 00  86 0F 03 00  0A 17 02 20  
 
    B00 D1E F00:  Intel 82801IBM/JBM I/O Controller Hub 9/10 (ICH9M/10M) 
                   
      Offset 000:  86 80 48 24  07 01 10 00  93 01 04 06  00 00 01 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 09 09 20  F0 00 80 22  
      Offset 020:  F0 FD F0 FD  F1 FF 01 00  00 00 00 00  00 00 00 00  
      Offset 030:  00 00 00 00  50 00 00 00  00 00 00 00  FF 00 02 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 12 00 00  
      Offset 050:  0D 00 00 00  43 10 97 18  00 00 00 00  00 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1F F00:  Intel 82801IM ICH9-M - LPC Bridge 
                   
      Offset 000:  86 80 19 29  07 00 10 02  03 00 01 06  00 00 80 00  
      Offset 010:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  E0 00 00 00  00 00 00 00  00 00 00 00  
      Offset 040:  01 08 00 00  80 00 00 00  01 05 00 00  10 00 00 00  
      Offset 050:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  8A 85 86 83  D0 00 00 00  80 87 84 8A  F8 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 02 0C  01 03 04 00  00 00 00 00  51 02 0C 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  AC 0A 00 00  39 02 80 00  13 1C 0A 00  00 03 00 C0  
      Offset 0B0:  00 00 F0 00  00 00 00 00  00 00 81 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  33 22 11 00  67 45 00 00  C0 C0 00 00  00 00 00 00  
      Offset 0E0:  09 00 0C 10  20 02 24 03  64 00 00 00  00 00 00 00  
      Offset 0F0:  01 C0 D1 FE  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B00 D1F F02:  Intel 82801IB ICH9 - 4-port SATA AHCI Controller 
                   
      Offset 000:  86 80 29 29  07 00 B0 02  03 01 06 01  00 00 00 00  
      Offset 010:  01 B0 00 00  01 AC 00 00  81 A8 00 00  01 A8 00 00  
      Offset 020:  81 A4 00 00  00 F0 FF F7  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  80 00 00 00  00 00 00 00  13 02 00 00  
      Offset 040:  00 80 00 80  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  01 A8 03 40  08 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  05 70 08 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  60 00 23 83  93 01 00 1C  00 00 01 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  12 B0 10 00  48 00 00 00  
      Offset 0B0:  13 00 06 03  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  86 0F 03 00  00 00 00 00  
 
    B01 D00 F00:  nVIDIA GeForce 9300M GS (Asus) Video Adapter 
                   
      Offset 000:  DE 10 E9 06  07 00 10 00  A1 00 00 03  08 00 00 00  
      Offset 010:  00 00 00 FB  0C 00 00 D0  00 00 00 00  04 00 00 F8  
      Offset 020:  00 00 00 00  01 CC 00 00  00 00 00 00  43 10 B2 19  
      Offset 030:  00 00 00 00  60 00 00 00  00 00 00 00  10 01 00 00  
      Offset 040:  43 10 B2 19  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  01 00 00 00  01 00 00 00  CE D6 23 00  00 00 00 00  
      Offset 060:  01 68 03 00  08 00 00 00  05 78 80 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  10 00 02 00  A0 84 2C 01  
      Offset 080:  10 29 00 00  02 2D 00 00  43 00 11 10  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  10 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  02 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
 
    B03 D00 F00:  Intel Shirley Peak (Shiloh) 1x2 MC Wireless WiFi Adapter 
                   
      Offset 000:  86 80 32 42  06 04 10 00  00 00 80 02  08 00 00 00  
      Offset 010:  04 E0 FF FC  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  86 80 01 12  
      Offset 030:  00 00 00 00  C8 00 00 00  00 00 00 00  00 01 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  01 D0 23 C8  00 00 00 0D  
      Offset 0D0:  05 E0 81 00  0C 30 E0 FE  00 00 00 00  52 49 00 00  
      Offset 0E0:  10 00 01 00  C0 8E 00 10  10 00 11 00  11 9C 06 00  
      Offset 0F0:  43 00 11 10  00 00 00 00  00 00 00 00  00 00 00 00  
 
    B08 D00 F00:  Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter 
                   
      Offset 000:  EC 10 68 81  07 00 10 00  02 00 00 02  08 00 00 00  
      Offset 010:  01 E8 00 00  00 00 00 00  0C F0 FF F6  00 00 00 00  
      Offset 020:  0C 00 FE F6  00 00 00 00  00 00 00 00  43 10 D5 16  
      Offset 030:  00 00 00 00  40 00 00 00  00 00 00 00  11 01 00 00  
      Offset 040:  01 50 C3 FF  08 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  05 70 82 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  10 B0 01 02  C1 86 28 00  10 50 11 00  11 3C 07 00  
      Offset 080:  41 00 11 10  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  10 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0B0:  11 D0 01 00  04 00 00 00  04 08 00 00  00 00 00 00  
      Offset 0C0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0D0:  03 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
 
    B09 D01 F00:  Ricoh RL5C832 IEEE1394 Controller 
                   
      Offset 000:  80 11 32 08  06 00 10 02  05 10 00 0C  08 20 80 00  
      Offset 010:  00 F8 FF FD  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  DC 00 00 00  00 00 00 00  10 01 02 04  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  00 80 A0 16  00 00 00 00  00 20 00 00  66 66 32 12  
      Offset 090:  48 60 66 10  00 00 02 00  0F 80 00 00  00 01 18 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  30 00 00 00  43 10 97 18  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 02 04  
      Offset 0C0:  00 30 00 00  00 00 00 00  00 00 00 02  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  01 00 02 C8  
      Offset 0E0:  00 C0 00 48  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
 
    B09 D01 F01:  Ricoh RL5C822 SD Bus Host Adapter 
                   
      Offset 000:  80 11 22 08  06 00 10 02  22 00 05 08  08 40 80 00  
      Offset 010:  00 F4 FF FD  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  80 00 00 00  00 00 00 00  11 02 00 00  
      Offset 040:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 050:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  01 00 02 FE  00 40 00 48  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 0B0:  04 00 02 00  00 00 00 00  00 00 00 00  A0 00 00 00  
      Offset 0C0:  00 30 00 00  00 00 00 00  00 00 00 02  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  A1 21 F0 01  00 00 00 00  40 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  C0 00 20 00  00 00 00 00  
 
    B09 D01 F02:  Ricoh RL5C592 Memory Stick Bus Host Adapter 
                   
      Offset 000:  80 11 92 05  06 00 10 02  12 00 80 08  08 40 80 00  
      Offset 010:  00 F0 FF FD  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  80 00 00 00  00 00 00 00  11 02 00 00  
      Offset 040:  00 00 02 00  00 00 00 00  00 00 02 00  00 00 00 00  
      Offset 050:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  01 00 02 FE  00 40 00 48  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 30 00 00  00 00 00 00  00 00 00 02  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  C0 00 00 00  00 00 00 00  
 
    B09 D01 F03:  Ricoh RL5C852 xD-Picture Card Controller 
                   
      Offset 000:  80 11 52 08  06 00 10 02  12 00 80 08  08 40 80 00  
      Offset 010:  00 EC FF FD  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 020:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 030:  00 00 00 00  80 00 00 00  00 00 00 00  11 02 00 00  
      Offset 040:  00 00 02 00  00 00 00 00  00 00 02 00  00 00 00 00  
      Offset 050:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 060:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 070:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 080:  01 00 02 FE  00 40 00 48  00 00 00 00  00 00 00 00  
      Offset 090:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0A0:  00 00 00 00  00 00 00 00  00 00 00 00  43 10 97 18  
      Offset 0B0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0C0:  00 30 00 00  00 00 00 00  00 00 00 02  00 00 00 00  
      Offset 0D0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0E0:  00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  
      Offset 0F0:  00 00 00 00  00 00 00 00  C0 00 00 00  00 00 00 00  
 
 
--------[ Debug - Video BIOS ]------------------------------------------------------------------------------------------ 
 
    C000:0000  U.r.K7400.L.w.VIDEO ......:...IBM VGA Compatible......@.06/18/08 
    C000:0040  ..................4.C.................".........PMIDl.o....... 
    C000:0080  .....3b$O...|................................................... 
    C000:00C0  ........................................HWEANB9M-GS E566 Sku 001 
    C000:0100   VGA BIOS ASID:N18M50.002$ ..................................Ver 
    C000:0140  sion 62.98.39.00.18 ...Copyright (C) 1996-2008 NVIDIA Corp...... 
    C000:0180  ...A....G98 Board - 05666e90...............Chip Rev   .......... 
    C000:01C0  ................................................PCIR............ 
    C000:0200  r.......HYB$..BIT......E2.....B.....C.....D.....A.....I.....L... 
    C000:0240  ..M.....N.....P.....S.....T.....U.....V.....c.....x...#.d...&.i. 
    C000:0280  &.(...N.z...a............9.b..................\\...............L 
    C000:02C0  ..N.4*..`.v.|...l...v.9........J.n...v...b...J...........6...BD 
    C000:0300  .....P=..W.(z....#..#.................:..9.b.....&.....06/16/08. 
    C000:0340  .........e..............+.$.g.^.X.X.m.y....... .........+.$.g.^. 
    C000:0380  X.X.,..._...1.r...4.5.r.T.{.u...G.....J...0.....{.Q...+.g.p..... 
    C000:03C0  q...r.r.X.m.r.r...a.r.^...f.P.P.P.m.....P.n.....q.P.q.t.^...T.x. 
 
 
--------[ Debug - Unknown ]--------------------------------------------------------------------------------------------- 
 
    Optical         HL-DT-ST DVDRAM GSA-T50N 
    SPD             No SPD module found! (BusCount = 0) 
 
 
------------------------------------------------------------------------------------------------------------------------ 
 
The names of actual companies and products mentioned herein may be the trademarks of their respective owners. 

```

---

### Post by pablo.s on 2009-04-13
A mi no me sirve. Si no podés 
ejecutar un simple comando y
copiar y pegar en un mensaje
te va a convenir seguir con
Vista.
Acá hay cuatro o cinco usuarios
principiantes por semana que
como primera prueba tienen que
hacer lo que a vos te sugerí y
lo hacen sin problemas.

No es de mala onda, por favor
que no se interprete asi, pero
abrí la cabeza para entrar en
un mundo nuevo o no va a haber
forma. Saludos.

---

### Post by sackm on 2009-04-13
pablo.s no es que no sepa ejecutar un simple comando como decis, simplemten que el comando que me dan ustedes no anda , las razones las desconosco

---

### Post by Mauro22 on 2009-04-13
Vamos que la tercera es la vencida:

Abrí la consola (o Terminal)

Menu -> Accesorios > Terminal:

te aparece algo asi, solo que con tu nombre y pc:

```
mauro@ubuntu:~$ 
```

ahi pones lspci ( ele ese pe ce i ) que viene de **l**i**s**tar** pci**

y le das enter y te sale algo como esto:
Lo seleccionas todo y le das clic derecho copiar y lo pegas aca, asi nomas:

mauro@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Muchos mas...

mauro@ubuntu:~$ 



):P

---

### Post by sackm on 2009-04-13
chicos es lo que exactamente hago u.u

---

### Post by Mauro22 on 2009-04-13
Estoy confundido...


Hasta aca llegue, si lspci no te devuelve nada... y dijiste que no te reconocio nada es porque... no hay nada que reconocer ??


Mientras no salga humo, tiene solucion... :D


A ver alguien que sepa!!

---

### Post by pablo.s on 2009-04-13
> **sackm said:**
> chicos es lo que exactamente hago u.u

Ahora mismo, estás en Linux
o estás en Vista?

---

### Post by sackm on 2009-04-13
jajaja chicos despues de intentar una y otra vez, de la nada salio, la verdad no se porque no salia, pero bueno aqui esta 

sadoc@sadoc-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Cantiga PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e9 (rev a1)
03:00.0 Network controller: Intel Corporation Unknown device 4232
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
sadoc@sadoc-laptop:~$

---

### Post by Mauro22 on 2009-04-13
Va quieriendo, viste!!


El <gran> problema es la falta de internet.

Tenes forma de conectarte por cable?? Porque necesitas internet para bajar los drivers de videos.

El video nvidia tendria que levantar activando los drivers en :

Menu -> Sistema > Administracion > Controlador de Hardware restringido.

Sino va asi, tenes que bajar e instalar envy-ng (cuando tengas internet)


sudo apt-get install envy-ng

te pide tu contraseña (escribila pero no ves nada) y dale enter.

te puede preguntar si estas seguro S/N, dale que si hasta que vuelva al prompt, en tu caso:
sadoc@sadoc-laptop:~$



Despues busca envy-ng en el menu e instalas los drivers adecuados...

---

### Post by pablo.s on 2009-04-13
Bajate esta imagen ISO:

[http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-beta-desktop-i386.iso](http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-beta-desktop-i386.iso)

Quemala con Nero o lo que
uses para grabar desde Vista.

Instalatela como instalaste la
versión anterior de Ubuntu.

Cuando haya instalado te va a decir
que drivers necesita instalar.

---

### Post by sackm on 2009-04-13
> **Mauro22 said:**
> Va quieriendo, viste!!


El <gran> problema es la falta de internet.

Tenes forma de conectarte por cable?? Porque necesitas internet para bajar los drivers de videos.

El video nvidia tendria que levantar activando los drivers en :

Menu -> Sistema > Administracion > Controlador de Hardware restringido.

Sino va asi, tenes que bajar e instalar envy-ng (cuando tengas internet)


sudo apt-get install envy-ng

te pide tu contraseña (escribila pero no ves nada) y dale enter.

te puede preguntar si estas seguro S/N, dale que si hasta que vuelva al prompt, en tu caso:
sadoc@sadoc-laptop:~$



Despues busca envy-ng en el menu e instalas los drivers adecuados...

ni por cable me anda :/ pero tengo instalado ubuntu y windows, por windows puedo entrar a internet :D

---

### Post by sackm on 2009-04-13
> **pablo.s said:**
> Bajate esta imagen ISO:

[http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-beta-desktop-i386.iso](http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-beta-desktop-i386.iso)

Quemala con Nero o lo que
uses para grabar desde Vista.

Instalatela como instalaste la
versión anterior de Ubuntu.

Cuando haya instalado te va a decir
que drivers necesita instalar.


Si es asi de facil como me dices , entonces lo bajo y ya :) lo hare y les informare los resultados :guitar: rebuena onda chicos muchas gracias :guitar:

---

### Post by pablo.s on 2009-04-13
Perdoná los ladridos.
Saludos

---

### Post by sackm on 2009-04-13
> **pablo.s said:**
> Perdoná los ladridos.
Saludos

ajaja todo bien pablo.s saludos :)

---

### Post by sackm on 2009-04-14
Chicos, ya instale ubuntu y por ahora todo bien con internet. Ando buscando los drivers del menu multimedia que tiene mi touchpad :D

---

### Post by pablo.s on 2009-04-14
Me alegro mucho. Es el link de la imagen
que te pasé ayer?

---

### Post by sackm on 2009-04-14
exacto :p

---

### Post by luks911 on 2009-04-14
Mirá, acá hay una wiki de ese modelo: [http://wiki.ubuntu.cz/Asus%20M50Vc](http://wiki.ubuntu.cz/Asus%20M50Vc)

está en checo pero la traducción de Google es bastante pasable: [http://translate.google.com/translate?prev=_t&hl=es&ie=UTF-8&u=http%3A%2F%2Fwiki.ubuntu.cz%2FAsus%2520M50Vc&sl=cs&tl=es&history_state0=cs|es|a%2520do%2520sekce%2520%2522ServerLayout%2522%2520doplnit%2520%25C5%2599%25C3%25A1dek%2520](http://translate.google.com/translate?prev=_t&hl=es&ie=UTF-8&u=http%3A%2F%2Fwiki.ubuntu.cz%2FAsus%2520M50Vc&sl=cs&tl=es&history_state0=cs|es|a%2520do%2520sekce%2520%2522ServerLayout%2522%2520doplnit%2520%25C5%2599%25C3%25A1dek%2520)

Todavía no dice como hacer funcionar el touchpad multimedia, pero tiene otros datos que pueden ser útiles. Ah, si llegás a usar algo de eso fijate que las partes que están sombreadas con naranja conviene tomarlas del original por si google traduce algo que no debería.

---

### Post by sackm on 2009-04-15
ahora tengo pedaso de problema... :( trate de reinstalar ubuntu creando tres particiones : una de 5 gb en raiz, 1gb de intercambio y el resto en home...me tiro error en la creacion de ficheros ext3 y no pude instalarlo.... trate de instalar denuevo y no anda... no logro instalarlo nuevamente :( me tira error una y otra vez al empezar a instalar :mad: ayuda plis :(

---

### Post by pablo.s on 2009-04-15
Podés formatear las particiones
en ReiserFS en lugar de Ext3.

---

### Post by faktorqm on 2009-04-17
Hola, pone un live cd (creo que el que usaste para instalar) y desde una terminal pone:

```
sudo fdisk -l
```

deletreo: ese u de o espacio efe de i ese ka espacio signo_menos ele

y ahi postea el resultado aca por favor. salu2!

---

### Post by sackm on 2009-04-20
uuuuuuuuuuufff e guerriado con ubuntu como loco, creo que ahora todo va bien, me faltan los drivers de sonido y video... en el video es raro porque trato de habilitar los drivers que me dice que estan disponibles y no me los habilita, se queda en 0%

---

### Post by luks911 on 2009-04-20
> **sackm said:**
> uuuuuuuuuuufff e guerriado con ubuntu como loco, creo que ahora todo va bien, me faltan los drivers de sonido y video... en el video es raro porque trato de habilitar los drivers que me dice que estan disponibles y no me los habilita, se queda en 0%

El sábado instalé la RC de 9.04 y tuve un problema similar. También tengo una placa nvidia y el instalador se quedó en el 0% y luego se colgó (sólo el instalador del driver). Hay una alternativa, que es instalarlo por terminal o synaptic: abrí una terminal y poné

```
sudo aptitude install nvidia-glx-180
``` 

Si te pregunta qué hacer porque necesita instalar otros paquetes, decile que sí. Al reiniciar deberías tener el driver andando.

---

### Post by sackm on 2009-04-20
Lista la de video:D, ahora queda la de sonido ;)

---

### Post by luks911 on 2009-04-20
> **sackm said:**
> Lista la de video:D, ahora queda la de sonido ;)

Genial. 
Con respecto al sonido, estaba viendo la wiki que te pasé unos post antes ([http://translate.google.com/translate?prev=_t&hl=es&ie=UTF-8&u=http%3A%2F%2Fwiki.ubuntu.cz%2FAsus%2520M50Vc&sl=cs&tl=es&history_state0=cs|es|a%2520do%2520sekce%2520%2522ServerLayout%2522%2520doplnit%2520%25C5%2599%25C3%25A1dek%2520](http://translate.google.com/translate?prev=_t&hl=es&ie=UTF-8&u=http%3A%2F%2Fwiki.ubuntu.cz%2FAsus%2520M50Vc&sl=cs&tl=es&history_state0=cs|es|a%2520do%2520sekce%2520%2522ServerLayout%2522%2520doplnit%2520%25C5%2599%25C3%25A1dek%2520)) y ahí dice que para el sonido tendrías que hacer lo siguiente.

1) abrir el archivo alsa-base con

```
sudo gedit /etc/modprobe.d/alsa-base
```

2) al final del archivo agregar una línea que diga (copiá y pegá)

```
options snd-hda-intel enable=1 index=0 model=m51va
```

3) guardar y reiniciar. Probá con eso a ver si va.

---

### Post by sackm on 2009-04-20
no paso nada :(

---

### Post by luks911 on 2009-04-20
Ok, no desesperes. Dos cosas:
1) ¿Qué es lo que no funciona del sonido, o sea, con qué probaste, qué archivos de audio? ¿Hiciste el intento con alguno de los .ogg que vienen con la instalación en la carpeta Examples? Esto para descartar que no sea falta de codecs.
2) También pegá acá el resultado del comando  
```
cat /etc/modprobe.d/alsa-base
```

---

### Post by sackm on 2009-04-20
trate con los archivos de la carpeta Example y lso reproduce pero no se escuchan

aqui esta el resultado del comando que me dijiste 

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

---

### Post by staar on 2009-04-20
dos cosas, un link (solución de un tipo con ubuntu y la misma placa que vos) [http://www.leprosys.info/2008/11/el-ich9-family-hd-audio-controller-no.html]("http://www.leprosys.info/2008/11/el-ich9-family-hd-audio-controller-no.html")...
y otra cosa, he visto varias veces que el problema, en algunos casos, pasa por que algo estaba en mute, hace una cosa, abri el control de volumen, anda a Preferencias,  seleccioná todas las pistas y después subiles el volumen (y chequeá que ninguna este en mute :-P)

saludos

---

### Post by sackm on 2009-04-20
ise lo del link y no paso nada, tambien comprobe lo que me dijiste  tampoco :(

---

### Post by staar on 2009-04-20
y probando estas en tu alsa-base?

```
sudo gedit /etc/modprobe.d/alsa-base
```

```
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
```

la solución esta en las opciones del driver HDA de intel, hay muchas más, el problema es encontrar cual corresponde a tu hardware específico, por ahora probá estas, si no te andan buscamos otras ;-) (cada revisión de modelos de placas es un mundo, puede ser el mismo modelo de placa, mismo nombre, todo, pero si cambiaron algo, se jode todo), acordate de reiniciar después de aplicar estos cambios, ya que estás modificando opciones del kernel ;-)

saludos

EDIT: sino querés andar reiniciando todo el tiempo, reiniciá alsa con ```
sudo /etc/init.d/alsa-utils restart
```

EDIT2: link al bug correspondiente en el launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424")

---

### Post by sackm on 2009-04-20
alsa base ? ajaja perdon soy novato

---

### Post by luks911 on 2009-04-20
alsa-base es un archivo de configuración de ALSA (Advanced Linux Sound Architecture, o en castellano, Arquitectura de Sonido Avanzada para Linux). O sea, de algún modo, y que me disculpen los que saben, el driver de sonido.
El archivo alsa-base lo modificás como te estuvimos indicando, con

```
sudo gedit /etc/modprobe.d/alsa-base
```

agregás las líneas que te sugerimos al final (probá con las que indicó staar) y guardás.

Y lo que hiciste antes con 

```
cat /etc/modprobe.d/alsa-base
```

era sólo ver el contenido del archivo.

---

### Post by sackm on 2009-04-21
no me resulto :( un dato no se si les servira...con ubuntu 9.04 la version de prueba, el audio me andaba. ahora ocupo el 8.10 :O sirve de algo :O?

---

### Post by luks911 on 2009-04-21
> **sackm said:**
> no me resulto :( un dato no se si les servira...con ubuntu 9.04 la version de prueba, el audio me andaba. ahora ocupo el 8.10 :O sirve de algo :O?

Sí, sirve. Por ser más reciente, 9.04 reconoce más hard y tiene una versión de alsa más nueva. Es muy probable que el sonido funcione cuando actualices. Lo podés hacer ahora, con la Release Candidate, o dentro de dos días con la versión final.

---

### Post by sackm on 2009-04-21
sonido funcionando :O:o quedaria el touchpad multimedia

---

### Post by staar on 2009-04-21
segun la wiki que te pasó luks, tenés que hacer lo siguiente:

editar el archivo /etc/X11/xorg.conf (este archivo contiene las configuraciones de lo que es placa de video, teclado, mouse, touchpad... OJO es muy sensible no borres nada porque siempre fue problematico, si te anda todo bien, no lo toques más...)

```
sudo gedit /etc/X11/xorg.conf
```
(sudo para obtener permisos de administrador, gedit es el editor de textos, y el resto es la ubicación del archivo ;-) )
agregá estas líneas al final
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
```
después busca la Section "ServerLayout" y agregale esta línea
```
InputDevice "Synaptics Touchpad"
```

guardá, reinicia y contanos

saludos

---

### Post by luks911 on 2009-04-21
Sumo algo a lo que dice staar. En realidad, lo que sugiere él, en la wiki dice que es para poder apagar el tocuhpad. Se me ocurre que podés aplicarlo y si con eso sólo no alcanza, también podés ir a Sistema > Preferencias > Combinaciones de teclas y ahí cambiar las correspondencias entre funciones y combinación. Por ejemplo: si el touchpad tiene una tecla que es play, en el listado de combinaciones buscás la que corresponde a "reproducir" y cambiás la combinación, en el lugar donde va la combinación, presionás la tecla del touchpad. Si te lo reconoce, va a aparecer un código donde va la combinación y es posible que funcione. Eso es lo que hice con las teclas multimedia de mi nootebok. 
Ah, en la wiki que te pasaba dice que esa función todavía no la probaron.

---

### Post by sackm on 2009-04-24
> **staar said:**
> segun la wiki que te pasó luks, tenés que hacer lo siguiente:

editar el archivo /etc/X11/xorg.conf (este archivo contiene las configuraciones de lo que es placa de video, teclado, mouse, touchpad... OJO es muy sensible no borres nada porque siempre fue problematico, si te anda todo bien, no lo toques más...)

```
sudo gedit /etc/X11/xorg.conf
```
(sudo para obtener permisos de administrador, gedit es el editor de textos, y el resto es la ubicación del archivo ;-) )
agregá estas líneas al final
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
```
después busca la Section "ServerLayout" y agregale esta línea
```
InputDevice "Synaptics Touchpad"
```

guardá, reinicia y contanos

saludos

No me aparece ninguna seccion con el nombre ServerLayout (como dato: me cambie a ubuntu 9.04 )

---

### Post by staar on 2009-04-24
si no te aparece ninguna sección con ese nombre, creala vos, agregale lo de InputDevice, y no te olvides de poner el EndSection al final, fijate como son las otras secciones, te vas a dar cuenta...

saludos

---

### Post by juancarlospaco on 2009-04-24
Si a HorizontalScroll le pones un 1 tenes ScrollHorizontal luego de reiniciar, 
hay un truco dando vueltas por ahi para hacer ese TouchPad tenga la funcion MultiTouch,
haces zoom como en el Iphone, el hardware puede 
*(aunque en windows no por que los drivers de windows no pueden)*,
yo lo hice y andubo.

---

### Post by sackm on 2009-04-25
> **staar said:**
> si no te aparece ninguna sección con ese nombre, creala vos, agregale lo de InputDevice, y no te olvides de poner el EndSection al final, fijate como son las otras secciones, te vas a dar cuenta...

saludos

Lo hice y no paso nadA, incluso no pudo iniciar ubuntu normalmente y me pidio entrar con baja resolucion y todo eso :S y tuve que borrar lo que me dijiste...lo revise por si me habia equivocado y estaba todo como me dijiste :(

---

### Post by staar on 2009-04-25
mmm, que raro, posteá acá los dos xorg.conf, para ver cual es el problema...

saludos

---

### Post by sackm on 2009-04-26
ahi esta :) 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by staar on 2009-04-26
probá con este, y contanos:```

Section "Monitor"
      Identifier     "Configured Monitor"
EndSection

Section "Screen"
      Identifier     "Default Screen"
      Monitor        "Configured Monitor"
      Device         "Configured Video Device"
      DefaultDepth   24
EndSection

Section "Module"
      Load           "glx"
EndSection

Section "Device"
      Identifier     "Configured Video Device"
      Driver         "nvidia"
      Option         "NoLogo"                "true"
EndSection 

Section "InputDevice"
      Identifier     "Synaptics Touchpad"
      Driver         "synaptics"
      Option         "SendCoreEvents"        "true"
      Option         "Device"                "/dev/psaux"
      Option         "Protocol"              "auto-dev"
      Option         "HorizScrollDelta"      "0"
      Option         "SHMConfig"             "on"
EndSection

Section "ServerLayout"
      Identifier     "Default Layout"
      Screen         "Default Screen"
      Inputdevice    "Synaptics Touchpad"
EndSection  
```

---

### Post by sackm on 2009-04-26
tal cual lo mandaste y sigue sin funcionar :(

---

### Post by staar on 2009-04-27
hiciste lo que te recomendo luks, después de poner el xorg que te pasé?

> **luks911 said:**
> Sumo algo a lo que dice staar. En realidad, lo que sugiere él, en la wiki dice que es para poder apagar el tocuhpad. Se me ocurre que podés aplicarlo y si con eso sólo no alcanza, también podés ir a Sistema > Preferencias > Combinaciones de teclas y ahí cambiar las correspondencias entre funciones y combinación. Por ejemplo: si el touchpad tiene una tecla que es play, en el listado de combinaciones buscás la que corresponde a "reproducir" y cambiás la combinación, en el lugar donde va la combinación, presionás la tecla del touchpad. Si te lo reconoce, va a aparecer un código donde va la combinación y es posible que funcione. Eso es lo que hice con las teclas multimedia de mi nootebok. 
Ah, en la wiki que te pasaba dice que esa función todavía no la probaron.

siceramente si no te funciona eso, no sabría como ayudarte, mucha info de esa máquina con ubuntu no hay (y la que hay esta en checo, polaco o ruso :-P ), pero al paracer hay algunas cositas que directamente no andan, habrá que esperar que se solucionen...

saludos

---

