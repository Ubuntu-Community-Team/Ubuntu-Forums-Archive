---
title: "Problema Configurar Nvidia GeForece4 MX 4000"
date: 2009-01-21
forum: Hardware
---

### Post by zeroadrenaline on 2009-01-21
Che, bueno, intente configurar esta plaquita con los driver pribativos, baje el recomendado por la pagina yanqui, despues baje el recomendado por la pagina en español, elimine el nvidia-kernel-common nvidia-.....No recuerdo los nombresitos, pero en fin, elimine los 3 que recomienda la guia ubuntu que elimine.
Despues baje los Drivers, tire abajo kdm, y corri el driver con 2 de los tres que probe, no me compilo los modulos y me dice que pruebe otro driver, me lei el log en /var/log/nvidia_setup o algo asi que te genera solito el script, y me decia que busque el 1.0.96xx lo baje, lo corri, y no me compila el modulo, concegui otro, el 100.44... del site en español, y bueno, lo compila, todo bonito, termina de instalalarlo, y cuando reinicie, CUAC! las X nunca aparecieron, intenta, titila un par de veces, y al la consola de una, por suerte, hombre precavido vale por dos, habia rescatado el xorg.conf original por las deudas, asique no fue tan grave, pero no tengo aceleracion y me frustra!.
No probe con envy porque no sabia si ENVY me daba aceleracion.
Si alguien sabe algo , y me tira una mano, buenisimo.

---

### Post by guillermolisi on 2009-01-21
Si no me equivoco para esa placa tenes que usar el paquete de nvidia privativo legacy (para placas de cierta antiguedad).

Proba con el Envy y si no resulta podes desinstalar el paquete tal como hiciste antes.

---

