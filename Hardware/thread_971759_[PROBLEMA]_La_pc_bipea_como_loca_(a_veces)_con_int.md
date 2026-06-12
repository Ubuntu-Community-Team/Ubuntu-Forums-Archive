---
title: "[PROBLEMA] La pc bipea como loca (a veces) con intrepid ibex"
date: 2008-11-05
forum: Hardware
---

### Post by Cripton on 2008-11-05
Es raro, pero en la carga del SO, empieza a bipear (hacer muchos beeps) el mother como si estuviera presionada alguna tecla del teclado, pero lo desconecté y pasa lo mismo..

tengo configurada la carga del kernel sin el "quiet", para ver que está haciendo en la carga, y empieza a hacer eso luego de colgarse medio segundo en algo que tiene que ver con ACPI, con hardy no me pasaba, lo más raro es que pasa aveces... aveces la prendo y no pasa nada, a veces la reinicio y sigue haciéndolo, a veces la reinicio y deja de hacerlo, ni idea

---

### Post by faktorqm on 2008-11-05
Si el quiet o con el nosplash? Yo tengo entendido que para ver la carga es agregandole nosplash, no sacando el quiet. Salu2!

---

### Post by hictio on 2008-11-05
Otra cosa que podes hacer para ver todo el proceso de boot, es deshabilitar el login grafico, asi hasta el minuto final ves que esta pasando.
(Cuando termina de bootear, te loggeas normalmente con tu usuario y passwd, y arrancas X Window/ Gnome, tipeando 'starx' en el prompt)
Yo [aca](http://oesediez.blogspot.com/2008/09/ubuntu-high-resolution-console.html) puse instrucciones para hacer eso, y ademas, subir la resolucion y cambiar la fuente de la consola.
Son para 8.04, todavia no pude probarlo en 8.10. pero el comando para apagar el login grafico es el mismo, despues lo volves a habiltar si lo queres.

---

### Post by Cripton on 2008-11-05
nono, si le sacás el quiet te muestra lo que hace durante la carga, el nosplash es para lo "pre"

igual ese no es mi problema, se como poner los logins gráficos y deshabilitarlos, el tema es con eso del bipeo, que debe estar haciendo algo indebido con la administración de energía..

faqtoqm, vos eras de ingeniería de la uba no?? colega!

---

### Post by erdosain9 on 2008-12-17
Mirá yo no soy de los especialistas (de hecho soy novato... y ahí me quedé)... en qué momento bipea tu máquina... si es mientras esta en la parte del boot, ni lo dudes que es algo del hard.... (me ha pasado).

Saludos.

---

### Post by erdosain9 on 2008-12-17
Bueno listo... hay que leer mejor: decís que es durante la carga del SO.....
Bue. 
Saludos nuevamente

---

