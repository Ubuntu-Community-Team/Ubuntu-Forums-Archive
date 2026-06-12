---
title: "moblin no deja entrar a ubuntu 10.04"
date: 2010-05-02
forum: Instalación y Actualización
---

### Post by Fraknet on 2010-05-02
Saludos a todos, soy nuevo en esto, explico lo que me sucedio:

Pasa que tengo un Netbook (Packard Bell Dot_SR.CL/003) con windows 7
Decidi abandonar windows en pro de linux a traves de ubuntu y a la vez probar moblin, las instalaciones quedaron sin problemas, todo fluido, primero ubuntu, luego moblin.
Pero moblin instalo un grub que no reconoce el acceso a ubuntu, y es mas, si intento arrancar otro live cd (win xp incluido) este no alcanza a ser reconocido por el bios y aparece el grub, aun estando todo configurado. 
Si alguien sabe que hacer favor ayudeme, ya que necesito borrar moblin y solo dejar ubuntu, ya que hasta ahora la unica solucion que tengo es formatear el hdd externamente y no tengo como hacerlo.

---

### Post by Carlos C on 2010-05-02
Probaste editar el GRUB?

[http://www.guia-ubuntu.org/index.php?title=GRUB](http://www.guia-ubuntu.org/index.php?title=GRUB)

---

### Post by Fraknet on 2010-05-02
> **Carlos C said:**
> Probaste editar el GRUB?

[http://www.guia-ubuntu.org/index.php?title=GRUB](http://www.guia-ubuntu.org/index.php?title=GRUB)

Si, ya lo intente, pero no logre resultados, solo me queda el formateo externo

---

### Post by Carlos C on 2010-05-02
Si nos explicas mejor lo que hiciste podemos tratar de ayudarte, es decir, qué cambios hiciste en el grub y cómo. 
En caso de que prefieras formatear (sigo creyendo que se puede arreglar el grub) puedes intentar hacerlo con un LiveCD de Ubuntu. Para eso debes cambiar el orden de booteo desde la BIOS del equipo. Cómo entrar a la bios depende de cada equipo, en general es posible ver alguna indicación durante un par de segundos al prender el computador.

---

### Post by Fraknet on 2010-05-02
Si, el bios esta todo configurado como corresponde, pero mi lector de cd externo no alcanza a ser reconocido cuando el grub ya aparece en pantalla.

Sobre el grub, pedi ayuda a un amigo que es entendido en los temas de linux, me ayudo a editar el archivo del grub para indicar la particion extacta de la ubicacion de ubuntu, aun asi no logre nada, hasta ahora solo me quedaria formatearlo por fuera

---

