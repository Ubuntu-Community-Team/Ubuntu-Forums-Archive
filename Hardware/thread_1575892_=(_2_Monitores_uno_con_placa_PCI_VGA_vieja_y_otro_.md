---
title: "=( 2 Monitores: uno con placa PCI VGA vieja y otro con Onboard VGA"
date: 2010-09-16
forum: Hardware
---

### Post by cellini on 2010-09-16
Hola a todos, este es mi primer post mundial en un foro GNU/Linux.

Tengo problemas para hacer andar mis 2 monitores 

1: ViewSonic 15` de tubo
2: Samsung 22`LCD) 

con:

1: VGA compatible controller: Trident Microsystems TGUI 9440 (rev e3) (PCI)
2: VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2) (Onboard)

Lo unico que hice fue cambiar el buteo para que arrancque con la onboard, y no reconoce nada del otro monitor.

Nada nada!

Este es el detalle de mi xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Muchas gracias por todo.

Manuel

---

### Post by juancarlospaco on 2010-09-16
Es que las placas de Video OnBoard estan hechas de tal manera que al conectarle una PCI,
la OnBoard se apaga, se desconecta, y es asi por Hardware.

---

### Post by cellini on 2010-09-17
Gracias por tu respuesta.
Es decir que independientemente que ponga placas de video (AGP, PCI) en mi PC, siempre va a levantar una sola? 
La unica solucion seria conseguir una placa con dos salidas entonces?

Gracias por todo.

Manuel.

---

### Post by guillermolisi on 2010-09-17
> **cellini said:**
> Gracias por tu respuesta.
Es decir que independientemente que ponga placas de video (AGP, PCI) en mi PC, siempre va a levantar una sola? 
La unica solucion seria conseguir una placa con dos salidas entonces?

Gracias por todo.

Manuel.
Si la nVidia que tiene el equipo no posee esa facilidad, si, tenes que conseguirte una placa que te permita manejar dos monitores (las nVidia que poseen esta caracteristica traen un conector especial, similar al DVI)

---

### Post by cellini on 2010-09-20
Gracias por aclararme el tema.
Ahora entonces tengo que buscar un adaptador DVI - VGA o HDMI - VGA  ya que la placa mader posee las 3 salidas!

Gracias.

Manuel.

---

