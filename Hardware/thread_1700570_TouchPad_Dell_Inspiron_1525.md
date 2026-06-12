---
title: "TouchPad Dell Inspiron 1525"
date: 2011-03-05
forum: Hardware
---

### Post by sebasthian777 on 2011-03-05
Hola gente,
Desde que instale Ubuntu en mi notebook, he notado que tiene algunas caracteristicas menos que los drivers de dell sobre windows.

Principalmente el unico que me gustaria tener, es el del touchpad, mas que nada por el tema de las aplicacione que tiene...

por ejemplo, el scroll es continuo, uno cuando lo usa puede empezar a dibujar circulos sobre el touchpad y el scroll sigue avanzando.
Mismo con el scroll horizontal. 

ademas del borde izquierdo del touchpad, se puede configurar para utilizar el zoom (como seria en muchos lados, CTRL + Rueda del Mouse.

Bueno eso solo, por ahi lo tendria que haber puesto en software, pero me parecio mejor ponerlo aca.

Saludetes!

---

### Post by guillermolisi on 2011-03-05
Esta perfecto aqui. Los drivers son parte necesaria del hardware y los consideramos como tal.

---

### Post by hectorivand on 2011-03-05
> **sebasthian777 said:**
> Hola gente,
Desde que instale Ubuntu en mi notebook, he notado que tiene algunas caracteristicas menos que los drivers de dell sobre windows.

Principalmente el unico que me gustaria tener, es el del touchpad, mas que nada por el tema de las aplicacione que tiene...

por ejemplo, el scroll es continuo, uno cuando lo usa puede empezar a dibujar circulos sobre el touchpad y el scroll sigue avanzando.
Mismo con el scroll horizontal. 

ademas del borde izquierdo del touchpad, se puede configurar para utilizar el zoom (como seria en muchos lados, CTRL + Rueda del Mouse.

Bueno eso solo, por ahi lo tendria que haber puesto en software, pero me parecio mejor ponerlo aca.

Saludetes!

Hola Seba, tenes la marca y modelo del touchpad?

---

### Post by sebasthian777 on 2011-03-06
> **hectorivand said:**
> Hola Seba, tenes la marca y modelo del touchpad?

Hola Hector,

Mira el modelo no lo tengo, la marca me acabo de fijar y es:
Alps Electric CO.

hice además un lshw, pero no me devolvió nada sobre el touchpad.

Alguna idea?

---

### Post by sebasthian777 on 2011-03-08
Bueno, lo solucione en parte, pero no estoy del todo contento.

Descubri que existe un soft GUI llamado gpointing
```
sudo apt-get install gpointing-device-settings
```

Es un entorno grafico para configurar el driver Synaptics touchpad del xserver. En fin.

Me dejo agregar el scroll circular que tanto extrañaba, pero no trae opcion para agregar el zoom en la parte izquierda del touchpad.

Asi que seguire buscando. Espero que si a alguien le pasa, sepa que con este "pointing device" puede habilitar muchas cosas.

=)

---

