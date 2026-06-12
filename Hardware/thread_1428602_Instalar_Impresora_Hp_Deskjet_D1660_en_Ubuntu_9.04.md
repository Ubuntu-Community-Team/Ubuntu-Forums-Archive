---
title: "Instalar Impresora Hp Deskjet D1660 en Ubuntu 9.04"
date: 2010-03-13
forum: Hardware
---

### Post by mecdem on 2010-03-13
He instalado antes varias impresoras HP en diferentes versiones de Ubuntu sin inconvenientes. Pero ahora una Deskjet D1660 se me resiste.
___________

LO QUE HICE PRIMERO

En ubuntu-es hallé esta instrucción ([http://www.ubuntu-es.org/?q=node/118977):](http://www.ubuntu-es.org/?q=node/118977):) “entrar en [http://hplipopensource.com](http://hplipopensource.com) y allí bajar hplip, seguramente deberás instalarlo...”.
En la URL indicada explica que “...the HPLIP software which supports 1,956 HP printers on nearly any Linux distribution available today”. Y agrega que “the current version of the HPLIP solution is version 3.10.2.”

Verifico si el soft está en Ubuntu (v. 9.04) y, efectivamente, encuentro el HPLIP version 3.9.2 - 3ubuntu4. Lo instalo.
___________

EL PROBLEMA

Conecto la impresora HP Deskjet D1660. El sistema la reconoce y la agrega a la lista de impresoras ya existentes, lo que me permite ajustar las configuraciones de la D1660 a mis necesidades.

Cuando intento imprimir el contenido de un archivo, en pantalla se abre la ventanita (negra) que informa haber recibido la orden de imprimir, y de inmediato se abre una segunda ventanita (negra) que informa que la tarea de impresión ha finalizado. Aclaro: esta información no alude a una finalización intempestiva de la tarea sino a que culminó exitosamente. Sin embargo, la impresora no ha dado ninguna señal de haber recibido la orden.

El problema no es el hardware: la impresora funciona bajo Windows.
___________

LO QUE HICE DESPUÉS

Como la versión de HPLIP instalada en mi equipo es más antigua que la que se baja desde [http://hplipopensource.com](http://hplipopensource.com), regreso al sitio donde al pedir el download se requiere contestar unas preguntas. Hecho, aparece este texto:

"You have selected Ubuntu 9.04 using the HP Deskjet 1600c Printer.
Ubuntu 9.04 supplies HPLIP 3.9.2 and it does support your printer.
As the version of HPLIP supplied with your operating system supports your printer, you may continue to use that version of HPLIP.
You may now optionally download the latest version of HPLIP to get access to new features and bug fixes".
___________

PREGUNTAS 

He bajado el HPLIP 3.10.2, pero antes de instalarlo pregunto:

¿Se puede instalar instalar esta versión más nueva pese a que el informe decía que la 9.04 actualmente instalada es la compatible con Ubuntu 9.04?

¿Alguna otra sugerencia para solucionar el problema?
___________

Agradezco desde ya la ayuda.
Saludos.

---

### Post by mecdem on 2010-03-13
Corrijo:

¿Se puede instalar instalar esta versión más nueva pese a que el informe decía que la [COLOR="Red"]**3.9.2**[/COLOR] actualmente instalada es la compatible con Ubuntu 9.04?

¿Alguna otra sugerencia para solucionar el problema?

---

### Post by z37a on 2010-03-25
Cuando me comentaste el error pensé que era por un problema de firmware, ahora que veo bien el detalle desconozco el error, peor por si las duda hay una prueba que hacer para ver si realmente es falta de firmware.

Necesitaría que inicies la PC en Windows, e imprimas algo, luego SIN APAGAR LA IMPRESORA reinicia el equipo e inicia con Ubuntu, una vez reiniciado proba ahí mismo de imprimir, si sale algo avisa, por que entonces es tema de Firmware.

PD: Lo del Firmware se da mucho en las lasers, los modelos 10XX viejos y los nuevos P100X que para abaratar no tienen una rom con el firmware y el driver lo que hace es cargar un FW en la RAM del equipo!!!!

---

### Post by mecdem on 2010-03-27
Hola, JM-z37a.

Gracias por la respuesta. Seguí las indicaciones:
Inicié la PC en Windows e imprimí algo. Luego SIN APAGAR LA IMPRESORA reinicié el equipo e inicié con Ubuntu. Una vez reiniciado probé ahí mismo a imprimir.

No pasó nada, siguió tirando sus avisos, uno de que está iniciando la impresión, otro (inmediato) de que la impresión ha finalizado, sin que la impresora diera señal de haber recibido nada.

Te ruego nuevas instrucciones que agradezco desde ahora.
Abrazo.

---

### Post by z37a on 2010-03-27
> **mecdem said:**
> Hola, JM-z37a.

Gracias por la respuesta. Seguí las indicaciones:
Inicié la PC en Windows e imprimí algo. Luego SIN APAGAR LA IMPRESORA reinicié el equipo e inicié con Ubuntu. Una vez reiniciado probé ahí mismo a imprimir.

No pasó nada, siguió tirando sus avisos, uno de que está iniciando la impresión, otro (inmediato) de que la impresión ha finalizado, sin que la impresora diera señal de haber recibido nada.

Te ruego nuevas instrucciones que agradezco desde ahora.
Abrazo.

Problema con el Firmware entonces no es, fijate de seguir este instructivo:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Ahi te detalla el como bajar e instalar hplips para tu impresora, al parecer esta no esta soportada en Ubuntu 9.04 segun HP, pero si bajas esa versión nueva de hplip si debería funcionar.

---

### Post by mecdem on 2010-03-28
[B][CENTER]:lol:  \\:D/  :-D  =D>

[SIZE="4"]¡¡ BINGO, JM-z37a !![/SIZE][/CENTER][/B]

Solucionado.
Muchísimas gracias.
Un abrazo al team.
):P

---

### Post by z37a on 2010-03-28
> **mecdem said:**
> [B][CENTER]:lol:  \\:D/  :-D  =D>

[SIZE="4"]¡¡ BINGO, JM-z37a !![/SIZE][/CENTER][/B]

Solucionado.
Muchísimas gracias.
Un abrazo al team.
):P

Menos mal, por que en AFCEA pensé que tenias un laser y el problema mas común es otro, de esta impresora no tenia idea jajaja, la verdad busque por ahí a ver como lo solucionaron algunos y me tope que no tiene soporte para 9.04, pero si para 9.10 y 10.04.

---

### Post by felipelerena on 2010-03-30
Mediante la presente pido perdon a MEC por haber ignorado su post y su mail categoricamente. En caso de que haya Dios, el mismo seguramente me castigara por eso.

---

### Post by mecdem on 2010-04-15
¡¡Hola, amigos!!

No había vuelto por aquí después de mi último post, así que no había visto los de ustedes.
______

**A z37a**:

"...y me tope que no tiene soporte para 9.04, pero si para 9.10 y 10.04"

Sí, que habría algo así sospeché, porque la impresora de nuestros desvelos está funcionando, sí, pero anda algo "errática". 

Entiendo, por lo que decís, que tendría que actualizar versión ¿no?
Bueno, leeré los comentarios que haya respecto de 10.04 y vemos. Mi 9.04 anda como un violín (un Guarnerius del Gesú, nada menos) y me resisto a actualizar. Después de todo, es un principio básico de la tecnología: si funciona no lo toques ¿no? :)

Beso.
______

**A felipelerena**:

Lipe, vos sabés que yo igual te quiero :-({|=
Ya te he perdonado. Ahora: con el señor dios, ... negociálo.

Otro beso.

---

