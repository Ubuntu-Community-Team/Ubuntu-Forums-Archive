---
title: "trackpad en macbook funciona muy mal"
date: 2011-02-08
forum: Hardware
---

### Post by panchoponcho on 2011-02-08
Buenas noches, tengo un gran problema ya que no puedo disfrutar ubuntu: 
intalé ubuntu 10.10 en mi macbook 4.1 pero el trackpad a pesar de que reconoce las opciones de scroll muy bien, al usarlo funciona pesimo, muy lento y cortado, es decir un movimiento no fluido. 
si alguien sabe como solucionar esto para hacer que el cursor funcione fluido se lo agradeceria mucho ya que sin esto no puedo usar el computador con ubuntu y he buscado mucho en internet pero no encuentro una solucion. 
de antemano muchas gracias

---

### Post by asterix77 on 2011-02-09
Haz probado configurarlo desde sistema----->preferencias------>ratón

también podrías instalar alguna utilidad para configurarlo, podrías ir a sistema---->Administración---->Synaptic y aquí buscar por touchpad o similares

Se me ocurre por ejemplo instalar kcm-touchpad, lo puedes instalar desde synaptic o escribiendo en la terminal:

$sudo apt-get install kcm-touchpad.

Al menos te garantizo que con esto puedes configurar la velocidad, lo del movimiento fluido no se si lo puedas arreglar con esto.

También tienes este otro

$sudo apt-get install gpointing-device-settings


Saludos

---

### Post by panchoponcho on 2011-02-09
mmm... intente con todo lo que me dijiste, y el problema persiste. de todas formas gracias por la respuesta. 
es extraño, por que pareciera que el trackpad estubiera medio malo, ya que al precionarlo mas fuerte funciona un poco mejor, pero de todas formas nada fluido. sin embargo en mac funciona perfecto de modo que no es el trackpad lo malo. 
¿alguien tiene mas ideas?

---

### Post by RafaelG on 2011-02-09
Panchoponcho,

Prueba con lo siguiente debes crear **appletouch.fdi**[INDENT]```
**sudo gedit /etc/hal/fdi/policy/appletouch.fdi**
```[/INDENT]Copia y pega lo siguiente:
 
 <?xml version="1.0" encoding="ISO-8859-1"?>
 <deviceinfo version="0.2">
 <device>
 <match key="input.x11_driver" string="synaptics">
 <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
 <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
 <merge key="input.x11_options.TapButton1" type="string">1</merge>
 <merge key="input.x11_options.TapButton2" type="string">3</merge>
 <merge key="input.x11_options.TapButton3" type="string">2</merge>
 <merge key="input.x11_options.FingerLow" type="string">10</merge>
 <merge key="input.x11_options.FingerHigh" type="string">20</merge>
 <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
 <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
 <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
 <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
 </match>
 </device>
 </deviceinfo>
 
 Reinicia y deberá de funcionar a la normalidad.

---

### Post by panchoponcho on 2011-02-10
estimado, muchas gracias por la respuesta. creé el archivo que me dices y reinicié. sin embargo no hay cambio, el problema persiste.
¿alguna otra idea? 
(ya no se que hacer, no puedo vivir sin ubuntu y se me hace imposible con este problema)

---

### Post by panchoponcho on 2011-03-12
¿nadie sabe como solucionar el problema?

---

### Post by panchoponcho on 2011-09-08
sigo con el problema. ¿no hay alguien que sepa hacer que el trackpad del macbook funcione bien en ubuntu?

---

### Post by patraicio on 2011-09-08
te fijaste que la solución que te dio Rafael era crear un archivo en específico en un directorio también específico? Pregunto por si no habías puesto cuidado en ello.

---

### Post by panchoponcho on 2011-09-20
si, lo hize, pero el problema sigue igual :(

---

### Post by olbapablo on 2011-11-06
Tengo el mismo problema, sin embargo en mi ubuntu 11.10 no existe la ruta "/etc/hal/" pero si existe "/usr/share/hal/fdi/policy" así que cree ese archivo ahí por probar pero no me ha funcionado. 
¿Alguien sabe la solución?

Saludos

---

### Post by panchoponcho on 2012-01-21
hola me pasa lo mismo que olda pablo, no existe la ruta ets/hal... 

por favor llevo casi un año con el problema... y no he podido solucionarlo...

---

### Post by PoMeLo on 2012-01-31
Yo también tengo el mismo problema, mi Macbook es una early-2008.

---

