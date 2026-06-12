---
title: "como configurar tarjeta video packard bell tr87"
date: 2009-12-28
forum: Hardware
---

### Post by cjrus on 2009-12-28
Bueno el problema, es que al actualizar de jaunty a karmic,no me reconocio la tarjeta de video, es mas solo puedo entrar en modo baja resolucion es decir 800x600,por favor trato y trato y no puedo configurarla, les dejo los datos

lspci |grep VGA:
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
lscpi

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100xorg.conf
> 
Section "Device"
    Identifier    "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Driver        "intel"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
EndSection

Section "Device"
    Identifier    "GMA500"
    Option    "AccelMethod" "EXA"
    Option    "DRI" "on"
    Option    "MigrationHeuristic" "greedy"
    Option    "IgnoreACPI" "yes"
    Driver    "psb"
EndSection
 
Section "DRI"
    Mode    0666
EndSectionBueno espero alguna respuesta y gracias!!

Pd: me di cuenta que quedo en el sub-foro de software porfavor si pueden moverlo al de hardware. gracias xD

---

### Post by moreback on 2009-12-28
Veo que tienes un /etc/X11/xorg.conf que viene de Jaunty. En la 9.10 ya no viene ninguno, así que podrías borrarlo (el /etc/X11/xorg.conf) y dejar que el servidor X detecte automáticamente el driver correcto.

Saludos.

---

### Post by cjrus on 2009-12-29
hola mira borre el archivo /etc/X11/xorg.conf pero ahora con apt-get update buscara el driver o es de otra forma, si es asi me podrias dar el codigo y gracias por responder

---

### Post by Carlos C on 2009-12-29
Las Intel funcionan con el driver libre, así que no es necesario instalar nada.

Saludos!

---

### Post by cjrus on 2009-12-29
hola mira reinicie el note y aun nada sigue diciendo que iniciara en baja resolucion, lei por internet y a varios les paso que no reconocia su pantalla y que se solucionaba con actualizar, pero ni con actualizar a mi se me arregla. dejo el xrandr:
> Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  y espero tu respuesta salu2

---

### Post by CdK1 on 2009-12-30
Haz lo que dice moreback, borra el archivo de xorg.conf, updatea, ve si el mismo servidor X te toma una configuracion correcta, si no es así, usa este archivo: 
[FONT=monospace]
[LIST=1]
[*]Section "Files"                 
[*]        FontPath        "/usr/share/fonts/X11/misc"
[*]        FontPath        "/usr/share/fonts/X11/cyrillic"
[*]        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
[*]        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
[*]        FontPath        "/usr/share/fonts/X11/Type1"
[*]        FontPath        "/usr/share/fonts/X11/100dpi"
[*]        FontPath        "/usr/share/fonts/X11/75dpi"
[*]        # path to defoma fonts  
[*]        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
[*]EndSection                      
[*]                                
[*]Section "Module"                
[*]        Load    "i2c"           
[*]        Load    "bitmap"        
[*]        Load    "ddc"           
[*]        Load    "dri"           
[*]        Load    "extmod"        
[*]        Load    "freetype"      
[*]        Load    "glx"           
[*]        Load    "int10"         
[*]        Load    "vbe"           
[*]EndSection                      
[*]                                
[*]Section "InputDevice"           
[*]        Identifier      "Generic Keyboard"
[*]        Driver          "kbd"   
[*]        Option          "CoreKeyboard"
[*]        Option          "XkbRules"      "xorg"
[*]        Option          "XkbModel"      "pc105"
[*]        Option          "XkbLayout"     "es"
[*]EndSection
[*] 
[*]Section "InputDevice"
[*]        Identifier      "Configured Mouse"
[*]        Driver          "mouse"
[*]        Option          "CorePointer"
[*]        Option          "Device"                "/dev/input/mice"
[*]        Option          "Protocol"              "ImPS/2"
[*]        Option          "ZAxisMapping"          "4 5"
[*]        Option          "Emulate3Buttons"       "true"
[*]EndSection
[*] 
[*]Section "InputDevice"
[*]        Identifier      "Synaptics Touchpad"
[*]        Driver          "synaptics"
[*]        Option          "SendCoreEvents"        "true"
[*]        Option          "Device"                "/dev/psaux"
[*]        Option          "Protocol"              "auto-dev"
[*]        Option          "HorizScrollDelta"      "0"
[*]EndSection
[*] 
[*]Section "InputDevice"
[*]        Driver          "wacom"
[*]        Identifier      "stylus"
[*]        Option          "Device"        "/dev/input/wacom"
[*]        Option          "Type"          "stylus"
[*]        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
[*]EndSection
[*] 
[*]Section "InputDevice"
[*]        Driver          "wacom"
[*]        Identifier      "eraser"
[*]        Option          "Device"        "/dev/input/wacom"
[*]        Option          "Type"          "eraser"
[*]        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
[*]EndSection
[*] 
[*]Section "InputDevice"
[*]        Driver          "wacom"
[*]        Identifier      "cursor"
[*]        Option          "Device"        "/dev/input/wacom"
[*]        Option          "Type"          "cursor"
[*]        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
[*]EndSection
[*] 
[*]Section "Device"
[*]        Identifier      "Generic Video Card"
[*]        Driver          "intel"
[*]        BusID           "PCI:0:2:0"
[*]        Option          "AddARGBGLXVisuals" "True"
[*]        Option          "DisableGLXRootClipping" "True"
[*]        Option          "XAANoOffscreenPixmaps"
[*]        Option          "UseFBDev"
[*]        Option          "TripleBuffer" "true"
[*]EndSection
[*] 
[*]Section "Monitor"
[*]        Identifier      "Generic Monitor"
[*]        Option          "DPMS"
[*]#       Modeline "1280x1024@60" 83.91 1280 1312 1624 1656 800 816 824 841
[*]EndSection
[*] 
[*]Section "Screen"
[*]        Identifier      "Default Screen"
[*]        Device          "Generic Video Card"
[*]        Monitor         "Generic Monitor"
[*]        DefaultDepth    24
[*]        Option         "AddARGBGLXVisuals" "True"
[*]SubSection     "Display"
[*]        Viewport    0 0
[*]    EndSubSection
[*]    SubSection     "Display"
[*]        Viewport    0 0
[*]        Depth       4
[*]    EndSubSection
[*]    SubSection     "Display"
[*]        Viewport    0 0
[*]        Depth       8
[*]    EndSubSection
[*]    SubSection     "Display"
[*]        Viewport    0 0
[*]        Depth       15
[*]    EndSubSection
[*]    SubSection     "Display"
[*]        Viewport    0 0
[*]        Depth       16
[*]    EndSubSection
[*]    SubSection     "Display"
[*]        Viewport    0 0
[*]        Depth       24
[*]        Modes       "1280x1024"
[*]    EndSubSection
[*]EndSection
[*] 
[*]Section "ServerLayout"
[*]        Identifier      "Default Layout"
[*]        Screen          "Default Screen"
[*]        InputDevice     "Generic Keyboard"
[*]        InputDevice     "Configured Mouse"
[*]        InputDevice     "stylus"        "SendCoreEvents"
[*]        InputDevice     "cursor"        "SendCoreEvents"
[*]        InputDevice     "eraser"        "SendCoreEvents"
[*]        InputDevice     "Synaptics Touchpad"
[*]EndSection
[*] 
[*]Section "DRI"
[*]        Mode    0666
[*]EndSection
[*] 
[*]Section "Extensions"
[*]    Option "Composite" "true"
[*]EndSection
[/LIST]
[/FONT]

---

### Post by cjrus on 2009-12-30
veras elimine en xorg y ademas update el sistema, pero igual no encuentra nada, sobre el archivo que pusiste es para dejarlo como el xorg.conf ? bueno espero tu respuesta y gracias salu2

---

### Post by CdK1 on 2009-12-30
Que no encuentras?, y SÍ OBVIO que es para crear un xorg.conf, respóndeme ésto:

Borraste tu /etc/X11/xorg.conf y updateaste el sistema?
Cúando hiciste eso, te levanto el entorno gráfico -aka X-, luego de reiniciar, y reitero, sin usar un archivo /etc/X11/xorg.conf 
Si no te levanto, probaste creando otro /etc/X11/xorg.conf con los datos que te dí, SIN LOS NUMEROS DE LA IZQUIERDA?

---

### Post by cjrus on 2009-12-30
perdon no me fije qe habias posteado...

---

### Post by CdK1 on 2009-12-30
Obvio que te muestra la tarjeta, el lspci es una herramienta diferente a la configuración, lo único que tienes que hacer es crear un /etc/X11/xorg.conf, usa los datos que te dí antes... y avisa...

---

### Post by cjrus on 2009-12-30
disculpa mira si hacia lo que ddecia de crear un xrog.conf con los datos que me das me dice que ubuntu iniciara en baja resolucion. pero ya encontre el problema, no es la tarjeta la que no reconoce sino que es la pantalla. concete una pantalla externa y puedo entrar activando efectos de escritorio, usando compiz, el problema esque mientras eso puedo hacer en la pantalla externa en la del note no pasa nada, no se como hacer para que reconozca la pantalla, quiza sea pork es del 2009 el note creo que salio en mayo al mercado y quiza karmic lo estaban haciendo desde antes, ademas es una pantalla led hd lcd, bueno espero tu respesta porfa que veo la interfaz que tiene y me da rabia no poder disfrutarla en mi note, ahora escribo desde la pantalla externa y me fije que hasta los iconos de cerrado, maximimado de ventanas son completamente distintos..:shock:

---

### Post by CdK1 on 2009-12-30
No iniciará en baja resolución, al contrario, cambia a la resolución que quieras y usa un xorg.conf, como el mío, sólo cambia la resolución...

---

### Post by cjrus on 2009-12-30
creo que no me entendiste hice lo que dijiste de agregar tus datos al xorg.conf y cuando lo hice, updatie y reinicie, cuando entre me dijo que entraria en baja resolucion, entre a ubnutu en baja resolucion fui a pantalla para ver si habian mas tamaños que soportara y me dijo que la pantalla no estaba reconocida, entonces elimine el xorg.conf que me pasaste , luego updatie y reinicie y sas! entro con todas las resoluciones que tengo disponibles, pero ese no es el problema porque me fije que yo puedo entrar en tres incios diferentes en el grub, si entro al primero y al segundo no se ve nada pero si se puede oir cuando inicia sesion, si entro al tercero ocurrer lo que he dicho antes, osea ahi es donde ahora me reconoce la pantalla pero no la tarjeta, y en la primera y segunda opcion que tengo en el grub me reconoce la tarjeta pero no la pantalla, lo comprobe ya que conecte una pantalla externa y en ella no hay problema funciona todo super bien. porfa no se que hacer!

PD: lo de los 3 inicios de sistema en el grub son sacando a sus respectivos restauradores de sistema que traen...

---

### Post by CdK1 on 2009-12-31
Trata de especificar en el xorg.conf la frecuencia del monitor...

---

