---
title: "Problema con la placa de video y con apt-get update"
date: 2009-04-24
forum: Hardware
---

### Post by ezesapo on 2009-04-24
Hola, que tal?
Hace mucho que no paso por aca.
La cuestion es que venia usando ubuntu 8.04 sin problemas en mi notebook.
Ayer decidi hacer una instalacion limpia del 9.04.
Instale el Compiz y no me funciona.
Voy a Sistema > Administracios > Controladores de hardware y no me aparece nada para instalar (no recuerdo si lo habia instalado asi la ultima vez:()
Y la verdad, no se como seguir..    si alguien me da una mano, le estare muy agradecido!
[I]
Y otra cosa. Cuando apt-get update me sale esto:
```
W: Error de GPG: http://ppa.launchpad.net jaunty Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 2ED6BB6042C24D89

```

Lei en una pagina que se resolvia si ejecutaba esto:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24
```

Pero no funciono.[/I]
[B]
Edit:[/B] Esto ultimo ya lo arregle, encontre un script que actualiza todas las claves GPG de Lanchpad para Ubuntu 8.04, 8.10 y 9.04. ([link]("http://obux.wordpress.com/2009/01/31/solucion-a-los-problemas-de-llaves-publicas-de-launchpad-error-de-gpg/"))

---

### Post by pablo.s on 2009-04-24
Lo que te pide es la clave pública
del PPA. Por lo general viene un
instructivo detallado de como
conseguir la clave en el mismo
PPA.
Compiz (dios mio) se activa desde
Sistema - Preferencias - Apariencia
y en la última solapa aparece
Defectos de escritorio, o efectos 
visuales.
Saludos.

---

### Post by ezesapo on 2009-04-24
> **pablo.s said:**
> Compiz (dios mio) se activa desde...

Disculpame si te jodio la pregunta. Si lo supiera hacer solo no consulto en el foro.
Tampoco soy nuevo en esto, hice eso y no me funciona, por eso necesito ayuda.

Cuando lo hago me aparece un cartel que dice "No se han podido activar los efectos de escritorio"

---

### Post by faktorqm on 2009-04-24
NAAAaaaaa no saltes que no hay charco.  no lo dijo con mala intención, lo dijo por que compiz es una cosa completamente accesoria come-recursos buena para nada (viste que bien que me porte hei? ;)) que seguro no le gusta ni le interesa al igual que a mi. Si al resto le gusta, todo bien, nos encanta que al resto le guste, pero jamás se lo recomendariamos a nadie. 

Con respecto al error, anda a aplicaciones -> accesorios -> terminal y escribi "glxinfo | grep direct" (sin comillas) y te deberia salir algo que diga

"direct rendering: yes" o te puede decir "no". postea el resultado. salu2!

---

### Post by ezesapo on 2009-04-24
Me aparece Direct rendering: Yes.

Eso es lo que no entiendo, si hago glxgears me aparecen las tuercas girando, todo.

Pero cuando voy  a Sistema > Preferencias > Apariencia > Efectos visuales  y elijo Extras, me aparece que "No se han podido activar los efectos de escritorio".

Puede ser por el driver de la placa?

Alguna configuracion del xorg?

---

### Post by pablo.s on 2009-04-24
Ezesapo: no lo tomés a mal, es
obvio que te estoy ayudando, pero
alguna opinioncita personal, asi
como para darle un aspecto humano
al tema, se me puede escapar, si?

Una pista: ejecutà Compiz (alabado
sea el todopoderoso) desde una
terminal y fijate que error puntual
te devuelve.

Saludos y a no enojarse eh!

PD: Faktor, vos si que me entendès...

---

### Post by ezesapo on 2009-04-24
Yo se que todo se hace con la mejor onda.
Sino, ni perderian el tiempo en responder.

Tampoco lo quise decir mal, ahora que lo releo suena un poco agresivo o a la defensiva.
No es la intencion. Porque ademas sino no me ayudarian (yo no ayudaria a alguien que me responde mal) :P

Cuando ejecuto el comando copiz desde un terminal, me sale esto:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

```

Gracias por la ayuda

---

### Post by pablo.s on 2009-04-24
> **ezesapo said:**
> Cuando ejecuto el comando copiz desde un terminal, me sale esto:
[code]Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 


Ahi te está diciendo que tu tarjeta de
video se encuentra "blacklisted" o mejor
dicho en castellano, está en la lista negra
seguramente por alguna incompatibilidad.
Pero no desesperes, hay alguna forma
de arreglarlo. Poné en un mensaje el
modelo de tu tarjeta y veamos como sigue.

---

### Post by ezesapo on 2009-04-24
```
~$ lspci |grep VGA 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

Tengo una DELL Inspiron 1520 (por si sirve de algo).

---

### Post by pablo.s on 2009-04-24
Tu problema ya está identificado,
justo hay otro muchacho que tiene
lo mismo. Le pasé una solución
que estaba en este mismo foro.

El Thread es [este]("http://ubuntuforums.org/showthread.php?t=1135606"). A ver si ayuda!

---

### Post by ezesapo on 2009-04-24
Me vino barbaro.

Gracias!

---

### Post by pablo.s on 2009-04-24
Lo solucionaste?

---

### Post by ezesapo on 2009-04-24
Sisi, probe poner: SKIP_CHECKS=yes compiz --replace
en la consola y funciono. Automaticamente volvio la magia del cubo :cool: y las ventanas que se sacuden cuando las muevo jaja

Ahora lo tengo que hacer script para que lo corra cada vez que prendo la maquina y listo.

Gracias por la ayuda

---

