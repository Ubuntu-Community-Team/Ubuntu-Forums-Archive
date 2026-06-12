---
title: "Ubuntu 10.04 no detecta ENLTV-FM"
date: 2010-07-25
forum: Hardware
---

### Post by eliux on 2010-07-25
Hola, estoy teniendo un problema con mi sintonizadora de tv ENLTV-FM el tema es asi, vi varios tutoriales y todos eran iguales asique decidi hacer lo mismo.
 Hice los pasos de los tutos instalar, mercurial, el dv4, tvtime, etc etc.
 Cuando arranco tvtime, me detecta la placa sintonizadora, y hsata funciona el control remoto, empiezo a probar la configuracion regiomal para poder sintonizar, entre varias pruebas el programa se reinicia y cuando intenta abrirse de nuevo me da un error, dice que no detecta el dispositivo /dev/video0  exactamente dice esto (desde terminal):

Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /root/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No existe el fichero ó directorio
Fallo de segmentación

Entro en el directorio /dev y fefinitivamente no hay video0 ni video1 si hago un ls en el directorio /dev  me da esto:
adsp
audio
block
bsg
bus
cdrom
cdrw
char
console
core
cpu_dma_latency
disk
dsp
dvd
dvdrw
ecryptfs
fb0
fd
full
fuse
hidraw0
hidraw1
hidraw2
hpet
input
kmsg
log
loop0
loop1
loop2
loop3
loop4
loop5
loop6
loop7
lp0
mapper
mcelog
mem
mixer
net
network_latency
network_throughput
null
nvidia0
nvidiactl
oldmem
parport0
pktcdvd
port
ppp
psaux
ptmx
pts
ram0
ram1
ram10
ram11
ram12
ram13
ram14
ram15
ram2
ram3
ram4
ram5
ram6
ram7
ram8
ram9
random
rfkill
root
rtc
rtc0
scd0
sda
sda1
sda2
sda4
sda5
sda6
sequencer
sequencer2
sg0
sg1
shm
snapshot
snd
sndstat
sr0
stderr
stdin
stdout
tty
tty0
tty1
tty10
tty11
tty12
tty13
tty14
tty15
tty16
tty17
tty18
tty19
tty2
tty20
tty21
tty22
tty23
tty24
tty25
tty26
tty27
tty28
tty29
tty3
tty30
tty31
tty32
tty33
tty34
tty35
tty36
tty37
tty38
tty39
tty4
tty40
tty41
tty42
tty43
tty44
tty45
tty46
tty47
tty48
tty49
tty5
tty50
tty51
tty52
tty53
tty54
tty55
tty56
tty57
tty58
tty59
tty6
tty60
tty61
tty62
tty63
tty7
tty8
tty9
ttyS0
ttyS1
ttyS2
ttyS3
urandom
usbmon0
usbmon1
usbmon2
vboxdrv
vboxnetctl
vcs
vcs1
vcs2
vcs3
vcs4
vcs5
vcs6
vcs7
vcsa
vcsa1
vcsa2
vcsa3
vcsa4
vcsa5
vcsa6
vcsa7
vga_arbiter
zero

Luego pruebo con un lspci y me da esto

02:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

 Y por ultimo dmesg | grep saa713 tira esto:

[   17.322098] saa7134: Unknown symbol ir_codes_avermedia_m135a_table
[   17.322327] saa7134: Unknown symbol ir_codes_pinnacle_color_table
[   17.322728] saa7134: Unknown symbol ir_codes_purpletv_table
[   17.322830] saa7134: Unknown symbol ir_codes_pixelview_table
[   17.323023] saa7134: Unknown symbol ir_codes_flyvideo_table
[   17.323099] saa7134: Unknown symbol ir_codes_asus_pc39_table
[   17.323748] saa7134: Unknown symbol ir_codes_pinnacle_grey_table
[   17.323824] saa7134: Unknown symbol ir_codes_hauppauge_new_table
[   17.323901] saa7134: Unknown symbol ir_codes_behold_table
[   17.324038] saa7134: Unknown symbol ir_codes_manli_table
[   17.324227] saa7134: Unknown symbol ir_codes_encore_enltv_table
[   17.324371] saa7134: Unknown symbol ir_codes_pctv_sedna_table
[   17.324493] saa7134: Unknown symbol ir_rc5_timer_keyup
[   17.324869] saa7134: Unknown symbol ir_extract_bits
[   17.324945] saa7134: Unknown symbol ir_rc5_timer_end
[   17.325077] saa7134: Unknown symbol ir_codes_eztv_table
[   17.325371] saa7134: Unknown symbol ir_codes_genius_tvgo_a11mce_table
[   17.325447] saa7134: Unknown symbol ir_codes_flydvb_table
[   17.325529] saa7134: Unknown symbol ir_codes_videomate_tv_pvr_table
[   17.325692] saa7134: Unknown symbol ir_input_init
[   17.325773] saa7134: Unknown symbol ir_codes_behold_columbus_table
[   17.325914] saa7134: Unknown symbol ir_codes_gotview7135_table
[   17.326200] saa7134: Unknown symbol ir_codes_encore_enltv_fm53_table
[   17.326590] saa7134: Unknown symbol ir_input_nokey
[   17.326961] saa7134: Unknown symbol ir_codes_avermedia_table
[   17.327125] saa7134: Unknown symbol ir_codes_cinergy_table
[   17.327296] saa7134: Unknown symbol ir_codes_msi_tvanywhere_plus_table
[   17.327438] saa7134: Unknown symbol ir_codes_kworld_plus_tv_analog_table
[   17.329221] saa7134: Unknown symbol ir_codes_videomate_s350_table
[   17.329394] saa7134: Unknown symbol ir_codes_proteus_2309_table
[   17.329477] saa7134: Unknown symbol ir_codes_real_audio_220_32_keys_table
[   17.329554] saa7134: Unknown symbol ir_input_keydown
[   17.329777] saa7134: Unknown symbol ir_codes_avermedia_a16d_table
[   17.333808] saa7134: Unknown symbol ir_codes_avermedia_m135a_table
[   17.334038] saa7134: Unknown symbol ir_codes_pinnacle_color_table
[   17.334438] saa7134: Unknown symbol ir_codes_purpletv_table
[   17.334540] saa7134: Unknown symbol ir_codes_pixelview_table
[   17.334733] saa7134: Unknown symbol ir_codes_flyvideo_table
[   17.334809] saa7134: Unknown symbol ir_codes_asus_pc39_table
[   17.335459] saa7134: Unknown symbol ir_codes_pinnacle_grey_table
[   17.335536] saa7134: Unknown symbol ir_codes_hauppauge_new_table
[   17.335612] saa7134: Unknown symbol ir_codes_behold_table
[   17.335720] saa7134: Unknown symbol ir_codes_manli_table
[   17.335908] saa7134: Unknown symbol ir_codes_encore_enltv_table
[   17.336081] saa7134: Unknown symbol ir_codes_pctv_sedna_table
[   17.336203] saa7134: Unknown symbol ir_rc5_timer_keyup
[   17.336580] saa7134: Unknown symbol ir_extract_bits
[   17.336656] saa7134: Unknown symbol ir_rc5_timer_end
[   17.336788] saa7134: Unknown symbol ir_codes_eztv_table
[   17.337082] saa7134: Unknown symbol ir_codes_genius_tvgo_a11mce_table
[   17.337159] saa7134: Unknown symbol ir_codes_flydvb_table
[   17.337240] saa7134: Unknown symbol ir_codes_videomate_tv_pvr_table
[   17.337404] saa7134: Unknown symbol ir_input_init
[   17.337485] saa7134: Unknown symbol ir_codes_behold_columbus_table
[   17.337626] saa7134: Unknown symbol ir_codes_gotview7135_table
[   17.337912] saa7134: Unknown symbol ir_codes_encore_enltv_fm53_table
[   17.338302] saa7134: Unknown symbol ir_input_nokey
[   17.338672] saa7134: Unknown symbol ir_codes_avermedia_table
[   17.338836] saa7134: Unknown symbol ir_codes_cinergy_table
[   17.339008] saa7134: Unknown symbol ir_codes_msi_tvanywhere_plus_table
[   17.339150] saa7134: Unknown symbol ir_codes_kworld_plus_tv_analog_table
[   17.342996] saa7134: Unknown symbol ir_codes_videomate_s350_table
[   17.343168] saa7134: Unknown symbol ir_codes_proteus_2309_table
[   17.343252] saa7134: Unknown symbol ir_codes_real_audio_220_32_keys_table
[   17.343329] saa7134: Unknown symbol ir_input_keydown
[   17.343552] saa7134: Unknown symbol ir_codes_avermedia_a16d_table
[  362.324340] saa7134: Unknown symbol ir_codes_avermedia_m135a_table
[  362.324578] saa7134: Unknown symbol ir_codes_pinnacle_color_table
[  362.324993] saa7134: Unknown symbol ir_codes_purpletv_table
[  362.325098] saa7134: Unknown symbol ir_codes_pixelview_table
[  362.325299] saa7134: Unknown symbol ir_codes_flyvideo_table
[  362.325379] saa7134: Unknown symbol ir_codes_asus_pc39_table
[  362.326051] saa7134: Unknown symbol ir_codes_pinnacle_grey_table
[  362.326131] saa7134: Unknown symbol ir_codes_hauppauge_new_table
[  362.326211] saa7134: Unknown symbol ir_codes_behold_table
[  362.326322] saa7134: Unknown symbol ir_codes_manli_table
[  362.326518] saa7134: Unknown symbol ir_codes_encore_enltv_table
[  362.326670] saa7134: Unknown symbol ir_codes_pctv_sedna_table
[  362.326795] saa7134: Unknown symbol ir_rc5_timer_keyup
[  362.327190] saa7134: Unknown symbol ir_extract_bits
[  362.327270] saa7134: Unknown symbol ir_rc5_timer_end
[  362.327405] saa7134: Unknown symbol ir_codes_eztv_table
[  362.327713] saa7134: Unknown symbol ir_codes_genius_tvgo_a11mce_table
[  362.327793] saa7134: Unknown symbol ir_codes_flydvb_table
[  362.327878] saa7134: Unknown symbol ir_codes_videomate_tv_pvr_table
[  362.328076] saa7134: Unknown symbol ir_input_init
[  362.328160] saa7134: Unknown symbol ir_codes_behold_columbus_table
[  362.328308] saa7134: Unknown symbol ir_codes_gotview7135_table
[  362.328607] saa7134: Unknown symbol ir_codes_encore_enltv_fm53_table
[  362.329014] saa7134: Unknown symbol ir_input_nokey
[  362.329395] saa7134: Unknown symbol ir_codes_avermedia_table
[  362.329566] saa7134: Unknown symbol ir_codes_cinergy_table
[  362.329745] saa7134: Unknown symbol ir_codes_msi_tvanywhere_plus_table
[  362.329894] saa7134: Unknown symbol ir_codes_kworld_plus_tv_analog_table
[  362.330131] saa7134: Unknown symbol ir_codes_videomate_s350_table
[  362.330308] saa7134: Unknown symbol ir_codes_proteus_2309_table
[  362.330395] saa7134: Unknown symbol ir_codes_real_audio_220_32_keys_table
[  362.330475] saa7134: Unknown symbol ir_input_keydown
[  362.330704] saa7134: Unknown symbol ir_codes_avermedia_a16d_table

 Alguien tiene idea de lo que pasa y puede ayudarme con esto??? Muchas Gracias...

---

### Post by guillermolisi on 2010-07-25
Con la maquina recien iniciada y en una consola/terminal, ingresa y mostra la salida de los siguientes comandos: ```
sudo lshw
``````
lsmod
```Con el primero deberiamos saber si tiene algun driver/modulo asociado o esta como unclaimed. Con el segundo sabremos que modulos estan cargados en memoria y que asociaciones tienen.

---

### Post by eliux on 2010-07-25
Guille hice lo que me dijiste y me tiro esto SUDO LSHW (NOTA SOLO DEJE LOS QUE DICEN UNCLAIMED):

     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
        *-multimedia UNCLAIMED
             description: Multimedia controller
             product: SAA7130 Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: 9
             bus info: pci@0000:02:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32 maxlatency=32 mingnt=84
             resources: memory:fdefe000-fdefe3ff

Y EL OTRO COMANDO lsmod DIO ESTO:

Module                  Size  Used by
pppoe                   8943  2 
pppox                   2074  1 pppoe
snd_hda_codec_analog    58598  1 
ppdev                   5259  0 
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
v4l2_common            15431  0 
hwmon_vid               2298  0 
parport_pc             25962  1 
snd_pcm                70662  2 snd_hda_intel,snd_hda_codec
snd_timer              19098  1 snd_pcm
videodev               34361  1 v4l2_common
v4l1_compat            13251  1 videodev
psmouse                63245  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
asus_atk0110            9017  0 
nvidia               9961216  38 
videobuf_dma_sg        10782  0 
videobuf_core          16356  1 videobuf_dma_sg
tveeprom               11102  0 
snd                    54148  10 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
k8temp                  3024  0 
i2c_nforce2             5199  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
forcedeth              49556  0 
sata_nv                19440  2 
pata_amd                8766  0 


espero que puedas ayudarme, te doy muchas gracias igualmente!

---

### Post by guillermolisi on 2010-07-25
Por lo pronto, segun lo que expusiste no tiene un driver asignado:
> *-multimedia UNCLAIMED
             description: Multimedia controller
             product: SAA7130 Video Broadcast Decoder
             vendor: Philips Semiconductors
             physical id: 9
             bus info: pci@0000:02:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32 maxlatency=32 mingnt=84
             resources: memory:fdefe000-fdefe3ff

Luego, habria que "descubrir" que modulo le corresponde a la placa en funcion del chip que utiliza (Philips SAA7130) .

De los modulos que se ven, los que me parecen relacionados son:
> v4l2_common            15431  0 
videodev               34361  1 v4l2_common
v4l1_compat            13251  1 videodev
pero no me queda claro si falta algo mas ya que (de nuevo) no tengo claro que procesador utiliza la placa. Videodev esta vinculandose con v4l2_common y v4l1_compat, a su vez, esta vinculado con videodev, lo cual me genera dudas respecto de usar v4l1 o v4l2 (me inclinaria a usar este ultimo).

Seria importante el aporte de quienes usan este tipo de hardware para aclarar la solucion.

---

### Post by eliux on 2010-07-25
Hola Guille, esuve buscando el driver del SAA7130 que es el procesador (creo) de la placa encore es un procesador o semiconductor de phillips.

 Encontre esto en esta pagina:
[http://dl.bytesex.org/releases/video4linux/saa7134-0.2.12.tar.gz](http://dl.bytesex.org/releases/video4linux/saa7134-0.2.12.tar.gz)
es de confianza este driver?

 Que me recomendas q haga para seguir probando, si surge algo lo posteo. Muchas Gracias!!! Esto me sirve porque aprendo cosas nuevas!

---

### Post by euzkoarima on 2010-07-30
Par de links donde dicen tener el mismo problema (o muy similar) y haberlo solucionado.

[http://www.ubuntu-pe.org/node/1543](http://www.ubuntu-pe.org/node/1543)
[http://www.ubuntu-es.org/node/134669](http://www.ubuntu-es.org/node/134669)

Saludos,
Eduardo

---

