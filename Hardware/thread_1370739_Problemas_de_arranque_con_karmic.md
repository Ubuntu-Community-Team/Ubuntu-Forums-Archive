---
title: "Problemas de arranque con karmic"
date: 2010-01-02
forum: Hardware
---

### Post by RafaelG on 2010-01-02
Bueno estuve utilizando Python en Karmic y cuando volvi a arrancar mi OS se queda en Negro y cuando voy a Modo Recovery me aparece la siguiente pantalla que dejo como attached, creo que despues de haber utilizado Python tuve que haber danado algo en el arranque estuve googliando pero no consegui algo al respecto, agradeciendo antemano cualquier ayuda.

Saludos Grandes.

---

### Post by RafaelG on 2010-01-02
Bueno Googliando consegui una pagina con varias Soluciones a mi problema, la primera Solucion mencionada fue la que funciono para mi:
[COLOR=Blue][B][U]

Error Initramfs en Ubuntu.[/U]
[/B][/COLOR]***[B][I][COLOR=#ff0000]BusyBox v1.1.3 (Ubuntu 1:1.1.3-5ubuntu7) Built-in Shell (ash)[/COLOR]***[/I][/B] 
***[B][I][COLOR=#ff0000]Enter &#8220;help&#8221; for a list of built-in commands[/COLOR]***[/I][/B] [B][I][COLOR=#ff0000][B][I]
(initramfs)[/I][/B][/COLOR][/I][/B]
[COLOR=Blue][COLOR=Black][COLOR=Blue][B][U]

Solucion[/U][/B][/COLOR]
Abrir desde LiveCD a modo de prueba, seguidamente abrir una Consola con permiso de root y acceder a esta ruta  [/COLOR][/COLOR][COLOR=#ff0000]&#8220;[/COLOR]**[COLOR=#ff0000]/boot/grub/menu.lst &#8220;[/COLOR]**. una ves hay ubicar nuestro Kernel,  es algo como esto [COLOR=#ff0000]**Kernel / boot/ vmlinuz-2.6.XX-X**[/COLOR], vamos hasta el final hasta donde dice: [COLOR=#ff0000]**[COLOR=#000000]&#8220;[/COLOR]**[/COLOR]**ro quiet splash&#8221;**y agregamos**[COLOR=Black] [B]"**[/COLOR][/B][COLOR=Black]**pci=nomsi"**[/COLOR], guardamos y reiniciamos de modo normal.


Link Original de la Solucion
[http://elendill.wordpress.com/2009/04/12/error-con-initramfs-ubuntu-804/](http://elendill.wordpress.com/2009/04/12/error-con-initramfs-ubuntu-804/)
[COLOR=Black] 

[/COLOR]Saludos Grandes.

---

### Post by moreback on 2010-01-04
No creo que Python cambie algo en los drivers de los discos, pero veo que el problema es que no te reconoció el disco raíz y por eso no pudo encontrar el programa /sbin/init (por eso te sale el busybox).

Esto podría ser por que apagaste a la mala el pc y eso daño tus archivos (incluso el recovery), tal como muestran las 3 primeras líneas.

Saludos.

---

