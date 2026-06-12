---
title: "Resolución de Pantalla en Karmic Koala"
date: 2009-11-16
forum: Hardware
---

### Post by polcla on 2009-11-16
Hola a todo el foro,  les paso la sgte consulta : He migrado de Win Xp a Ubuntu 9.10   y tengo el siguiente incoveniente  no puedo ajustar la resolución de pantalla a más de 800*600 .
He leído los hilos de problemas similares al mío , pero no he llegado a encontrar la solución ,desde ya agradecería si me pueden dar una mano con esto.
Acá abajo transcribo el resultado de los comandos lspci ,dmesg, glxinfo. El fichero xorg.conf no existe ( tengo entendido que desaparece en esta versión de Ubuntu).
El monitor es un  LCD Samsung Syncmaster 933SN de 18.5" .
Saludos
Claudio. 
 
[EMAIL="rocla@rocla-desktop:~$"]rocla@rocla-desktop:~$[/EMAIL] lspci | egrep "VGA"
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC AGP (rev 3a)
[EMAIL="rocla@rocla-desktop:~$"]rocla@rocla-desktop:~$[/EMAIL] dmesg | grep video
[    0.581198] pci 0000:01:00.0: Boot video device

[EMAIL="rocla@rocla-desktop:~$"]rocla@rocla-desktop:~$[/EMAIL] glxinfo | grep direct
direct rendering: Yes
[EMAIL="rocla@rocla-desktop"]rocla@rocla-desktop[/EMAIL]:

---

