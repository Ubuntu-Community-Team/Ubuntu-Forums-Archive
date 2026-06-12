---
title: "HOWTO: Desactivar Synaptics touchpad al tipear"
date: 2008-07-14
forum: Hardware
---

### Post by sergiom99 on 2008-07-14
Lo traduzco y pongo en nuestro foro, para cuando este la web poder ponerlo ahí:

Procedimiento:
_*1. Activar SHMCONFIG*_
A. Abrir una Terminal.
B. *sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_synbackup*
C. *sudo mcedit /etc/X11/xorg.conf *
D. Buscar una sección como esta:

    Section "InputDevice"
    Identifier "Synaptics Touchpad"
    ...
    End Section 

E. Agregar una línea antes de End Section:

*    Option "SHMConfig" "on"*
[img]http://www.ubuntuforums.org/attachment.php?attachmentid=16864&stc=1&d=1159952821[/img]


F. Salvar el archivo.
G. Anotar estos comandos por si este cambio rompió el sistema gráfico: 
[I]sudo cp /etc/X11/xorg.conf_synbackup /etc/X11/xorg.conf 
killall gdm 
sudo gdm
[/I]
H. Reiniciar X: Ctrl-Alt-Backspace. 
Si no inicia OK, correr los comandos del punto G.

_*2. Agregar el comando de Inicio*_ **(GNOME)**
A. Abrir el administrador de sesiones: System -> Preferences -> Sessions
B. Clickear la solapa 'Startup Programs'
C. Clickear el botón 'Add'
D. Tipear: *syndaemon -i 1 -d*
[img]http://www.ubuntuforums.org/attachment.php?attachmentid=16865&stc=1&d=1159952821[/img]
E. Apretar OK y Salir.

_*2. Agregar el comando de Inicio*_ **(KDE)**
A. Abrir una Konsola
B. Tipear: *mcedit /home/username/.kde/Autostart/syndaemon*
C. Tipear en el archivo: 
[I]         #!/bin/sh
         syndaemon -i 1 -d
[/I]D. Salvar.
E. Tipear: *chmod 775 /home/username/.kde/Autostart/syndaemon*

Nota: reemplazar username por tu nombre de usuario.

Listo! Esto comienza a tener efecto al reiniciar.

El thread original con capturas: [http://ubuntuforums.org/showthread.php?t=271052](http://ubuntuforums.org/showthread.php?t=271052)
**Creditos a Mais que posteó el original.**

---

