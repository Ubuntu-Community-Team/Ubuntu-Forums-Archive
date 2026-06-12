---
title: "consulta"
date: 2009-05-16
forum: Hardware
---

### Post by cartos on 2009-05-16
hola gente como va???

una consulta aguien sabe de los drivers para el toochpad de una cq-50??


saludos

---

### Post by Hei Ku on 2009-05-16
Postea el resultado de lsusb y lspci, para tener datos concretos.

---

### Post by cartos on 2009-05-16
lsusb

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device

lspci

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200M G (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


es esto no?

---

### Post by Hei Ku on 2009-05-16
si, y el touchpad no se ve por ningun lado. Cual es la marca y modelo completo de la notebook?

---

### Post by cartos on 2009-05-16
es una cq50-110us

---

### Post by Hei Ku on 2009-05-16
Ok. Es una Compaq Presario cq50-110us.

Que version de ubuntu usas? 
Que sucede con el touchpad? No te lo reconoce o anda mal?

---

### Post by cartos on 2009-05-17
sisi es una compaq presario 

tengo el ubuntu 9.04 

lo que sucede es que la laptop tiene un boton para desactivar el touchpad donde lo acciono y no hace nada solo cambia la luz y el touchpad sigue funcionando

desde que tengo ubuntu hace ya 6 meses 8.04, 8.10 siempre lo tube asi, siempre estuve buscando si a alguien le susedio pero no veo nada al respecto

es que me molesta para tipear y sin darme cuenta aveses rozo con el pulgar el touchpad y se me va el cursor es molesto ya que habia tipeado una banda y al mirar me doy cuenta que no tipie nada

gracias

saludos

---

### Post by luks911 on 2009-05-17
Veo un par de comentarios en el foro con el mismo problema. Un alternativa es esto[0], que te permite desactivar automáticamente y por un período que vos seteas el touchpad mientras escribís. El botón va a seguir sin funcionar pero ya no vas a tener el problema de antes.
Lo que hay que hacer es modificar el xorg.conf y ejecutar una aplicación al inicio que va a encargarse desactivar el touchpad cuando tipeas.

[0] [http://arkanus.wordpress.com/2008/07/15/desactivar-el-touchpad-cuando-escribes-o-conectas-un-mouse-en-linux/](http://arkanus.wordpress.com/2008/07/15/desactivar-el-touchpad-cuando-escribes-o-conectas-un-mouse-en-linux/)

---

### Post by Hei Ku on 2009-05-17
eventualmente, se puede ver si te detecta esa tecla y configurarla para que ejecute la desactivacion del touchpad.

Tambien podrias ponerte en contacto con el fabricante y reclamar el driver. ;)

---

### Post by hictio on 2009-05-17
> **cartos said:**
> sisi es una compaq presario 

tengo el ubuntu 9.04 

lo que sucede es que la laptop tiene un boton para desactivar el touchpad donde lo acciono y no hace nada solo cambia la luz y el touchpad sigue funcionando

desde que tengo ubuntu hace ya 6 meses 8.04, 8.10 siempre lo tube asi, siempre estuve buscando si a alguien le susedio pero no veo nada al respecto

es que me molesta para tipear y sin darme cuenta aveses rozo con el pulgar el touchpad y se me va el cursor es molesto ya que habia tipeado una banda y al mirar me doy cuenta que no tipie nada

gracias

saludos


Mmhhh, sólo por descartar, probaste desactivando el touchpad en:

System > Preferences > Mouse > Touchpad tab

Y deschequeá la opción "Enable Touchpad".

En mi Compaq F700 el botón (y el LED que indica el status) funciona perfecto para habilitar/ deshabiltar el touchpad desde Hardy hasta Jaunty.

---

