---
title: "Ubuntu Studio 10.04 TS Wi-fi"
date: 2010-04-26
forum: Hardware
---

### Post by pipopf on 2010-04-26
Hola estimados. Es la primera vez que escribo acá así que seguramente me faltará algo de cancha para esto. 
Instalé la versión Studio 10.04 TS y no pude configurar la red inalámbrica. No aparece la opción ni para autodetectarla ni para hacerlo manualmente. El controlador se instaló bien pero no permite detectar la red si no que lo detecta como una placa ethernet más.

Los datos técnicos.
PC: Laptop Dell Inspiron 1545

El inconveniente sería que a la hora de configurar la red no permite seleccionar si es inalámbrica o cableada.

Espero sus respuestas. Saludos.

---

### Post by guillermolisi on 2010-04-27
La mejor forma de saber como reconoce el hardware instalado es ingresando estos comandos en consola/terminal:
```

sudo lshw
```y
```
sudo lsusb
```Copia y pega en un mensaje nuevo la salida de ambos. Lo que mas nos interesa es lo relacionado con la placa WiFi (por si no queres pegar todo).

Cuando te pida la clave de tu usuario (para sudo) vas a ver que no se escribe nada pero te la toma igual. Eso es por seguridad.

Fijate de tener actualizado el sistema al dia ya que esa version tendra novedades periodicamente por un tiempo mas.

---

### Post by olivermusico on 2010-05-04
Me pasa algo similar, Instalación limpia de ubuntu studio 10.04 (64 bits) y nm-applet no aparecía. instalé, desinsalé, volví a instalar network.manager y de pronto apareció unos días, pero luego no volvió a aparecer...
no sé si será un bug, pero la versión 9.10 de ubuntu studio funcionaba mejor...
ahora estoy probando hacer una nueva instalación desde 0 para ver si me equivoqué en algo o mi dvd tenía algo.. cuento luego...
saludos!
Ó.

---

