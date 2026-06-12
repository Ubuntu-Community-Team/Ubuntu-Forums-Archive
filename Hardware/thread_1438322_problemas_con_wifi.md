---
title: "problemas con wifi"
date: 2010-03-24
forum: Hardware
---

### Post by zionwing on 2010-03-24
tengo problemas con la wifi 
no se porque pero la version 9.10 me da problemas con la wifi del dpto 
pero coloque el livecd de la version 9.04 y funciona la wifi muy bien.
 
 
a todo esto el drama que me da la wifi en la version 9.10 es que me muestra q tengo señal pero se demora en conectar 
y una vez conectado, el firefox hace como que estuviera trantato de cargar una pagina, pero al final pasan los minutos y no carga la pagina. 
 tambien probé con chrome y me pasa lo mismo.

espero puedan ayudarme.




aki le dejo unas de los comandos ke dicen en otro topic ke posteara.
(lspci  , lsmod   , iwconfig)

#lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


#lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
kvm_amd                41556  0 
kvm                   190648  1 kvm_amd
joydev                 13088  0 
snd_hda_codec_realtek   277860  1 
pcmcia                 40116  0 
arc4                    2144  2 
ecb                     3296  2 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
acer_wmi               18504  0 
psmouse                57124  0 
serio_raw               6596  0 
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
yenta_socket           27628  1 
rsrc_nonstatic         11840  1 yenta_socket
pcmcia_core            42692  3 pcmcia,yenta_socket,rsrc_nonstatic
k8temp                  5504  0 
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
i2c_piix4              11728  0 
ath5k                 137352  0 
mac80211              210040  1 ath5k
led_class               5256  3 acer_wmi,sdhci,ath5k
ath                    10304  1 ath5k
cfg80211              109144  3 ath5k,mac80211,ath
shpchp                 37756  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
8139too                27360  0 
8139cp                 23200  0 
mii                     6368  2 8139too,8139cp
radeon                684576  2 
ttm                    43056  1 radeon
drm                   194400  4 radeon,ttm
i2c_algo_bit            7076  1 radeon

#iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"CRISTIAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:12:B1:5F:10   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by CdK1 on 2010-03-25
Comenta esta línea "blacklist ath5k" en /etc/modprobe.d/madwifi.conf y en
/etc/modprobe.d/blacklist-ath_pci.conf 

Avisa como te va...

---

### Post by Carlos C on 2010-03-25
Debiera funcionar con el módulo ath5k, que, por lo que muestra lsmod, ya está instalado. Prueba ir al panel superior, en Sistema-->Administración-->Controladores de Hardware y ve si no hay algún driver sugerido que pueda funcionar mejor.

Saludos.

---

### Post by asterix77 on 2010-03-26
Según iwconfig, está asociado al punto de acceso, por lo que debiera tener acceso a internet, salvo que haya algún tipo de filtro en el punto de acceso que lo esté impidiendo.

Pregunta: ¿has manejado algún cortafuegos en tu sistema?

Debieras digitar lo siguiente para ver si puedes escanear puntos de acceso con tu tarjeta inalámbrica, en la terminal

#sudo iwlist wlan0 scanning


Saludos

---

