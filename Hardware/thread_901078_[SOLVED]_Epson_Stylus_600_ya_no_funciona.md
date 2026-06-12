---
title: "[SOLVED] Epson Stylus 600 ya no funciona"
date: 2008-08-26
forum: Hardware
---

### Post by DrJuano on 2008-08-26
Resulta que estuve de viaje y mi novia instaló 50 actualizaciones. Hoy me encuentro con la situación de tener que imprimir y, al largar la impresión, el dispositivo no mueve un pelo.

Se trata de una Epson Stylus Color 600 (puerto paralelo): normalmente utilizaba lp0, que para mi sorpresa ya no está. 

El comando dmesg | grep lp me arroja lo siguiente:
lp: driver loaded but no devices found.

Conexiones y todo lo demás corroborados. Win$ imprime. Me llamó la atención que la interfaz gráfica de gnome no reconce nada conectado al puerto paralelo (nunca reconoció la impresora por si mismo, pero notaba que había algo enchfuado en LPT1.) En /dev encontré que existe un parport0 pero al elegirlo manualmente no funciona. Tampoco echo hola > /dev/parport0 (error de escritura, argumento inválido.)

Gracias por leer mi problema.

---

### Post by faktorqm on 2008-08-26
de nada, y si booteas con el kernel anterior imprime? va, supongo que te actualizo uno. salu2!

---

### Post by rojojuan on 2008-08-26
> **DrJuano said:**
> Resulta que estuve de viaje y mi novia instaló 50 actualizaciones. Hoy me encuentro con la situación de tener que imprimir y, al largar la impresión, el dispositivo no mueve un pelo.

Se trata de una Epson Stylus Color 600 (puerto paralelo): normalmente utilizaba lp0, que para mi sorpresa ya no está. 

El comando dmesg | grep lp me arroja lo siguiente:
lp: driver loaded but no devices found.



Conexiones y todo lo demás corroborados. Win$ imprime. Me llamó la atención que la interfaz gráfica de gnome no reconce nada conectado al puerto paralelo (nunca reconoció la impresora por si mismo, pero notaba que había algo enchfuado en LPT1.) En /dev encontré que existe un parport0 pero al elegirlo manualmente no funciona. Tampoco echo hola > /dev/parport0 (error de escritura, argumento inválido.)

Gracias por leer mi problema.


Te dejo una página donde te soluciona el problema directamente. Esta en castellano. 
[http://localhost:631/printers](http://localhost:631/printers)
Suerte

---

### Post by faktorqm on 2008-08-26
jajajajajaj muy bueno! salu2!

---

### Post by DrJuano on 2008-08-27
Gracias por la idea de bootear con kernel viejo, voy a probar. También gracias por el irónico consejo de administrar samba con la interfaz html (sólo que no es para nada últil y aparentemente no leiste mi problema.)

No quieor ser grosero, pero si pido ayuda por favor no me tomen el pelo (siempre lo mismo.) Hay quienes usamos la pc, no solo nos divertimos con ella.

---

### Post by DrJuano on 2008-08-27
Bueno, he solucionado el problema. Estuve tratando de hacer andar un joystick por puerto serial, aparentemente cargué unos módulos que ocupaban dicho puerto. Simplemente borré los modulos de /etc/modules y dejé una linea con "lp" (sin comentar, como estaba antes.)

Problema resuelto. Gracias igual.

---

### Post by rojojuan on 2008-08-27
No quieor ser grosero, pero si pido ayuda por favor no me tomen el pelo (siempre lo mismo.) Hay quienes usamos la pc, no solo nos divertimos con ella.[/QUOTE]

Hace mucho tiempo usé esa página para detectar el puerto de la impresora, no era joda.
Te aclaro que no fue mi intención hacer una joda.

---

