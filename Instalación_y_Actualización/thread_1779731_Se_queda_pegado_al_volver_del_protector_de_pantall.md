---
title: "Se queda pegado al volver del protector de pantalla (ubuntu 11.04)"
date: 2011-06-10
forum: Instalación y Actualización
---

### Post by motemei on 2011-06-10
Hola, soy nuevo en esto de Ubuntu, y ultimamente se ha comenzado a quedar pegado despues de haber cerrado la tapa del notebook, o despues de un rato con el protector de pantalla. No responde nada, lo unico que he logrado hacer despues de buscar en google es reiniciar mediante la combinacion de teclas Alt +  ImprPant + RSEIUB, pero no es la idea estar reiniciando el equipo cada vez que se quede pegado. Alguna idea de solucion?

---

### Post by Lutho on 2011-06-10
Deberías de ver los log.

Sistema-> Administración->Visor de archivos de sucesos.

Saludos

---

### Post by silex89 on 2011-06-11
Cuando cierras la tapa del computador de verdad se suspende o hiberna?

---

### Post by motemei on 2011-06-12
lo tengo configurado para que al cerrar la tapa solo se apague la pantalla. Voy a revisar lo del visor de sucesos.

De todas maneras googleando en ingles, no soy el unico al que le sucede. Se responzabilizó al protector de pantalla, pero hice los cambios que mencionaban y sigue sucediendo... menos, pero sucede

A continuación la unica solucion que encontré, pero que somo digo, no lo solucionó 100%

[http://www.multimediaboom.com/fix-screensaver-freezes-in-ubuntu-11-04/](http://www.multimediaboom.com/fix-screensaver-freezes-in-ubuntu-11-04/)

---

### Post by motemei on 2011-06-28
Solucionado. La ultima actualizacion del kernel arregla este problema.

---

### Post by moreback on 2011-07-16
Yo juraba que era algo de compiz, por lo que cuando me pasa pulso Ctrl+Alt+F1, me logeo y luego ingreso

```
pkill -9 compiz
```

y vuelvo finalmente a la sesión gráfica con Ctrl+Alt+F7

Saludos.

---

