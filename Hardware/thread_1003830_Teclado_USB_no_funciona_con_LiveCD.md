---
title: "Teclado USB no funciona con LiveCD"
date: 2008-12-06
forum: Hardware
---

### Post by pante on 2008-12-06
¡Hola!

Les cuento: 

En una PC no tengo instalado Ubuntu. Tuve un problema de hardware (ambos puertos PS/2 fallecieron) y tuve que comprar un ratón y un teclado USB. Ambos dispositivos funcionan perfectamente en Windows XP.

Cuando puse el Live CD de Ubuntu 7.10, en el menú de arranque puedo usar el teclado para elegir mi opción y para elegir idioma y tipo de teclado, pero un par de segundos después de darle a Enter para que inicie el LED de Bloq Num se apaga y el teclado deja de responder. Ubuntu arranca sin otro problema y puedo usar el ratón para hacer todo. Pero el teclado está muerto. No toqué mucho el Ubuntu. El Visor de sucesos del sistema dice, entre otras cosas: 
```
usb 1-1: new low speed USB device using uhci_hcd and address *
```
El mensaje se repite cada ~15 segundos y el número que simbolicé con * aumenta. Cuando desconecté el teclado el mensaje dejó de aparecer.

El teclado también funciona sin sistema operativo: puedo apretar F8 al arrancar la PC y seleccionar con el teclado desde qué dispositivo cargar el sistema operativo. Probé el Live CD de Knoppix y tanto el ratón como el teclado funcionan perfectamente. En resumen, el teclado funciona en la configuración del BIOS, con Windows, con Knoppix y en la pantalla de inicio de Ubuntu.

¿Hay algo que pueda hacer? ¿Es problema del live CD que se resuelve instalando? ¿Faltan datos de dónde los saco?

No he probado entrar al instalador y ver si el teclado sigue funcionando.

Gracias:p
_____________________________________________________

Agregado:

Probé un CD de instalación 'Alternate' y el teclado sigue funcionando durante la instalación.

Con el Live CD si desconecto el ratón y lo vuelvo a conectar lo reconoce normalmente; al teclado lo desconoce con el mensaje que cité antes.

No he probado con 8.10 porque no lo tengo y no sé si vale la pena probarlo cuando el Knoppix que tiene un año y medio me reconoce el teclado.
__________________________________________________________________

Agregado 2:

Arrancando con el teclado desconectado, cuando lo conecto ya con Ubuntu corriendo no cambia nada.

---

### Post by z37a on 2008-12-06
Solo por curiosidad, que marca de teclado es? y modelo?

---

### Post by pante on 2008-12-06
> **z37a said:**
> Solo por curiosidad, que marca de teclado es? y modelo?
El teclado es Noganet NKB-2828.

Saludos :)

---

### Post by Hei Ku on 2008-12-06
Probá de conectarlo en otro port USB.

---

### Post by pante on 2008-12-07
> **Hei Ku said:**
> Probá de conectarlo en otro port USB.

Ya había hecho eso (olvidé decirlo) y no pasó nada. Pero voy a probar de nuevo, esta vez intercambiando ratón por teclado.

Saludos :)

---

### Post by z37a on 2008-12-08
> **pante said:**
> El teclado es Noganet NKB-2828.

Saludos :)

No podras conseguir auqnue sea temporalmente otro teclado USB(otra marca) para dejarlo enchufado y tirar un lsusb a ver que te da?

---

### Post by santiagoward2000 on 2008-12-08
Una solución temporal es usar **onBoard**, un teclado en la pantalla que ya viene instalado. Hacé click derecho en el menú arriba (Aplicaciones Lugares Sistema), elegís editar menú, y en **Sistema > Preferencias** habilitás onBoard. Ahora lo podés abrir desde **Sistema > Preferencias**, y vas a poder ver si el **lsusb** te tira algo en la terminal, como dijo z37a.
Saludos!

---

### Post by pante on 2008-12-21
```
ubuntu@ubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
ubuntu@ubuntu:~$

```
:(

---

### Post by c4d0rn4 on 2008-12-21
estaba conectado el teclado? =S
ni da la hora el guacho.

---

### Post by pante on 2008-12-23
Probé el Live CD de Ubuntu 8.10 y tampoco pasa nada. :confused:

A partir del resultado con Knoppix, desempolvé (literalmente) un CD de Ubuntu 6.06 para probar. ¡Y funciona! 

```
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 002: ID 1c4f:0002
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
ubuntu@ubuntu:~$

```

Ahora la pregunta es por qué no funciona en las últimas versiones. 

Supongo que ahora tendré que ver cuál es la versión más nueva que funciona (6.10, 7.04) para instalar esa y actualizar. Espero que así no se rompa el soporte a mi teclado. :(

Saludos:)

---

### Post by Hei Ku on 2008-12-24
en alguno que te ande, pone lsmod, para ver qué drivers carga.

---

### Post by pante on 2008-12-24
Tenía por ahí un CD de Xubuntu 7.04, lo probé y también funciona.

```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
ppdev                  10116  0 
lp                     12452  0 
savage                 34048  2 
drm                    81044  3 savage
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
container               5248  0 
button                  8720  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
fuse                   46612  1 
ipv6                  268704  8 
snd_via82xx            29208  1 
gameport               16520  1 snd_via82xx
snd_ac97_codec         98336  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
xpad                    9988  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_prosavage           5248  0 
i2c_algo_bit            8712  1 i2c_prosavage
snd_timer              23684  2 snd_pcm,snd_seq
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
psmouse                38920  0 
serio_raw               7940  0 
i2c_viapro             10132  0 
i2c_core               22784  4 i2c_ec,i2c_prosavage,i2c_algo_bit,i2c_viapro
via_ircc               27540  0 
irda                  201276  1 via_ircc
crc_ccitt               3072  1 irda
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
via_agp                11264  1 
agpgart                35400  2 drm,via_agp
af_packet              23816  2 
joydev                 10816  0 
tsdev                   8768  0 
evdev                  11008  5 
squashfs               49028  1 
loop                   17800  2 
unionfs                74020  1 
isofs                  36284  1 
nls_iso8859_1           5120  0 
nls_cp437               6784  1 
vfat                   14208  0 
fat                    53916  1 vfat
ide_disk               17024  0 
ide_cd                 32672  2 
cdrom                  37664  1 ide_cd
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
usbhid                 26592  0 
hid                    27392  1 usbhid
via82cxxx              10372  0 [permanent]
floppy                 59524  0 
via_rhine              25608  0 
mii                     6528  1 via_rhine
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  5 xpad,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
ubuntu@ubuntu:~$ 

```

Estoy cada vez más cerca, pero la duda de por qué persiste.

Saludos:)

---

### Post by Hei Ku on 2008-12-24
Postea el de Ubuntu 8.10. Me parece que el problema puede venir por el lado del usbhid.

---

### Post by pante on 2009-01-01
En el Live CD de Ubuntu 8.10 no encuentro ningún teclado en pantalla, así que no puedo teclear ningun comando.

Hoy probé un CD de Damn Small Linux y el teclado no funcionó. Durante el arranque aparece un mensaje que dice algo así como "USB ... managed by **hotplug**" (más o menos). Como DSL es un derivado de Knoppix, con el que el teclado sí anda, busqué el mismo mensaje al arranque y dice algo así como "USB ... managed by **udev**".

¿Será ese el problema? Desde mi ignorancia supongo que el problema puede ser que Ubuntu esté usando *hotplug* que tiene problemas con mi teclado.

Saludos:)

---

### Post by Hei Ku on 2009-01-01
Una consulta, originalmente habías probado el 7.10. Probaste finalmente el 8.10 y tampoco anda?

EDIT: Este parece ser un bug reportado. [https://bugs.launchpad.net/ubuntu/+source/gfxboot/+bug/35530](https://bugs.launchpad.net/ubuntu/+source/gfxboot/+bug/35530)

---

### Post by pante on 2009-01-03
???

---

### Post by pante on 2009-01-08
Sintetizo lo que probé:

* Ubuntu 7.10 y 8.10, y Kubuntu 7.10 **No funcionan** 

* Ubuntu 6.06 y Xubuntu 7.04 **Sí funcionan** (también Knoppix CD 5.1.1)

Le voy a echar un ojo a ese bug reportado, si puedo aportaré allí y si tengo novedades las postearé por aquí por si alguien lo necesitara/le interesara.

Saludos:D

Edito para no hacer doble post:

Instalé el Xubuntu 7.04 que funcionaba y todo anduvo bien. Actualicé todo y todo siguió andando bien. Actualicé a Xubuntu 7.10 y siguió funcionando hasta que reinicié.

Al reiniciar tenía dos versiones de kernel en el menú: 

* Ubuntu 7.10, kernel 2.6.22-14-generic

* Ubuntu 7.10, kernel 2.6.20-17-generic

Con el 2.6.22-14-generic el teclado **no funciona**, aunque sí funciona con el otro.

Como sin el teclado no puedo entrar (no puedo escribir ni usuario ni contraseña), no puedo probar nada con la versión que no funciona bien.

Saludos:)

Edito de nuevo porque el foro me dió unos errores y dejó el mensaje como se ve y no puedo eliminarlo.

---

### Post by pante on 2009-01-17
Yo sigo posteando porque realmente me interesa saber el porqué y (si se puede) encontrar una solución. Porque actualmente estoy estancado en un Ubuntu 7.10 con kernel viejo. 

En este post voy a mostrar los resultados de *lsusb*, *lsusb -v*, *lsmod* y *dmesg* en el Xubuntu en el que me funciona el teclado y en el Kubuntu 7.10 donde no funciona pero tengo teclado en pantalla para usar el terminal.

**Xubuntu 7.04 actualizado a 7.10, usando el kernel 2.6.20** (2.6.22 no detecta el teclado).

lsusb y lsusb -v

```
pablo@pablo-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1c4f:0002  
Bus 001 Device 001: ID 0000:0000  

pablo@pablo-desktop:~$ lsusb -v

Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0458 KYE Systems Corp. (Mouse Systems)
  idProduct          0x003a 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      62
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)


Bus 001 Device 003: ID 1c4f:0002  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1c4f 
  idProduct          0x0002 
  bcdDevice            1.10
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      54
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
pablo@pablo-desktop:~$
```

dmesg 

```
pablo@pablo-desktop:~$ dmesg
[    0.000000] Linux version 2.6.20-17-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed Aug 20 16:47:34 UTC 2008 (Ubuntu 2.6.20-17.39-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000006000 end: 00000000000d6000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 00000000276f0000 end: 00000000277f0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000277f0000 size: 0000000000008000 end: 00000000277f8000 type: 3
[    0.000000] copy_e820_map() start: 00000000277f8000 size: 0000000000008000 end: 0000000027800000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000277f0000 (usable)
[    0.000000]  BIOS-e820: 00000000277f0000 - 00000000277f8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000277f8000 - 0000000027800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 631MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb810
[    0.000000] Entering add_active_range(0, 0, 161776) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   161776
[    0.000000]   HighMem    161776 ->   161776
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   161776
[    0.000000] On node 0 totalpages: 161776
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1231 pages used for memmap
[    0.000000]   Normal zone: 156449 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AMI                                   ) @ 0x000f9db0
[    0.000000] ACPI: RSDT (v001 AMIINT VIA_P6   0x00000010 MSFT 0x00000097) @ 0x277f0000
[    0.000000] ACPI: FADT (v001 AMIINT VIA_P6   0x00000011 MSFT 0x00000097) @ 0x277f0030
[    0.000000] ACPI: MADT (v001 AMIINT VIA_P6   0x00000009 MSFT 0x00000097) @ 0x277f00c0
[    0.000000] ACPI: DSDT (v001    VIA APOLLO-P 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 27800000:d7400000)
[    0.000000] Detected 1800.039 MHz processor.
[   23.036486] Built 1 zonelists.  Total pages: 160513
[   23.036501] Kernel command line: root=UUID=27fc47f1-7a12-4dcb-ad4d-2b21f56c1126 ro quiet splash locale=es_ES
[   23.036773] mapped APIC to ffffd000 (fee00000)
[   23.036779] mapped IOAPIC to ffffc000 (fec00000)
[   23.036785] Enabling fast FPU save and restore... done.
[   23.036791] Enabling unmasked SIMD FPU exception support... done.
[   23.036815] Initializing CPU#0
[   23.036982] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   23.038839] Console: colour VGA+ 80x25
[   23.040965] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.044417] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.076318] Memory: 630072k/647104k available (1993k kernel code, 16324k reserved, 900k data, 328k init, 0k highmem)
[   23.076334] virtual kernel memory layout:
[   23.076335]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   23.076337]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.076338]     vmalloc : 0xe8000000 - 0xff7fe000   ( 375 MB)
[   23.076340]     lowmem  : 0xc0000000 - 0xe77f0000   ( 631 MB)
[   23.076341]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   23.076343]       .data : 0xc02f2699 - 0xc03d36d4   ( 900 kB)
[   23.076344]       .text : 0xc0100000 - 0xc02f2699   (1993 kB)
[   23.076350] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.152807] Calibrating delay using timer specific routine.. 3603.43 BogoMIPS (lpj=7206876)
[   23.152906] Security Framework v1.0.0 initialized
[   23.152920] SELinux:  Disabled at boot.
[   23.152969] Mount-cache hash table entries: 512
[   23.153322] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   23.153347] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   23.153351] CPU: L2 cache: 128K
[   23.153356] CPU: Hyper-Threading is disabled
[   23.153359] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   23.153387] Compat vDSO mapped to ffffe000.
[   23.153395] Remapping vsyscall page to ffffe000
[   23.153423] Checking 'hlt' instruction... OK.
[   23.169074] SMP alternatives: switching to UP code
[   23.170030] Freeing SMP alternatives: 11k freed
[   23.170661] Early unpacking initramfs... done
[   23.665147] ACPI: Core revision 20060707
[   23.668690] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.671436] CPU0: Intel(R) Celeron(R) CPU 1.80GHz stepping 09
[   23.671499] Total of 1 processors activated (3603.43 BogoMIPS).
[   23.671703] ENABLING IO-APIC IRQs
[   23.671958] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.815946] Brought up 1 CPUs
[   23.816564] Booting paravirtualized kernel on bare hardware
[   23.816837] Time: 15:31:30  Date: 00/17/109
[   23.816931] NET: Registered protocol family 16
[   23.817310] EISA bus registered
[   23.817332] ACPI: bus type pci registered
[   23.823840] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[   23.823845] PCI: Using configuration type 1
[   23.823847] Setting up standard PCI resources
[   23.843231] ACPI: Interpreter enabled
[   23.843244] ACPI: Using IOAPIC for interrupt routing
[   23.845269] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.845281] PCI: Probing PCI hardware (bus 00)
[   23.847061] PCI quirk: region 0800-087f claimed by vt8235 PM
[   23.847071] PCI quirk: region 0400-040f claimed by vt8235 SMB
[   23.847614] Boot video device is 0000:01:00.0
[   23.847724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.881008] ACPI: Power Resource [URP1] (off)
[   23.881321] ACPI: Power Resource [URP2] (off)
[   23.881618] ACPI: Power Resource [FDDP] (off)
[   23.881917] ACPI: Power Resource [LPTP] (off)
[   23.887202] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   23.887904] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   23.888540] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[   23.889182] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   23.889758] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.889807] pnp: PnP ACPI init
[   23.896382] pnp: PnP ACPI: found 8 devices
[   23.896396] PnPBIOS: Disabled by ACPI PNP
[   23.896615] PCI: Using ACPI for IRQ routing
[   23.896625] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.899956] NET: Registered protocol family 8
[   23.899961] NET: Registered protocol family 20
[   23.901843] PCI: Bridge: 0000:00:01.0
[   23.901852]   IO window: disabled.
[   23.901860]   MEM window: dfd00000-dfefffff
[   23.901866]   PREFETCH window: cfb00000-dfbfffff
[   23.901897] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.901997] NET: Registered protocol family 2
[   23.935826] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.936589] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.940965] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.942843] TCP: Hash tables configured (established 131072 bind 65536)
[   23.942859] TCP reno registered
[   23.951957] checking if image is initramfs... it is
[   24.877444] Freeing initrd memory: 6768k freed
[   24.879317] audit: initializing netlink socket (disabled)
[   24.879357] audit(1232206290.924:1): initialized
[   24.879856] VFS: Disk quotas dquot_6.5.1
[   24.879916] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.880087] io scheduler noop registered
[   24.880094] io scheduler anticipatory registered
[   24.880098] io scheduler deadline registered
[   24.880139] io scheduler cfq registered (default)
[   24.880926] isapnp: Scanning for PnP cards...
[   25.234662] isapnp: No Plug & Play device found
[   25.454670] Real Time Clock Driver v1.12ac
[   25.454879] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.455172] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.458681] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.459999] mice: PS/2 mouse device common for all mice
[   25.463239] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.463861] input: Macintosh mouse button emulation as /class/input/input0
[   25.464041] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.464050] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.464861] PNP: No PS/2 controller found. Probing ports directly.
[   25.465462] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.465476] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.466081] EISA: Probing bus 0 at eisa.0
[   25.466130] EISA: Detected 0 cards.
[   25.496300] TCP cubic registered
[   25.496330] NET: Registered protocol family 1
[   25.496402] Using IPI No-Shortcut mode
[   25.496693] ACPI: (supports S0 S1 S4 S5)
[   25.496793]   Magic number: 9:314:538
[   25.497206] Time: tsc clocksource has been installed.
[   25.498282] Freeing unused kernel memory: 328k freed
[   27.081395] Capability LSM initialized
[   27.204384] ACPI: Processor [CPU1] (supports 16 throttling states)
[   27.204409] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   28.756737] usbcore: registered new interface driver usbfs
[   28.756801] usbcore: registered new interface driver hub
[   28.756902] usbcore: registered new device driver usb
[   28.758878] USB Universal Host Controller Interface driver v3.0
[   28.759054] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 16
[   28.759080] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   28.759415] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   28.759469] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000dc00
[   28.759756] usb usb1: configuration #1 chosen from 1 choice
[   28.759828] hub 1-0:1.0: USB hub found
[   28.759887] hub 1-0:1.0: 2 ports detected
[   28.864607] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 16
[   28.864635] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   28.864727] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   28.864772] uhci_hcd 0000:00:10.1: irq 16, io base 0x0000e000
[   28.865042] usb usb2: configuration #1 chosen from 1 choice
[   28.865113] hub 2-0:1.0: USB hub found
[   28.865145] hub 2-0:1.0: 2 ports detected
[   28.875018] SCSI subsystem initialized
[   28.887289] libata version 2.20 loaded.
[   28.922835] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   28.971906] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 16
[   28.971935] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   28.972017] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   28.972067] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000e400
[   28.972363] usb usb3: configuration #1 chosen from 1 choice
[   28.972450] hub 3-0:1.0: USB hub found
[   28.972483] hub 3-0:1.0: 2 ports detected
[   29.039997] Floppy drive(s): fd0 is 1.44M
[   29.081984] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 16
[   29.082022] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   29.082138] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   29.082236] ehci_hcd 0000:00:10.3: irq 16, io mem 0xdffffe00
[   29.082248] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.082508] usb usb4: configuration #1 chosen from 1 choice
[   29.082609] hub 4-0:1.0: USB hub found
[   29.082637] hub 4-0:1.0: 6 ports detected
[   29.108277] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   29.109024] FDC 0 is a post-1991 82077
[   29.198604] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   29.198645] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   29.198649] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   29.198668] VP_IDE: chipset revision 6
[   29.198671] VP_IDE: not 100% native mode: will probe irqs later
[   29.198690] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   29.198704]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[   29.198729]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[   29.198745] Probing IDE interface ide0...
[   29.618608] hda: HDS728040PLAT20, ATA DISK drive
[   30.065900] hdb: TSSTcorpCD/DVDW SH-S182F, ATAPI CD/DVD-ROM drive
[   30.122733] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.138125] Probing IDE interface ide1...
[   30.425211] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   30.645833] usb 1-1: configuration #1 chosen from 1 choice
[   30.696188] hdc: LITE-ON CD-RW SOHR-5238S, ATAPI CD/DVD-ROM drive
[   30.888473] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   31.065634] usb 2-1: configuration #1 chosen from 1 choice
[   31.081233] usbcore: registered new interface driver hiddev
[   31.094246] input: USB USB Keykoard as /class/input/input1
[   31.094298] input: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:10.0-1
[   31.368038] ide1 at 0x170-0x177,0x376 on irq 15
[   31.372823] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 17
[   31.376970] eth0: VIA Rhine II at 0x1d400, 00:0d:87:f2:58:a1, IRQ 17.
[   31.377696] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   31.422327] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   31.422348] Uniform CD-ROM driver Revision: 3.20
[   31.448699] hda: max request size: 512KiB
[   31.448870] hda: 80418240 sectors (41174 MB) w/1719KiB Cache, CHS=16383/255/63
[   31.449043] hda: cache flushes supported
[   31.449136]  hda:<6>hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   31.472436]  hda1 hda2 < hda5 hda6 hda7 > hda3
[   31.964119] Attempting manual resume
[   31.964130] swsusp: Resume From Partition 3:6
[   31.964134] PM: Checking swsusp image.
[   31.969266] PM: Resume from disk failed.
[   32.020909] kjournald starting.  Commit interval 5 seconds
[   32.020947] EXT3-fs: mounted filesystem with ordered data mode.
[   41.093232] drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
[   41.093261] drivers/usb/input/hid-core.c: timeout initializing reports
[   41.093480] input: USB USB Keykoard as /class/input/input2
[   41.093527] input: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:10.0-1
[   41.205301] input: Genius Optical Mouse as /class/input/input3
[   41.205360] input: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:10.1-1
[   41.205397] usbcore: registered new interface driver usbhid
[   41.205405] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   42.176033] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   43.747059] NET: Registered protocol family 17
[   45.480643] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.484246] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.677317] Linux agpgart interface v0.102 (c) Dave Jones
[   45.724056] irda_init()
[   45.724096] NET: Registered protocol family 23
[   45.753728] agpgart: Detected VIA P4M266x/P4N266 chipset
[   45.759220] agpgart: AGP aperture is 64M @ 0xe0000000
[   46.247520] parport: PnPBIOS parport detected.
[   46.247600] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   46.671332] input: PC Speaker as /class/input/input4
[   46.875419] usbcore: registered new interface driver xpad
[   46.875432] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   47.528519] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 18
[   47.528691] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   49.361823] fuse init (API version 7.8)
[   49.424864] lp0: using parport0 (interrupt-driven).
[   49.533391] Adding 514040k swap on /dev/hda6.  Priority:-1 extents:1 across:514040k
[   49.924462] EXT3 FS on hda7, internal journal
[   50.390571] NET: Registered protocol family 10
[   50.390813] lo: Disabled Privacy Extensions
[   58.673108] ibm_acpi: ec object not found
[   58.728232] Using specific hotkey driver
[   58.811912] No dock devices found.
[   58.923559] input: Power Button (FF) as /class/input/input5
[   58.924278] ACPI: Power Button (FF) [PWRF]
[   58.943545] input: Power Button (CM) as /class/input/input6
[   58.944290] ACPI: Power Button (CM) [PWRB]
[   58.955516] input: Sleep Button (CM) as /class/input/input7
[   58.956251] ACPI: Sleep Button (CM) [SLPB]
[   59.275396] pcc_acpi: loading...
[   61.331594] eth0: no IPv6 routers present
[   64.472875] Capability LSM initialized
[   65.637318] [drm] Initialized drm 1.1.0 20060810
[   65.671017] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   65.673411] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   65.674553] mtrr: base(0xd2000000) is not aligned on a size(0x5000000) boundary
[   65.676679] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   65.677358] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[   65.678024] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[   65.830816] ppdev: user-space parallel port driver
[   66.751858] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   66.751869] apm: overridden by ACPI.
pablo@pablo-desktop:~$ 

```

lsmod

```
pablo@pablo-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
ppdev                  10116  0 
savage                 34048  2 
drm                    81044  3 savage
capability              5896  0 
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
sbs                    15652  0 
button                  8720  0 
container               5248  0 
dock                   10268  0 
ac                      6020  0 
video                  16388  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
i2c_ec                  6016  1 sbs
battery                10756  0 
ipv6                  269088  8 
lp                     12452  0 
fuse                   46612  5 
snd_via82xx            29208  1 
gameport               16520  1 snd_via82xx
snd_ac97_codec         98464  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11272  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
xpad                    9988  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                38920  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
serio_raw               7940  0 
snd                    54020  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_prosavage           5248  0 
i2c_algo_bit            8712  1 i2c_prosavage
via_ircc               27540  0 
via_agp                11264  1 
irda                  201276  1 via_ircc
crc_ccitt               3072  1 irda
agpgart                35400  2 drm,via_agp
i2c_viapro             10132  0 
i2c_core               22656  4 i2c_ec,i2c_prosavage,i2c_algo_bit,i2c_viapro
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
soundcore               8672  1 snd
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  5 
joydev                 10816  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_disk               17024  5 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
generic                 5124  0 [permanent]
usbhid                 26592  0 
hid                    27392  1 usbhid
via82cxxx              10372  0 [permanent]
floppy                 59524  0 
via_rhine              25608  0 
mii                     6528  1 via_rhine
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  5 xpad,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
commoncap               8192  1 capability
pablo@pablo-desktop:~$ 

```

Continúa en el siguiente...

---

### Post by pante on 2009-01-17
_Kubuntu 7.10 (Live CD)_

**lsusb y lsusb -v**

```
buntu@ubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
ubuntu@ubuntu:~$ lsusb -v

Bus 004 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3
  iProduct                2
  iSerial                 1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3
  iProduct                2
  iSerial                 1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0458 KYE Systems Corp. (Mouse Systems)
  idProduct          0x003a
  bcdDevice            1.00
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      62
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3
  iProduct                2
  iSerial                 1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3
  iProduct                2
  iSerial                 1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
ubuntu@ubuntu:~$ 
```

**lsmod**

```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
ipv6                  273892  8
af_packet              24840  2
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
savage                 34176  2
drm                    83348  3 savage
ppdev                  10244  0
lp                     12580  0
speedstep_lib           6404  0
cpufreq_userspace       5280  0
cpufreq_stats           7232  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9612  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0
video                  18060  0
sbs                    19592  0
container               5504  0
button                  8976  0
dock                   10656  0
ac                      6148  0
snd_via82xx            29336  1
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0
usblp                  15104  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
i2c_prosavage           5248  0
i2c_algo_bit            7428  1 i2c_prosavage
i2c_viapro             10004  0
via_ircc               27668  0
irda                  202300  1 via_ircc
crc_ccitt               3072  1 irda
psmouse                39952  0
serio_raw               8068  0
snd_seq                53232  6
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0
i2c_core               26112  3 i2c_prosavage,i2c_algo_bit,i2c_viapro
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  13
snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
via_agp                11264  1
shpchp                 34580  0
agpgart                35016  2 drm,via_agp
pci_hotplug            32704  1 shpchp
evdev                  11136  3
battery                11012  0
usbhid                 29536  0
hid                    28928  1 usbhid
squashfs               48132  1
loop                   19076  2
unionfs                77096  1
isofs                  36412  1
ext3                  133896  0
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
nls_iso8859_1           5120  0
nls_cp437               6784  1
vfat                   14080  0
fat                    54300  1 vfat
ide_cd                 32672  1
cdrom                  37536  1 ide_cd
ide_disk               18560  2
ata_generic             8452  0
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
floppy                 60004  0
via_rhine              25992  0
mii                     6528  1 via_rhine
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
ehci_hcd               36492  0
uhci_hcd               26640  0
usbcore               138632  5 usblp,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor
ubuntu@ubuntu:~$
```

**dmesg**

```
ubuntu@ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc
version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP
Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000277f0000 (usable)
[    0.000000]  BIOS-e820: 00000000277f0000 - 00000000277f8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000277f8000 - 0000000027800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 631MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb810
[    0.000000] Entering add_active_range(0, 0, 161776) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   161776
[    0.000000]   HighMem    161776 ->   161776
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   161776
[    0.000000] On node 0 totalpages: 161776
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1231 pages used for memmap
[    0.000000]   Normal zone: 156449 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F9DB0 checksum 0
[    0.000000] ACPI: RSDP 000F9DB0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 277F0000, 002C (r1 AMIINT VIA_P6         10
MSFT       97)
[    0.000000] ACPI: FACP 277F0030, 0081 (r1 AMIINT VIA_P6         11
MSFT       97)
[    0.000000] ACPI: DSDT 277F0120, 2EC0 (r1    VIA APOLLO-P     1000
MSFT  100000D)
[    0.000000] ACPI: FACS 277F8000, 0040
[    0.000000] ACPI: APIC 277F00C0, 005C (r1 AMIINT VIA_P6          9
MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap:
27800000:d7400000)
[    0.000000] Built 1 zonelists.  Total pages: 160513
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz
file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz
quiet splash -- locale=es_ES console-setup/layoutcode=latam
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1799.983 MHz processor.
[   54.163606] Console: colour VGA+ 80x25
[   54.165655] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   54.169022] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   54.200521] Memory: 629388k/647104k available (2015k kernel code,
17044k reserved, 916k data, 364k init, 0k highmem)
[   54.200537] virtual kernel memory layout:
[   54.200539]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   54.200542]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   54.200544]     vmalloc : 0xe8000000 - 0xff7fe000   ( 375 MB)
[   54.200546]     lowmem  : 0xc0000000 - 0xe77f0000   ( 631 MB)
[   54.200547]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   54.200549]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   54.200550]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   54.200555] Checking if this processor honours the WP bit even in
supervisor mode... Ok.
[   54.200620] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4,
CPUs=1, Nodes=1
[   54.280530] Calibrating delay using timer specific routine..
3603.59 BogoMIPS (lpj=7207190)
[   54.280581] Security Framework v1.0.0 initialized
[   54.280599] SELinux:  Disabled at boot.
[   54.280623] Mount-cache hash table entries: 512
[   54.280966] CPU: After generic identify, caps: bfebfbff 00000000
00000000 00000000 00004400 00000000 00000000
[   54.280994] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   54.280999] CPU: L2 cache: 128K
[   54.281004] CPU: Hyper-Threading is disabled
[   54.281009] CPU: After all inits, caps: bfebfbff 00000000 00000000
0000b080 00004400 00000000 00000000
[   54.281037] Compat vDSO mapped to ffffe000.
[   54.281070] Checking 'hlt' instruction... OK.
[   54.296826] SMP alternatives: switching to UP code
[   54.297778] Freeing SMP alternatives: 11k freed
[   54.298601] Early unpacking initramfs... done
[   54.834165] ACPI: Core revision 20070126
[   54.834316] ACPI: Looking for DSDT in initramfs... error, file
/DSDT.aml not found.
[   54.837157] CPU0: Intel(R) Celeron(R) CPU 1.80GHz stepping 09
[   54.837225] Total of 1 processors activated (3603.59 BogoMIPS).
[   54.837431] ENABLING IO-APIC IRQs
[   54.837672] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   54.983633] Brought up 1 CPUs
[   54.984026] Booting paravirtualized kernel on bare hardware
[   54.984193] Time:  4:46:08  Date: 00/17/109
[   54.984282] NET: Registered protocol family 16
[   54.984679] EISA bus registered
[   54.984720] ACPI: bus type pci registered
[   54.991181] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[   54.991185] PCI: Using configuration type 1
[   54.991189] Setting up standard PCI resources
[   55.003712] ACPI: EC: Look up EC in DSDT
[   55.010309] ACPI: Interpreter enabled
[   55.010323] ACPI: (supports S0 S1 S4 S5)
[   55.010372] ACPI: Using IOAPIC for interrupt routing
[   55.026131] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   55.026148] PCI: Probing PCI hardware (bus 00)
[   55.026979] PCI quirk: region 0800-087f claimed by vt8235 PM
[   55.026987] PCI quirk: region 0400-040f claimed by vt8235 SMB
[   55.027696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   55.053129] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   55.053352] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   55.053562] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[   55.053779] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   55.054212] ACPI: Power Resource [URP1] (off)
[   55.054299] ACPI: Power Resource [URP2] (off)
[   55.054379] ACPI: Power Resource [FDDP] (off)
[   55.054457] ACPI: Power Resource [LPTP] (off)
[   55.054509] Linux Plug and Play Support v0.97 (c) Adam Belay
[   55.054551] pnp: PnP ACPI init
[   55.054583] ACPI: bus type pnp registered
[   55.060578] pnp: PnP ACPI: found 8 devices
[   55.060588] ACPI: ACPI bus type pnp unregistered
[   55.060598] PnPBIOS: Disabled by ACPI PNP
[   55.060811] PCI: Using ACPI for IRQ routing
[   55.060818] PCI: If a device doesn't work, try "pci=routeirq".  If
it helps, post a report
[   55.064034] NET: Registered protocol family 8
[   55.064039] NET: Registered protocol family 20
[   55.067359] Time: tsc clocksource has been installed.
[   55.096161] PCI: Bridge: 0000:00:01.0
[   55.096166]   IO window: disabled.
[   55.096174]   MEM window: dfd00000-dfefffff
[   55.096180]   PREFETCH window: cfb00000-dfbfffff
[   55.096213] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   55.096252] NET: Registered protocol family 2
[   55.135390] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   55.136004] TCP established hash table entries: 131072 (order: 8,
1572864 bytes)
[   55.142678] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   55.144785] TCP: Hash tables configured (established 131072 bind 65536)
[   55.144798] TCP reno registered
[   55.155658] checking if image is initramfs...<6>Switched to high
resolution mode on CPU 0
[   55.607123]  it is
[   56.188930] Freeing initrd memory: 7313k freed
[   56.190579] audit: initializing netlink socket (disabled)
[   56.190621] audit(1232167568.764:1): initialized
[   56.200817] VFS: Disk quotas dquot_6.5.1
[   56.201123] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   56.201665] io scheduler noop registered
[   56.201673] io scheduler anticipatory registered
[   56.201676] io scheduler deadline registered
[   56.201774] io scheduler cfq registered (default)
[   56.201803] PCI: VIA PCI bridge detected. Disabling DAC.
[   56.201891] Boot video device is 0000:01:00.0
[   56.202619] isapnp: Scanning for PnP cards...
[   56.556487] isapnp: No Plug & Play device found
[   56.780484] Real Time Clock Driver v1.12ac
[   56.780956] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports,
IRQ sharing enabled
[   56.781139] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   56.784293] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   56.788479] RAMDISK driver initialized: 16 RAM disks of 65536K size
1024 blocksize
[   56.789147] input: Macintosh mouse button emulation as /class/input/input0
[   56.789824] PNP: No PS/2 controller found. Probing ports directly.
[   56.790385] serio: i8042 KBD port at 0x60,0x64 irq 1
[   56.790404] serio: i8042 AUX port at 0x60,0x64 irq 12
[   56.791348] mice: PS/2 mouse device common for all mice
[   56.791982] EISA: Probing bus 0 at eisa.0
[   56.792039] EISA: Detected 0 cards.
[   56.792286] TCP cubic registered
[   56.792340] NET: Registered protocol family 1
[   56.792411] Using IPI No-Shortcut mode
[   56.793036]   Magic number: 9:901:767
[   56.793324]   hash matches device ptyp3
[   56.794817] Freeing unused kernel memory: 364k freed
[   58.407703] AppArmor: AppArmor
initialized<5>audit(1232167570.764:2):  type=1505 info="AppArmor
initialized" pid=1161
[   58.429743] fuse init (API version 7.8)
[   58.446005] Failure registering capabilities with primary security module.
[   58.488025] ACPI: Processor [CPU1] (supports 16 throttling states)
[   58.488069] ACPI Exception (processor_core-0783): AE_NOT_FOUND,
Processor Device is not present [20070126]
[   60.274878] usbcore: registered new interface driver usbfs
[   60.274961] usbcore: registered new interface driver hub
[   60.275067] usbcore: registered new device driver usb
[   60.276979] USB Universal Host Controller Interface driver v3.0
[   60.277160] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level,
low) -> IRQ 16
[   60.277185] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   60.277534] uhci_hcd 0000:00:10.0: new USB bus registered, assigned
bus number 1
[   60.277588] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000dc00
[   60.277898] usb usb1: configuration #1 chosen from 1 choice
[   60.277994] hub 1-0:1.0: USB hub found
[   60.278021] hub 1-0:1.0: 2 ports detected
[   60.379057] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level,
low) -> IRQ 16
[   60.379080] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   60.379153] uhci_hcd 0000:00:10.1: new USB bus registered, assigned
bus number 2
[   60.379195] uhci_hcd 0000:00:10.1: irq 16, io base 0x0000e000
[   60.379452] usb usb2: configuration #1 chosen from 1 choice
[   60.379542] hub 2-0:1.0: USB hub found
[   60.379565] hub 2-0:1.0: 2 ports detected
[   60.424969] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   60.424982] ide: Assuming 33MHz system bus speed for PIO modes;
override with idebus=xx
[   60.474001] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   60.482835] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level,
low) -> IRQ 16
[   60.482858] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   60.482936] uhci_hcd 0000:00:10.2: new USB bus registered, assigned
bus number 3
[   60.482982] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000e400
[   60.483253] usb usb3: configuration #1 chosen from 1 choice
[   60.483347] hub 3-0:1.0: USB hub found
[   60.483373] hub 3-0:1.0: 2 ports detected
[   60.542095] Floppy drive(s): fd0 is 1.44M
[   60.589000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level,
low) -> IRQ 16
[   60.589036] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   60.589146] ehci_hcd 0000:00:10.3: new USB bus registered, assigned
bus number 4
[   60.589238] ehci_hcd 0000:00:10.3: irq 16, io mem 0xdffffe00
[   60.618398] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   60.618433] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00,
driver 10 Dec 2004
[   60.618706] usb usb4: configuration #1 chosen from 1 choice
[   60.618794] hub 4-0:1.0: USB hub found
[   60.618822] hub 4-0:1.0: 6 ports detected
[   60.627602] FDC 0 is a post-1991 82077
[   60.723150] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   60.723192] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   60.723195] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   60.723218] VP_IDE: chipset revision 6
[   60.723222] VP_IDE: not 100% native mode: will probe irqs later
[   60.723242] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on
pci0000:00:11.1
[   60.723257]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings:
hda:DMA, hdb:DMA
[   60.723281]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings:
hdc:pio, hdd:pio
[   60.723295] Probing IDE interface ide0...
[   60.997693] end_request: I/O error, dev fd0, sector 0
[   61.137566] hda: HDS728040PLAT20, ATA DISK drive
[   61.920301] hdb: TSSTcorpCD/DVDW SH-S182F, ATAPI CD/DVD-ROM drive
[   61.976765] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   61.993136] Probing IDE interface ide1...
[   62.071956] end_request: I/O error, dev fd0, sector 0
[   62.167797] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   62.519445] hdc: LITE-ON CD-RW SOHR-5238S, ATAPI CD/DVD-ROM drive
[   63.146214] end_request: I/O error, dev fd0, sector 0
[   63.190463] ide1 at 0x170-0x177,0x376 on irq 15
[   63.206389] SCSI subsystem initialized
[   63.220028] libata version 2.21 loaded.
[   63.225283] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level,
low) -> IRQ 17
[   63.230075] eth0: VIA Rhine II at 0x1d400, 00:0d:87:f2:58:a1, IRQ 17.
[   63.230802] eth0: MII PHY found at address 1, status 0x786d
advertising 05e1 Link 45e1.
[   63.255056] hda: max request size: 512KiB
[   63.284639] hda: 80418240 sectors (41174 MB) w/1719KiB Cache,
CHS=16383/255/63, UDMA(133)
[   63.289403] hda: cache flushes supported
[   63.289516]  hda: hda1 hda2 < hda5 hda6 hda7 > hda3
[   63.354337] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB
Cache, UDMA(33)
[   63.354354] Uniform CD-ROM driver Revision: 3.20
[   63.373401] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   64.220443] end_request: I/O error, dev fd0, sector 0
[   65.328941] kjournald starting.  Commit interval 5 seconds
[   65.328978] EXT3-fs: mounted filesystem with ordered data mode.
[   65.883431] ISO 9660 Extensions: Microsoft Joliet Level 3
[   65.946217] ISO 9660 Extensions: RRIP_1991A
[   66.205122] Registering unionfs 1.4
[   66.205129] unionfs: debugging is not enabled
[   66.257178] loop: module loaded
[   66.511794] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[   67.364837] usb 1-1: configuration #1 chosen from 1 choice
[   72.356792] usb 1-1: can't set config #1, error -110
[   72.594782] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   72.768102] usb 2-1: configuration #1 chosen from 1 choice
[   73.018141] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   73.195425] usb 2-2: configuration #1 chosen from 1 choice
[   73.217898] usbcore: registered new interface driver hiddev
[   73.237298] input: Genius Optical Mouse as /class/input/input1
[   73.237366] input: USB HID v1.10 Mouse [Genius Optical Mouse] on
usb-0000:00:10.1-1
[   73.237413] usbcore: registered new interface driver usbhid
[   73.237422] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c:
v2.6:USB HID core driver
[  154.993271] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  155.066926] Linux agpgart interface v0.102 (c) Dave Jones
[  155.126664] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  155.185301] agpgart: Detected VIA P4M266x/P4N266 chipset
[  155.191789] agpgart: AGP aperture is 64M @ 0xe0000000
[  156.793321] input: PC Speaker as /class/input/input2
[  156.813399] parport_pc 00:03: reported by Plug and Play ACPI
[  156.813479] parport0: PC-style at 0x378 (0x778), irq 7, dma 3
[PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  157.192785] irda_init()
[  157.192829] NET: Registered protocol family 23
[  158.032716] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c:
usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04B8
pid 0x0005
[  158.032770] usbcore: registered new interface driver usblp
[  158.032776] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c:
v0.13: USB Printer Device Class driver
[  158.658625] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level,
low) -> IRQ 18
[  158.658789] PCI: Setting latency timer of device 0000:00:11.5 to 64
[  161.206921] Adding 514040k swap on /dev/hda6.  Priority:-1
extents:1 across:514040k
[  165.594625] No dock devices found.
[  166.007852] input: Power Button (FF) as /class/input/input3
[  166.019016] ACPI: Power Button (FF) [PWRF]
[  166.074305] input: Power Button (CM) as /class/input/input4
[  166.075023] ACPI: Power Button (CM) [PWRB]
[  166.102269] input: Sleep Button (CM) as /class/input/input5
[  166.102973] ACPI: Sleep Button (CM) [SLPB]
[  172.449194] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  177.793017] lp0: using parport0 (interrupt-driven).
[  177.899873] ppdev: user-space parallel port driver
[  183.364954] [drm] Initialized drm 1.1.0 20060810
[  183.393253] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level,
low) -> IRQ 19
[  183.395364] [drm] Initialized savage 2.4.1 20050313 on minor 0
[  183.396613] mtrr: base(0xd2000000) is not aligned on a
size(0x5000000) boundary
[  183.397924] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  183.398203] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[  183.398444] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[  183.923609] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  183.923619] apm: overridden by ACPI.
[  186.996756] Failure registering capabilities with primary security module.
[  192.249117] Bluetooth: Core ver 2.11
[  192.249387] NET: Registered protocol family 31
[  192.249395] Bluetooth: HCI device and connection manager initialized
[  192.249403] Bluetooth: HCI socket layer initialized
[  192.456205] Bluetooth: L2CAP ver 2.8
[  192.456216] Bluetooth: L2CAP socket layer initialized
[  192.794595] Bluetooth: RFCOMM socket layer initialized
[  192.794839] Bluetooth: RFCOMM TTY layer initialized
[  192.794847] Bluetooth: RFCOMM ver 1.8
[  195.400564] NET: Registered protocol family 17
[  202.064426] NET: Registered protocol family 10
[  202.064925] lo: Disabled Privacy Extensions
[  212.786053] eth0: no IPv6 routers present
[  333.353392] usb 1-1: USB disconnect, address 3
[  334.347715] usb 1-1: new low speed USB device using uhci_hcd and address 4
[  349.946287] usb 1-1: new low speed USB device using uhci_hcd and address 5
[  365.544840] usb 1-1: new low speed USB device using uhci_hcd and address 6
[  380.576382] usb 2-2: USB disconnect, address 3
[  380.576784] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c:
usblp0: removed
[  381.127416] usb 1-1: new low speed USB device using uhci_hcd and address 7
[  396.582201] usb 1-1: new low speed USB device using uhci_hcd and address 8
[  412.037017] usb 1-1: new low speed USB device using uhci_hcd and address 9
[  427.491779] usb 1-1: new low speed USB device using uhci_hcd and address 10
[  442.946562] usb 1-1: new low speed USB device using uhci_hcd and address 11
[  458.401356] usb 1-1: new low speed USB device using uhci_hcd and address 12
[  473.856112] usb 1-1: new low speed USB device using uhci_hcd and address 13
[  489.310912] usb 1-1: new low speed USB device using uhci_hcd and address 14
[  504.765717] usb 1-1: new low speed USB device using uhci_hcd and address 15
[  520.220490] usb 1-1: new low speed USB device using uhci_hcd and address 16
[  535.675291] usb 1-1: new low speed USB device using uhci_hcd and address 17
[  551.130059] usb 1-1: new low speed USB device using uhci_hcd and address 18
[  566.584850] usb 1-1: new low speed USB device using uhci_hcd and address 19

...(se sigue repitiendo)

[ 1076.592743] usb 1-1: new low speed USB device using uhci_hcd and address 52
[ 1092.047537] usb 1-1: new low speed USB device using uhci_hcd and address 53
[ 1107.502329] usb 1-1: new low speed USB device using uhci_hcd and address 54
ubuntu@ubuntu:~$
```

Saludos:)

---

### Post by abn91c on 2009-01-17
Revisa el BIOS de la computadore, busca una linea que decie "USB Support in DOS" o algo similar

---

