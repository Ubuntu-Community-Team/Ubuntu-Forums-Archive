---
title: "Problema con discos"
date: 2009-04-14
forum: Hardware
---

### Post by Nikolopulus on 2009-04-14
Hola, estoy teniendo un problema con los discos duros de mi compu, digo discos porque con este es el segundo que se daña en dos o tres meses. El primero murió directamente, el que estoy usando actualmente parece estar dañado en algún sector vinculado con linux, porque con windows arranca, anda a pedales, pero arranca.
Esto lo note cuando prendí la maq y ubuntu no arranco. Cuando arranqué en modo de recuperación y después de unos minutos mi tiró el siguiente código:

```
[79.146511] end_request: I/O error, des sda, sector 8740098
init: rc_default main process (2414) terminated with status 2
```

¿alguien me puede confirmar que mi disco está dañado? o sino que me ayude a solucionar el problema que tengo, sea lo que sea.

Ah, también traté de reinstalar linux, reconoce el disco todo bien, con las particiones que tengo, pero cuando pongo para formatear me tira un error y vuelve para atras, y desde ahí ya no reconoce ninguna partición, ni las de ubuntu ni las de windows.

Muchas gracias por la ayuda

---

### Post by staar on 2009-04-14
dos discos en tres meses? eso es malo, chequeaste los cables? la fuente?

saludos

---

### Post by guillermolisi on 2009-04-15
Temperatura y calidad de los discos/proveedor.

Si bien uno ve que el disco es de marca, etc., etc., no todos los que se venden en el mercado local son iguales. Inclusive se puede tener problemas con discos de muy buena marca y buen control de calidad.
Me ha pasado con discos SCSI HotPlug Seagate de HP, por ejemplo. Cuatros discos de una misma partida, lote, que presentaban los mismos sintomas.

Y el tema temperatura es crucial. Que un dsco este trabajando por encima de los 50° en forma permanente lo termina cocinando con el paso del tiempo.

---

### Post by Nikolopulus on 2009-04-15
Los cables no son, la fuente la voy a revisar el finde, durante la semana no tengo un minuto.
Con respecto al tema de la temperatura, la verdad no tengo idea de como revisarla, aunque la maquina que tengo tiene 2 coolers laterales, con lo que supongo que refrigerará bastante

---

### Post by abn91c on 2009-04-15
a cambiado el motherboard o el regualdor de la corriente electrica recientemente? puede que necesite un regualdor mas poderoso como de mas de 350 watts

---

### Post by guillermolisi on 2009-04-15
> **Nikolopulus said:**
> Los cables no son, la fuente la voy a revisar el finde, durante la semana no tengo un minuto.
Con respecto al tema de la temperatura, la verdad no tengo idea de como revisarla, aunque la maquina que tengo tiene 2 coolers laterales, con lo que supongo que refrigerará bastante
Si los discos tienen sensor de temperatura, les habilitas la funcion SMART y usas algun paquete de sensores tipo LM-Sensors o similar, deberias poder ver a que temperatura trabajan.

Los fans laterales pueden ser efectivos siempre que entre disco y disco se deje suficiente separacion como para que circule aire. En general los discos estan mas adelante en el gabiente que el flujo de aire de los ventiladores laterales.

Si estan pegados, con muy poca separacion (menor a la altura de un disco), el calor del de abajo cocina al de arriba (suponiendo un gabinete tower).

Lo mejor es poner forzadores interiores en el frente, soplando hacia la parte posterior del gabiente, pasando por los discos.

---

