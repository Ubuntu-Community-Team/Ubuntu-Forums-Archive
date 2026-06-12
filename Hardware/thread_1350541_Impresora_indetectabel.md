---
title: "Impresora indetectabel"
date: 2009-12-09
forum: Hardware
---

### Post by ponchomx on 2009-12-09
Hola, nuevamente solicitando vuestra ayuda. Hace dos días, después de la última actualización de Ubuntu 9.10, mis impresoras, una lexmark E210 y una Epson T20 ya no aparecen detectadas en mi ubuntu, al querer conectarla como nueva en configuración de impresoras me da el siguiente error:

> **Error del servidor Cups**
Se ha producido un error en CUPS durante la operación: «httpConnectionEncrypt failed».

Desde consola al querere resetear el servidor cups:

> sudo service cups restart

Me arroja:

> * Restarting Common Unix Printing System: cupsd
cupsd: Child exited on signal 15!                  [**fail**]
                                                                 

Gracias y Salu2

---

### Post by juancarlospaco on 2009-12-09
Tenes todos los updates?

Las Lexmark no son muy amigas de nada diferente a Windows.

---

### Post by ponchomx on 2009-12-09
> **juancarlospaco said:**
> Tenes todos los updates?

Las Lexmark no son muy amigas de nada diferente a Windows.

En los años que llevo usando ubuntu no se me había presentado este problema, pareciera que no existen las impresoras. Con la lexmark siempre la he usado en linux, desde hace cinco años, ni idea de como funcione en windows. ;)

---

### Post by ponchomx on 2009-12-09
He encontrado la solución, en el foro de ingles.

Resulta que la última actualización se realizo hace dos días, yo me encontraba en el trabajo y no pudo estar al pendiente mi maquina, esta también realizaba algunas descargas de archivos de internet y la partición se lleno, tengo la partición / (raiz) y /home juntas, lo cula termino llenando la partición raíz, despues de batallar un poco, el sistema ya no queria arrancar en moido grafico hasta que huve de vaciar un poco el disco duro, comentan que se "borra" o más bien queda en blanco un archivo de la configuración de **cups**, pero como todo en linux por lo general se guarda copia el mismo sistema, el asunto es sustituirlo:

> sudo mv /etc/cups/cupsd.conf.O /etc/cups/cupsd.conf

Despues reiniciar el servidor **cups**:

> sudo service cups restart 

Y listo, las impresoras vuelven a ser reconocidas y funcionales.

Salu2

---

### Post by ponchomx on 2009-12-09
He encontrado la solución, en el foro de ingles.

Resulta que la última actualización se realizo hace dos días, yo me encontraba en el trabajo y no pudo estar al pendiente mi maquina, esta también realizaba algunas descargas de archivos de internet y la partición se lleno, tengo la partición / (raiz) y /home juntas, lo cula termino llenando la partición raíz, despues de batallar un poco, el sistema ya no queria arrancar en moido grafico hasta que huve de vaciar un poco el disco duro, comentan que se "borra" o más bien queda en blanco un archivo de la configuración de **cups**, pero como todo en linux por lo general se guarda copia el mismo sistema, el asunto es sustituirlo:

> sudo mv /etc/cups/cupsd.conf.O /etc/cups/cupsd.conf

Despues reiniciar el servidor **cups**:

> sudo service cups restart 

Y listo, las impresoras vuelven a ser reconocidas y funcionales.

Salu2

---

### Post by jgoyesa on 2011-09-26
También se puede considerar lo siguiente: 
Renombrar los archivos 
/etc/cups/ssl/server.crt
/etc/cups/ssl/server.key

Renombrar con el comando:
mv /etc/cups/ssl/server.crt   /etc/cups/ssl/server.crt.old
mv /etc/cups/ssl/server.key  /etc/cups/ssl/server.key.old

Reinciar el servicio
/etc/ini.d/cups restart

Esto debe resolver el problema.

---

