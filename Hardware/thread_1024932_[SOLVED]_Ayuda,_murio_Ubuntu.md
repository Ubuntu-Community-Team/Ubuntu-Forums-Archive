---
title: "[SOLVED] Ayuda, murio Ubuntu"
date: 2008-12-29
forum: Hardware
---

### Post by Applelnx on 2008-12-29
Gente, estaba usando Ubuntu tranquilamente. Decidi sacar los efectos visuales y reiniciar para probar la placa de tv. Cuando reinicie Ubuntu no arranco nunca mas. En el primer intento me dijo que faltaba un archivo para el boot. Reinicie y cargaba todo hasta antes de la pantalla de login. En ese momento se apaga la pantalla, se queda en negro. Probe con el modo de recuperacion con un par de opciones (reparar paquetes y uno mas). Probe desde el live cd pero no me arranca ni el live cd. No se que hacer, reinstalo? Se agradece todo tipo de ayuda :confused:

---

### Post by faktorqm on 2008-12-29
Hola, si podes entra en el modo recuperacion, eso te deja en un consola de root, y de ahi podes probar

```
sudo dpkg-reconfigure xserver-xorg
```

Si el problema es la parte grafica.... que segun lo que decis parece ser eso. Salu2!

---

### Post by Applelnx on 2008-12-29
No se de donde sacaste esa linea de codigo biblica y no se que acabo de hacer pero funciono. Mil gracias :D

PD: me anote esta linea en la mano solo por las dudas :P

---

### Post by faktorqm on 2008-12-29
Figura en el encabezado del archivo /etc/X11/xorg.conf 
Me alegro muchisimo de que te haya servido. Salu2!!!

---

### Post by Applelnx on 2008-12-29
Se podria decir que funciono provisoriamente, cuando reinicie volvio a pasar lo mismo :(

Otras 2 cositas al margen por si saben:

1) cuando apago la maquina me dice "checking battery state" y se queda colgado, tengo que poner ctrl + alt + del para sacarlo.

2) sin querer elimine el boton de apagar, lo agregue de nuevo pero solo tiene la opcion de cambiar de usuario, alguien sabe como volverlo a la normalidad?

---

### Post by Applelnx on 2008-12-30
Me sigue pasando lo mismo, solo puedo iniciar cuando reconfiguro con esa linea. Que hago? Reinstalo todo? Ma paso de nuevo al 8.04? :confused:

EDIT: Todo funciona bien si arranco desde un kernel mas viejo, por ahora lo soluciono asi

---

### Post by totolinux on 2008-12-31
Hola amigo, no soy un experto pero hace 2 años que soy usuario y solucioné un problema similar editando la opción del grub y agregando al final  noapic  sin comillas. saludos

---

### Post by Applelnx on 2008-12-31
> **totolinux said:**
> Hola amigo, no soy un experto pero hace 2 años que soy usuario y solucioné un problema similar editando la opción del grub y agregando al final  noapic  sin comillas. saludos

Hola totolinux, gracias por responder. Me podrias decir como agrego eso porque la verdad que para cambiar las cosas del grub siempre use el "startup manager" que es totalmente grafico. Que archivo tengo que cambiar y en donde se ubica?

---

### Post by totolinux on 2008-12-31
creo que es asi, en el inicio pone escape (acá vas a ver las diferentes opciones y abajo estan las instrucciones que yo te indico a continuación) luego andá a las que querés editar y apretas letra E y en el final de toda la linea coloca noapic luego enter y luego letra B. mas o menos suerte.

---

### Post by totolinux on 2008-12-31
agrego: esto es para cambiar las opciones en forma temporal, par cambiar de forma permanente usa startup manager.

---

### Post by Applelnx on 2009-01-05
Totolinux, gracias por responder, la verdad que no tuve tiempo de ocuparme del problema y para cuando volvi ya habia actualizaciones que lo solucionaron. Gracias de todas maneras ;)

---

