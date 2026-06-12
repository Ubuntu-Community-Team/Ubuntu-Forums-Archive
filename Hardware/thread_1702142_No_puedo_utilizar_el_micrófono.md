---
title: "No puedo utilizar el micrófono"
date: 2011-03-07
forum: Hardware
---

### Post by Brath-ga on 2011-03-07
Hola a todos.
Llevo investigando y googleando para encontrar solución, pero sin resultados.
Mi sobremesa tiene una tarjeta de sonido integrada de la casa Realtek y otra en la tarjeta gráfica Nvidia.
Yo quiero usar la de Realtek.
si escribo:
> 
cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio
 2 snd_hda_intel


y si escribo:

> 
lspci -k | grep -i audio
06:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


Creo que el problema me viene de la tarjeta de Nvidia
Como puedo hacer para que me coja siempre la Realtek?

---

### Post by josecuervo86 on 2011-03-07
Hola Brath-ga, si vas a **sistema** > **preferencias** > **sonido**, en la solapa **hardware** te va a aparecer una lista con la(s) placa(s) de sonido que tengas disponible, luego en la solapa **entrada**, y en caso de que tengas mas de una vas a poder elegir por cual queres que ingrese el sonido.

---

### Post by Brath-ga on 2011-03-13
Gracias josecuervo86 por tu respuesta.
Ya tenía las preferencias de sonido bien configuradas, pero hice cambios sobre ellas para ver si surtían efecto con resultado negativo.
Sigo sin saber como poder hacer funcionar bien el sonido de entrada en mi equipo.

---

### Post by Brath-ga on 2011-03-13
Espera!!!!!!!
Acabo de solucionarlo.
Vaya tontería:
En preferencias de sonido > entrada, tenía como conector microphone 1 y yo tengo el micro conectado en el frontal.
Al cambiar a microphone 2 se solucionó el problema.
Creí que no tenía opción para cambiar el micrófono.
Gracias.

---

