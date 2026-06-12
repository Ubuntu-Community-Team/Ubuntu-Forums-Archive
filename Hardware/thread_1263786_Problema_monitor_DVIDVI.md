---
title: "Problema monitor DVI/DVI"
date: 2009-09-11
forum: Hardware
---

### Post by nemodot on 2009-09-11
Buenas,
Me acabo de comprar un tremendo monitor de 23'' samsung.

Sucede que cuando uso el cable DVI a DVI en ubuntu el monitor se queda en negro con el boton de encendido titilando y un cartelito que indica "analog" y cambia a "digital" repetitivamente. En windows funciona bien.
Y cuando uso el cable DVI/D-sub, como ahora, funciona bien en ubuntu.

Pero yo quiero aprovechar la ventaja de tener la conexión digital DVI a DVI.

Hay algo que pueda hacer?

---

### Post by anarko on 2009-09-11
> **nemodot said:**
> Buenas,
Me acabo de comprar un tremendo monitor de 23'' samsung.

Sucede que cuando uso el cable DVI a DVI en ubuntu el monitor se queda en negro con el boton de encendido titilando y un cartelito que indica "analog" y cambia a "digital" repetitivamente. En windows funciona bien.
Y cuando uso el cable DVI/D-sub, como ahora, funciona bien en ubuntu.

Pero yo quiero aprovechar la ventaja de tener la conexión digital DVI a DVI.

Hay algo que pueda hacer?

Que placa de video tenes? seguramente es problema de conf. del driver o el xorg que le esta diciendo a la placa que use el analog en lugar del digital.

proba reconfigurar el x-org o el driver de video.

---

### Post by nemodot on 2009-09-11
Tengo una Nvidia 6600GT y la verdad que odio el *BEEP* Xorg.conf,
me ha vuelto a suceder que no se conserva la resolución elegida y no hay modo de corregirlo.

Hay alguna solución definitiva para esto? Hacer que el xorg me reconozca la conexión digital y al mismo tiempo que me conserve la resolución?

---

### Post by jorgemarmo on 2009-09-20
tengo mucho tiempo con el mismo problema, con un samsung p2070 en una nvidia GeForce MX 420, la solución es definir un modeline para tu monitor.... ya he logrado obtener el modeline pero en jaunty cambiaron el modo en que se maneja el xorg.conf y no he podido agregar este modeline al X...

para aclarar la cosas checka:
[http://ubuntuforums.org/showthread.php?t=1053040](http://ubuntuforums.org/showthread.php?t=1053040)
[http://ubuntuforums.org/showthread.php?t=1270805](http://ubuntuforums.org/showthread.php?t=1270805)

---

