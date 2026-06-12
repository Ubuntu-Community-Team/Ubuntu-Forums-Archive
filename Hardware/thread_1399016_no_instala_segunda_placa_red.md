---
title: "no instala segunda placa red"
date: 2010-02-05
forum: Hardware
---

### Post by santiago79 on 2010-02-05
hola gente tengo un problema si otro  jeje.
resulta que estoy instalando ubuntu server para usarlo como gateway y en el momento de instalar me detecta las 2 placas que tengo puestas son 2 pci una es realtek y la otra nose pero en cuention cuando termina la instalación la realtek no esta cuando pongo ifconfig no aparece mi segunda placa de red (realtek)

---

### Post by guillermolisi on 2010-02-05
> **santiago79 said:**
> hola gente tengo un problema si otro  jeje.
resulta que estoy instalando ubuntu server para usarlo como gateway y en el momento de instalar me detecta las 2 placas que tengo puestas son 2 pci una es realtek y la otra nose pero en cuention cuando termina la instalación la realtek no esta cuando pongo ifconfig no aparece mi segunda placa de red (realtek)
Copia y pega para que veamos la salida del comando en consola/terminal "lspci" (sin las comillas). Eso nos dira que placa/chip es la de la cuestion.

---

### Post by santiago79 on 2010-02-05
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
00:0e.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev d2)

---

### Post by JuanitoMint on 2010-02-05
por las dudas ejecutá como root:
#depmod -a
#modprobe -a

y dps pegate el resultado de: #lsmod

para ver qué modulos te cargó.

---

### Post by santiago79 on 2010-02-05
Module                  Size  Used by
aoe                    25504  0
ipt_MASQUERADE          2204  1
iptable_nat             5500  1
nf_nat                 17808  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13352  4 iptable_nat,nf_nat
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
xt_state                1820  1
nf_conntrack           67608  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT              2812  2
xt_tcpudp               2780  4
bridge                 47952  0
stp                     2272  1 bridge
snd_ens1371            22112  0
gameport               11368  1 snd_ens1371
iptable_filter          3100  1
snd_rawmidi            22208  1 snd_ens1371
ip_tables              11692  2 iptable_nat,iptable_filter
snd_seq_device          6920  1 snd_rawmidi
x_tables               16544  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
snd_ac97_codec        101216  1 snd_ens1371
ac97_bus                1532  1 snd_ac97_codec
snd_pcm                75488  2 snd_ens1371,snd_ac97_codec
snd_timer              22276  1 snd_pcm
lp                      8964  0
snd                    59204  6 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer
intel_agp              27748  1
parport                35340  1 lp
psmouse                56180  0
soundcore               7264  1 snd
agpgart                35020  1 intel_agp
i2c_piix4              10124  0
shpchp                 32336  0
serio_raw               5280  0
snd_page_alloc          9252  1 snd_pcm
tulip                  48768  0
ne2k_pci                8544  0
8390                    9756  1 ne2k_pci
floppy                 54980  0

---

### Post by guillermolisi on 2010-02-05
Segun lei en [http://hardware4linux.info/component/17100/](http://hardware4linux.info/component/17100/) el modulo que soporta esa placa esta cargado y es este > tulip                  48768  0

---

### Post by santiago79 on 2010-02-05
si pero cuando voy a /etc/network/interfaces me parece solo una placa y si pongo ifconfig también
osea tengo estas 2
00:0e.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
 y solo me carga la admtek nc100
la realtek no aparece

---

### Post by guillermolisi on 2010-02-05
> **santiago79 said:**
> si pero cuando voy a /etc/network/interfaces me parece solo una placa y si pongo ifconfig también
osea tengo estas 2
00:0e.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
 y solo me carga la admtek nc100
la realtek no aparece
Disculpa, tenes razon y mi despiste fue porque es muy raro que una placa Realtek no funcione al toque. De ahi que conteste otra cosa.

El driver/modulo de la Realtek es: > ne2k_pci                8544  0asi que deberia funcionar.

Podrias mostrarnos la salida de: ```
lshw
``` donde se muestra la referencia a esa placa, como el ejemplo que te muestro a continuacion:
> *-network
                description: Ethernet interface
                product: RTL-8029(AS)
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 00
                serial: 00:60:52:05:a4:b4
                width: 32 bits
                clock: 33MHz
                capabilities: ethernet physical
                configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=10.21.4.180 latency=0 module=ne2k_pci multicast=yesFijate que en el ejemplo, la placa se muestra con una IP asignada lo cual es muy bueno.

---

### Post by santiago79 on 2010-02-11
bueno les comento que edite el fichero interfaces manualmente como si estaria la placa ahi, porque puse ifconfig -a y me detecta las 2 placas.
solo me falta probar si funciona como gateway ni bien pueda les comento lo que paso
muchas gracias por todo

---

### Post by alfplayer on 2010-02-11
> **santiago79 said:**
> bueno les comento que edite el fichero interfaces manualmente como si estaria la placa ahi, porque puse ifconfig -a y me detecta las 2 placas.
solo me falta probar si funciona como gateway ni bien pueda les comento lo que paso
muchas gracias por todo

No hay que olvidarse de ejecutar ifconfig con la opción -a para ver **todas** las interfaces de red!

---

