---
title: "No puedo guardar configuración de Nvidia en el Xorg"
date: 2008-04-22
forum: Hardware
---

### Post by aregnando on 2008-04-22
Hola a todos: tengo el siguiente problema, instalé Envy para poner el driver de nvidia (gforce fx 5200)  en mi máquina, hasta ahí todo ok, el driver se instaló perfecto y todo anduvo de maravillas pero al fijarme en nvidia settings me aparece la resolución que utilizo siempre 1024 x 768, está bien, pero a 60 Hz, cosa que modifico a 85 Hz le doy aplicar y queda.
Al apagar la máquina vuelve a los 60 Hz. que se pone por defecto y al querer guardar la configuración en el xorg me sale:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Realmente me gustaría dejar seteado a 85 Hz. y no se como hacerlo, agradezco cualquier ayuda que me puedan dar.

---

### Post by InsektO on 2008-04-22
Para que nvidia-settings pueda escribir en /etc/X11... tenés que correrlo con sudo adelante.

Saludos!

---

### Post by guisheca on 2008-04-22
Espero esto te ayude:
[http://guisheca.wordpress.com/2007/12/29/mantener-la-configuracion-del-nvidia-settings/](http://guisheca.wordpress.com/2007/12/29/mantener-la-configuracion-del-nvidia-settings/)

---

### Post by faktorqm on 2008-04-23
Ir a sistema -> preferencias -> menu principal.
Buscas ahi el elemento del menu y le pones click derecho -> propiedades. En el cuadro que dice "comando" escribi "gksudo" antes del comando que aparezca. Cerra todo, y cuando ahora abras el nvidia settings te va a aparecer un hermoso cartel pidiendote la contraseña (el sudo grafico) y listo el pollo.
Salu2!!

---

### Post by aregnando on 2008-04-23
> **InsektO said:**
> Para que nvidia-settings pueda escribir en /etc/X11... tenés que correrlo con sudo adelante.

Saludos!

Muchas gracias a todos, InsektO tal como me dijiste abriendo el nvidia settings desde terminal y con sudo te permite hacer el cambio y queda guardado en el xorg, asi que puedo ponerlo como SOLVED.
Gracias.

---

### Post by edelcid on 2009-09-19
Me resultó fantástica la solución de [faktorqm]("http://ubuntuforums.org/member.php?u=101828"). Fue la más práctica ya que, al no saber qué comando escribir en el terminal, me fue más cómodo entrar por las Propiedades. Chas gracias. :P

---

