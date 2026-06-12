---
title: "Problema Resolución de la Pantalla"
date: 2008-11-26
forum: Hardware
---

### Post by --Lutari-- on 2008-11-26
Les cuento Tenia la Resolución en 1024x768 al apagar la computadora y volver a dia siguiente me encuentro con la pantalla de 800x600. Dije bueno lo cambiare pero no tengo la opción la mas alta es 800x600 y yo antes tenia de 1024x768. Alguien que me diga por favor como cambiar.

---

### Post by faktorqm on 2008-11-26
Hola, probaste con

```
sudo displayconfig-gtk
```

si eso no te sirve, por favor postea la salida de 

```
cat /etc/X11/xorg.conf
```

Gracias y salu2!

---

### Post by guillermolisi on 2008-11-26
> **--Lutari-- said:**
> Les cuento Tenia la Resolución en 1024x768 al apagar la computadora y volver a dia siguiente me encuentro con la pantalla de 800x600. Dije bueno lo cambiare pero no tengo la opción la mas alta es 800x600 y yo antes tenia de 1024x768. Alguien que me diga por favor como cambiar.

Estas usando que version de Ubuntu, la 8.10 o una anterior. Cual ?
Que placa de video estas usando ?
Podes mostrar la salida del comando lspci ?

---

