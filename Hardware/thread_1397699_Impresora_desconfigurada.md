---
title: "Impresora desconfigurada?"
date: 2010-02-03
forum: Hardware
---

### Post by as1590 on 2010-02-03
Hola,

Uso ubuntu (garza robusta)en mi viejo pc (el único que he tenido..) y una impresora también vieja (canon bjc-2000).
El problema: Uso ubuntu desde hace cási ya 1 año, y siempre he podido imprimir "de perillas", pero desde hace un tiempo a ésta parte creo que la impresora se ha desconfigurado, puesto que, aunque suene redundante, ya no imprime, es decir, a veces imprime entre líneas cortadas, a veces un parrafo que otro, otras veces derechamente no imprime, y otras veces hace un ruido... y obviamente sin imprimir. (y si preguntan por la tinta... si tiene tinta!)

La cosa es que ésta misma impresora funciona perfectamente en windows xp (en el pc, tengo 2 particiones, una con winxp y otra con ubuntu)... por lo que pienso que el problema pueden ser los drivers o no?, la cosa es que he intentado reinstalarla en ubuntu de varias formas (vía menu de sistema, impresora, agregar nueva impresora...o vía CUPS "*Common UNIX Printing System*" creo que se llama y que se hace pormedio del navegador en la pagina [http://localhost:631/](http://localhost:631/) ) y en ninguna he podido solucionar el problema

alguien me puede ayudar?

Saludos.-

---

### Post by Carlos C on 2010-02-04
¿Esto te pasa con todos los programas o con alguno en especial?

---

### Post by as1590 on 2010-02-04
> **Carlos C said:**
> ¿Esto te pasa con todos los programas o con alguno en especial?

con todos los programas (open office, abiword, firefox, chrome, etc...)

---

### Post by Carlos C on 2010-02-08
Tendrías que ver si estás usando el driver gutenprint, que es el recomendado para ese modelo:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-2000](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-2000)

Sé que esos modelos en ocasiones deben ser reseteados para que los niveles de tinta se detecten correctamente, pero por lo que dices intenta imprimir, no se bloquea, y puedes trabajar sin problemas en windows.

Verifica que no sea un problema de driver, en el enlace que añado es posible descargar el paquete deb.

---

### Post by as1590 on 2010-02-08
Gracias.... pero...
mmm ... y siendo yo un novato en esto del linux...
en ésa página hay varios "paquetes deb":
 "*x86 32 bit (RPM for LSB 3.1), x86 32 bit (DEB for LSB 3.1), x86 32 bit (RPM for LSB 3.2), x86 32 bit (DEB for LSB 3.2)...*"

y hay varios para 32 bits... cual elijo? ... y como lo instalo?

tomando en cuenta esto de que soy novato en linux...

Saludos.-

---

### Post by Carlos C on 2010-02-08
RPM son paquetes para red hat y aquellas distribuciones basadas o afines con red hat. Lo que necesitas es un paquete deb. Te sugiero que pruebes con este paquete:

[http://www.linuxprinting.org/download/printdriver/debian/dists/lsb3.2/gutenprint/binary-i386/openprinting-gutenprint_5.2.4-1lsb3.2_i386.deb](http://www.linuxprinting.org/download/printdriver/debian/dists/lsb3.2/gutenprint/binary-i386/openprinting-gutenprint_5.2.4-1lsb3.2_i386.deb)

Saludos.

---

### Post by as1590 on 2010-02-09
El problema persiste...
instalé el paquete señalado
luego instalé nuevamente la impresora... pero el problema persiste...
ahora intento imprimir una pagina (1 plana para ser exactos) y la imprime en partes... lo que debería ser 1 plana, al final se termina imprimiendode forma entrecortada (entrecorta los parrafos) como en 4 o 5 planas...
:cry:

---

