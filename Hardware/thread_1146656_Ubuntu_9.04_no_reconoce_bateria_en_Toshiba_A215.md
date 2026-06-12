---
title: "Ubuntu 9.04 no reconoce bateria en Toshiba A215"
date: 2009-05-02
forum: Hardware
---

### Post by Tenisfan on 2009-05-02
Hola amigos, hace poco instale por primera vez Ubuntu en mi laptop Toshiba A215-S5822, la verdad es que soy muy novato en el tema y necesito su ayuda. Al parecer el sistema no me reconoce la bateria cuando esta desconectada, sigue andando pero no me indica ni cuanto tiempo me queda ni tampoco tengo la posibilidad de ajustar el consumo ni el brillo de la pantalla (en Win podes adoptar distintos perfiles). Me fijé en las opciones de energía, y no me da la opción de la batería.Por otro lado, tengo problemas con las teclas especiales (tecla Fn y las de multimedia) el card reader y la web cam, pero ahora lo que mas me preocupa es la bateria. Bueno, espero que se entienda cual es el problema y puedan darme una mano, muchas gracias desde ya
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by z37a on 2009-05-02
> **Tenisfan said:**
> Hola amigos, hace poco instale por primera vez Ubuntu en mi laptop Toshiba A215-S5822, la verdad es que soy muy novato en el tema y necesito su ayuda. Al parecer el sistema no me reconoce la bateria cuando esta desconectada, sigue andando pero no me indica ni cuanto tiempo me queda ni tampoco tengo la posibilidad de ajustar el consumo ni el brillo de la pantalla (en Win podes adoptar distintos perfiles). Me fijé en las opciones de energía, y no me da la opción de la batería.Por otro lado, tengo problemas con las teclas especiales (tecla Fn y las de multimedia) el card reader y la web cam, pero ahora lo que mas me preocupa es la bateria. Bueno, espero que se entienda cual es el problema y puedan darme una mano, muchas gracias desde ya
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]


Por casualidad no tocastes nada del ACPI durante la instalacion o tenes algo con esta palabra deshabilitado?

---

### Post by Tenisfan on 2009-05-03
> **z37a said:**
> Por casualidad no tocastes nada del ACPI durante la instalacion o tenes algo con esta palabra deshabilitado?
mmm no creo, pero por las dudas...como podría verificarlo? gracias nuevamente

---

### Post by Electron on 2009-05-03
Intentastes "right click" en el panel y "add to panel" busca por el simbolo de la bateria... 
Dejame saber si eso funciona.

---

### Post by Tenisfan on 2009-05-04
> **Electron said:**
> Intentastes "right click" en el panel y "add to panel" busca por el simbolo de la bateria... 
Dejame saber si eso funciona.
Intenté eso, pero me decía que no encontraba ninguna batería. Te cuento que me baje la versión de 64 bits, y...andan todos los comandos que dependen del ACPI!!!:confused: Ahora, no se a que se debe eso, en este momento estoy escribiendo en la version liveCD,y funciona la ruedita del volumen, las funciones de las teclas especiales, la tecla Fn (se usa para ajustar el brillo, entre otras cosas) En definitiva, puedo hacer todo lo que no podía en la version q tengo instalada de 32 bits!!! 
Estuve leyendo bastante, y parece ser que esas funciones ACPI estan diseñadas para windows,(tengo Bios Phoenix v1.80, la última que salió) y por eso puede haberme dado esos problemas...Ahora la gran pregunta: podré resolver esos problemas en la versión de 32 bits? O debo instalar la de 64?
En otro post les pondré en detalle lo que me aparece cuando carga la versión de 32 bits, creo q ahi está la clave del problema (me salen varios errores)
Bueno, gracias por sus respuestas, espero que puedan ayudarme

---

### Post by z37a on 2009-05-06
> **Tenisfan said:**
> Intenté eso, pero me decía que no encontraba ninguna batería. Te cuento que me baje la versión de 64 bits, y...andan todos los comandos que dependen del ACPI!!!:confused: Ahora, no se a que se debe eso, en este momento estoy escribiendo en la version liveCD,y funciona la ruedita del volumen, las funciones de las teclas especiales, la tecla Fn (se usa para ajustar el brillo, entre otras cosas) En definitiva, puedo hacer todo lo que no podía en la version q tengo instalada de 32 bits!!! 
Estuve leyendo bastante, y parece ser que esas funciones ACPI estan diseñadas para windows,(tengo Bios Phoenix v1.80, la última que salió) y por eso puede haberme dado esos problemas...Ahora la gran pregunta: podré resolver esos problemas en la versión de 32 bits? O debo instalar la de 64?
En otro post les pondré en detalle lo que me aparece cuando carga la versión de 32 bits, creo q ahi está la clave del problema (me salen varios errores)
Bueno, gracias por sus respuestas, espero que puedan ayudarme

Yo soy partidario de que si tenes menos de 4GB y procesador Intel en la laptop, uso 32 bits, por mas que funcione la de 64!!! Todavía hay muchas cosas que solo funcionan en 32 o que requieren las librerías de 32 bits y eso me molesta mucho, pro suerte cada vez son menos pero bueno... es cuestion de tiempo.

---

### Post by Tenisfan on 2009-05-06
> **z37a said:**
> Yo soy partidario de que si tenes menos de 4GB y procesador Intel en la laptop, uso 32 bits, por mas que funcione la de 64!!! Todavía hay muchas cosas que solo funcionan en 32 o que requieren las librerías de 32 bits y eso me molesta mucho, pro suerte cada vez son menos pero bueno... es cuestion de tiempo.
En mi caso, mi máquina tiene procesador AMD, no me quedó otra que instalar la versión de 64 bits:(.
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by Hei Ku on 2009-05-06
Aunque tengas un AMD podes instalar la version de 32 bits, salvo que eso haya cambiado en Jaunty. Igual, ya la mayoria de cosas funcionan sin problemas en 64 bits.

---

### Post by josecuervo86 on 2009-05-06
> **Hei Ku said:**
>  Igual, ya la mayoria de cosas funcionan sin problemas en 64 bits.

Menos Flash :(

---

### Post by Hei Ku on 2009-05-06
> **josecuervo86 said:**
> Menos Flash :(
Tengo una pagina de YouTube con videos que dice lo contrario. Es cierto que funciona con un plugin que sirve de wrapper al de 32 bits de Flash, pero anda. ;)

Y la instalación es tan simple como correr un script y reiniciar Firefox.

---

### Post by josecuervo86 on 2009-05-06
> **Hei Ku said:**
> Tengo una pagina de YouTube con videos que dice lo contrario. Es cierto que funciona con un plugin que sirve de wrapper al de 32 bits de Flash, pero anda. ;)

Y la instalación es tan simple como correr un script y reiniciar Firefox.

Entonces no se si tengo el el plugin correcto, porque andar anda pero solo cuando el quiere :D

---

### Post by z37a on 2009-05-06
Che, les comento que yo uso 64 bits hace rato, y el flash plugin de 64 bits si bienn es alpha anda bastante bien ahora!!! Yo desde hace unos 2 meses que no uso mas flash de 32 bits, si no veo el video ni me caliento, son pocos los sitios incompatibles.

---

### Post by Tenisfan on 2009-05-08
Gente, con el tema del flash no tengo ningun problema, ahora estoy usando la version d e 64 bits y anda perfecto..

---

