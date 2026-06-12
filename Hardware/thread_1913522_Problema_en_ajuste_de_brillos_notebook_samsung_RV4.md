---
title: "Problema en ajuste de brillos notebook samsung RV411 S02"
date: 2012-01-22
forum: Hardware
---

### Post by axabalata on 2012-01-22
Resulta que si bien las teclas fn funcionan mostrando la imagen y el  ícono del brillo bajando o subiendo según corresponda, la pantalla sigue  intacta con el mismo brillo al máximo.


 He intentado diversas soluciones, como estas [http://www.ubuntu-es.org/node/127655](http://www.ubuntu-es.org/node/127655), [http://www.taringa.net/posts/linux/11452722/Samsung-n145-ubuntu-brillo-de-pantalla-solucionado.html](http://www.taringa.net/posts/linux/11452722/Samsung-n145-ubuntu-brillo-de-pantalla-solucionado.html),[http://www.taringa.net/posts/linux/8344358/Samsung-R430-BACKLIGHT_brillo-Ubuntu-10_04.html](http://www.taringa.net/posts/linux/8344358/Samsung-R430-BACKLIGHT_brillo-Ubuntu-10_04.html) y otras mas que e encontrado en el foro, pero ninguna me ha dado resultado.

 
 Gracias

---

### Post by zkual0 on 2012-07-31
Hola que tal, hace poco tuve el mismo problema. Aqui pongo el link con la solución que funciono para mi equipo

[http://algodecodigo.blogspot.mx/2012/07/problema-al-cambiar-brillo-en-pantalla.html](http://algodecodigo.blogspot.mx/2012/07/problema-al-cambiar-brillo-en-pantalla.html)

Saludos :popcorn:

---

### Post by Robinsxsoad on 2012-08-16
> **zkual0 said:**
> Hola que tal, hace poco tuve el mismo problema. Aqui pongo el link con la solución que funciono para mi equipo

[http://algodecodigo.blogspot.mx/2012/07/problema-al-cambiar-brillo-en-pantalla.html](http://algodecodigo.blogspot.mx/2012/07/problema-al-cambiar-brillo-en-pantalla.html)

Saludos :popcorn:
Una más de las soluciones que pruebo y no me funciona :(

---

### Post by Coldbeerx on 2012-08-25
Buenas, yo tengo un Samsung R430 y tambien el problema del brillo me hizo volver a win varias veces hasta que ahora buscando alguna solucion la encontre y creo que tambien te servira.

lo primero que debes hacer es:

Comentar con #

```
blacklist samsung-laptop" en /etc/modprobe.d/samsung-backlight.conf
```


entonces 

```
sudo nano /etc/default/grub
```

y agrega 

```
acpi_sleep=nonvs acpi_backlight=vendor pcie_aspm=force
```

a GRUB_CMDLINE_LINUX dentro del "


Luego vas a:

sudo nano /etc/X11/xorg.conf y en la seccion que diga Device agregas abajo

```
Option "RegistryDwords" "EnableBrightnessControl=1"
```

debiera quedar algo asi:


```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```


guardas los cambios y haces:


```
sudo update-grub2
```



Reinicias y ya deberias tener funcionando las teclas funcion de control de brillo de tu samsung.


Yo soy un completo novato en linux pero me senti bien cuando pude hacer funcionar el control de brillo.



Saludos y ojala te sirva.









PD: Si te funciona o no me avisas para saber.

---

