---
title: "[SOLVED] Driver para impresora Epson Stylus T23"
date: 2008-07-26
forum: Hardware
---

### Post by acdm86 on 2008-07-26
Hola, compre una impresora Stylus T23 y no la puedo hacer funcionar, la reconoce pero no anda, dice en el icono de la impresora "procesando" y no pasa nada, mande un correo al soporte de la impresora y me contestaron que no hacen drivers para linux, desde ya les agradezco y seria muy agradable para mi tener que dejar de usar xp a la hora de imprimir

---

### Post by ariel on 2008-07-29
> **acdm86 said:**
> Hola, compre una impresora Stylus T23 y no la puedo hacer funcionar, la reconoce pero no anda, dice en el icono de la impresora "procesando" y no pasa nada, mande un correo al soporte de la impresora y me contestaron que no hacen drivers para linux, desde ya les agradezco y seria muy agradable para mi tener que dejar de usar xp a la hora de imprimir

mi comentario no te va a servir para nada... pero si algun dia volvés a comprar una impresora/scanner, te recomiendo que sea HP. los pibes de hp escriben y mantienen su propio driver open source para linux desde hace años y el soporte es buenisimo. Todas las distros lo incluyen.

---

### Post by Aspergillus on 2008-07-30
mira...

aca encontre una pagina con los drivers para esa impresora, pero estan para OpenSuse, Mandriva y Fedora...lo que te propongo es lo siguiente

[http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do)

tenes que elegir la impresora en la lista que te aparece y hacer unos pasos en un formulario al final, en una parte dice que te deja elegir la distribucion por mas que elijas debian no hay drivers para debian, mi sugerencia es que una vez que te lleve a la pagina de descarga, bajes el archivo .tar.gz y lo compiles a un .deb, luego seguramente te deje instalarlo

a ver si tenes suerte

---

### Post by acdm86 on 2008-07-30
Gracias a todos, todavia no segui los consejos, esta bien lo de comprar HP por lo que me comentas, pero esta impresora es barata $180, y los cartuchos tambien lo son, es un tema que hay que tener en cuenta, bueno en cuanto llegue a casa me dedico a la impresora y comento como me fue, quiza me tome un tiempo, soy nuevo en Linux y los archivos tar.gz no favorecen mi humilde desempeño

---

### Post by acdm86 on 2008-07-31
Problema solucionado, Aspergillus segui tu consejo pero no alcanzo, entonces cambie la url de la impresora a "epson:/dev/usb/lp0 y elegi modelo de impresora cx 5600  cups + guteprint v5.0.2 simplified.Gracias Ariel y Aspergillus.

---

### Post by User21 on 2008-08-01
Si el tema fue solucionado, ponele** [SOLVED]** a hilo, desde las "Thread Tools". 
No solo le haces saber a la comunidad que lo solucionaste, sino que nos ahorras pasar por el post  a aquellos que aun intentan ayudarte.  Bienvenido al software libre.

---

