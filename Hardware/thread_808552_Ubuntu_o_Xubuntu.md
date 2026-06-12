---
title: "Ubuntu o Xubuntu?"
date: 2008-05-26
forum: Hardware
---

### Post by madelaki on 2008-05-26
Hardy Heron, idling, usa entre 300 y 400 MB de RAM. Con un par de aplicaciones corriendo al mismo tiempo llega a los 500 y los pasa sin problema. Mi procesador es un Athlon 64 3000+ a 1.8GHz, tengo 1GB de RAM DDR2 y una VGA low-end (Nvidia GeForce 7200 GS). Que hago? Me paso a Xubuntu? Estoy bastante nervioso con el tema del "lavado de cara" en Intrepid Ibex que dudo seriamente mejore la situacion. Cabe aclarar que no me molestaria para nada pasarme a XFCE, no descargue Ubuntu solo por Compiz Fusion, pero ustedes sabran mejor que me conviene: Dejar Ubuntu y rezar o pasarme a Xubuntu y olvidarme de los problemas de rendimiento.

---

### Post by Mister X on 2008-05-26
No se si entiendo bien tu problema, vos notas lenta ahora tu maquina con Ubuntu?
Si es por el tema del uso de memoria, con 1Gb debe funcionar sin problemas.
Cuando veas que el uso de RAM sube despues de abrir varias aplicaciones es porque tenes mucha memoria cacheada, cosa que está perfecto para optimizar al funcionamiento del sistema.

---

### Post by andy_91 on 2008-05-26
> **Mister X said:**
> No se si entiendo bien tu problema, vos notas lenta ahora tu maquina con Ubuntu?
Si es por el tema del uso de memoria, con 1Gb debe funcionar sin problemas.
Cuando veas que el uso de RAM sube despues de abrir varias aplicaciones es porque tenes mucha memoria cacheada, cosa que está perfecto para optimizar al funcionamiento del sistema.
no te entiendo tu problema pero con 1GB de ram deberia andar bien?

cuanto tenes de SWAP?

ahora si queres pasarte a Xfce tambien podes usar compiz (por ej en Linux mint xfce viene instalado por defecto)

nose cuanta memoria tiene tu procesador no se entiende bien esa parte, pero seguro ronda entre los 1.8GHz o mas

en mi punto de vista salvo por las transparencias del panel no hay nada que hagas con gnome que no hagas con Xfce

---

### Post by valucha on 2008-05-26
[COLOR="DarkOrchid"]Yo tengo una compu muy parecida a la tuya, y la verdad que Ubuntu vuela, y aveces cuando pongo algun screenlet para ver cuanta memoria tengo usada llega hasta el 50% pero anda volando.
Tenés que tener en cuenta que el manejo de la memoria y todo es diferente que en Windows o MAC.. por lo que solo pasate si no te gusta Gnome o sentís la compu no tan rápida como vos querés, pero no te guíes por la memoria ocupada, porque no es símbolo de bajo rendimiento.

(un ej, para que te des cuenta, la 1era vez que abris el firefox apenas  prendés la compu a mi me tarda 3 - 4 segundos, después de eso lo puedo cerrar y abrir cuanto quiera que siempre va a tardar menos de 1 segundo en abrirse)

Espero guiarte, saludos.[/COLOR]

---

### Post by madelaki on 2008-05-26
No tengo ningun problema, pero por lo que se este foro es general, no solo de soporte tecnico. En cuanto a si la noto lenta, idling no, para nada, pero soy de tener muchas aplicaciones abiertas al mismo tiempo y ahi si se nota un poco la perdida en velocidad de respuesta. Pero mi miedo mas importante es que cambie para peor con II. Por cierto, a ustedes les parece poco 500MB como promedio? Esta bien que tenga 1GB, pero todavia hay mucha gente que tiene menos.

---

### Post by AnRa on 2008-05-26
Xubuntu Hardy está bastante pulido, yo diría que vale la pena probarlo. De cualquier modo, siempre se puede volver hacia atrás. ;-)

---

### Post by margori on 2008-05-26
> **madelaki said:**
> No tengo ningun problema, pero por lo que se este foro es general, no solo de soporte tecnico. ... Por cierto, a ustedes les parece poco 500MB como promedio?

He puesto la mejor onda para intentar entenderte, pero no lo logro. Dices no tenés problemas con tu Ubuntu, cosa que es lógica con esa compu, pero que querés iniciar una charla de interés general, y la verdad es muy dificil entender para donde queres rumbear esta discución.

Me imagino que nos estas tratando decir que Ubuntu usa mucha memoria porque facilmente ocupa 500MB, y esta incinuano que la memoria utilizada debe siempre estar al menor valor posible. Ese pensamiento esta lejos de ser cierto. Memoria fisica no utilizada es memoria desperdiciada. Si está el recurso se usa. (Aunque es discutible es uso de memoria swap)

Por favor, aclaranos tus post. Gracias.

---

### Post by madelaki on 2008-05-26
Basicamente, quiero saber si me conviene seguir con Ubuntu o cambiar a Xubuntu.

---

### Post by guillermolisi on 2008-05-26
> **madelaki said:**
> Basicamente, quiero saber si me conviene seguir con Ubuntu o cambiar a Xubuntu.

La diferencia entre uno y otro "sabor" esta solamente en el escritorio grafico.

En el fondo vas a seguir con Ubuntu, sea HH o II, pero Ubuntu al fin de cuentas. Con las caracteristicas que te han mencionado antes: La memoria libre se usa como cache para mejorar la respuesta del sistema y evitar accesos al disco rigido, etc., etc.

Xubuntu se recomienda en maquinas que podrian clasificarse como bastante menos potentes que la tuya. Ejemplo PII, sin aceleracion grafica y alrededor de 256 Mb RAM, mega mas mega menos.

Podes probar los dos escritorios y despues decidir.

Y si dudas de que no te alcance para II, espera primero a que salgan las versiones alfa y beta (es que estamos recien en casi Junio :-)  )

---

### Post by madelaki on 2008-05-27
Tenes razon. Pasa que lei tanto sobre la nueva GUI y tan poco sobre otras novedades que tenia miedo de que Intrepid Ibex fuera el Vista de Ubuntu. Esperare a una Alfa importante o a la Beta.

---

### Post by kowal on 2008-05-27
> **madelaki said:**
> No tengo ningun problema, pero por lo que se este foro es general, no solo de soporte tecnico. En cuanto a si la noto lenta, idling no, para nada, pero soy de tener muchas aplicaciones abiertas al mismo tiempo y ahi si se nota un poco la perdida en velocidad de respuesta. Pero mi miedo mas importante es que cambie para peor con II. Por cierto, a ustedes les parece poco 500MB como promedio? Esta bien que tenga 1GB, pero todavia hay mucha gente que tiene menos.

Yo tengo la misma PC y es raro que pase los 500mb (igual aclaro que uso KDE en lugar de Gnome.. y Konqueror en lugar de Firefox)

Podés usar los dos escritorios a los que te referís (Gnome o XFCE) sin mayores problemas, como te decían arriba. Para instalar Xubuntu en Ubuntu basta con ingresar en la consola:

```
sudo aptitude install xubuntu-desktop
```

Saludos.

---

### Post by faktorqm on 2008-05-27
Yo tengo 512mb de ram ddr 400mhz, con un athlon xp 2600+ (barton) y una mother msi k7n2g-l. Uso ubuntu 8.04 y si bien tiene varias optimizaciones tipicas de mi ansiedad :P a mi me anda perfecto y puedo abrir muchas cosas y no pasa nada, es decir, tarda "lo normal" para una pc (para mi "vieja" ya...) con un sistema 2008!! o sea, a la mia le instalo xp y... si abro muchas cosas o se me cuelga, o se relentiza, o me agarra un virus y pierdo todo :lolflag: 
Pero ya se observo en repetidas oportunidades en este foro que ubuntu año 2008 va mas rapido o rinde mejor que xp año 2002, vista mejor ni hablar.... Mas alla de eso, otra conclusion que tambien sacamos, (lo podes probar vos mismo) es que, sin hacer nada, tenes ocupado 130mb de ram, abris el firefox, y seguis con 130mb.... hasta que no abris muchas cosas, ese consumo no se levanta, y llegamos a la conclusion de que ubuntu intenta una especie de pre-consumo de memoria, de modo que tiene programado que vas a abrir algo de antemano, o alguna tecnologia de ese estilo (hay muchas).
Otra cosa, en linux, sin hacer nada, tengo 160mb ocupados no mas, obviamente no uso compiz ni conky ni nada, pero no me parece tan descabellado que vos tengas 500mb ocupados teniendo 1gb.
Me parece que tendrias que buscar guias de optimizacion de ubuntu. Podes buscar readahead o redahead, no recuerdo. y bueno, la guia para compilar el kernel vamos a ver si la hacemos. Salu2!

---

### Post by margori on 2008-05-27
> **madelaki said:**
> Tenes razon. Pasa que lei tanto sobre la nueva GUI y tan poco sobre otras novedades que tenia miedo de que Intrepid Ibex fuera el Vista de Ubuntu. Esperare a una Alfa importante o a la Beta.

Veo muy dificil que Intrepid Ibex pueda llegar a ser el "Vista de Ubuntu". Creo que los desarrolladores saben muy bien que sus clientes quieren que de version a version sean parecidos requerimientos.

Por otro lado, podrías citar los lugares donde leíste eso y así sacar entre todos nuevas conclusiones.

Por otro lado, Canonical se esmera en entregar sistemas "copados" con LTPS, como Dapper y Hardy. Las demás entregas creo que buscan "experimentar un poco".

---

### Post by Hei Ku on 2008-05-27
Mi PC llega a tomar 1GB de RAM con el Firefox y el KDevelop abierta. Ahora, si abro ademas el Kontact, Konqueror y varios tabs en el Firefox sigue igual y no noto baja en la performance. Al menos KDE hace un prefetch de lo que pueda necesitar, pero si necesita va limpiando y reemplazando por lo que realmente usa. Salvo que tenga algun acceso a disco ***** (tengo un SATA viejito), como mientras hago una compilacion de cero, no noto ninguna baja en la performance aunque tenga todo abierto. El consumo total de RAM no es un parametro para medir la performance de un Linux. Digamos que aprovecha la RAM mejor que Windows, y ademas la libera como corresponde. Antes de bajarla la ultima vez para hacer un chequeo de disco, el sistema habia estado 1800 horas sin reiniciar, con el entorno abierto y apenas un reinicio de X a la mitad, para que me tome bien los parametros del decorator de ventanas nuevo.
Y si II es el nuevo Vista (que lo dudo, tendrían que esforzarse MUUUUUUCHO) entonces tenes OpenSuse, Fedora, Gentoo, y muchas mas. No es linda la libertad? :D

---

### Post by pol666 on 2008-05-27
Ubuntu anda muy lindo.. no hace falta que te pases... Lo que ralentiza es el Compiz y los programas que inician con el sistema

---

### Post by andy_91 on 2008-05-27
> **madelaki said:**
> Tenes razon. Pasa que lei tanto sobre la nueva GUI y tan poco sobre otras novedades que tenia miedo de que Intrepid Ibex fuera el Vista de Ubuntu. Esperare a una Alfa importante o a la Beta.

punto numero uno no podes comparar naranjas con manzanas ni con ventanas

el dos no creo que ubuntu 8.10 sea el nuevo vista, derecho para mi ubuntu 7.10 fue el xp de ubuntu pero en una vercion perfecta y ubuntu 8.04 el comienso del nuevo vista por decirlo de alguna forma(errada pero en fin forma entendible)

y el tres..... el problema esta en vos por que con tu maquina debería corre bien ubuntu, no te hagas paranoia de lo que posiblemente no sea

---

### Post by madelaki on 2008-05-27
No me entendiste. No los estoy comparando (por cierto no veo porque no se pueden comparar, son sistemas operativos), me referia a lo que Vista significo para Windows, no al sistema operativo en si.

---

### Post by andy_91 on 2008-05-28
> **madelaki said:**
> No me entendiste. No los estoy comparando (por cierto no veo porque no se pueden comparar, son sistemas operativos), me referia a lo que Vista significo para Windows, no al sistema operativo en si.
si las naranjas y las manzanas tambien son frutas y no por eso valen lo mismo en la verduleria o se venden juntas

y si es por lo que significo, vista para microsoft fue una perdida

entonses que es lo que intentas decir

---

### Post by madelaki on 2008-05-28
Lo que significo para Windows, no para MicroSoft. Vista para muchos fue la gota que rebalso el vaso y la respuesta de MS (borrar XP del mercado) no ayudo en lo mas minimo. No estoy comparando Ubuntu con Windows, pero sinceramente esperaba mas de Hardy Heron, y hoy en dia es mucho mas normal ver que despues de la primer caida se caiga todo que una recuperacion completa para la proxima version.

---

### Post by SuperCurro on 2009-03-08
> **Mister X said:**
> No se si entiendo bien tu problema, vos notas lenta ahora tu maquina con Ubuntu?
Si es por el tema del uso de memoria, con 1Gb debe funcionar sin problemas.
Cuando veas que el uso de RAM sube despues de abrir varias aplicaciones es porque tenes mucha memoria cacheada, cosa que está perfecto para optimizar al funcionamiento del sistema.


Yo tengo 1 GB de ram, y en cuanto se llena la ram y llevo 300 megas de swap el ordenador se vuelve lento, muy muy lento, tan lento que el servidor web no funciona, bueno, ni te puedes mover por la pantalla, parece que se cuelga (aunque no se cuelga). Hasta 300 megas va muy bien, de resto un desastre, el disco duro no para se queda medio colgado.

---

### Post by Hei Ku on 2009-03-08
Que haces que llenas 1Gb y despues 300MB de swap? Los unicos casos en que me pasa es cuando se tara el Firefox y empieza a comer memoria sin control.

PD: Movido a Hardware

---

