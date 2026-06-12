---
title: "Problemas luego de actualizar Karmic Koala..."
date: 2010-01-21
forum: Instalación y Actualización
---

### Post by kiltro on 2010-01-21
Tengo un notebook toshiba tecra a4 con Ubuntu 9.10, luego de instalar varias aplicaciones que necesitaba (MySql, Netbean, Temas, etc.) traté de reinicializarlo y se queda pegado antes de mostrar la venta de identificación. En fin, debo apagar la maquina por hardware, luego parto en modo seguro para el mismo kernel aparentemente sin problemas, luego reinicio y trato de partir en forma normal y...voila...parte sin problermas.

En resumen, para que parta bien antes debo iniciar en modo seguro y reinicializar!

Help me?

Existe alguna herramienta o técnica que me permita determinar que hace que se pegue en la partida?

Saludos!

---

### Post by Carlos C on 2010-01-22
Prueba viendo los mensajes del sistema escribiendo "dmesg" en el terminal. También puedes mirar en el archivo "/var/log/messages".

Saludos.

---

### Post by kiltro on 2010-01-27
Apenas llegue a casa lo hago, gracias de antemano.

Debo mencionar además que los prblemas en la partida se han vuelto aleatorios. Ultimamente he estado partiendo en modo recupración y arrancando la interfaz gráfica a mano, pero ayer me quedé sin sonido, traté de arrancar en modo recuperación pero se quedo pegado despueés de la pantalla negra, luego probé arrancado ubuntu en modo normal y partió sin problemas y con sonido! Plop!

A pesar de los problemas no vuelvo a Microsoft...

Gracias por tu ayuda,

Saludos!

---

### Post by kiltro on 2010-01-27
Probe 'dmesg' en el terminal y  miré el archivo '/var/log/messages', en ambos casos filtré 'error' y 'warning' porque la salida era mucha, encontrando estás dos lineas:

...ahcii probe of 0000:00:1f.2 failed with error -22
...WARNING at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()

Saludos!

---

