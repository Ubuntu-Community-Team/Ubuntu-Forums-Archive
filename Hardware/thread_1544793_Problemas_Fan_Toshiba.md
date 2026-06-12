---
title: "Problemas Fan Toshiba"
date: 2010-08-03
forum: Hardware
---

### Post by EmiOk on 2010-08-03
Hola, llego a este foro con el fin de ver si alguien me puede llegar a ayudar, el problema es el ste:

Se tilda el Fan (ventilador o cooler) de la notebook, si antes de entrar a ubuntu el ventilador no funcionaba porq estaba fría la pc, no funciona luego de entrar aunq este a 70 grados. Si el ventilador estaba encendido antes de inciar ubunto, queda encendido y no para en ningún momento.

Conclusión: no detecta el sistema cuando debe prender o apagar el ventilador.

La verdad no se a que se debe, ya eh buscado por todos lados y nadie me sabe dar una solución.

Saludos y gracias!

---

### Post by Maverick_Meerkat on 2010-08-03
Toshiba Specific Utlities for Linux 
[http://www.buzzard.me.uk/toshiba/index.html](http://www.buzzard.me.uk/toshiba/index.html)

---

### Post by EmiOk on 2010-08-06
> **Maverick_Meerkat said:**
> Toshiba Specific Utlities for Linux 
[http://www.buzzard.me.uk/toshiba/index.html](http://www.buzzard.me.uk/toshiba/index.html)


gracias! estuve viendo igualmente sigo sin encontrar la solución, le mande un mail al de la página pero no me respondió.

Si alguien mas sabe como solucionar el problema le agradecería!

---

### Post by guillermolisi on 2010-08-06
Podes probar esa maquina pero con otro sistema operativo, Windows por ejemplo, y ver si se comporta igual ? Esto seria para verificar algun problema de hardware, especificamente.

Se me ocurren dos posibilidades, independientemente de la version de Ubuntu que estes usando (cosa que aun no aclaraste y seria informacion minima a brindar):

Que Ubuntu este iniciando con la opcion acpi=off por no poder reconocer bien la tabla acpi del BIOS (acpi es el firmware que ayuda a administrar el consumo de energia del hardware y facilita el reconocimiento de algunos componentes como el caso de pacas de video con aceleracion grafica).

Que el modulo gnome-power-manager no este funcionando bien.

---

### Post by EmiOk on 2010-08-06
> **guillermolisi said:**
> Podes probar esa maquina pero con otro sistema operativo, Windows por ejemplo, y ver si se comporta igual ? Esto seria para verificar algun problema de hardware, especificamente.

Se me ocurren dos posibilidades, independientemente de la version de Ubuntu que estes usando (cosa que aun no aclaraste y seria informacion minima a brindar):

Que Ubuntu este iniciando con la opcion acpi=off por no poder reconocer bien la tabla acpi del BIOS (acpi es el firmware que ayuda a administrar el consumo de energia del hardware y facilita el reconocimiento de algunos componentes como el caso de pacas de video con aceleracion grafica).

Que el modulo gnome-power-manager no este funcionando bien.

Hola gracias por responder!

Si con windows anda, de ahi la estoy usando, pero es una lastima no poder usar ubuntu por ese problema.

La versión es karmic 9.10.

Como verifico eso de acpi? no soy un usuario muy experimentado en linux...


Saludos!!

---

### Post by guillermolisi on 2010-08-08
En la medida que el problema te deje, intentaria actualizar a la ultima version de Ubuntu, la 10.04 que tiene muchos problemas resueltos.

Con la nueva version funcionando y si el problema continua, ahi profundizamos

---

### Post by EmiOk on 2010-08-14
Hola, eh actualizado la versión, y con una actualización de ubuntu ahora el problema cambió pero se sigue tildando.

Lo que pasa ahora es que llega a una temperatura de 68 grados mas o menos y enciende el fan a máxima potencia (es lógico por que está caliente), pero luego no para, es decir llega a tan baja temperatura (unos 24 a 30 grados, cosa que es bajo para esta notebook) y aún asi siguen al máximo, deberían cesar en algún momento como lo hacen en windows.

En definitiva sigo con el mismo problema pero esta vez se que no se me va a quemar la pc sino el fan jajaj, si alguien sabe como solucionar este problema se lo agradezco enormemente.

Saludos!!

---

### Post by hectorivand on 2010-10-20
> **EmiOk said:**
> Hola, eh actualizado la versión, y con una actualización de ubuntu ahora el problema cambió pero se sigue tildando.

Lo que pasa ahora es que llega a una temperatura de 68 grados mas o menos y enciende el fan a máxima potencia (es lógico por que está caliente), pero luego no para, es decir llega a tan baja temperatura (unos 24 a 30 grados, cosa que es bajo para esta notebook) y aún asi siguen al máximo, deberían cesar en algún momento como lo hacen en windows.

En definitiva sigo con el mismo problema pero esta vez se que no se me va a quemar la pc sino el fan jajaj, si alguien sabe como solucionar este problema se lo agradezco enormemente.

Saludos!!

Disculpa que reflote este tema, pero has podido solucionar el tema de la temperatura y del fan?

Saludos
Nacho

---

