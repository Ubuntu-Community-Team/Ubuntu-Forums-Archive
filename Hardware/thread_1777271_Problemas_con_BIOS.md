---
title: "Problemas con BIOS?"
date: 2011-06-07
forum: Hardware
---

### Post by Vero1 on 2011-06-07
Buenos días a todos,

Desde hace un tiempo a esta parte cuando enciendo la computadora, me sale una pantalla negra donde dice: Bad BIOS checksum y que no encuentra puertos USB y tampoco CD Rom y repite lo mismo hasta que reinicio y a veces engancho, pero a veces tengo que reiniciar hasta 4 veces para que enganche.

Consulté en ubuntu-es y me dijeron que podía ser la pila de la mother, pero la mother es prácticamente nueva.

Tienen uds. alguna idea de lo que pueda ser o de qué manera puedo hacer un chequeo del estado de BIOS, pila, etc.?

Desde ya agradezco comentarios.

Saludos

---

### Post by sanguinoso on 2011-06-07
Lo siento para mi español. ¿Ha tratado de restablecer la CMOS?

---

### Post by samigina on 2011-06-07
Tambien pienso en un problema con la pila.

Prueba reseteando la bios, suele haber un jumper cerca del chip o la pila de la bios; solo ponlo en la posicion correcta (suele haber un indicador) la dejas 15 sec y lo devuelves a su posicion original.

---

### Post by Vero1 on 2011-06-07
Bueno, gracias a los dos.

Ya que coinciden, trataré de sacar la pila y hacer lo que dice samigina.

saludos

---

### Post by Vero1 on 2011-06-09
Hola,
He sacado la pila y la tuve fuera 15 segundos, como me indicaron.

Lamentablemente no ha servido para que desaparecieran los dichosos mensajes.

Ahora bien, entrando en BIOS hay un tool que sirve para actualizarlo. Les parece que haga éso?

La antigüedad del BIOS es de fines de 2010. 

Gracias

---

### Post by alfplayer on 2011-06-09
Otra cosa para probar: "Load setup defaults" (o parecido) en la configuración del BIOS.

---

### Post by samigina on 2011-06-09
En las boards modernas no basta con sacar la pila, busca un jumper.

La actualización puede ser buena idea desde que obtengas tal actualizacion directamente del fabricante.

---

### Post by alfplayer on 2011-06-09
> **samigina said:**
> En las boards modernas no basta con sacar la pila, busca un jumper.

La actualización puede ser buena idea desde que obtengas tal actualizacion directamente del fabricante.

Sí.

Pero primero es recomendable que pruebe lo de "Load setup defaults" que sería más fácil.

---

### Post by Vero1 on 2011-06-09
Alfplayer, justamente hace media hora hice lo que comentas porque me acordé haber visto algo de setup default, así que le dí el ok.
Veo si mañana, al reiniciar, sigue o no saliendo el mensaje.

Gracias

Samigina,
Si no surtió efecto lo que le comento a Alfplayer, veré de sacar el jumper que dices, ya que actualizar algo que es de Octubre 2010 me parece prematuro.

Gracias
p.d.
les informaré de los resultados.

---

### Post by Vero1 on 2011-06-10
Hola,

Parece que ha surtido efecto lo de Load Setup Defaults porque dejó de aparecer el mensaje.

Gracias por vuestra ayuda.

Saludos.

---

### Post by Vero1 on 2011-06-12
> **Vero1 said:**
> Hola,

Parece que ha surtido efecto lo de Load Setup Defaults porque dejó de aparecer el mensaje.

Gracias por vuestra ayuda.

Saludos.

Bueno, volvió a aparecer el mensaje, entonces opté por sacar la pila y cambiar el jumper y luego volverlo a su lugar.
Ahora parece que no hay mas problemas.

Estuve pensando cuál podía ser el motivo de esos mensajes y me acordé que hace muy poco se ha cambiado el mother(el anterior se había quemado) y el técnico se ve que no entró en el BIOS para chequear fecha y hora porque cuando entré yo, ambas cosas estaban mal. No sé si me equivoco al pensar que ése fue el motivo del Bad Checksum. Qué opinan?

saludos

---

### Post by alfplayer on 2011-06-12
> **Vero1 said:**
> Bueno, volvió a aparecer el mensaje, entonces opté por sacar la pila y cambiar el jumper y luego volverlo a su lugar.
Ahora parece que no hay mas problemas.

Estuve pensando cuál podía ser el motivo de esos mensajes y me acordé que hace muy poco se ha cambiado el mother(el anterior se había quemado) y el técnico se ve que no entró en el BIOS para chequear fecha y hora porque cuando entré yo, ambas cosas estaban mal. No sé si me equivoco al pensar que ése fue el motivo del Bad Checksum. Qué opinan?

saludos

Estás quitándole la conexión a 220 V al gabinete/motherboard? Si es así la pila puede estar con poca carga y necesita ser reemplazada (se puede chequear con un multímetro/tester). Una nueva no es cara y se puede cambiar fácilmente.

Además, si hiciste el clear CMOS con éxito, no cambiaste nada de hardware después que te lo entregaron y el técnico entregó con otra pila (como decís, hace muy poco tiempo, sin tiempo a que la pila nueva se agote), el problema sería responsabilidad del técnico. Si es así podrías devolverlo o que se haga cargo de una nueva pila.

---

### Post by biale on 2011-06-12
> me acordé que hace muy poco se ha cambiado el mother(el anterior se había quemado)

Que tan poco tiempo?   Porque se quemo la motherb anterior?

Para descartar la pila simplemente desconecta la computadora de la red durante toda una noche y fijate a nivel del BIOS las derivas del reloj (fecha y hora)

Pero cualquier cosa que este conectada a la motherb puede también provocar ese error. Por ejemplo la fuente de poder, que no alcance a sostener alguna de las tensiones eléctricas para un funcionamiento correcto.

---

