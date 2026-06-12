---
title: "Ubuntu 8.04.1 + ATI Radeon X1200 = Imposible rotar la pantalla?"
date: 2008-11-02
forum: Hardware
---

### Post by petruza on 2008-11-02
Hola, tengo lo siguiente:
Ubuntu 8.04.1
ATI Radeon X1200

En el panel de configuración de resolución de pantalla, no me da la opción de rotarla.

Intenté agregar a xorg.conf La opción [Option "RandRRotation" "true"]
Pero el X arrancó con resolución mínima hecho garompa.

O sea, la conclusión, no se puede rotar la pantalla con mi placa de video? hay algo de software, configuración, etc. que se pueda hacer para lograrlo?

Gracias!

Por las dudas cito el output de "xrandr -q":
```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      75.0*    70.0     60.0  
   1280x960       60.0  
   1280x768       60.0  
   1152x864       75.0     70.0     60.0  
   1024x768       85.0     75.0     72.0     70.0     60.0  
   800x600        85.0     75.0     72.0     70.0     60.0     56.0  
   640x480        85.0     75.0     72.0     60.0  
   640x400        75.0     60.0  
   512x384        75.0     60.0  
   400x300        75.0     60.0  
   320x240        75.0     60.0  
   320x200        75.0     60.0

```

La verdad, leí el man xrandr pero no me queda claro si este output dice que puedo o no rotar el display.

---

### Post by Hei Ku on 2008-11-04
Probaste usar el grandr? Es una aplicación gráfica para el xrandr

---

### Post by petruza on 2008-11-04
No, no lo conocía, ahora lo voy a probar, pero igualmente creo que mi problema se solucionó, aunque de la peor manera :(
Instalé el 8.10, ahora me reconoce el monitor, todo lindo, me da la opción de rotar la pantalla...
Pero si la roto, después el update de la pantalla es lentíiiiiiiisimo, evidentemente el driver debe estar rotando el framebuffer en memoria y después pegándolo en la pantalla y todo ese proceso va muy lento.
A alguien más le pasó eso?
Saludos!

---

