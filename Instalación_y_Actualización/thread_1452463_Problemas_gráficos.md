---
title: "Problemas gráficos"
date: 2010-04-12
forum: Instalación y Actualización
---

### Post by Grasber on 2010-04-12
Buenas..
Hace poco instalé Ubuntu 9.10 (actualizándolo desde 9.04).
La cosa es que en una sesión podía activar los efectos de las ventanas y en otra sesión no podía.
Al final tuve problemas con la sesión en que andaban los gráficos (se ponía ultralento el pc).
Ahora sólo tengo una sesión en que la máxima resolución de pantalla es de 1024*768 cuando en verdad debería llegar a 1280*768 (o algo así).
La VGA es una ATI Radeon 9700 que por lo que tengo entendido ya no tiene más soporte por parte de ATI, por lo que es conveniente usar el driver open source. Lo malo es que al parecer no está reconociendo la tarjeta o el driver no está asociado a la tarjeta...

---

### Post by Carlos C on 2010-04-13
Como actualizaste desde 9.04 puede que estés usando un archivo /etc/X11/xorg.conf. Si ese archivo existe copia acá su contenido.

Saludos.

---

### Post by Grasber on 2010-04-16
Bueno, lo de la resolución está solucionado.
Pero aún no puedo activar los efectos de las ventanas. Como que se pone a buscar los drivers del video y luego dice que no se pudieron activar los efectos.

Éste es mi archivo xorg.conf:
> Section "Monitor"
    Identifier    "Configured Monitor"
EndSection



Section "Module"
    Load    "dri"
    Load    "GLcore"
EndSection


Section "Device"
        Identifier "ATI Radeon"
        Driver "ati"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AccelDFS" "true"
        Option "EnablePageFlip" "true"
        Option "EnableDepthMoves" "true"
EndSection

Section "Screen"
    Identifier    "Default Screen"
        Device          "ATI Radeon"
    DefaultDepth    24
EndSection

---

### Post by Grasber on 2010-04-17
Problema resuelto. Finalmente la cosa se solucionó completamente. Nunca supe cómo, pero ya está bien :)

---

