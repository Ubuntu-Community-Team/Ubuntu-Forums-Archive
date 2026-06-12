---
title: "Tiembla pantalla con nuevo MoBo"
date: 2009-09-04
forum: Hardware
---

### Post by Andyvec on 2009-09-04
Hola a todos

Cambié mi antiguo motherboard por un XFX 8200 y reintalé mi Ubuntu, el tema es que alctivar los drivers Nvidia veo un ligero temblor en la pantalla, es realmente pequeño pero se nota principalmente cuando leo algo con fondo blanco (mi actividad principal).

Mi monitor es un LCD Samsung 19 pulgadas SynMaster933SN

Estube mirando la configuración del asistente Nvidia y dice la Refresh Date es de 60.02 hz, no me deja cambiarla ¿Tiene algo que ver?

Con el mother y la placa de video aterior (GeForce 6200) y el mismo monitor no tenía problemas, se veía perfecto. ¿Alguna idea?

---

### Post by Andyvec on 2009-09-05
Ya encontré la solución, la posteo por si le sirve a alguien que tenga problemas con pequeños temblores en los drivers Nvidia.

Desde la consola ejecutar lo siguiente:

```
sudo /etc/init.d/dbus restart
```

Acto seguido se me cuelga ubuntu, no es posible responder de ninguna forma, ni cambiar a una terminan por lo tanto debí presionar el botón de apagado de mi máquina (no cortar la corriente, sino forzar un apagado) y luego al volver a prender todo solucionado.

No se si será la mejor opción, pero a mi me resultó.

Saludos

---

### Post by Hei Ku on 2009-09-05
Es raro, porque dbus no tiene nada que ver con los drivers de video. Es un bus de comunicaciones entre aplicaciones del entorno de escritorio.
Lo mas probable es que tuviera que ver con el reinicio.

---

