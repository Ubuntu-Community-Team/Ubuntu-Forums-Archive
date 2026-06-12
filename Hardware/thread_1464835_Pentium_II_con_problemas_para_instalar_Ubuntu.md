---
title: "Pentium II con problemas para instalar Ubuntu"
date: 2010-04-28
forum: Hardware
---

### Post by Inconsciente_Colectivo on 2010-04-28
¡Hola a todos! Es mi primera vez en este foro, es más, recién me registré por un problema que tengo.

Pues, tengo una PC Compaq cuyos datos relevantes son que tiene un Pentium II y una memoria de 64 Mb. en RAM junto con otra de 512 que le agregué hoy. Más datos no tengo, la PC es viejita.

Cuando traté de instalar Ubuntu la primera vez lo que pasó fue que no quería arrancar y saltaba el cartel de "Panic_Kernel" porque tenía memoria RAM insuficiente. Por eso, le agregué una de 512 ahora porque Windows 98 no va más y leí por ahí que un Pentium II y Ubuntu son perfectos.

Ahora, después de que me tomara los cambios recientes en el hardware, trato de instalar Ubuntu, arrancando con la opción de instalar y luego tratando de entrar a Ubuntu sin modificar nada del PC, o sea, con el arrancando usando el CD. Dado esto, me saltan dos errores. Si opto por la primera me salta, en la última línea error, el siguiente mensaje: "Kernel_thread_helper+0x7/0x10". Si voy por la segunda, éste (en la última línea de error": "i386_start_kernel+0x7c/0x83". Cito sólo la última línea de cada error respectivamente porque el log de error largo.

PD: Leí también que puede ser un error de la memoria RAM. Si dejo la nueva, la PC no prende, no muestra nada en el monitor y hace un pitido corto y dos largos simbolizando el error en las memorias RAM. Pero si dejo la vieja y la nueva, anda joya. No importa en cuál de los tres slots ponga la nueva memoria, la PC no arranca. Sólo lo hace con la vieja.

Espero que me puedan ayudar porque ya quiero tener Ubuntu en esta PC cavernícola.

Muchas gracias a todos por cualquier ayuda que puedan aportarme.

Salu2, ;)

---

### Post by guillermolisi on 2010-04-28
Por lo que comentas pareceria que alguna de las placas de memoria no esta del todo buena o no son completamente compatibles. Ademas, habria que revisar en el BIOS que parametros de trabajo estan configurados para con la memoria RAM (entre ellos, la velocidad por ejemplo).
No me parece bien que la maquina no quiera iniciar solo con la placa de RAM nueva.

Podrias pasar caracteristicas de las placas RAM que estas usando ? Esto es, capacidad, velocidad/ancho de banda operativo (100Mhz, 133Mhz, 66Mhz, etc.), densidad de cada banco de memoria (esto es algo mas dificil de averiguar sin conocer modelos de los chips).

Luego, que version de Ubuntu queres instalar y que uso le vas a dar a esa maquina ?

---

### Post by Inconsciente_Colectivo on 2010-04-28
> **guillermolisi said:**
> Por lo que comentas pareceria que alguna de las placas de memoria no esta del todo buena o no son completamente compatibles. Ademas, habria que revisar en el BIOS que parametros de trabajo estan configurados para con la memoria RAM (entre ellos, la velocidad por ejemplo).
No me parece bien que la maquina no quiera iniciar solo con la placa de RAM nueva.

Podrias pasar caracteristicas de las placas RAM que estas usando ? Esto es, capacidad, velocidad/ancho de banda operativo (100Mhz, 133Mhz, 66Mhz, etc.), densidad de cada banco de memoria (esto es algo mas dificil de averiguar sin conocer modelos de los chips).

Luego, que version de Ubuntu queres instalar y que uso le vas a dar a esa maquina ?

¡Hola, Guillermolisi! Gracias por responder. Me había olvidado de aclarar las características de las memorias RAM: La nueva, supongo que de marca genérica porque ni siquiera venía en blister, es un modelo PC-133. Con densidad de banco de memoria, me mataste. Probablemente tenga que configurar el jumper. También leí de gente que compraba esas mismas memorias para utilizarlas en PCs como por ejemplo IBM y no andaban. En este caso, me tira un pitido corto y dos largos que son insoportables por el simple hecho de que la memoria debería ser compatible con la PC pero no me la toma.

En cuando a la distro de Ubuntu que pensaba instalarle era la versión Ubuntu Karmic Koala 9.10.

Me voy a poner a indagar en el asunto para ver si realmente hay que cambiar el jumper de la Motherboard porque es imposible que no me tome el módulo nuevo de la RAM.

EDIT: También me olvide de mencionar que el módulo viejo sólo funciona en el primer slot, en los demás, no.

Muchas gracias.

Salu2! ;)

---

