---
title: "Problema con Modem Huawei E166 - Ubuntu 910"
date: 2009-11-21
forum: Hardware
---

### Post by neiker on 2009-11-21
Buenas... 
Tengo un modem [Huawei E166 de Claro]("http://www.blogdemoviles.com.ar/huawei-e166-modem-3g-de-claro/"), y algunos problemas para instalarlo en Ubuntu 9.10 32bits en mi notebook:[INDENT]HP Compaq F506LA
AMD Turion™ 64 MK-36 de 2,0 GHz
([info]("http://www.compusariato.com/hpf506lagb124LA.html"))
[/INDENT]Al conectar el modem me aparece lo siguiente:
[IMG]http://img214.imageshack.us/img214/5310/pgsm.jpg[/IMG]

Y desaparece a los pocos segundos.
Así que cree la conexion a mano (Click derecho en el icono de conexiones y configurar conexiones, o "editar" no estoy seguro), al crear la conexion veo que hay una opcion para elegir el modem, pero ahi no aparece ninguno. Igualmente hice la conexion pero no me aparece:
[IMG]http://img10.imageshack.us/img10/1930/pant02.jpg[/IMG]

Tambien instalé el gnome-ppp pero en la configuracion pongo "Detectar" y me dice que no se encuentra ningun modem.

El lsusb -v me da lo siguiente:
```
Bus 002 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x1001 E620 USB Modem
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          108
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)


```el wvdial tampoco detecta el modem (me dice que no encuentra el modem o el modem está en uso)

Alguien tiene idea de que es lo que estoy haciendo mal?


Saludos!

EDITO:
El dmesg me da lo siguiente:
```
[COLOR=#000000][FONT=Times New Roman][COLOR=#222222][FONT=arial]neiker@neiker-laptop:~$ dmesg
[  384.112034] usb 2-2: new full speed USB device using ohci_hcd and address 6
[  384.348137] usb 2-2: configuration #1 chosen from 1 choice
[  384.353250] scsi1607 : SCSI emulation for USB Mass Storage devices
[  384.354221] usb 2-2: USB disconnect, address 6
[  384.360256] usb-storage: device found at 6
[  384.360260] usb-storage: waiting for device to settle before scanning
[  385.124069] usb 2-2: new full speed USB device using ohci_hcd and address 7
[  385.340286] usb 2-2: configuration #1 chosen from 1 choice
[  385.348638] option 2-2:1.0: GSM modem (1-port) converter detected
[  385.348819] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  385.354453] option 2-2:1.1: GSM modem (1-port) converter detected
[  385.354621] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  385.381712] option 2-2:1.2: GSM modem (1-port) converter detected
[  385.381884] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  385.384970] scsi1611 : SCSI emulation for USB Mass Storage devices
[  385.391882] usb-storage: device found at 7
[  385.391890] usb-storage: waiting for device to settle before scanning
[  390.396099] usb-storage: device scan complete
[  390.408093] scsi 1611:0:0:0: CD-ROM            HUAWEI   Mass
Storage     2.31 PQ: 0 ANSI: 2
[  390.420097] scsi 1611:0:0:1: Direct-Access     HUAWEI   SD Storage
    2.31 PQ: 0 ANSI: 2
[  390.500071] sr1: scsi-1 drive
[  390.500207] sr 1611:0:0:0: Attached scsi CD-ROM sr1
[  390.500276] sr 1611:0:0:0: Attached scsi generic sg2 type 5
[  390.500378] sd 1611:0:0:1: Attached scsi generic sg3 type 0
[  390.537046] option: option_instat_callback: error -108
[  390.544179] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  390.544194] option 2-2:1.0: device disconnected
[  390.545737] modem-manager[959]: segfault at 52452045 ip 00d3f166 sp
bff6a1f8 error 6 in libdbus-1.so.3.4.0[d21000+37000]
[  390.556121] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  390.556140] option 2-2:1.1: device disconnected
[  390.556193] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  390.556207] option 2-2:1.2: device disconnected
[  390.732038] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  390.940171] option 2-2:1.2: GSM modem (1-port) converter detected
[  390.940267] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  390.949124] option 2-2:1.1: GSM modem (1-port) converter detected
[  390.949221] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  390.957135] option 2-2:1.0: GSM modem (1-port) converter detected
[  390.957238] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  390.999042] option: option_instat_callback: error -108
[  391.004179] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  391.004194] option 2-2:1.0: device disconnected
[  391.004249] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  391.004265] option 2-2:1.1: device disconnected
[  391.004311] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  391.004324] option 2-2:1.2: device disconnected
[  391.188064] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  391.404909] option 2-2:1.2: GSM modem (1-port) converter detected
[  391.405003] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  391.405060] option 2-2:1.1: GSM modem (1-port) converter detected
[  391.405105] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  391.405147] option 2-2:1.0: GSM modem (1-port) converter detected
[  391.405198] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  391.443039] option: option_instat_callback: error -108
[  391.445005] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  391.445024] option 2-2:1.0: device disconnected
[  391.445078] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  391.445092] option 2-2:1.1: device disconnected
[  391.445141] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  391.445154] option 2-2:1.2: device disconnected
[  391.620113] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  391.873177] option 2-2:1.2: GSM modem (1-port) converter detected
[  391.873274] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  391.877177] option 2-2:1.1: GSM modem (1-port) converter detected
[  391.877273] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  391.885979] option 2-2:1.0: GSM modem (1-port) converter detected
[  391.886080] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  391.923037] option: option_instat_callback: error -108
[  391.927163] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  391.927183] option 2-2:1.0: device disconnected
[  391.927238] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  391.927252] option 2-2:1.1: device disconnected
[  391.927300] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  391.927313] option 2-2:1.2: device disconnected
[  392.096066] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  392.300121] option 2-2:1.2: GSM modem (1-port) converter detected
[  392.300213] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  392.309113] option 2-2:1.1: GSM modem (1-port) converter detected
[  392.309208] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  392.316585] option 2-2:1.0: GSM modem (1-port) converter detected
[  392.316689] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  392.351041] option: option_instat_callback: error -108
[  392.360411] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  392.360431] option 2-2:1.0: device disconnected
[  392.360486] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  392.360500] option 2-2:1.1: device disconnected
[  392.360546] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  392.360559] option 2-2:1.2: device disconnected
[  392.527983] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  392.732172] option 2-2:1.2: GSM modem (1-port) converter detected
[  392.732266] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  392.735188] option 2-2:1.1: GSM modem (1-port) converter detected
[  392.735280] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  392.735327] option 2-2:1.0: GSM modem (1-port) converter detected
[  392.735380] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  392.793045] option: option_instat_callback: error -108
[  392.798972] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  392.798986] option 2-2:1.0: device disconnected
[  392.799041] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  392.799055] option 2-2:1.1: device disconnected
[  392.799103] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  392.799116] option 2-2:1.2: device disconnected
[  392.964057] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  393.176169] option 2-2:1.2: GSM modem (1-port) converter detected
[  393.176265] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  393.184583] option 2-2:1.1: GSM modem (1-port) converter detected
[  393.184678] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  393.192365] option 2-2:1.0: GSM modem (1-port) converter detected
[  393.192469] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  393.193932] sd 1611:0:0:1: [sdb] Attached SCSI removable disk
[  393.231041] option: option_instat_callback: error -108
[  393.232174] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  393.232188] option 2-2:1.0: device disconnected
[  393.232242] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  393.232257] option 2-2:1.1: device disconnected
[  393.232306] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  393.232320] option 2-2:1.2: device disconnected
[  393.404062] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  393.607820] option 2-2:1.2: GSM modem (1-port) converter detected
[  393.607912] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  393.620154] option 2-2:1.1: GSM modem (1-port) converter detected
[  393.620250] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  393.623899] option 2-2:1.0: GSM modem (1-port) converter detected
[  393.624046] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  393.667039] option: option_instat_callback: error -108
[  393.670369] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  393.670384] option 2-2:1.0: device disconnected
[  393.670437] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  393.670452] option 2-2:1.1: device disconnected
[  393.670499] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  393.670512] option 2-2:1.2: device disconnected
[  393.850595] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  394.061185] option 2-2:1.2: GSM modem (1-port) converter detected
[  394.061281] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  394.064777] option 2-2:1.1: GSM modem (1-port) converter detected
[  394.064873] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  394.079210] option 2-2:1.0: GSM modem (1-port) converter detected
[  394.079307] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  394.123043] option: option_instat_callback: error -108
[  394.125678] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  394.125692] option 2-2:1.0: device disconnected
[  394.125746] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  394.125761] option 2-2:1.1: device disconnected
[  394.125809] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  394.125822] option 2-2:1.2: device disconnected
[  394.296128] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  394.497179] option 2-2:1.2: GSM modem (1-port) converter detected
[  394.497272] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  394.501165] option 2-2:1.1: GSM modem (1-port) converter detected
[  394.501261] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  394.508508] option 2-2:1.0: GSM modem (1-port) converter detected
[  394.508607] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  394.550050] option: option_instat_callback: error -108
[  394.560404] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  394.560424] option 2-2:1.0: device disconnected
[  394.560476] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  394.560490] option 2-2:1.1: device disconnected
[  394.560535] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  394.560549] option 2-2:1.2: device disconnected
[  394.728057] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  394.948791] option 2-2:1.2: GSM modem (1-port) converter detected
[  394.948884] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  394.951282] option 2-2:1.1: GSM modem (1-port) converter detected
[  394.951400] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  394.960132] option 2-2:1.0: GSM modem (1-port) converter detected
[  394.960232] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  394.997042] option: option_instat_callback: error -108
[  395.003429] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  395.003447] option 2-2:1.0: device disconnected
[  395.003500] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  395.003514] option 2-2:1.1: device disconnected
[  395.003562] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  395.003575] option 2-2:1.2: device disconnected
[  395.168057] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  395.387595] option 2-2:1.2: GSM modem (1-port) converter detected
[  395.387688] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  395.397145] option 2-2:1.1: GSM modem (1-port) converter detected
[  395.397239] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  395.404093] option 2-2:1.0: GSM modem (1-port) converter detected
[  395.404196] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  395.440043] option: option_instat_callback: error -108
[  395.444326] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  395.444346] option 2-2:1.0: device disconnected
[  395.444402] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  395.444416] option 2-2:1.1: device disconnected
[  395.444464] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  395.444478] option 2-2:1.2: device disconnected
[  395.612142] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  395.822184] option 2-2:1.2: GSM modem (1-port) converter detected
[  395.822278] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  395.822321] option 2-2:1.1: GSM modem (1-port) converter detected
[  395.822366] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  395.822408] option 2-2:1.0: GSM modem (1-port) converter detected
[  395.822460] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  395.885046] option: option_instat_callback: error -108
[  395.888176] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  395.888197] option 2-2:1.0: device disconnected
[  395.888252] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  395.888266] option 2-2:1.1: device disconnected
[  395.888312] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  395.888324] option 2-2:1.2: device disconnected
[  396.068055] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  396.292255] option 2-2:1.2: GSM modem (1-port) converter detected
[  396.292350] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  396.301597] option 2-2:1.1: GSM modem (1-port) converter detected
[  396.301692] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  396.309135] option 2-2:1.0: GSM modem (1-port) converter detected
[  396.309238] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  396.361045] option: option_instat_callback: error -108
[  396.364170] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  396.364190] option 2-2:1.0: device disconnected
[  396.364245] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  396.364259] option 2-2:1.1: device disconnected
[  396.364305] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  396.364319] option 2-2:1.2: device disconnected
[  396.544065] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  396.764169] option 2-2:1.2: GSM modem (1-port) converter detected
[  396.764262] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  396.772581] option 2-2:1.1: GSM modem (1-port) converter detected
[  396.772677] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  396.781115] option 2-2:1.0: GSM modem (1-port) converter detected
[  396.781218] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  396.821041] option: option_instat_callback: error -108
[  396.823891] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  396.823910] option 2-2:1.0: device disconnected
[  396.823965] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  396.823979] option 2-2:1.1: device disconnected
[  396.824084] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  396.824099] option 2-2:1.2: device disconnected
[  396.992057] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  397.212107] option 2-2:1.2: GSM modem (1-port) converter detected
[  397.212199] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  397.221120] option 2-2:1.1: GSM modem (1-port) converter detected
[  397.221213] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  397.228707] option 2-2:1.0: GSM modem (1-port) converter detected
[  397.228809] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  397.269045] option: option_instat_callback: error -108
[  397.272191] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  397.272211] option 2-2:1.0: device disconnected
[  397.272266] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  397.272279] option 2-2:1.1: device disconnected
[  397.272326] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  397.272341] option 2-2:1.2: device disconnected
[  397.436056] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  397.650173] option 2-2:1.2: GSM modem (1-port) converter detected
[  397.650264] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  397.650308] option 2-2:1.1: GSM modem (1-port) converter detected
[  397.650355] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  397.650397] option 2-2:1.0: GSM modem (1-port) converter detected
[  397.650448] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  397.709045] option: option_instat_callback: error -108
[  397.712182] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  397.712203] option 2-2:1.0: device disconnected
[  397.712257] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  397.712272] option 2-2:1.1: device disconnected
[  397.712321] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  397.712333] option 2-2:1.2: device disconnected
[  397.884067] usb 2-2: reset full speed USB device using ohci_hcd and address 7
[  398.094219] option 2-2:1.2: GSM modem (1-port) converter detected
[  398.094313] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  398.101160] option 2-2:1.1: GSM modem (1-port) converter detected
[  398.101255] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  398.108115] option 2-2:1.0: GSM modem (1-port) converter detected
[  398.108212] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  398.167040] option: option_instat_callback: error -108
[  398.168155] option1 ttyUSB2: GSM modem (1-port) converter now
disconnected from ttyUSB2
[  398.168175] option 2-2:1.0: device disconnected
[  398.168231] option1 ttyUSB1: GSM modem (1-port) converter now
disconnected from ttyUSB1
[  398.168244] option 2-2:1.1: device disconnected
[  398.168291] option1 ttyUSB0: GSM modem (1-port) converter now
disconnected from ttyUSB0
[  398.168305] option 2-2:1.2: device disconnected
[  398.344495] usb 2-2: reset full speed USB device using ohci_hcd and address 7
neiker@neiker-laptop:~$[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#000000][FONT=Times New Roman][COLOR=#222222][FONT=arial]

[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by neiker on 2009-11-22
"dobleposteo" para revivir el thread...

[COLOR=#000000][FONT=Times New Roman][COLOR=#222222][FONT=arial]Problema solucionado... ¿Como? Bueno, le pedi a un amigo un modem ZTE que no usaba (aprobeche porque mi modem ya andaba de ultimas). Al conectarlo tampoco me funcionaba, asi que me puse a googlear y encontre esto:
[http://josernestodavila.blogspot.com/2009/11/zte-mf626-de-movistar-en-ubuntu-910.html](http://josernestodavila.blogspot.com/2009/11/zte-mf626-de-movistar-en-ubuntu-910.html)
Que son los mismos pasos que seguia yo, pero yo no expulzaba el disco. Asi que expluse el disco y el modem salio andado, pero no me conectaba, asi que cambie los datos de conexion que tiene ubuntu sobre claro por estos que son los que tenia en windows:
APN: internet.ctimovil.com.ar 
Numero:*99# 
Usuario: ctigprs 
Contraseña: ctigprs

[/FONT][/COLOR][/FONT][/COLOR]

Ahora si, nunca mas con Windows...  :D

Saludos!

---

