---
title: "Problemas con Xorg en ubuntu 10.04"
date: 2010-07-09
forum: Hardware
---

### Post by ArgentinoGuy on 2010-07-09
Hola, creo este hilo porque no se me ocurre como googlear el error que tengo.
Antes que nada comento que pase de 8.10 a 9.04 a 9.10 y finalmente 10.04 (soy muy vago para quemar un cd con 10.04).
El problema que tengo es que despues de hacer login gnome intenta arrancar y se sale de vuelta a la pantalla de login pidiendomelo nuevamente interminablemente. Solo puedo acceder a traves del modo a prueba de fallos (desde donde escribo esto). No se me ocurre que &#7765;uede ser el error que claramente en el modo a prueba de fallos no ocurre.
Les pego los tails de unos cuantos logs.

root@Penny:/var/log# tail Xorg.0.log
(II) intel(0): Modeline "1440x900"x0.0   97.78  1440 1488 1520 1760  900 903 909 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1440x900"x0.0   81.49  1440 1488 1520 1760  900 903 909 926 -hsync -vsync (46.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16435
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/event8)
(II) No input driver/identifier specified (ignoring)

root@Penny:/var/log# tail Xorg.failsafe.log
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

Claramente hay diferencias entre lo ultimo que cargaron

root@Penny:/var/log# tail -30 messages
Jul  9 17:22:13 Penny kernel: [   34.587145] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Jul  9 17:22:13 Penny kernel: [   34.587403] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jul  9 17:22:13 Penny kernel: [   34.587451] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jul  9 17:22:13 Penny kernel: [   34.587455] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
Jul  9 17:22:13 Penny kernel: [   34.591216] vga16fb: mapped to 0xc00a0000
Jul  9 17:22:13 Penny kernel: [   34.591220] vga16fb: not registering due to another framebuffer present
Jul  9 17:22:13 Penny kernel: [   34.667154] Registered led device: iwl-phy0::radio
Jul  9 17:22:13 Penny kernel: [   34.667595] Registered led device: iwl-phy0::assoc
Jul  9 17:22:13 Penny kernel: [   34.667844] Registered led device: iwl-phy0::RX
Jul  9 17:22:13 Penny kernel: [   34.668094] Registered led device: iwl-phy0::TX
Jul  9 17:22:13 Penny kernel: [   34.707740] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  9 17:22:13 Penny kernel: [   34.757194] Console: switching to colour frame buffer device 180x56
Jul  9 17:22:14 Penny kernel: [   35.039460] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
Jul  9 17:22:17 Penny kernel: [   38.131380] type=1505 audit(1278706937.156:9):  operation="profile_load" pid=826 name="/usr/bin/evince"
Jul  9 17:22:17 Penny kernel: [   38.132597] type=1505 audit(1278706937.160:10):  operation="profile_load" pid=826 name="/usr/bin/evince-previewer"
Jul  9 17:22:17 Penny kernel: [   38.133328] type=1505 audit(1278706937.160:11):  operation="profile_load" pid=826 name="/usr/bin/evince-thumbnailer"
Jul  9 17:22:17 Penny kernel: [   38.470875] NET: Registered protocol family 15
Jul  9 17:22:17 Penny kernel: [   38.472855] alg: No test for cipher_null (cipher_null-generic)
Jul  9 17:22:17 Penny kernel: [   38.472890] alg: No test for ecb(cipher_null) (ecb-cipher_null)
Jul  9 17:22:17 Penny kernel: [   38.472920] alg: No test for digest_null (digest_null-generic)
Jul  9 17:22:17 Penny kernel: [   38.473226] alg: No test for compress_null (compress_null-generic)
Jul  9 17:22:17 Penny kernel: [   38.482394] padlock: VIA PadLock Hash Engine not detected.
Jul  9 17:22:17 Penny kernel: [   38.499288] padlock: VIA PadLock Hash Engine not detected.
Jul  9 17:22:17 Penny kernel: [   38.522457] padlock: VIA PadLock not detected.
Jul  9 17:22:19 Penny kernel: [   40.316275] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Jul  9 17:22:19 Penny kernel: [   40.550309] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
Jul  9 17:22:48 Penny kernel: [   69.533047] CE: hpet increasing min_delta_ns to 15000 nsec
Jul  9 17:23:59 Penny kernel: [  140.200063] CE: hpet increasing min_delta_ns to 22500 nsec
Jul  9 17:35:00 Penny kernel: [  801.431922] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  9 17:35:14 Penny pulseaudio[1619]: ratelimit.c: 3 events suppressed

Si a  alguien se le prende la lamparita estaria muy agradecido.

Saludos!

---

### Post by guillermolisi on 2010-07-09
Contanos que placa de video estas usando ya que solo puedo inferir que es una Intel. Si no sabes marca y modelo, mostranos la salida del comando ```
lshw
```.

Si usas "tail" para mostrar los logs, solo podremos ver las ultimas 10 lineas de cada uno y no todo el contenido.

---

### Post by ArgentinoGuy on 2010-07-09
Si, use tail asumiendo que el error se reportaria al final.

La placa es la intel 965 muy generica y muy usada no creo que sea problema de hardware.

*-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f8200000-f82fffff

subi el log completo del xorg

Saludos.

---

### Post by guillermolisi on 2010-07-09
Vi varios errores, indicados con EE en el log que pasaste y me llama la atencion que la placa sea reportada como Unclaimed en la salida del lshw.

Por lo que indica el log adjunto, la maquina tendria 2Gb RAM de los cuales se toman 256Mb para video. Esto es correcto ?

Si es asi, no deberias tener inconvenientes por el lado de la memoria asignada.
Tambien hay algun problemita con ACPI en la motherboard pero no me queda claro si es vnculante con el problema que tenes.

Si probas con un LiveCD, que pasa ? Como funciona ?

---

### Post by ArgentinoGuy on 2010-07-09
No tengo un cd con el 10.04 tendria que quemar uno, pero como expuse antes, esta maquina tiene ubuntu hace mucho y es la primera vez que tengo ese problema, tendria que ver de remover los drivers para la placa e instalarlos de nuevo con apt a ver si de esa forma mejora algo o por lo menos descartar problemas.

---

### Post by ArgentinoGuy on 2010-07-09
bueno, saque un driver xserver-xorg-video-intel-i740 que estaba instalado y seguia teniendo el mismo problema y tmb saque el driver xserver-xorg-video-intel que es para todas las placas y el problema se soluciono. Ahora voy a reinstalar el driver y ver si es eso o si reinstalando tmb sigue andando bien.

---

### Post by ArgentinoGuy on 2010-07-09
Si definitivamente era eso! problema resuelto

---

