---
title: "Problemas con dpkg: no puedo instalar ni actualizar software"
date: 2009-06-26
forum: Instalación y Actualización
---

### Post by El Flauta on 2009-06-26
Hola

Tengo un problema de hace ya un tiempecillo en mi UbuntuStudio 9.04, y es que no me deja actualizar. Me explico:

Cada vez que intento actualizar mi sistema o instalar nuevo software, me aparece el siguiente aviso:
> E: dpkg se interrumpió, debe ejecutar manualmente <<sudo dpkg --configure -a>> para corregir el problema.
E: _cache->open() failed, please report.


Luego que escribo en consola *sudo dpkg --configure -a*, me aparece el siguiente mensaje:
> Configurando openoffice.org-emailmerge (1:3.0.1-9ubuntu3) ...
Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py


Luego la consola es capaz de quedarse así pegada por horas, quizá días... eso cuando no termina congelándome el sistema al cabo de 10 minutos.

Como me da lo mismo si OpenOffice está actualizado o no, quise probar incluso desinstalándolo para luego reinstalarlo... sin embargo, tampoco es posible, pues me sale el mismo error tanto en el gestor de actualizaciones como en el "Añadir y Quitar"... ¡incluso en Synaptic, cuando intento abrirlo!

De hace un año más menos que las versiones de Ubuntu me han salido realmente infestadas de bugs, pero ya este ha resultado ser muy limitante, ya que no puedo ni instalar ni desinstalar nada nuevo... ¿qué puedo hacer?

---

### Post by Carlos C on 2009-06-26
No uso Ubuntu Studio, pero al menos a mí Ubuntu no me ha dado problemas. De hecho Jaunty hasta ahora va invicto, por primera vez identificó todo sin tener que modificar nada.

Respecto al problema que tienes, por favor escribe en el terminal:
```
sudo dpkg -C
```
Eso debiera darte alguna pista de cómo solucionar el problema. Si no puedes resolverlo de un modo más elegante entonces puedes escribir en el terminal:
```
sudo dpkg -r --force-remove-reinstreq openoffice.org-emailmerge
```
Eso debiera eliminar el paquete a la fuerza, lo que te permitirá volver a instalarlo. Pero yo lo haría como última opción.
Saludos.

---

### Post by El Flauta on 2009-06-26
Gracias por tu respuesta, Carlos. He probado a tipear en consola lo que me has dicho, y esta ha sido la salida:

```
$ sudo dpkg -C
Los siguientes paquetes han sido desempaquetados pero no configurados aún.
Deben ser configurados mediante dpkg --configure o la opción `configure'
en dselect para que funcionen:
 openoffice.org       full-featured office productivity suite
 openoffice.org-emailmerge full-featured office productivity suite -- email mai
 libwps-0.1-1         Works text file format import filter library (shared libr
 libcolamd-3.2.0      column approximate minimum degree ordering library for sp
 openoffice.org-java-common full-featured office productivity suite -- arch-ind
 openoffice.org-impress full-featured office productivity suite -- presentation
 openoffice.org-officebean full-featured office productivity suite -- Java bean
 ttf-liberation       Free fonts with the same metrics as Times, Arial and Cour
 openoffice.org-base  full-featured office productivity suite -- database
 libservlet2.4-java   Servlet 2.4 and JSP 2.0 Java library.
 openoffice.org-math  full-featured office productivity suite -- equation edito
 openoffice.org-draw  full-featured office productivity suite -- drawing
 libhsqldb-java       Java SQL database engine
 libwpg-0.1-1         WordPerfect graphics import/convert library (shared libra
 openoffice.org-filter-mobiledev full-featured office productivity suite -- mob
 openoffice.org-writer2latex Writer/Calc to LaTeX/XHTML converter extension for
 openoffice.org-calc  full-featured office productivity suite -- spreadsheet
 openoffice.org-filter-binfilter full-featured office productivity suite -- leg
 lp-solve             Solve (mixed integer) linear programming problems
 openoffice.org-report-builder-bin OpenOffice.org extension for building databa
 openoffice.org-base-core full-featured office productivity suite -- shared lib
 openoffice.org-writer full-featured office productivity suite -- word processo
 libwpd8c2a           Library for handling WordPerfect documents (shared librar
```

*(Sale así tal cual, recortado)*

Intenté instalar dselect desde consola, pero bueno... como siempre, se puso a intentar configurar el emailemerge.py, así que quedé más o menos igual :-\"

Quizá me convenga más la última opción de la que me hablas... Como decía, las últimas versiones de Ubuntu *(Ubuntu "normal" o UbuntuStudio, me pasa igual)* me han funcionado muy, muy mal en mi computador. Por ejemplo, ahora tengo aceleración 3D a medias, pues si activo Compiz el sistema se congela *(antes estuve 1 año sin aceleración 3D, con la misma tarjeta que sí funcionaba en versiones anteriores)*. A veces se congela de la nada, lo que ha hecho que de Abril a la fecha, las veces que he podido apagarlo de forma normal han sido sólamente 2. El resto de las veces he tenido que apagarlo a la mala no más. En fin... ya no me interesa vivir esclavo de la eterna configuración de mi sistema, pero aún así ahora necesito reparar este cacho :P

---

### Post by Carlos C on 2009-06-26
Ok, entiendo que ya intentaste hacer un "sudo dpkg --configure -a", tampoco pudiste desinstalarlo con Synaptic. por lo tanto probemos lo drástico:
```
sudo dpkg -r --force-remove-reinstreq openoffice.org
```
Con eso se desinstala a la fuerza y puede que algunos paquetes queden en el sistema, pero serán ignorados por dpkg, olvidará que están ahí, así que podrás instalar nuevamente como si nada hubiera pasado.

---

### Post by leonpuro on 2009-08-09
¡Hey! Mi nombre es Leonardo Puerta Rodríguez, y les quiero agradecer. He tenido el mismo problema con Ubuntu Studio 9.04 (Problema que, como ya dijo Carlos, no sucede en Ubuntu, y como ya comprobé, tampoco en Kubuntu. No sabía qué hacer ante esto, porque soy muy nuevo en Ubuntu Studio (Que, por cierto, yo diría que tengo Kubuntu Studio, porque a Ubuntu Studio le instalé KDE, y me gusta más así), y como no había visto este tema, opté por reinstalar no sé cuántas veces el sistema operativo. Pero así ya me quito un dolor de cabeza.

Dios los bendiga.

---

### Post by asterix77 on 2010-01-13
bb

---

### Post by CdK1 on 2010-01-14
Cuando un package me da muchos problemas a la hora de instalar, etc, prefiero:

o usar:

apt-get -f install 
dpkg —configure -a
for i in $(dpkg —get-selections | grep -v deinstall | awk ‘{print $1}’); do apt-get install -y —reinstall $i; don

o lo más fácil, ir directamente a:

Caturra:/# cd var/lib/dpkg/info/
Caturra:/var/lib/dpkg/info# 

encontrar el package y borrar el .postinst, también puedes editarlo etc, pero en lo personal encuentro más fácil borrarlo y usar apt-get nuevamente...

---

### Post by Carlos C on 2010-01-14
> **asterix77 said:**
> bb

Disculpa, ¿cuál sería la razón de revivir un thread tan antiguo? No me queda claro.

Saludos.

---

### Post by CdK1 on 2010-01-14
Mmm a quién le preguntas?

---

### Post by asterix77 on 2010-01-14
Disculpas Carlos

Es solo que me equivoqué en postear en el lugar adecuado un tema. Tengo la costumbre de navegar abriendo varias pestañas. No encontré como borrar el post.

Saludos

---

### Post by CdK1 on 2010-01-14
Solucionaste el problema?

---

### Post by Carlos C on 2010-01-15
La persona que preguntó lo hizo en junio de 2009. asterix77 se equivocó y publicó en este thread sin querer. Para terminar con la confusión lo cierro.

Saludos.

---

