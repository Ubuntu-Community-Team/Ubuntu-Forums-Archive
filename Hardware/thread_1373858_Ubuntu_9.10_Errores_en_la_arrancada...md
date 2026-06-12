---
title: "Ubuntu 9.10 Errores en la arrancada.."
date: 2010-01-06
forum: Hardware
---

### Post by prostata on 2010-01-06
Hoy al arrancar la máquina y sin más motivo ubuntu me ha enviado estos mensages y no me permitia seguir.


Device descriptor read /64 error 62
Device not accepting address 9 error 62
Unable to enumerate USB device on port 3

He arrancado en Mode Recovery: resume normal root, y otro que permite arreglar los paquetes rotos, de hecho no sabía que hacer, para encontrar el error y la causa.

He parado la máquina y luego de un rato la prendí nuevamente arrancando bien sin más.

¿cuál podría ser la causa de estos mensages, y cuál la solución, pues no entiendo nada de nada.?

Saludos

_________

---

### Post by guillermolisi on 2010-01-06
Los logs del sistema suelen registrar informacion util para este tipo de situaciones.
En general, en /var/log/dmesg y /var/log/messages deberias encontrar algun indicio.

La duda que me genera tu mensaje es si luego inicio bien como consecuencia de lo que hiciste o solo fue un problema circunstancial.

---

### Post by prostata on 2010-01-06
> **guillermolisi said:**
> Los logs del sistema suelen registrar informacion util para este tipo de situaciones.
En general, en /var/log/dmesg y /var/log/messages deberias encontrar algun indicio.

La duda que me genera tu mensaje es si luego inicio bien como consecuencia de lo que hiciste o solo fue un problema circunstancial.

Pues esa es la misma duda que me genera a mi, miraré lo que dices y os tendré informados, pero botepronto, me tiene alucinado...hasta luego

Saludos

---

### Post by prostata on 2010-01-06
> **prostata said:**
> Pues esa es la misma duda que me genera a mi, miraré lo que dices y os tendré informados, pero botepronto, me tiene alucinado...hasta luego

Saludos


He mirado lo que me indicas, para empezar hay cientos de lineas, y aunque busco por fecha/hora, no veo nada que me ayude a dar con la causa, podría ser que tampoco se bien, bien por dónde buscar concepto por el que investigar...si me dieras una pista...

Saludos

---

### Post by guillermolisi on 2010-01-06
Por lo sintetico de los mensajes de error que mencionaste, pareceria haber algun tema con los ports USB, en particular el port 3, pero es una sospecha inducida por el ultimo de ellos.

---

### Post by prostata on 2010-01-08
Pues como comentario final:

Ignoro las causas de esos mensajes, pero debo decir que desde ya todo funciona correctamente, si acaso ampliar que a veces cuando quiero quemar un dvd con k3b o el brasero no me reconoce el dsipositivo....

Saludos y gracias

---

### Post by guillermolisi on 2010-01-08
> **prostata said:**
> Pues como comentario final:

Ignoro las causas de esos mensajes, pero debo decir que desde ya todo funciona correctamente, si acaso ampliar que a veces cuando quiero quemar un dvd con k3b o el brasero no me reconoce el dsipositivo....

Saludos y gracias
Con esto ultimo ya nos fuimos de tema pero hay problemas reportados y conocidos respecto del kernel 2.6.31 y el reconocimiento de DVDs en unidades IDE. Si se usa unidades opticas SATA pareceria no existir tal inconveniente.

---

