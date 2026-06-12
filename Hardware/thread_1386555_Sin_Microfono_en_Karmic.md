---
title: "Sin Microfono en Karmic"
date: 2010-01-20
forum: Hardware
---

### Post by radixs on 2010-01-20
Hola todos, la verdad no soy de los que escribe pidiendo alguna respuesta aquí en el foro, generalmente busco, busco. Ahora no se si estoy bloqueado y que se yo, pero no doy con una solución.

Al Grano: Resulta que no eh podido activar el micrófono en Karmic. Aquí mi lspci de audio:

```
01:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

```

Tengo una Soundblaster Audigy SE, Las preferencia de sonido la tarjeta esta configurada con Audio Estero Duplex y aun así no hay señal de micrófono.

---

### Post by vargux on 2010-01-21
mmmmm ... una solución, espero esto exista en tu versión de ubuntu, ya que lo traduje desde: [aquí]("http://ubuntuforums.org/showthread.php?t=425098"), para un problema similar en kubuntu 6.10 (bastate tiempo atrás)... si no existe el archivo que se menciona, mejor ni intentar nada:


Reemplaza el archivo **.asoundrc** (en la carpeta **home**, elige la opción **"Mostrar archivos ocultos"**) con esta secuencia de comandos ó script:


################################################## #######
# Esta es la configuración estándar (ver: "!default")
# Este perfil, el valor predeterminado cargado, upmixes sonido estéreo a 5.1.

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
################################################## ######
# Este es el perfil normal de salida SPDIF (óptico, Toslink).

pcm.!spdif {
type plug
slave.pcm "hw:0,1"
}

################################################## #####
# Esto es lo que podríamos llamar el "ajuste de fábrica", en otras palabras, sólo reproduce los canales reales. FX por lo que si quieres ver una película de 5,1, en la salida analógica, esta es la opción que desee.


pcm.analog {
type plug
slave analog_slave;
}

pcm_slave.analog_slave {
pcm surround51;
format S32_LE;
}
[I]
[/I]*...guardarlo, y luego cierra la sesión (Ctrl-Alt-Retroceso), accede de nuevo y esperemos que funcione.... sino me llegan los retos :)*

Salu2 !!!

---

