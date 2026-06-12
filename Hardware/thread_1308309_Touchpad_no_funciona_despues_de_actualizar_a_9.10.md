---
title: "Touchpad no funciona despues de actualizar a 9.10"
date: 2009-10-31
forum: Hardware
---

### Post by cdii on 2009-10-31
Amigos, asi es, como lo indica el titulo se murio el touchpad de mi notebook compaq V2424.
Siempre ha funcionado sin problemas, busque en todos lados, provee varias "soluciones" pero todavia no puedo hacerlo andar.
A alguien lo ocurrio lo mismo???
Ojala me puedan orientar.

Cristian

---

### Post by VonlisT on 2009-11-01
A mi me pasó y además no veía siquiera el grub, prueba arrancando con el kernel anterior si es que has actualizado desde 9.04. A mi me funcionaba bien el touch con ese kernel, después de modificar el arranque para poder ver el sistema con el último kernel, funcionó bien y ya no fue necesario utilizar el kernel 2.6.28

Por ahora no sé una solución definitiva, pero me parece haber visto en google, ya que también tuve tu mismo problema.

Saludos

---

### Post by Carlos C on 2009-11-02
> **cdii said:**
> Amigos, asi es, como lo indica el titulo se murio el touchpad de mi notebook compaq V2424.
Siempre ha funcionado sin problemas, busque en todos lados, provee varias "soluciones" pero todavia no puedo hacerlo andar.
A alguien lo ocurrio lo mismo???
Ojala me puedan orientar.

Cristian

Hola. Me surgen algunas dudas: cuando dices que actualizaste tengo la impresión de que tenías Jaunty e hiciste que el sistema se actualizara, no es que hayas formateado ni nada por el estilo, ¿verdad? Tengo que preguntarlo para estar seguros de qué hablamos.

¿Qué procedimientos probaste? Te sugiero siempre digas lo que hiciste, para no darte consejos que en realidad ya probaste. También ojalá nos dijeras qué tipo de errores obtuviste en cada procedimiento.

Existe un bug reportado, lo puedes ver [aquí]("https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/384641"), pero en ese caso lo que no funciona es el "tap to click", ¿es ese tu caso?

---

### Post by cdii on 2009-11-02
Gracias por sus consejos.
Tienen razón, me falto mas detalle.
Lo actualice desde 9.04 y el touchpad simplemente no funciona.
Me di cuenta que en el archivo xorg.conf no estaba señalado el touchpad, asi agregue la lineas necesarias y tampoco.
Luego para volver a configurar xorg.conf lo renombre e igual partio en ambiente grafico, por lo que segui investigando y claro ahora se ocupa HAL, por lo que encontre por ahi una archivo xml que habia que colocar en cierta ruta, pero tampoco me funciono.
No se me habia ocurrido devolverme en la version de kernel......
a la espera que el tema se solucione definitivamente.
Voy a probar en la casa.
Gracias nuevamente y saludos.
Cristian.

---

