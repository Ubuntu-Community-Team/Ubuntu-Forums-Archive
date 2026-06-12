---
title: "Salió Ubuntu 8.04.1 confirman problemas con el audio"
date: 2008-07-04
forum: Hardware
---

### Post by atari130xe on 2008-07-04
Hoy salió la version 8.04.1 de Hardy, incluye el arreglo de varios bugs (errores) de la 8.04, como el problema del audio en mi caso se volvío una obsesión jejeje pensé será un bug lo del sonido de multiples fuentes a la vez? como leí por ahí, no soy el único con ese inconveniente entonces se me ocurrió consultarles la configuracion de su pc (placa madre y de sonido) para ver si es o nó un "bug" que por lo que sospecho si lo es, pero antes de volcarlo en launchpad me gustaria corroborarlo con ustedes (viene de versiones anteriores tmb por eso estaría bueno encontrarle una solución). 
Si les funca con que configuracion y a los que no tmb. :)

la mia:
Mother ASUS M2N SLI placa de sonido: Genius soundmaker 5.1 value PCI Chip de audio C-Media8738

---

### Post by MeduZa on 2008-07-06
> **atari130xe said:**
> Hoy salió la version 8.04.1 de Hardy, incluye el arreglo de varios bugs (errores) de la 8.04, como el problema del audio en mi caso se volvío una obsesión jejeje pensé será un bug lo del sonido de multiples fuentes a la vez? como leí por ahí, no soy el único con ese inconveniente entonces se me ocurrió consultarles la configuracion de su pc (placa madre y de sonido) para ver si es o nó un "bug" que por lo que sospecho si lo es, pero antes de volcarlo en launchpad me gustaria corroborarlo con ustedes (viene de versiones anteriores tmb por eso estaría bueno encontrarle una solución). 
Si les funca con que configuracion y a los que no tmb. :)

la mia:
Mother ASUS M2N SLI placa de sonido: Genius soundmaker 5.1 value PCI Chip de audio C-Media8738

todos los problemas los solucione quitando pulse audio, hablamos del tema en [este thread]("http://ubuntuforums.org/showthread.php?t=760611")

Mother Asus a8n-e
Sondo: sound Blaster Audigy2 
Chip de audio: emu10k1

todo funcionaba bien en GG y en HH lo hace despues de quitar pulseaudio

---

### Post by atari130xe on 2008-07-07
Sip, en versiones anteriores tenia problemas con la mezcla de sonidos tmb pero era otro hard mas viejo, con este que es bastante mas nuevo, me doy cuenta que por ej: con Ubuntu es un historia con los sonidos múltiples pero para probar instalé Kubuntu 8.04 y con ArtsD noté que era diferente, pero como KDE no me resulta cómodo lo desintalé. Igual entré en Launchpad y lo posteé y de echo si lo es, pero el thread habia sido abierto el año pasado y como la persona que lo había echo no le dió mucha importancia (no lo siguió) el thread se dejó inactivo, yo lo reabrí con la versión Hardy (las otras eran la 7.04 y la 7.10 en esas con una modificación en el archivo asoundrc todo quedaba funcionando). Veremos como sigue el tema.

---

