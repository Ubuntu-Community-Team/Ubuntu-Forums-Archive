---
title: "Toshiba A205-5820 Problemas Drivers Audio y Video"
date: 2009-06-14
forum: Hardware
---

### Post by jpoeta on 2009-06-14
Hace mucho tiempo deje Ubuntu en la version 6.10, hace poco me compre una Laptop tenía Windows Vista pero decidí volver a Ubuntu y en la nueva versión el Wifi corrió de forma automática y sin Problemas. Eso me animó a instalarme el 9.04 ayer.
Bueno les explico los problemas que estoy teniendo, el audio que normalmente es potente aqui tiene un volumen muy bajo en parlantes y microfono. 
Por el lado de el video no puedo disfrutar de los efectos siempre me lanza el error no se han podido activar efectos de escritorio.
Pese a que mi red y laptop es relativamente potente, las conversaciones en skype no son muy buenas, yo uso skype siempre para estar en contacto con mi familia.
Agradesco de antemano su ayuda, tengo un gran recuerdo del argentina loco team por eso vengo aqui, donde siempre me siento como en casa.

Jpoeta;) 

P.d Qué programa me recomendarian para sincronisar mi ipod nano?

---

### Post by guillermolisi on 2009-06-14
> **jpoeta said:**
> Hace mucho tiempo deje Ubuntu en la version 6.10, hace poco me compre una Laptop tenía Windows Vista pero decidí volver a Ubuntu y en la nueva versión el Wifi corrió de forma automática y sin Problemas. Eso me animó a instalarme el 9.04 ayer.
Bueno les explico los problemas que estoy teniendo, el audio que normalmente es potente aqui tiene un volumen muy bajo en parlantes y microfono. 
Por el lado de el video no puedo disfrutar de los efectos siempre me lanza el error no se han podido activar efectos de escritorio.
Pese a que mi red y laptop es relativamente potente, las conversaciones en skype no son muy buenas, yo uso skype siempre para estar en contacto con mi familia.
Agradesco de antemano su ayuda, tengo un gran recuerdo del argentina loco team por eso vengo aqui, donde siempre me siento como en casa.

Jpoeta;) 

P.d Qué programa me recomendarian para sincronisar mi ipod nano?
Podiras correr en consola/terminal el comando lspci y mostrar su salida ?

Creo que esa maquina tiene video ATI pero no se que modelo es.
Tampoco recuerdo que audio tiene, asi que con la salida de ese comando podremos trabajar sobre una base mas firme.

---

### Post by jpoeta on 2009-06-14
jpoeta@jpoeta-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

Gracias de Antemano =):D

---

### Post by guillermolisi on 2009-06-16
Fijate en estos threads que hablan sobre los problemas de las nuevas placas de video Intel 965, como la que tenes en tu maquina:

[http://ubuntuforums.org/showthread.php?t=1136987&highlight=intel+965](http://ubuntuforums.org/showthread.php?t=1136987&highlight=intel+965)

[http://ubuntuforums.org/showthread.php?t=1135606&highlight=intel+965](http://ubuntuforums.org/showthread.php?t=1135606&highlight=intel+965)

[http://ubuntuforums.org/showthread.php?t=1154070&highlight=intel+965](http://ubuntuforums.org/showthread.php?t=1154070&highlight=intel+965)

[http://ubuntuforums.org/showthread.php?t=1150520&highlight=intel+965](http://ubuntuforums.org/showthread.php?t=1150520&highlight=intel+965)

[http://ubuntuforums.org/showthread.php?t=1130135&highlight=intel+965](http://ubuntuforums.org/showthread.php?t=1130135&highlight=intel+965)

---

