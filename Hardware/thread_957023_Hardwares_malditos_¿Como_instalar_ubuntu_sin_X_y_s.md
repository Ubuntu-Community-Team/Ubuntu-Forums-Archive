---
title: "Hardwares malditos: ¿Como instalar ubuntu sin X y sin internet?"
date: 2008-10-23
forum: Hardware
---

### Post by c4d0rn4 on 2008-10-23
He querido instalar en lo de un amigo ubuntu, varias veces, pero siempre siempre siempre, logro nada. La cosa es así, tiene una placa nvidia y no arranca el X, la verdad no estoy tan ducho con la consola pero de a poco la voy entendiendo.

¿Hay una manera de arrancar el live-cd en modo consola para cargar los drivers de nvidia que ya bajé?

Tengo la idea de que la hay.


Por otro lado tengo el problema de que me pide que haga **make**, y la única vez que pude hacer un make sin errores en mi corta vida en linux fue en DSL! siempre he tenido problemas con ubuntu... que me falta los headers, que no encuentra el kernel (cuando ya instalé los headers), que me falta GCC, CC, y la mar en coche... Esos paquetes no están en el cd o no se instalan usualmente?

Bajarlos actualmente es poco probable, porque tiene un arescom NDS1060 USB que es un chipset eagle. Por lo cual voy a probar suerte con [http://ubuntuforums.org/showthread.php?t=846069&highlight=eagle](http://ubuntuforums.org/showthread.php?t=846069&highlight=eagle) ... creen que sirva?

En realidad inicialmente, quiere probar el live cd... y con solo ver que anda, instalarlo. Se me ocurrió el alternarte cd, pero dudo que aún teniendolo instalado pueda hacerlo andar y aparte no quiero andar haciendole quilombo en la pc para que después no ande.

Pd. en contrapartida a esta pc hija de ****, en lo de otro amigo con su notebook acer le reconocio TODO, hasta la placa de wi-fi, bluetooth y el wiimote LOL xD... simplemente no lo podía creer! Eso demuestra que no todos los hardware son malditos hijos de ****, pero esa pc de la consulta me tiene los quinotos por el piso.

Pd2. Creen que con Arch pueda compilar bien? hay algún live-cd?

---

### Post by hictio on 2008-10-23
Los programas para poder hacer un 'make' es decir, compilar algo, no se instalan por default.
Una vez que termines la instalacion, y estas conectado a internet (!), tipea:
```

sudo aptitude install build-essential

```

Que no te arranque X porque es una tarjeta NVIDIA es raro, que tarjeta es exactamente? En mi laptop X, es decir, Gnome andaba perfecto, pero no en la resolucion nativa, solo a 1024x800, pero despues de instalar los drivers "propietarios" de Ubuntu para NVIDIA, un reboot, o reinit de X, y tudo joia.

> 
¿Hay una manera de arrancar el live-cd en modo consola para cargar los drivers de nvidia que ya bajé?


Te podes pasar a una consola virtual, Ctrl + Alt F(1 al 7, para volver), si los drivers los podes instalar en una live session, yo lo probe en 7.04 creo que era, en una maquina que estaba probando con una tajeta de video que daba miedo de lo buena que era, casi daba lastima tener que rebootear y salir de Ubuntu.

---

### Post by sajnox on 2008-10-23
Probaste con el alternate??

La otra opcion para las placas nvidia es cuando arranca el live cd, despues de elegir el idioma apretas f6 y le agregas lo siguiente:

```
noapic nolapic vga=771
```

Proba con eso y contanos

---

### Post by faktorqm on 2008-10-24
Si mal no recuerdo hay un modo en el cd que se llama modo vga, lo probaste? 
Y si no tiene internet podes probar mi script de configuracion de adsl que lo postie en la seccion hardware... te bajas el paquete, lo descomprimis, ejecutas el script y (supuestamente) tenes que salir con internet andando. Ahi instalas el envy y olvidate de compilar el driver de nvidia. Salu2!

---

### Post by c4d0rn4 on 2008-10-24
Muchas gracias por las respuestas,
La cosa "terminó" bien. Puede arrancar el X y hacer andar el modem!! pero no todo fue a las buenas y primeras.

> **sajnox said:**
> Probaste con el alternate??

La otra opcion para las placas nvidia es cuando arranca el live cd, despues de elegir el idioma apretas f6 y le agregas lo siguiente:

```
noapic nolapic vga=771
```

Proba con eso y contanos

no se si lo habré escrito mal o que, pero no anduvo para nada, quedo trabada =S

Después reinicie y puse safe graphic y salio 10 puntos a la resolución que correspondía y bien proporcional. Luego de otros reinicios, que explico más abajo, salió un error (kernel panic y otras cosas xD) con el safe graphic y no había manera de que arranque.

Un par de intentos después de modo normal arranco pero con una resolución que no correspondía con la pantalla. Cambié a 800x600 y entró bien. Más intentos con respecto a eso no hubo.

> **faktorqm said:**
> Si mal no recuerdo hay un modo en el cd que se llama modo vga, lo probaste? 
Y si no tiene internet podes probar mi script de configuracion de adsl que lo postie en la seccion hardware... te bajas el paquete, lo descomprimis, ejecutas el script y (supuestamente) tenes que salir con internet andando. Ahi instalas el envy y olvidate de compilar el driver de nvidia. Salu2!

Usé tu script, pero la verdad que no anduvo y después traté con este tuto [http://ubuntuforums.org/showthread.php?t=895491&highlight=programa+pppoeconf](http://ubuntuforums.org/showthread.php?t=895491&highlight=programa+pppoeconf) y me dijo que nas0 ya existía. Así que reinicie a ver pasaba con ese tuto solo, y después de agarrarle la mano al modem conectó. El modem como que se frezea y hay que desconectarlo y volverlo a conectar luego de hacer modprobe ueagle-atm para que se de por aludido.

---

### Post by santiagoward2000 on 2008-10-25
Hola gente!
Por lo del modem, la verdad que nunca probé el script de faktorqm (no te enojes ;)), pero cuando yo tenía uno igual (Arescom 1060 usb del ****) lo había hecho andar con esta guía:
[http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810]("http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810")
Fijate si te sirve. Es un toque más largo, pero te aseguro que a mí me anduvo.
Suerte!

---

### Post by faktorqm on 2008-10-25
No me enojo, pero decime cual usaste, por que la verdad que hay varios, y no se si todos estan en su ultima version. La ultima es la 0.7 y viene con desinstalador, asi que si no tiene desinstalador ya sabes por que no te anduvo. Salu2!

---

