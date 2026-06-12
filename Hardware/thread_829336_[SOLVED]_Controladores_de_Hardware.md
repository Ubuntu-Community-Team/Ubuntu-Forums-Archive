---
title: "[SOLVED] Controladores de Hardware"
date: 2008-06-14
forum: Hardware
---

### Post by Vero1 on 2008-06-14
Hola,

Ayer tuve un problema con el controlador de Nvidia porque no tomaba en cuenta la habilitación del controlador, a pesar de que en Controladores de Hardware figuraba que estaba habilitado y en uso. No me permitía cambiar la resolución de la pantalla, que era muy baja. Cansada de probar cosas, opté por iniciar en Modo Recovery y allí le pedí fix X server. Con eso se arregló el asunto de la resolución, pero tengo un problema ahora.

Cuando voy a Controladores de Hardware, la pantalla está en blanco y no presenta ningun controlador. En el xorg.conf figura Nvidia pero al  correr nvidia xconfig me dice que no está instalado el driver.

Aparte al querer utilizar Efectos de Escritorio en Compiz-Fusion, me dice que no se puede habilitar.

Quisiera saber si puedo recuperar el texto que debe figurar en Controladores de Hardware y qué es lo que puedo hacer con respecto al controlador de Nvidia.

Desde ya, muchas gracias.

---

### Post by sergiolib on 2008-06-14
Haz esto:
sudo apt-get install nvidia-glx

Reinicia y cuentanos como te fue.

---

### Post by Vero1 on 2008-06-15
Hola sergio,

Lamentablemente no surtió efecto. 
Me sale una pantallita donde dice que no ha podido encontrar la pantalla, ni el controlador y que lo configure yo.

Configuré Nvidia FX generic porque yo tengo Nvidia FX 5200(que no figura), pero al reiniciar tengo una resolución de 800x600 y no me dá opciones de cambiar.

Si te parece, te extracto del Xorg.conf la parte que hace mención a pantalla y controlador, a ver si hay algo fuera de lugar.

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"
        Screen  0

Section "device" #
        Identifier      "device1"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "640x480@60"

La verdad no sé de donde sale Vesa... Evidentemente todo está fuera de lugar.

Gracias

---

### Post by Vero1 on 2008-06-16
Sólo para decir que ya está solucionado lo de la pantallita.

Actualicé el repositorio restricted y se instaló nuevamente.

Gracias.

---

