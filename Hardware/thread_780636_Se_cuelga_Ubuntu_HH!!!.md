---
title: "Se cuelga Ubuntu HH!!!"
date: 2008-05-03
forum: Hardware
---

### Post by _kAz_ on 2008-05-03
Nunca creí que iba a decir esto, pero se me está colgando Ubuntu en repetidas y consecutivas ocasiones.

Estoy haciendo algo de lo más bien y de repente se para en seco, o sea ni siquiera empieza a "cargarse de actividad", sino que es de golpe, se tilda el puntero y ya sé que no hay vuelta atrás. A alguien más le pasa algo así???

Posible causas que presumo:
1. Firefox **BETA** :roll:
2. Transmission
3. Firefox Beta+Transmission (a este le pongo todas las fichas)
4. Todo lo anterior combiando con AWN.

Me pinta que tiene que ver más con Firefox porque me parece que sucede cuando está cargando alguna página, llega al 80% más o menos y ahí palmó.

En consecuencia no me queda otra que reiniciar. Recién lo tuve que hacer 3 veces en un lapso de 10 minutos ](*,).

---

### Post by RATM_Owns on 2008-05-03
¿Es su computadora anticuada? Si es así considere el usar de Xubuntu. ¿Si no, cuánto RAM usted tiene? Realmente no entendía lo que usted dijo. Apesadumbrado. xD

Estoy utilizando una cosa en línea del traductor. Apesadumbrado si suena extraña.

---

### Post by _kAz_ on 2008-05-03
Sí, suena extraño :lol: :lol: :lol: :lol:

El inconveniente puntual es que la máquina se para, se tilda de repente.

La computadora es una Pentium IV y tiene sus buenos 2 años. Ahora tiene 712 mb de RAM (originalmente eran 256).

---

### Post by MetallicA15 on 2008-05-03
> **_kAz_ said:**
> Sí, suena extraño :lol: :lol: :lol: :lol:

El inconveniente puntual es que la máquina se para, se tilda de repente.

La computadora es una Pentium IV y tiene sus buenos 2 años. Ahora tiene 712 mb de RAM (originalmente eran 256).

problemas con capacidad de RAM no parece ser....

¿esto te pasaba antes ?

fijate que por ahí lo único que se me ocurre es que el micro levante mucha temperatura o la instalación está defectuosa.

No quiero ser erroneo, pero es lo que se me pasa ahora por la cabeza.... Puede ser que sea un problema de la versión ? =S

---

### Post by _kAz_ on 2008-05-03
Nop... no me pasaba, o quizás no tan asiduamente. Instale Hardy Heron el martes pasado, pero me parece que el problema ha sido más en los últimos días.

Quizás sea que esta muy atareada en ese momento. Recuerdo que además de lo que me pasa cuando está Firefox, en algun momento también se quería tildar el emesene mientras escribia -usando transmission además-, pero no paso a mayores y no volvio a molestar.

El denominador común de esos cuelgues es el Firefox, a lo mejor será porque es versión beta todavía; es lo unico que se me ocurre.

---

### Post by Hei Ku on 2008-05-03
Hay distintos niveles de cuelgue, y depende de cada uno, se puede mas o menos saber la causa.
Cuando se cuelga:
- se mueve el mouse?
- podes cambiar a una consola apretando Ctrl+F1?
- si apretas el bloqueo de mayusculas, la luz del teclado prende y apaga?
- el disco tiene actividad mientras pasa esto?
- te podes conectar remotamente a la maquina? Te permite loguearte por ssh, ftp, etc?
- tenes instalado Compiz o alguno similar?

De acuerdo a las respuestas, seguimos viendo.

---

### Post by _kAz_ on 2008-05-03
> **Hei Ku said:**
> Hay distintos niveles de cuelgue, y depende de cada uno, se puede mas o menos saber la causa.
Cuando se cuelga:
1. se mueve el mouse?
2. podes cambiar a una consola apretando Ctrl+F1?
3. si apretas el bloqueo de mayusculas, la luz del teclado prende y apaga?
4. el disco tiene actividad mientras pasa esto?
5. te podes conectar remotamente a la maquina? Te permite loguearte por ssh, ftp, etc?
6. tenes instalado Compiz o alguno similar?

De acuerdo a las respuestas, seguimos viendo.

1. El mouse se queda congelado.
2. No probe esa combinación, la proxima vez me fijo.
3. Idem a la anterior. Calculo que el teclado tampoco responde porque le doy a Ctrl+Aly+Supr y nada.
4. Creo que el disco parece seguir trabajando... pero a media máquina, como si funcionara normalmente
5. Chino basico para mi, jeje.
6. El compiz parece que está instalado, pero no tengo ninguno de esos efectos raros del cubo o esas cosas, supongo que las tengo que ir agregando.

---

### Post by pol666 on 2008-05-03
es que con Crtl alt spr no pasa nunca XD


pra reiniciar el entorno grafico 

Ctrol + alt +Backspace


Igual no justifica que se te tilde :\

---

### Post by Hei Ku on 2008-05-03
hasta saber si se cuelga el teclado tambien, puede ser algo con Firefox. En alguna epoca, con Flash o cuando se morfaba mucha memoria, el procesador se iba a tope y la maquina dejaba casi de responder. Con paciencia, apretando Ctrl+Alt+F1, logueandome por consola y poniendo top podia ver el proceso que estaba descontrolado y matarlo.
Asi que esperemos hasta que te pase la proxima (espero que sea dentro de muuuucho tiempo) y vemos que pasa. La prueba del teclado es clave. Si las luces se cuelgan, es que el cuelgue es irrecuperable. Y gralmente apunta a un problema de hardware.

---

### Post by clasificado on 2008-05-03
> **_kAz_ said:**
> sino que es de golpe

A mi pc le pasaba. Al principio creia que era aleatorio, pero despues vi que era con ciertos programas

Al final, descubrí que eran mis drivers propietarios NVIDIA. Cuando cambiaba al open source "nv" funcionaba joya.

Afinando la configuración de mi xorg pude hacerlo andar con "nvidia" y 3d y toda la perinola.

clasificado

---

### Post by _kAz_ on 2008-05-03
Quizás tenga que ver eso... Yo tengo una ATi Radeon 9550 creo, y está funcionando con los drivers que vienen por defecto en Ubuntu (controlador de hardware privativo), pero no con drivers "propios" por decirlo de alguna manera. En Kubuntu nunca lo pude instalar correctamente y plenamente funcional -nunca me salía en la consola que estuviera ok la aceleración 3D-, veré ahora en ubuntu que onda.

---

### Post by Hei Ku on 2008-05-03
En las ATI, si tu placa esta soportada por el driver libre te conviene usar ese. Es mas estable, aunque un poco mas lento. Pero realmente anda de 10 para la mayoria de las cosas.

---

### Post by niko_3100 on 2008-05-04
A mi tambien se me estaba colgando y creeo que era por usar netbeans o eclips (ide de desarrollo en java) probe dos java 1.5 y seguia colgandose, cambia a java 6 y al parecer pude arreglarlo, lo unico malo es que en el laburo programamos con java 5 y no 6 pero bue... para casos extremos....

---

### Post by zql9000 on 2008-05-06
A mi tambien se me cuelga, lo primero que se me ocurrio fue reinstalar todo, ya que era una instalacion nueva (estoy empezando a usar ubuntu).
Anteriormente habia probado la GG y se me habia colgado una sola vez. En esta version (la HH) se me colgo varias veces de las cuales 2 veces fueron al hilo...

Una vez se me colgo, y me quede esperando unos 3 minutos y volvio a responder, pero no es muy practico esperar todo ese tiempo...

Las veces que se me colgo estaba haciendo cosas distintas y solo tenia 2 aplicaciones abiertas, asi que no creo que sea por memoria (tengo 1GB de RAM).

No busque nada en internet, ni mire logs porque como dije antes, lo primero que se me ocurrio fue reinstalar.

Saludos!

---

### Post by Mister X on 2008-05-06
Muy pocas veces los cuelgues son irrecuperables. Si el teclado deja de responder, se puede intentar acceder por ssh (el limitante es que debemos tener otra maquina en red). Abrimos una consola remota, matamos el proceso rebelde y a seguir trabajando)

---

### Post by niko_3100 on 2008-05-11
Se me sigue colgando muchachos a alguno tambien les pasa?

---

### Post by _kAz_ on 2008-05-12
Me paso un par de veces más, pero no tan seguidas como cuando postee por primera vez.

El inconveniente ahora es que probe lo que me dijeron, de apretar las teclas a ver si respondian (por ejemplo el Bloq Mayús) y NADA; debo suponer que es un problema de hardware???

---

### Post by niko_3100 on 2008-05-12
No se, no creo porque el otro dia estube en xp haciendo cosas en C para la facu y estubo todo el dia y no se colgo nunca, debe haber algo mal, un bug de esos molestos...

---

### Post by eldragon on 2008-05-12
ok, probaron los comandos directos al kernel sysrq?

de esta manera se pueden fijar si el kernel deja de responder completamente o si es un tema externo al mismo.

vean: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

yo probaria:
```

alt - sysrq - s  (sincroniza las particiones montadas, en caso de que haya quedado algo en cache, lo flushea)
alt - sysrq - u  (remonta en read-only todas las particiones)
alt - sysrq - o (apaga el sistema

```

apretarlas por un segundo una combinacion a la vez
si esto responde, quiere decir que el kernel todavia funciona. y algun modulo esta rompiendo las catingas.

en fin, vale la pena probar con otros kernels. instalenlos desde synaptic y booteen con ellos a ver si el problema persiste.

algo que esta trayendo problemas por lo general es el sound server de pulse. prueben con deshabilitar el sonido. (mute)


todas ideas.

saludos

---

### Post by faktorqm on 2008-05-12
En castellano... [http://doc.ubuntu-es.org/Pet_Sis](http://doc.ubuntu-es.org/Pet_Sis) y tambien [http://www.kalcobrena.com/?p=39](http://www.kalcobrena.com/?p=39) Salu2!!

---

### Post by niko_3100 on 2008-05-12
Uj muy bueno si se em vuelve a colgar pruebo esos comandos a ver que onda.

---

### Post by pol666 on 2008-05-15
Che es verdad para ser una LTS esta MUY inestable

---

### Post by faktorqm on 2008-05-16
los drivers privativos son los que desestabilizan el sistema. Un linux sin nada "extraño" anda de 10. Salu2!

---

### Post by niko_3100 on 2008-05-17
No creo que sea eso, todavia se me sigue colgando y no se por que... tengo mucha bronca jejej!! Igual estoy viendo de hacer una instalacion de cero, sera recomendable?? Aunque admit que es un bajon hacer una instalacion de cero otra ves...:(

---

### Post by _kAz_ on 2008-05-17
> **niko_3100 said:**
> No creo que sea eso, todavia se me sigue colgando y no se por que... tengo mucha bronca jejej!! Igual estoy viendo de hacer una instalacion de cero, sera recomendable?? Aunque admit que es un bajon hacer una instalacion de cero otra ves...:(

A mi también se me sigue colgando LPM!!!!

Encima el jueves estaba haciendo un práctico para la facu y no perdí mucho pero igual te llenas de bronca. Se supone que ESTO ES LINUX, NO DEBERIA PASAR COMO EN WINBUGS!!!

Como ya dije, el denominador común parece ser Firefox, pero a veces pienso que es el sonido (tendrá algo que ver con alsa???).

---

### Post by pol666 on 2008-05-17
a mi se me tilda Gedit, Sinaptyc, y otras cosasa que requieren de administracion

---

### Post by Patchiu on 2008-05-17
A mi no me ha pasado tanto...
Pero alguna que otra vez se me ha colgado..

Lo que si noto, es que esta version comparada con la anterior es LENTISIMA..
A mi la version anterior me andaba de 10.. pero con esta... siempre veo que esta a full, es mas, noto que generalmente tiene tendencia a usar el CPU a full, la Ram hasta la mitad, la memoria de intercambio la usa siempre en porcentaje bajo.

No se cual sera el problema, pero he visto que vaaaarios tienen problemas con HH...
Ojala se solucionen pronto..
Salu2!

---

### Post by pol666 on 2008-05-17
Eso es verdad consume mas memoria y mas CPU pero aun asi anda mas rapido.. Todo anda ams rapido, abre las cosas mas rapido, inicia y cierra con mas velocidad. Pasa archivos a buena velocidad.

---

### Post by WanderingKnight on 2008-05-17
Recuerden que se cambió el scheduler del kernel, gente (el programa que se encarga de administrar los recursos), es probable que por eso sea el tema del elevado uso del CPU que estamos viendo. Yo noto que las cosas andan ligeramente más rápido, aunque se nota que el procesador labura más.

---

### Post by pol666 on 2008-05-17
> **WanderingKnight said:**
> Recuerden que se cambió el scheduler del kernel, gente (el programa que se encarga de administrar los recursos), es probable que por eso sea el tema del elevado uso del CPU que estamos viendo. Yo noto que las cosas andan ligeramente más rápido, aunque se nota que el procesador labura más.


Exacto. mas claro no lo podias decir

---

### Post by alejandro.mc on 2008-05-17
Hola Kaz. Bueno seguramente estas teniendo el problema que estamos teniendo muchos. Hay muchos que no experimentaron, no se si sera compatiblidad con hardware o que, no parece sin embargo, y todavia tampoco le han encontrado la solucion. 

Si entendes ingles te dejo estos dos links donde se posteo mucho, obviamente sin solucion por el momento, y el de launchpad donde ya se registro el bug. Bastante feo por cierto, porque inahibilita todas las funciones y no deja ningun registro de porque se produjo el lockdown. Sospechoso eh? =)

Hay algunos patrones que se registraron como estar usando el firefox, y la multitarea, tipos tener abierto mas de 5 o seis programitas y pum, se lockea.

[http://ubuntuforums.org/showthread.php?t=765510](http://ubuntuforums.org/showthread.php?t=765510)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209830)

Yo estoy experimentando esos locks muy seguido, pasa mucho cuando usas multimedia tambien. 

Saludos!

---

### Post by niko_3100 on 2008-05-18
Sip, yo estoy sufriendo ese bug cada tanto... :( espero se solucione rapido, el tema es que se cuelga totalmente y ni siquiera te loguea el error eso es lo peor.

---

### Post by _kAz_ on 2008-05-18
> **alejandro.mc said:**
> Hola Kaz. Bueno seguramente estas teniendo el problema que estamos teniendo muchos. Hay muchos que no experimentaron, no se si sera compatiblidad con hardware o que, no parece sin embargo, y todavia tampoco le han encontrado la solucion. 

Si entendes ingles te dejo estos dos links donde se posteo mucho, obviamente sin solucion por el momento, y el de launchpad donde ya se registro el bug. Bastante feo por cierto, porque inahibilita todas las funciones y no deja ningun registro de porque se produjo el lockdown. Sospechoso eh? =)

Hay algunos patrones que se registraron como estar usando el firefox, y la multitarea, tipos tener abierto mas de 5 o seis programitas y pum, se lockea.

[http://ubuntuforums.org/showthread.php?t=765510](http://ubuntuforums.org/showthread.php?t=765510)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209830)

Yo estoy experimentando esos locks muy seguido, pasa mucho cuando usas multimedia tambien. 

Saludos!

Bueno, al menos es bueno saber que no soy el único... "mal de muchos consuelo de tontos" :lolflag:

Y es cierto, siempre pasa cuando tengo Exaile y Firefox, pero muchas otras veces sólo tengo Firefox y los mismo pasa, muy posiblemente porque está a full con el flash.

Pregunto, ¿tendrá algo que ver con lo del consumo elevado de la pc como se habla en otro thread? Según Conky el mío nunca baja de 97%.

---

### Post by alejandro.mc on 2008-05-21
Algo asi debe ser. Yo no tengo consumo de cpu alto constante, pero si tengo picos, por ejemplo abro el amarok y se dispara el consumo, y va y viene tan alto el consumo que lagea las otras cosas.

Saludos.

---

### Post by niko_3100 on 2008-05-22
Eso no sera porque tu cpu aumenta y disminuye la velocidad de procesamiento? A mi me hace lo mismo va de 800 a 1600 y 1800, es por el daemon powernowd

---

### Post by Mister X on 2008-05-22
Los que tienen alto consumo de CPU constantemente, identificaron el/los procesos que causan el consumo?
Pueden hacerlo con el comando top

---

### Post by maxkcr on 2008-05-22
yo quise activar los efectos de escritorio y ahora se me queda la pantalla en blanco y lo unico que veo es el puntero del mouse

alguien me puede decir como lo desactivo para volver a la normalidad????

---

### Post by niko_3100 on 2008-05-26
No Puedo Trabajar Con Mi Notebook En Hardy!!!! Si Estoy Gritando, Uso El Netbeans Y Cada 10 Minutos Se Me Cuelga.... Hardyyy!!!!! La Que Te Pario!!!

---

### Post by madelaki on 2008-05-27
Encontraron dos posibles soluciones. Updatear el kernel no le fallo a nadie hasta ahora pero proba el remove antes porque la verdad es mucho mas facil.

1) Updatear el kernel a 2.6.25 
2) sudo apt-get remove powernowd

---

### Post by niko_3100 on 2008-05-27
Yaaaa pruebo con powernowd les comento yo antes de tener hardy tenia feisty la verdad que me andaba de pelos pero con compiz y feisty si tenia activado el powernowd se me alentaba cuando hacia  los efectos, esto no pasa ahora con hardy por eso no tube la necesidad de remover powernowd, pero con esto que me decis ya lo estoy sacando y vuelvo a probar. Yo tengo el kernel 2.6.24 como lo podria actualizar al 2.6.25?? Desde synaptics?? o tendria que bajarme el fuente compilarlo y eso?

---

### Post by oaglp on 2008-05-27
yo tengo una compaq f566la y hardy se me esta colgando cada 2x3 ya no aguanto mas no puedo terminar mi tesis.
antes tenia festy y me funcionaba de 10 y ahora que estoy con hardy se me cuelga muy seguido
tengo instalado los drivers de nvida probe cambiando en la xorg "nvidia" por "nv" y los drives funcionan mal los driver wifi no lo tengo instalado.
la verdad nesesito ayuda ya que no quiero cambiar de distro y yo no quiero usar win

---

### Post by pol666 on 2008-05-27
Para mi el secreto esta en el Kernel medio rayado ese que tiene

---

### Post by oaglp on 2008-05-27
y como hago para cambiar el kernel??

---

### Post by lushnok on 2008-05-29
A mi también se me cuelga... supongo será por algo en el rhythmbox (que lo pario).
En algún udpdate de estos días bajó el kernel 2.6.24-17 (tenía el 16) y en realidad, novato yo, no sé mucho en qué ha variado, más que descajetarme el teclado y no poder ver TN en firefox.

El kernel 25 ¿no está en desarrollo o algo así?

---

### Post by madelaki on 2008-05-29
Prueben con el remove powernowd antes. A mi se me soluciono con eso, no hubo necesidad de updatear el kernel.

---

