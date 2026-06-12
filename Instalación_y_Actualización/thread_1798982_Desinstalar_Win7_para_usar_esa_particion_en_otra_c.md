---
title: "Desinstalar Win7 para usar esa particion en otra cosa"
date: 2011-07-06
forum: Instalación y Actualización
---

### Post by vandroiy.cl on 2011-07-06
Hola, tanto tiempo xD

Una duda, creo que simple. Ocurre que tengo linux y win7 en mi notebook, en distintas particiones, la primera particion es la de Win7, el que quiero desinstalar y utilizar esa particion para el VirtualBox y poder probar distintas distros.

La pregunta es, si formateo esa particion, ocurrira algun problema con el MBR o algo asi?? o como es GRUB lo q me aparece al principio no habria ningun problema en llegar y formatearla?

Y respecto al formateo, abro el gparted como root pero me tira un msje de que no tengo los permisos para montar/desmontar esa particion!! wtf?

Saludos y gracias por su atencion ^^

---

### Post by nechus on 2011-07-07
Como dijo Jack el Destripador, "vamos por parte". :)

>"la primera particion es la de Win7, el que quiero desinstalar y utilizar esa particion para el VirtualBox y poder probar distintas distros."

No necesitas una partición exclusiva para VirtualBox. VirtualBox se instala como cualquier aplicación y el disco duro virtual es un archivo que encontrarás en una carpeta oculta en tu carpeta personal.

>"si formateo esa particion, ocurrira algun problema con el MBR o algo asi?? o como es GRUB lo q me aparece al principio no habria ningun problema en llegar y formatearla?"

Al menos en mi experiencia, cuando uno instala Ubuntu, lo normal es que Ubuntu quede como el sistema operativo por defecto. Si quieres iniciar Windows tienes que seleccionarlo. Por lo tanto, mientras la partición de Ubuntu siga intacta, puedes hacer lo que quieras con las demás particiones: achicarlas, agrandarlas, borrarlas, mezclarlas... menos moverlas porque puedes mover la de Ubuntu y dejas la...

>"Y respecto al formateo, abro el gparted como root pero me tira un msje de que no tengo los permisos para montar/desmontar esa particion!! wtf?"

Meterse con los permisos es una lata. Lo mejor es que descargues una versión LiveCD de gparted y lo ejecutes desde el CD. Así trabajas sin necesidad de montar o desmontar cosas. ¡Pero no toques la partición de Ubuntu!

Advertencia: Todo lo anterior corre por tu propia cuenta y riesgo. Todos los computadores son diferentes así que los resultados podrían variar. Se recomienda ENCARECIDAMENTE respaldar los datos importantes al intrusear con particiones.

---

### Post by vandroiy.cl on 2011-07-07
Es q se me ocurrio q seria una mejor idea tener el disco virtual en una particion aparte para controlar el espacio, pq pretendo instalar como 3 sist operativos por lo menos.

Lo hare como dices, con un CD. 
Saludos y gracias por tu respuesta !!

(quien marca esto como solved? ^^)

---

### Post by moreback on 2011-07-16
No se puede desmontar la partición / porque siempre está en uso. Por eso hay que usar un cd como gparted-live o con uno de Ubuntu e iniciar el pc con éste.

Saludos.

---

