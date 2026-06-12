---
title: "Cuelgues Repentinos. Acer Aspire One + Ubuntu 9.10"
date: 2010-04-03
forum: Hardware
---

### Post by Astantler on 2010-04-03
Saludos a todos:



Veran, tengo un gran problema con Ubuntu 9.10, estoy desesperado (Me ha tocado a punta de Windows XP :( ).
He instalado la Distro en un Netbook Acer Aspire One ZG5 (Intel Atom N270 1.6GHz, 1GB RAM, 8.9" Scrn, Intel GMA 950 Chipset).
Todo va muy bien, hasta que de un momento a otro, sin razon alguna el SO muere, se congela, el puntero no responde ni tampoco el teclado, me toca apagarlo de la manera "Mala".
Lo mas curioso de este problema es que el cuelgue es aleatorio, no se da haciendo alguna accion predeterminada, simplemente puede que abras Firefox, y muere, Abras la Terminal, y muere, estes copiando un archivo, y muere. Lo peor de todo es que reinstale de nuevo la Distro, y solo pasaron 5min desde que entre al sistema "Nuevo", abri la terminal para instalar los restricted-extras y murio, solo 5min despues de haber iniciado por primera vez con el sistema nuevo.

Le he dado la vuelta a google tratando de buscar alguna solucion para este problema, y en efecto, se reportan cuelgues, pero por razones predeterminadas, a las cuales les trato de dar "solucion", pero todo sigue igual, y la verdad estoy desesperado por no poder trabajar en mi "entorno natural".

Cabe aclarar que no uso compiz, no lo he instalado en ninguna ocasion, ya que de eso se discute mucho como la causa del cuelgue. La resolucion tambien es normal (En este caso: 1024x600). Incluso llegue a instalar Kubuntu 9.10, y en efecto, el mismo problema surgia.

Alguien por favor podria orientarme un poco acerca de este problema? Si algien puede ayudarme, se le agradecería en el alma!

---

### Post by guillermolisi on 2010-04-03
Todo pareceria indicar que la causa de los cuelgues esta relacionada con el hardware.
Podria ser memoria y/o exceso de temperatura.

---

### Post by Astantler on 2010-04-03
> **guillermolisi said:**
> Todo pareceria indicar que la causa de los cuelgues esta relacionada con el hardware.
Podria ser memoria y/o exceso de temperatura.

guillermolisi, pero, si fueran problemas de HW, Los Otros SO deberian fallar, no? Este equipo Tuvo Windows 7, tiene XP y Ubuntu 9.10 en este momento, y ps, por este mismo problema me ha tocado trabajar siempre en XP, y nunca me ha pasado un cuelgue de esos, ni reinicios, ni BSoD's ni nada que sospeche problemas con HW. He descartado practicamente todo, y sigue igual...

---

### Post by guillermolisi on 2010-04-03
> **Astantler said:**
> guillermolisi, pero, si fueran problemas de HW, Los Otros SO deberian fallar, no? Este equipo Tuvo Windows 7, tiene XP y Ubuntu 9.10 en este momento, y ps, por este mismo problema me ha tocado trabajar siempre en XP, y nunca me ha pasado un cuelgue de esos, ni reinicios, ni BSoD's ni nada que sospeche problemas con HW. He descartado practicamente todo, y sigue igual...
Veamos, como para confirmar que entiendo bien la situacion:

La maquina vino con Windows originalmente y luego le cambiaste/agregaste otro sistema operativo y desde su instalacion y hasta algun momento no muy lejano, tanto Win como otros SOs funcionaban sin cuelgues o solo funciona bien cuando estas con Win ?

Con Ubuntu 9.10 siempre, desde el inicio, tuviste estos problemas de cuelgues o tuvo su momento de estabilidad ?

Si inicias la maquina con un Live pendrive de Ubuntu, tambien se cuelga ?

---

### Post by Astantler on 2010-04-03
> **guillermolisi said:**
> Veamos, como para confirmar que entiendo bien la situacion:

La maquina vino con Windows originalmente y luego le cambiaste/agregaste otro sistema operativo y desde su instalacion y hasta algun momento no muy lejano, tanto Win como otros SOs funcionaban sin cuelgues o solo funciona bien cuando estas con Win ?

Con Ubuntu 9.10 siempre, desde el inicio, tuviste estos problemas de cuelgues o tuvo su momento de estabilidad ?

Si inicias la maquina con un Live pendrive de Ubuntu, tambien se cuelga ?


No, la maquina no se cuelga al iniciar con el Pendrive, al contrario, es el momento donde mas bien rinde, no hay cuelgues ni problemas. La maquina vino con Windows XP, le instale Windows 7, junto con Ubuntu, me aburri de 7 por problemas con el y me devolvi a XP, volvi a instalar Ubuntu junto con XP y el problema persiste, llevo mas de un mes en las mismas, con Netbook Remix es la misma cosa, al igual que con Kubuntu. 

[I]"La maquina vino con Windows originalmente y luego le cambiaste/agregaste  otro sistema operativo y desde su instalacion y hasta algun momento no  muy lejano, tanto Win como otros SOs funcionaban sin cuelgues o solo  funciona bien cuando estas con Win ?" 

[/I]Como te digo, originalmente vino con XP, el SO que agregue fue ubuntu, y siempre el de los fallos fue Ubuntu, Windows no ha fallado (Cosa muy extraña, no?)

Espero haberme hecho entender....

---

### Post by guillermolisi on 2010-04-03
> **Astantler said:**
> No, la maquina no se cuelga al iniciar con el Pendrive, al contrario, es el momento donde mas bien rinde, no hay cuelgues ni problemas. La maquina vino con Windows XP, le instale Windows 7, junto con Ubuntu, me aburri de 7 por problemas con el y me devolvi a XP, volvi a instalar Ubuntu junto con XP y el problema persiste, llevo mas de un mes en las mismas, con Netbook Remix es la misma cosa, al igual que con Kubuntu. 

[I]"La maquina vino con Windows originalmente y luego le cambiaste/agregaste  otro sistema operativo y desde su instalacion y hasta algun momento no  muy lejano, tanto Win como otros SOs funcionaban sin cuelgues o solo  funciona bien cuando estas con Win ?" 

[/I]Como te digo, originalmente vino con XP, el SO que agregue fue ubuntu, y siempre el de los fallos fue Ubuntu, Windows no ha fallado (Cosa muy extraña, no?)

Espero haberme hecho entender....
Sabes si el BIOS de esa maquina tiene alguna opcion especial para Win ?
Generalmente es una ampliacion a la caracteristica que define si el OS es "Plug'n play". En algunas maquinas modernas le han agregado WinXP, WinVista, OtherOS, etc.
Me ha pasado que sin haber revisado antes, comienzo la instalacion y despues vienen los problemas hasta que cambio de Win<lo_que_sea> a OtherOS y todo vuelve a la normalidad.

Me llama la atencion que desde el Livependrive funciona bien. No sera la configuracion de la interface de discos rigidos IDE/SATA en el BIOS ?

Como ves, pueden ser varias las posibilidades.

---

### Post by Astantler on 2010-04-03
> **guillermolisi said:**
> Sabes si el BIOS de esa maquina tiene alguna opcion especial para Win ?
Generalmente es una ampliacion a la caracteristica que define si el OS es "Plug'n play". En algunas maquinas modernas le han agregado WinXP, WinVista, OtherOS, etc.
Me ha pasado que sin haber revisado antes, comienzo la instalacion y despues vienen los problemas hasta que cambio de Win<lo_que_sea> a OtherOS y todo vuelve a la normalidad.

Me llama la atencion que desde el Livependrive funciona bien. No sera la configuracion de la interface de discos rigidos IDE/SATA en el BIOS ?

Como ves, pueden ser varias las posibilidades.


Guillermolisi: Si, este PC tiene la opcion "D2D Recovery" en la BIOS, que sinceramente, creo (mas no estoy seguro) que cuando se activa, al encender el PC, en la pantalla POST de la BIOS, al Teclear ALT+F10, automaticamente te lleva al programa de recuperacion de acer, que lo que hace es ponerte tu pc como vino de fabrica (Osea, con WXP), se me habia olvidado mencionarlo, hay una particion oculta, que precisamente trae XP mas todos los Drivers.
La configuracion de los Discos? La verdad no me he fijado en ello,pero si te refieres al "Modo de Compatibilidad SATA", la verdad no lo he visto en la BIOS, aunque voy a revisar ese detalle y te lo comentaré, es que hasta a mi se me hace extraño que desde el Pendrive no pone ningun problema, luego de instalado...

---

### Post by guillermolisi on 2010-04-03
> **Astantler said:**
> Guillermolisi: Si, este PC tiene la opcion "D2D Recovery" en la BIOS, que sinceramente, creo (mas no estoy seguro) que cuando se activa, al encender el PC, en la pantalla POST de la BIOS, al Teclear ALT+F10, automaticamente te lleva al programa de recuperacion de acer, que lo que hace es ponerte tu pc como vino de fabrica (Osea, con WXP), se me habia olvidado mencionarlo, hay una particion oculta, que precisamente trae XP mas todos los Drivers.

Entiendo, pero no me referia a la recuperacion/restauracion/reinstalacion del OS original sino a una opcion que tienen los BIOS modernos para asignar interrupciones de hardware a cada dispositivo utilizando la funcionalidad Plug and Play del sistema operativo. He visto motherboards que te permitian establecer genericamente que el SO a utilizar poseia la capacidad P&P, otros mas especificamente te preguntaban que version de Win usarias para iniciar la PC. Con cada eleccion se modifican varios parametros del BIOS y me ha pasado que estando configurado WinVista en esa opcion no podia instalar WinXP, para mencionar un caso homgeneo con Win, porque al iniciar XP me daba una BSoD, hasta que me avive y lo puse como correspondia. Luego cero problemas.
> La configuracion de los Discos? La verdad no me he fijado en ello,pero si te refieres al "Modo de Compatibilidad SATA", la verdad no lo he visto en la BIOS, aunque voy a revisar ese detalle y te lo comentaré, es que hasta a mi se me hace extraño que desde el Pendrive no pone ningun problema, luego de instalado...Dale. Cuando inicias desde el Livependrive no usas disco ni su interface IDE/SATA.

---

### Post by Astantler on 2010-04-03
> **guillermolisi said:**
> Entiendo, pero no me referia a la recuperacion/restauracion/reinstalacion del OS original sino a una opcion que tienen los BIOS modernos para asignar interrupciones de hardware a cada dispositivo utilizando la funcionalidad Plug and Play del sistema operativo. He visto motherboards que te permitian establecer genericamente que el SO a utilizar poseia la capacidad P&P, otros mas especificamente te preguntaban que version de Win usarias para iniciar la PC. Con cada eleccion se modifican varios parametros del BIOS y me ha pasado que estando configurado WinVista en esa opcion no podia instalar WinXP, para mencionar un caso homgeneo con Win, porque al iniciar XP me daba una BSoD, hasta que me avive y lo puse como correspondia. Luego cero problemas.
Dale. Cuando inicias desde el Livependrive no usas disco ni su interface IDE/SATA.

Perfecto, ya te entendi, voy a explorar la BIOS y te comentare en las proximas horas que obtengo, lo mas certero que te puedo decir en este momento, si te es de ayuda es que la bios es de marca "InsydeH2O", revisare parametro por parametro y te reportaré lo que obtenga.

Agradezco muchisimo la ayuda que me has brindado

---

### Post by Lucas-A on 2010-04-04
Hola, que tal no se si te sirva de mucho esta info, pero a mi me pasó con una Acer aspire 5315 que funcionaba perfecto en XP y vista.. pero se apagaba "Erraticamente" en algunas distribuciones como ubuntu. Resultó ser con ubuntu no funcionaba el cooler. El timpo que andaba dependía de la temp ambiente, y de la exigencia que se le hacía al micro.  Todo se solucionó con una actualización del bios.
Para descartar esto, tendrías que correr alguna aplicación pesada en ubuntu, y fijarte si sentís que el cooler funciona.

suerte con eso.

Saludos, Lucas

---

### Post by Astantler on 2010-04-30
Hola Guillermolisi:


No se si estaras por ahi, espero aceptes mis disculpas por no haber respondido en este hilo, se que no se debe hacer, pero debido a problemas ajenos a mi he estado ausente durante un buen tiempo. Y bien, vuelvo aqui en tu ayuda. Ayer ha saludo Ubuntu 10.04, y con la esperanza de que fuera algun bug de la 9.10, me apresure a descargarlo e instalarlo. todo fue normal. Despues de haber reiniciado e intentar probar el sistema, a los 5 min de estar interactuando con el, murio... Estoy realmente desesperado, no se que hacer, en la Wiki de ubuntu no hhay casos por el estilo documentados y los foros a los que he recurrido y consultado no han sido de ayuda. Todo es absolutamente normal, entonces no entiendo que pasa. Estoy condenado a no poder usar Ubuntu en mi Netbook?

He revisado la temperatura, y pues la verdad el "chiquito" no esta caliente, ni nada por el estilo, no he revisado la temperatura desde algun programa, ya que por el mismo problema de los cuelgues, me es imposible trabajar aunque sea 5min sin que pase el misterioso Freeze.
Disculpame si te molesto una vez mas, pero no se te ocurre algo mas que pueda ser?

Muchisimas gracias

---

### Post by alfplayer on 2010-04-30
En la web hay información de usuarios que usan un módulo de kernel llamado acerhdf para controlar la temperatura.

Agrego: si se resuelve con una actualización de BIOS puede ser que ubuntu nunca lo resuelva.

---

### Post by guillermolisi on 2010-05-01
> **alfplayer said:**
> En la web hay información de usuarios que usan un módulo de kernel llamado acerhdf para controlar la temperatura.

Agrego: si se resuelve con una actualización de BIOS puede ser que ubuntu nunca lo resuelva.
Alf, algun link que hayas leido al respecto como para recomendarle o una punta de como utilizan ese modulo ? Va en /etc/modules ? Va en el Grub ?

---

### Post by sitiomatic on 2010-05-02
No pusiste que modelo de AAO tenes y no todos los modelos tienen los mismos problemas y soluciones.
Leete primero las soluciones que dan aqui para tu modelo. [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")
Yo tengo una ao751h, use bastante Ubuntu 9.04 y siguiendo los consejos de esa pagina no tenia problemas.(ahora estoy usando otra distro basada en UNR 9.04)
Tambien estoy usando Ubuntu en una acer aspire 5315 hace un monton y anda joya (no tiene dual boot).

---

### Post by guillermolisi on 2010-05-02
Con esto no alcanza para saber que modelo es ?
> He instalado la Distro en un Netbook Acer Aspire One ZG5 (Intel Atom  N270 1.6GHz, 1GB RAM, 8.9" Scrn, Intel GMA 950 Chipset).

---

### Post by Astantler on 2010-05-02
> **sitiomatic said:**
> No pusiste que modelo de AAO tenes y no todos los modelos tienen los mismos problemas y soluciones.
Leete primero las soluciones que dan aqui para tu modelo. [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
Yo tengo una ao751h, use bastante Ubuntu 9.04 y siguiendo los consejos de esa pagina no tenia problemas.(ahora estoy usando otra distro basada en UNR 9.04)
Tambien estoy usando Ubuntu en una acer aspire 5315 hace un monton y anda joya (no tiene dual boot).

Sitiomatic: Coloque el Modelo al principio de este Hilo. Es un Netbook, Acer Aspire One ZG5 (O AAO 150), y ya me he pasado por esa wiki, y no reportan el problema que tengo.

Alfplayer: No puedo actualizar la BIOS, este PC tiene la 3310, y tiene un problema con la ultima BIOS (La 3314, que es la conocida "Muerte del Acer Aspire One", toca downgradear la BIOS, asi que la Actualizacion no es una opcion)

Guillermolisi, precisamente me estaba dando una vuelta por los foros de USA (Aqui en Ubuntuforums) y hay un hilo, de mas de 19 pags en donde debaten el mismo problema, incluso con PC's de escritorio, y no hay ninguna solucion concreta. El acerhdf lo configuré creando un archivo acerhdf.conf, agregandole lo siguiente:

```
options acerhdf interval=5 fanon=60 fanoff=55 kernelmode=1
```Es lo que muchos foros (incluso este) dicen, ya que los Acer tienen una pesima gestion del fan en Ubuntu. Hice esto, y la temperatura del Netbook no sobrepasaba los 50°C, cuando ocurrieron dos cuelgues, uno despues de haber trabajado durante hora y media y el otro tan pronto reinicie el Pc, de el primer cuelgue.

Descartado temperatura, incluso he visto en foros donde se comenta que los Intel Atom pueden soportar hasta 99°C antes de que el PC se apague.

La verdad ya estoy aburrido de todo esto, no entiendo que pueda ser lo que este fallando, he estado leyendo acerca de los demonios que gestionan la energia, y segun eso a algunos les ha funcionado. Intentare a ver que sucede

Muchas gracias a todos por su paciencia, con base en estos datos que les he dado, si tienen algo mas para recomendarme, les agradeceria mucho.

Gracias a todos

---

### Post by sitiomatic on 2010-05-02
> **guillermolisi said:**
> Con esto no alcanza para saber que modelo es ?

jeje no, no tiene el numero de serie :)
Bueno, estaba muy dormido, al menos le dije donde buscar la solucion

---

### Post by alfplayer on 2010-05-02
Si duraba cinco minutos y después duró una hora y media, eso reforzaría que es un problema de temperatura. Que se haya congelado al instante posterior de reiniciar la netbook reforzaría más la idea de problemas de temperatura, porque los componentes siguen estando calientes.

No se qué componente estaba a 50º, qué valor debe tener esa temperatura, ni conozco las temperaturas adecuadas para esa netbook.

Algunas ideas:

[LIST]
[*]Verificar los valores y tratar de aumentar las velocidades de los ventiladores al máximo (no se cuántos tiene la AAO ZG5).
[*]Verificar y tratar de disminuir (modificando las velocidades de ventiladores) todas las temperaturas posibles. En las pc de escritorios hay varias temperaturas importantes que deben tener valores correctos: CPU, GPU, memoria, northbridge, southbridge, etc.
[/LIST]
Si están cargados los módulos del kernel para monitoreo adecuados estos valores deberían aparecer en /sys/class/hwmon/...

---

### Post by Astantler on 2010-05-02
> **alfplayer said:**
> Si duraba cinco minutos y después duró una hora y media, eso reforzaría que es un problema de temperatura. Que se haya congelado al instante posterior de reiniciar la netbook reforzaría más la idea de problemas de temperatura, porque los componentes siguen estando calientes.

No se qué componente estaba a 50º, qué valor debe tener esa temperatura, ni conozco las temperaturas adecuadas para esa netbook.

Algunas ideas:

[LIST]
[*]Verificar los valores y tratar de aumentar las velocidades de los ventiladores al máximo (no se cuántos tiene la AAO ZG5).
[*]Verificar y tratar de disminuir (modificando las velocidades de ventiladores) todas las temperaturas posibles. En las pc de escritorios hay varias temperaturas importantes que deben tener valores correctos: CPU, GPU, memoria, northbridge, southbridge, etc.
[/LIST]
Si están cargados los módulos del kernel para monitoreo adecuados estos valores deberían aparecer en /sys/class/hwmon/...

Alfplayer:

Pensaba igual acerca de la temperatura, pero cuelgues anteriores hacen que no sea valido. Como Un Netbook recien encendido, que marca 34°C de temperatura (Siempre me refiero a la temperatura de la CPU) Se Cuelga 2min despues de encenderlo, sin haber hecho uso previo de el (Permanecio apagado durante mas de 2 dias)???, esa situacion me ha ocurrido 4 veces ya, lo que confirma que no puede ser temperatura. Ademas, cuando me lo llevo a mi lugar de estudio, trabajando con WXP alcanza temperaturas cercanas a los 80°C, se pone demasiado caliente, ya que el lugar es muy cerrado, y hasta el momento jamas se me ha colgado de esa manera en XP (Obvio, exceptuando BSOD's que pasan de vez en mes, lo tipico en Windows).

En Ubuntu tengo instalado el paquete "lm-sensors" y uso el applet "Monitor De Sensores" incluido en GNOME. Los valores adecuados para este notebook estan por debajo de 69°C, aunque como lo decia anteriormente, este netbook puede llegar hasta los 99°C, y de verdad lo he comprobado con WXP. Entonces, no se que mas pueda ser, no creo que cualquer PC se vaya a colgar por debajo de los 50°C de temperatura. Como te digo, todos los valores de los que te hablo son de la CPU (Intel Atom N270), el HDD se mantiene estable entre 31° y 38°C.

---

### Post by alfplayer on 2010-05-02
> **Astantler said:**
> Alfplayer:

Pensaba igual acerca de la temperatura, pero cuelgues anteriores hacen que no sea valido. Como Un Netbook recien encendido, que marca 34°C de temperatura (Siempre me refiero a la temperatura de la CPU) Se Cuelga 2min despues de encenderlo, sin haber hecho uso previo de el (Permanecio apagado durante mas de 2 dias)???, esa situacion me ha ocurrido 4 veces ya, lo que confirma que no puede ser temperatura. Ademas, cuando me lo llevo a mi lugar de estudio, trabajando con WXP alcanza temperaturas cercanas a los 80°C, se pone demasiado caliente, ya que el lugar es muy cerrado, y hasta el momento jamas se me ha colgado de esa manera en XP (Obvio, exceptuando BSOD's que pasan de vez en mes, lo tipico en Windows).

En Ubuntu tengo instalado el paquete "lm-sensors" y uso el applet "Monitor De Sensores" incluido en GNOME. Los valores adecuados para este notebook estan por debajo de 69°C, aunque como lo decia anteriormente, este netbook puede llegar hasta los 99°C, y de verdad lo he comprobado con WXP. Entonces, no se que mas pueda ser, no creo que cualquer PC se vaya a colgar por debajo de los 50°C de temperatura. Como te digo, todos los valores de los que te hablo son de la CPU (Intel Atom N270), el HDD se mantiene estable entre 31° y 38°C.

Con todo esto sigo sin estar seguro de que no sea un problema de temperatura porque como dije si hay problemas con los ventiladores pueden estar muchos componentes afectados, algunos pueden dejar de funcionar antes que el Atom.

Yo chequearía las temperaturas y velocidades como dije antes, prefiero usar el comando sensors, no el applet de gnome, que puede mostrar valores diferentes.

Otra cuestión importante es probar con la versión final de 10.04, no con una versión de desarrollo.

---

### Post by Astantler on 2010-05-02
> **alfplayer said:**
> Con todo esto sigo sin estar seguro de que no sea un problema de temperatura porque como dije si hay problemas con los ventiladores pueden estar muchos componentes afectados, algunos pueden dejar de funcionar antes que el Atom.

Yo chequearía las temperaturas y velocidades como dije antes, prefiero usar el comando sensors, no el applet de gnome, que puede mostrar valores diferentes.

Otra cuestión importante es probar con la versión final de 10.04, no con una versión de desarrollo.

Alfplayer, precisamente, estoy con la Final de Ubuntu 10.04, Al igual que con la 9.10, que me presentaba el mismo problema, pero seguire tus consejos, rechequeare las temperaturas y te dire que tal me va...

---

### Post by Astantler on 2010-05-03
Gracias A Todos:


La verdad es la primera vez que me sucede algo como esto, y la verdad desisto. Espere dos meses, buscando solucion, y esperanzado de que Lucid lo solucionase, pero no fue asi. Necesito Usar Alguna Distro, Y por lo menos Los derivativos de Ubuntu, incluso UbuntuStudio siguen poniendo el mismo problema... Seguire con ubuntu en el Desktop e Intentare de nuevo con Fedora...


Gracias a todos por sus respuestas.

---

