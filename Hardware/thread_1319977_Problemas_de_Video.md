---
title: "Problemas de Video"
date: 2009-11-08
forum: Hardware
---

### Post by gran.rodriguez on 2009-11-08
Hola a todos!:

Les cuento, llevo un tiempo ya utilizando Ubuntu. Por problemas con algunos softwares, tuve que volver a Windows hace un par de meses, pero ahora quise volver a instalar Ubuntu y... bueno. Aquí viene el problema.

La instalación va estupendamente bien, superó por completo mis expectativas. Inicia bien también. El problema parte cuando intento utilizar doble monitor. Si reflejo las pantallas, no hay problema, pero cuando intento utilizarlas por separado, los efectos visuales no me andan :S, y en realidad no entiendo por qué. Quise ver si quizás era un problema de controladores, pero al parecer no lo es. 

Buscando en internet encontré algunos comandos para probar en la consola, como este:

glxinfo | grep direct

y el resultado es:
direct rendering: Yes

con "glxgears", aparece que en 5 segundos, tengo en promedio algo de 3000 frames.


Tengo 1536 de Ram, Pentium 4 de 3 GHz, y 400 GB de disco. Una tarjeta gráfica Ati Radeon 9200 de 256.

Espero puedan ayudarme. Saludos :D

---

### Post by Carlos C on 2009-11-09
Cuando dices que quieres usar ambos monitores por separado, ¿te refieres a que deseas tener un escritorio independiente en cada uno o a que quieres extender el escritorio (un gran escritorio que abarque ambos monitores)?

En mi caso mi tarjeta ati no soporta la resolución de un escritorio extendido si ubico ambas pantallas una al lado de la otra. Tengo que juntarlas verticalmente, una arriba de la otra, para que compiz se active. En este momento no estoy en mi computador, por lo que no puedo decirte cuál es la resolución máxima que mi ati soporta, pero te sugiero que por ahora pruebes ubicando las pantallas verticalmente para ver si ese es el problema.

Saludos.

---

### Post by moreback on 2009-11-09
Pienso que puede ser un problema de Compiz, ya que yo con mi tarjeta Intel he notado que al hacer presentaciones con un datashow, si extiendo el escritorio quedando en 1280x800 + 1024x768, quedando esta última en el proyector, noto que hay una franja donde no se dibuja el fondo y de hecho no se borra nada que uno ponga ahí (se ve un lindo efecto cuando arrastro una ventana por esa zona).

---

### Post by gran.rodriguez on 2009-11-09
Probé lo de poner las pantallas en vertical, pero no pasa nada. De hecho, ahora ya no puedo volver a la configuración que tenía antes, al salir de la sesión (lo pide al momento de aplicar cambios) y al volver a entrar, las pantallas aparecen duplicadas. 

Cuando hablo de utilizar las dos pantallas, me refiero a extender el escritorio. 

En realidad ya no sé que más podrá ser, compiz funciona sin ningún problema cuando utilizo un monitor o duplico las pantallas, el problema viene cuando intento extender el escritorio.

A veces, sucede que claro, puedo utilizar compiz con las dos pantallas, pero sólo si el fondo de escritorio (misteriosamente, y no por algo que yo haya hecho), se pone negro :S, se pone negro y no veo ningún icono, y tampoco puedo poner yo un wallpaper. Lo curioso, es que cuando está así, al momento de cerrar sesión, por un instante se logra visualizar el wallpaper... qué dicen?, será un asunto de configuración?

---

### Post by moreback on 2009-11-10
Yo creo que es algo de Compiz, probaste extender el escritorio con los efectos desactivados? (es decir con metacity --replace)

---

