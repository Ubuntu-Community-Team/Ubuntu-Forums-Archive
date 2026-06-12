---
title: "ATI Radeon IGP 330M/340M/350M en Ubuntu 9.10"
date: 2009-11-03
forum: Hardware
---

### Post by GGsalas on 2009-11-03
Hola. Actualicé a Ubuntu 9.10 y han vuelto problemas con mi placa e video. En Ubuntu 9.04 modifiqué el xorg.conf y logré que mi placa funcionara a 420.000 FPS (deshabilitando los efectos de escritorio), ahora no llega a 2000 FPS.

No puedo modificar de nuevo el xorg.conf porque no existe. Si hubiera una solución mejor la haría (no ando cómodo modificando archivos de sistema)

Mis 2 principales problemas son:

**Blender ya no inicia**, da error:
```
$ blender
Compiled with Python version 2.6.4.
Checking for installed Python... got it!
Segmentation fault

```

**Qcad 2.2.2.0 funciona lento**

Agrego esto:
```
$ glxinfo | grep direct
direct rendering: Yes
$ glxgears
1299 frames in 5.0 seconds
1586 frames in 5.0 seconds
1624 frames in 5.0 seconds
```


Gracias, saludos.

---

### Post by GGsalas on 2009-11-03
Probando de bajar la memoria de la placa desde el BIOS me di cuenta de este problema:   [Window corruption with older ATI graphics cards]("https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Window%20corruption%20with%20older%20ATI%20graphics%20cards")

Para solucionarlo hice lo siguiente:

Ctrl+Alt+F1
```
sudo service gdm stop
```
```
sudo Xorg -configure
```
```
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
```
```
sudo nano /etc/X11/xorg.conf
```

Agrego la opción 'RenderAccel' de esta manera:
```

Section "Device"
        ...
        Driver "radeon"
        Option "RenderAccel" "off"
EndSection
```
```
sudo service gdm start
```

:popcorn: **Ahora funciona más rápido Qcad y puede iniciar y funcionar Blender, todo con mi placa de video con 16Mb asignados.**

---

### Post by guillermolisi on 2009-11-03
Entonces quedo resuelto el tema ?

---

### Post by GGsalas on 2009-11-03
> **guillermolisi said:**
> Entonces quedo resuelto el tema ?

Resultó que con un poco de trabajo pude hacer funcionar Blender y hacer que Qcad funcione decentemente. No probé dibujar mucho en Blender asi que no se cuando va a fallar, lo que si se es que algunos protectores de pantalla hacen colgar toso el sistema y debo apagarlo y volver a encenderlo. No se si es por el cambio que hice en el xorg.conf o porque sólo le asigno 16Mb a la placa de video.

Gracias

---

### Post by guillermolisi on 2009-11-03
> **GGsalas said:**
> Resultó que con un poco de trabajo pude hacer funcionar Blender y hacer que Qcad funcione decentemente. No probé dibujar mucho en Blender asi que no se cuando va a fallar, lo que si se es que algunos protectores de pantalla hacen colgar toso el sistema y debo apagarlo y volver a encenderlo. No se si es por el cambio que hice en el xorg.conf o porque sólo le asigno 16Mb a la placa de video.

Gracias
Y ... si me preguntas que me parecen los 16Mb para video te voy a decir que me parecen como pocos, muy pocos para ciertos usos.

---

### Post by GGsalas on 2009-11-04
> **guillermolisi said:**
> Y ... si me preguntas que me parecen los 16Mb para video te voy a decir que me parecen como pocos, muy pocos para ciertos usos.

Si, es muy extraño, pero parece que Qcad necesita RAM y poca placa de video. Un protector de pantalla necesita más placa de video que Qcad. Mi laptop tiene 512 Mb de ram, como está viejita antes de gastar dinero en ram, lo gasto en otra máquina.

---

