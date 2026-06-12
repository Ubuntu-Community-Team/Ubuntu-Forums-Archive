---
title: "Audio ¡ayuda por favor! ¿OSS, ALSA?"
date: 2009-08-05
forum: Hardware
---

### Post by christian_lms on 2009-08-05
Yo estoy hace más de dos semanas tratando de hacerla andar y no puedo.

Tengo una Sound Blaster AWE 64 (ISA/PnP). Estoy con **Ubuntu 9.04**, núcleo Linux** 2.6.28-14-generic**  y cargado el modulo de **ALSA** **snd-sbawe**, **creo** que me detecta la placa, pero ya subí los volúmenes en alsamixer, y sigo sin escuchar algunas cosas.
 
Detallo, en _Preferencias de sonido_ tengo estos mezcladores:
* CTL1745 (OSS Mixer)
* Sound Blaster 16 (Alsa mixer )
 
Y en las pruebas de sonido por ejemplo de "Eventos de sonido" el pipeline me funciona solo con OSS y **NO** con ALSA ni en autodetectar, así que selecciono en todos OSS (y funcionan), cuando abro Rhythmbox escucho bien los mp3. pero por ejemplos los eventos de botones o el sonido de bienvenida al sistema no los escucho :confused: (tengo activados esos sonidos).

Igual creo que algo está mal configurado, porque tendría que funcionar la prueba en autodetectar no?

[IMG]http://img268.imageshack.us/img268/9579/pantallazo1g.png[/IMG]

[IMG]http://img200.imageshack.us/img200/993/pantallazo2f.png[/IMG]

Les dejo algunos pantallazos de consola como para que tengan una idea: 
  
Con isapnp detecté mi placa, en el archivo info elegí las opciones que iban.
```

root@christian-desktop:/home/christian# pnpdump>info
root@christian-desktop:/home/christian# gedit info
root@christian-desktop:/home/christian# isapnp info
Board 1 has Identity 8e 18 4b 79 4e c5 00 8c 0e:  CTL00c5 Serial No 407599438 [checksum 8e]
CTL00c5/407599438[0]{Audio               }: Ports 0x220 0x330 0x388; IRQ5 DMA1 DMA5 --- Enabled OK
CTL00c5/407599438[1]{Game                }: Port 0x200; --- Enabled OK
CTL00c5/407599438[2]{WaveTable           }: Port 0x620; --- Enabled OK

```Esto es después de cargar el modulo snd-sbawe
```

root@christian-desktop:/home/christian# cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.18rc3 emulation code)
Kernel: Linux christian-desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Sound Blaster 16 at 0x220, irq 5, dma 1&5

Audio devices:
0: DSP v4.16 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: Sound Blaster 16 MIDI

Timers:
31: system timer

Mixers:
0: CTL1745

```Algo que no se si estará bién es que después de esto me aparece esto en lspnp -v...
```

root@christian-desktop:/home/christian# lspnp
00:00 PNP0c01 System board
00:01 PNP0a03 PCI bus
00:02 PNP0c02 Motherboard resources
00:03 PNP0200 AT DMA controller
00:04 PNP0b00 AT real-time clock
00:05 PNP0800 AT speaker
00:06 PNP0c04 Math coprocessor
00:07 PNP0700 PC standard floppy disk controller
00:08 PNP0501 16550A-compatible serial port
00:09 PNP0501 16550A-compatible serial port
00:0a PNP0400 Standard LPT printer port
00:0b PNP0303 IBM enhanced keyboard (101/102-key, PS/2 mouse support)
01:01.00 CTL0045 (unknown)
01:01.01 CTL7002 (unknown)
01:01.02 CTL0022 (unknown)

root@christian-desktop:/home/christian# lspnp -v
... (Borro los que no tienen nada que ver..)
01:01.00 CTL0045 (unknown)
    state = active
    irq 5
    dma 1
    dma 5
    io 0x220-0x22f
    io 0x330-0x331
    io 0x388-0x38b

01:01.01 CTL7002 (unknown)
    state = disabled

01:01.02 CTL0022 (unknown)
    state = active
    io 0x620-0x623
    io 0xa20-0xa23
    io 0xe20-0xe23

```

¡¡¡AYUDA!!!

---

### Post by guillermolisi on 2009-08-05
Solo por si se te paso por alto, es recomendable entrar al BIOS y reservar la interrupcion 5 para ISA, asi la placa de audio que tenes no necesita compartir ese nivel de interrupcion con dispositivos PCI.

---

### Post by christian_lms on 2009-08-06
> **guillermolisi said:**
> Solo por si se te paso por alto, es recomendable entrar al BIOS y reservar la interrupcion 5 para ISA, asi la placa de audio que tenes no necesita compartir ese nivel de interrupcion con dispositivos PCI.
  
Gracias pero si ya tengo bien configurada la BIOS.

Algo realmente raro es que cuando entra a la pantalla de entrada del sistema, sin haber ingresado a mi usuario todavía, escucho el sonido de que debo ingresar el usuario y contraseña. Pero una vez que ingreso ya no, ¿no serán problemas con el usuario?, yo ya le di los permisos para "usar dispositivos de sonido".

Dejo otra captura, no tendría que tener más opciones acá, que tienen ustedes?
[IMG]http://img208.imageshack.us/img208/250/pantallazo3i.png[/IMG]

---

### Post by christian_lms on 2009-08-07
Descubrí algo que creo que es clave, cuando voy a las preferencias del sonido directamente desde SISTEMA --> PREFERENCIAS --> SONIDO las pruebas de sonido en ALSA NO me funcionan, pero acá está lo interesante...

cuando ejecuto en la consola **como root**:

$ gnome-sound-properties

:o ... me funciona perfecto, esto sin dudas es un problema de permisos. 

Ahora ¡¿qué será no tengo idea!? :confused:

Yo me acuerdo que cree un grupo AUDIO y agregue a mi usuario ahí, lo que hizo que mi usuario tenga marcada la opcion "usar dispositivos de sonido". Así que ya no se qué puede ser...

---

### Post by guillermolisi on 2009-08-07
En relacion con eso de agregar la cuenta de user al grupo Audio, me fije en una de mis maquinas y en ese grupo no tengo ninguna cuenta asociada. El grupo existe desde la instalacion, no lo cree intencionalmente.

El audio funciona perfecto (no es ISA) y estoy usando KDE 4.3 (no es Gnome).

Que pasa si quitas del grupo a tu user, cerras la sesion y volves a iniciarla ?

---

