---
title: "Al cambiar mother hay que reinstalar ubuntu?"
date: 2009-02-01
forum: Hardware
---

### Post by arysar on 2009-02-01
voy a cambiar el mother y procesador de la pc, actualmente tengo un AMD ATHLON y voy a pasar a un Intel Dual Core, tengo instalado ubunto 8.10, tengo que reinstalar ubuntu o hay algún procedimiento para que se actualice sin reinstalar.
Gracias!

---

### Post by gmunioz on 2009-02-01
Hola ary.....:
Si no vas a cambiar de gráficas, simplemente cierra normalmante y muda el disco rígido a la otra mother.
Si cambias de gráficas, configurala antes de apagar a modo vesa en 800 x 600, para que inicie con cualquier tarjeta.
Averigua antes si la placa de red, si es nueva e integrada tiene soporte nativo o es necesario bajar algun driver, para no quedarte sin red.
Esos son los únicos problemas, gráficas y red ethernet y o wifi.
Saludos.
Gabriel.
**Solo doy soporte para Ubuntu** - *Existen muchas soluciones - Las equivocadas y la mia.*

---

### Post by biale on 2009-02-02
Estoy en un trámite parecido: además de lo anterior, suele haber problemas con el hardware de sonido (integrado)?   Gracias.

---

### Post by guisheca on 2009-02-02
Verás hasta donde se, se supone que los sistemas con núcleo linux, como ubuntu, levantan en forma dinámica todos los driver cada ver que bootean, es decir, cada ves que bootean se fijan donde están coriendo y van activando los drivers necesarios (si, así de sorprendente es el núcleo linux). Es por eso que se denomina a GNU/Linux un sistema "portable".
Ahora bien, el problema viene cuando hacen falta drivers de componentes que no están en el núcleo. Por ejemplo, si pasás de una gráfica nvidia a una ati, o pasas a algún otro componente que no tenga soporte por parte del núcleo, como las gráficas SiS.
Saludos.

---

