---
title: "[SOLUCIONADO] lexmark x1185 en ubuntu 9.04???"
date: 2009-07-28
forum: Hardware
---

### Post by danny.woodstock on 2009-07-28
este... bueno.. recuerdo que cuando usaba ubuntu 8.04 para poder exar a andar esta multifuncional (lexmark x1185) tenia que hacer instalando los dirves de una lexamr z600.. o algo asi.. la cosa esque tenia que hacer un webeo para que ubuntu recnociera y funcionara la impesora... me gustaria saber si ahora con la version 9.04 tendre que hacer lo mismo???

---

### Post by robertor on 2009-08-08
Hola!
en [0] encontrarás una lista con los drivers e impresoras soportadas. Esto es genérico para CUPS, por ende debiera funcionar sin mayores problemas en Ubuntu.
Saludos!
Roberto

[0] [http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting)

---

### Post by cahv on 2009-08-11
:P s[FONT=Arial][SIZE=3]i no lo logras por el sistema, prueba en esta pagina, añ parecer la configura en forma virtual pero te la deja ok te aparecera un aviso que te pedira ingresar usuario y password pero debes ingresar las mismas que usas para ingresar a tu equipo

[http://localhost:631/](http://localhost:631/)

tambien te pedira el archivo *.ppd que se encuetra en  /usr/share/cups/model

espero te sirva[/SIZE][/FONT]

---

### Post by Carlos C on 2009-08-12
> **cahv said:**
> :P s[FONT=Arial][SIZE=3]i no lo logras por el sistema, prueba en esta pagina, añ parecer la configura en forma virtual pero te la deja ok te aparecera un aviso que te pedira ingresar usuario y password pero debes ingresar las mismas que usas para ingresar a tu equipo

[http://localhost:631/](http://localhost:631/)

tambien te pedira el archivo *.ppd que se encuetra en  /usr/share/cups/model

espero te sirva[/SIZE][/FONT]
Solo quiero señalar que es necesario tener instalado el paquete "cups" si quieres usar esta modalidad de configuración. Puede que venga instalado por defecto, no lo sé.
Saludos.

---

### Post by AlanAbbott on 2009-08-21
[http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting) NO HAY UN SOTO DE LEXMARK X1185 aqui,

---

### Post by Carlos C on 2009-08-21
Estas impresoras necesitan el driver z600. Para instalarlo puedes mirar en Ubuntu Documentation:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)

Saludos.

---

### Post by danny.woodstock on 2009-08-21
hola... gracias por la respuetas...
segui el mismo tutorial que utilize para ubuntu 8.04 y me funciono a la perfeccion :)
asique ahroa tngo funcionnado mi impresora...
:)
asike problema solucionado :)
gracias :)

---

### Post by Carlos C on 2009-08-22
> **danny.woodstock said:**
> hola... gracias por la respuetas...
segui el mismo tutorial que utilize para ubuntu 8.04 y me funciono a la perfeccion :)
asique ahroa tngo funcionnado mi impresora...
:)
asike problema solucionado :)
gracias :)

Por favor pon el enlace de ese tutorial, así quienes tengan el mismo problema podrán resolverlo.
Saludos.

---

### Post by AlanAbbott on 2009-08-24
Me queda colgado el SCANEO, 
encontre [http://manpages.ubuntu.com/manpages/jaunty/man5/sane-lexmark.5.html](http://manpages.ubuntu.com/manpages/jaunty/man5/sane-lexmark.5.html) 
dice que con "sane-backends 1.0.19-23ubuntu7 (source) in ubuntu jaunty"
anda la X1185 completo 
¿Como lo instalo?
how install sane-lexmark - SANE backend for Lexmark

---

### Post by danny.woodstock on 2009-08-24
no encontre el tutorial original!...
pero aqui esta otro que tambien sirve!
[http://linuxbot.wordpress.com/2009/04/27/instalando-impresora-lexmark-x1100-series-en-ubuntu/](http://linuxbot.wordpress.com/2009/04/27/instalando-impresora-lexmark-x1100-series-en-ubuntu/)

---

### Post by danny.woodstock on 2009-08-24
> **AlanAbbott said:**
> Me queda colgado el SCANEO, 
encontre [http://manpages.ubuntu.com/manpages/jaunty/man5/sane-lexmark.5.html](http://manpages.ubuntu.com/manpages/jaunty/man5/sane-lexmark.5.html) 
dice que con "sane-backends 1.0.19-23ubuntu7 (source) in ubuntu jaunty"
anda la X1185 completo 
¿Como lo instalo?
how install sane-lexmark - SANE backend for Lexmark

con el escaner nunca he tenido ningun problema... tanto en ubuntu 8.04, 8.10 y ahora la 9.04
xsane me reconoce inmediatamente el escaner de la multifuncional
indistintamente de lo que es impresion
xsane viene instalado ubutntu buscalo en
Aplicaciones/Gráficos/Programa de escaneo de imágenes XSane

---

