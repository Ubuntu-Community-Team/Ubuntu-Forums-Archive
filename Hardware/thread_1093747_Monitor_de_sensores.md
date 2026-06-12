---
title: "Monitor de sensores"
date: 2009-03-11
forum: Hardware
---

### Post by losoollenos on 2009-03-11
Hola que tal, buenas noches a tod@s.
He instalado el monitor de sensores con el comando "sudo apt-get install sensors-applet lm-sensors" y alguno que otro más. La cuestión es que quisiera estar seguro de qué me indica cada uno (a que corresponden) y, si fuera posible, me digan si son valores "normales". Es que en realidad sólo esperaba encontrarme con un indicador de temperatura del micro y no mucho más, no imaginaba que había tantos sensores, supongo que en el mother?
El panel ahora tiene estos indicadores:
 
CPU 40ºC
temp1 40ºC
Core0 Temp 7º----(este se repete pero el otro indica 6º)
Core1 Temp 5ºC---(  "   "    "     "    "   "     "  11º)
fan1 2960 RPM----(  "    "   "     "    "   "     "  0º)
temp1 16ºC
temp2 32ºC
temp3 25ºC
(disculpen, no se cómo poner el cerito de grados....)

Después en propiedades vi que hay un montón de sensores más.......agrego/quito alguno a la lista?

Muchísimas gracias a todos !!!!

saludos

---

### Post by MeduZa on 2009-03-11
podes poner o quitar el que quieras, tambien dependiendo del motherboard capas tengas que hacer correcciones, en la pagina de lm-sensors hay informacion y ademas capas este el .conf para tu motherboard

---

### Post by guillermolisi on 2009-03-11
> **losoollenos said:**
> Hola que tal, buenas noches a tod@s.
He instalado el monitor de sensores con el comando "sudo apt-get install sensors-applet lm-sensors" y alguno que otro más. La cuestión es que quisiera estar seguro de qué me indica cada uno (a que corresponden) y, si fuera posible, me digan si son valores "normales". Es que en realidad sólo esperaba encontrarme con un indicador de temperatura del micro y no mucho más, no imaginaba que había tantos sensores, supongo que en el mother?
El panel ahora tiene estos indicadores:
 
CPU 40ºC
temp1 40ºC
Core0 Temp 7º----(este se repete pero el otro indica 6º)
Core1 Temp 5ºC---(  "   "    "     "    "   "     "  11º)
fan1 2960 RPM----(  "    "   "     "    "   "     "  0º)
temp1 16ºC
temp2 32ºC
temp3 25ºC
(disculpen, no se cómo poner el cerito de grados....)

Después en propiedades vi que hay un montón de sensores más.......agrego/quito alguno a la lista?

Muchísimas gracias a todos !!!!

saludos
Y si nos das una idea de que hardware tenes enuso y monitoreado con lm-sensors podriamos darte alguna informacion mas precisa.

Aparentemente y si no entendi mal, pareceria que tenes un Core2Duo (dos CPU con dos nucleos y te marca la temperatura para cada par de nucleos por CPU). Ademas te da la lectura de la temperatura del procesador completo (el chip en su totalidad).

Luego tenes que ubicar la temperatura de la motherboard (en realidad es del chipset) y pareceria que tambien te mide temperatura de discos o video.

Las vueltas en rpm son del fan del procesador.

No tomes lo que estoy diciendo al pie de la letra ya que desconozco totalmente que hardware tenes. Es solo un intento de acercamiento a lo que podria ser.

---

### Post by losoollenos on 2009-03-11
Es un athlon x2 5200, mother Ecs geforce6100pm-m2, disco samsung 500gb, 2gb ram 800, todo on-board....

saludos

---

### Post by guillermolisi on 2009-03-12
> **losoollenos said:**
> Es un athlon x2 5200, mother Ecs geforce6100pm-m2, disco samsung 500gb, 2gb ram 800, todo on-board....

saludos
Bien, entonces recurriendo a la info tecnica de la motheboard podrias saber cuantos sensores posee y que monitorean en cada caso. Luego intentar establecer, en base a temperaturas razonables para cada componente, que sensor esta siendo representado con que nombre por LM-Sensors.

Otra posibilidad es que te instales sensors-applet ([http://sensors-applet.sourceforge.net](http://sensors-applet.sourceforge.net)), si usas Gnome, que posiblemente te ayude a clarificar tus dudas al respecto. Despues, si no te gusta, retiras de la barra los monitores que no queres ver y listo.

---

### Post by pabloatilio on 2009-03-12
> **losoollenos said:**
> Hola que tal, buenas noches a tod@s.
He instalado el monitor de sensores con el comando "sudo apt-get install sensors-applet lm-sensors" y alguno que otro más. La cuestión es que quisiera estar seguro de qué me indica cada uno (a que corresponden) y, si fuera posible, me digan si son valores "normales". Es que en realidad sólo esperaba encontrarme con un indicador de temperatura del micro y no mucho más, no imaginaba que había tantos sensores, supongo que en el mother?
El panel ahora tiene estos indicadores:
 
CPU 40ºC
temp1 40ºC
Core0 Temp 7º----(este se repete pero el otro indica 6º)
Core1 Temp 5ºC---(  "   "    "     "    "   "     "  11º)
fan1 2960 RPM----(  "    "   "     "    "   "     "  0º)
temp1 16ºC
temp2 32ºC
temp3 25ºC
(disculpen, no se cómo poner el cerito de grados....)

Después en propiedades vi que hay un montón de sensores más.......agrego/quito alguno a la lista?

Muchísimas gracias a todos !!!!

saludos

En principo los valores son normales, por lo menos en cuanto a temperatura de cpu, temperatura del mother, velocidad del ventilador (si es un cooler estándar está funcionando un poco rápido pero es un valor normal y depende de algunos factores que te cuento más adelante). 

Tendrías que ver en el manual de tu mother y de tu micro cuales son los sensores que trae y consultar los valores normales de trabajo para ellos, ya que varían un poco dependiendo del fabricante, además, los equipos más viejos como por ej el que tengo yo no te da 40º de CPU ni por casualidad (en verano), 60º mínimo y gracias.

En especial con las temperaturas tenes que tener presente que el valor "normal" depende de la temperatura ambiente, de si la cpu está funcionando al 100 % o no, de si el disipador del micro y la mother están BIEN limpios, de si la grasa siliconada que va entre ellos no esta reseca o vieja, de si tu gabinete tiene ventiladores extras que hagan circular el aire correctamente, o si todos los cables y cosas de dentro del gabinete están correctamente dispuestas para que el aire pueda circular libremente. Además las nuevas tecnologías de fabricación de procesadores lograron componentes que trabajan con menores temperaturas que por ej equipos de hace 3 años atrás.

La velocidad del cooler o ventilador, según cómo hayas configurado la bios puede ser constante o variable adaptándose a los picos de trabajo del cpu, o le podés indicar una temperatura de referencia que la bios trata de mantener, adaptando la velocidad del ventilador.

Otro aspecto que te puede influir en la temperatura, sobre todo del mother, es la capacidad (en watts) de la fuente de alimentación y si la misma cuenta o no con ventiladores propios que ayuden a una correcta circulación del aire.

En fin, hay muchas otras cosas a tener en cuenta. ¿Los sensores los instalaste por algún problema puntual que estás teniendo con el hardware ?

Saludos

Pablo A

---

### Post by losoollenos on 2009-03-12
Gracias por la atención y los aportes, ahora se por dónde seguir.....cualquier cosa consulto.
La idea de monitorear es porque cambié mother-micro y como dicen que Amd es delicado con la temperatura, que cualquier problemita "vuela", me pareció útil este applet, eso es todo.

Saludos y gracias

---

### Post by guillermolisi on 2009-03-12
> **losoollenos said:**
> Gracias por la atención y los aportes, ahora se por dónde seguir.....cualquier cosa consulto.
La idea de monitorear es porque cambié mother-micro y como dicen que Amd es delicado con la temperatura, que cualquier problemita "vuela", me pareció útil este applet, eso es todo.

Saludos y gracias
El verdadero y autentico Ubuntero criollo siempre cuida muy bien del entorno donde vive su Ubuntu querido monitoreando los componentes mas sensibles ;)

---

### Post by losoollenos on 2009-03-12
Bueno yo no me podré quizás llamar "verdadero ubuntero criollo", pero sí se que ya no podré sacar mi Ubuntu del alma, y no soy romantiquero......

Saludos y gracias a todos !!!

---

### Post by kornykyano on 2009-03-13
ya que salio el tema, ademas de **sensors** instalá para monitorear el CPU **Computer Temperatura Monitor** con:

**sudo apt-get install computertemp**

mas info: [http://computertemp.berlios.de/index.php]("http://computertemp.berlios.de/index.php")

Se agrega en el panel y lo controlas cada segundo ;)

Saludos.

---

