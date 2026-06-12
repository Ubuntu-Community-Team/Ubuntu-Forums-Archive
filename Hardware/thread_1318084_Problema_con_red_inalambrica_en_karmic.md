---
title: "Problema con red inalambrica en karmic"
date: 2009-11-07
forum: Hardware
---

### Post by sartrejp on 2009-11-07
Me había pasado al actualizar de jaunty a karmic, como no tenía tiempo para intentar solucionarlo, decidí reinstalar jaunty.
Ahora acabo de completar una instalación limpia de Karmic, y el problema persiste.
Lo primero que pasa es que la red inalambrica aparece no activada, la marco y me dice que el dispositivo no está listo.

si pongo iwconfig para ver las extensiones me sale
> lo no wireless extension
eth0 no wireless extension
vmaster no wireless extension
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Iwlist scan me da> 
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

En el irc me recomendaron que baje y levante el modulo pero no lo encontre, el resultado de lsmod es
> Module                  Size  Used by
isofs                  31620  1 
udf                    80900  0 
nls_iso8859_1           3740  2 
nls_cp437               5372  2 
vfat                   10716  2 
fat                    51452  1 vfat
usb_storage            52544  2 
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_codec_realtek   203328  1 
rt73usb                26336  0 
crc_itu_t               1852  2 udf,rt73usb
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
rt2x00usb              11548  1 rt73usb
rt2x00lib              29756  2 rt73usb,rt2x00usb
joydev                 10272  0 
snd_hwdep               7200  1 snd_hda_codec
iptable_filter          3100  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
ip_tables              11692  1 iptable_filter
pcmcia                 36808  0 
input_polldev           3716  1 rt2x00lib
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
sdhci_pci               7100  0 
mac80211              181236  2 rt2x00usb,rt2x00lib
sdhci                  17472  1 sdhci_pci
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
uvcvideo               59080  0 
yenta_socket           24200  1 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               93052  2 rt2x00lib,mac80211
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               36736  1 uvcvideo
rsrc_nonstatic         11644  1 yenta_socket
led_class               4096  2 rt2x00lib,sdhci
psmouse                56180  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
v4l1_compat            14496  2 uvcvideo,videodev
serio_raw               5280  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  4 
drm                   159584  4 i915
i2c_algo_bit            5760  1 i915
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
intel_agp              27484  2 i915
video                  19380  1 i915
output                  2780  1 video
agpgart                34988  2 drm,intel_agp

Si a alguien le pasó, o sabe como solucionarlo, le agradezco

---

### Post by SLA_leandrin on 2009-11-07
Con que Kernel estás booteando?

Yo tengo instalados el 2.6.31-14 y el 2.6.31-11 

Con el -14 tengo problemas con el wi-fi por lo que tengo que usar por ahora el 2.6.31-11

---

### Post by sartrejp on 2009-11-07
con el 2.6.31-14 que es el único que me instaló Karmic

---

### Post by luks911 on 2009-11-07
Me parece que el módulo es 
```
rt73usb
```
De todos modos, por qué no pegás el resultado de lsusb o lspci para ver qué placa es.

---

### Post by sartrejp on 2009-11-09
No hay caso, no logré hacerlo funcionar, reinstalé Jaunty porque necesitaba salir con la notebook, además así, al actualizar, tengo el kernel anterior para pdoer conectarme (que en una instalación limpia no). Cuando vuelva de viaje, sigo posteando los avances (o retrocesos al respecto)

---

