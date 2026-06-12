---
title: "Ubuntu y Speedy"
date: 2007-12-08
forum: Hardware
---

### Post by nandazo on 2007-12-08
Holas y saludos a todos.
Bueno desde hace ya algunas semanas q tengo ubuntu 7.10 instalado en la pc, al igual q winxp, hace un par de semanas me conecte a internet con speedy la coneccion obviamnet la tengo en windows, y desde hace dos semanas q trato de conectarme a internet desde ubuntu y no puedo.
Tengo un modem ethernet SmartAX MT880 de Huawei y la coneccion a speedy es de ip dinamico, trate de configurar la coneccion a internet en ubuntu seleccionando configuarcion automatica DHCP y lo acepta y todo y reconoce q hay una conecion cableada, pero no hay internet por ningun lado, es decir ¿como configuro a speedy como mi servidor de internet en ubuntu.
Agradeceria mucho q me ayuden con eso. Gracias y bye.

---

### Post by Mauro22 on 2007-12-08
Fiajte si sirve

[http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810](http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810)

---

### Post by BiTFx on 2007-12-08
Hola, yo tengo un modem ethernet Huawei MT810 y estos son los pasos que seguí para conectarme a través de Speedy:

Esto lo pongo de memoria, tal vez me confundo en la ubicación de algun menu, o algo por el estilo, pero tal vez te guie.
 
Primero que nada, vamos a ver la configuracion de tu placa de red, y si está habilitada:
 
**Sistema -> Administracion -> red** (seguramente te pida la contraseña de usuario, que es la que usas para loguearte en Ubuntu)
 
Ahi doble click sobre la placa de red que está conectada al modem de speedy, supongo que tenes una sola placa.
 
Ahora en la ventanita que se abre desmarcá la opción que aparece arriba a la izquierda (de la ventanita) y Seleccioná en la lista desplegable IP Fija, poné la ip que te proporciona speedy (en mi caso es 192.168.1.10), Mascara de subred (hace click y se pone automaticamente 255.255.255.0) en puerta de enlace yo pongo 192.168.1.1
 
Ahora en la solapa de la derecha (Propiedades) colocá los DNS que te dieron, los mios son: 200.51.211.7 y el secundario es 200.51.212.7. 
 
Ahora cerrá la ventanita, y listo esta parte.
 
Encendé el modem de speedy y chequea que esté conecatdo el cable entre él y la placa de red de tu pc.
 
Ejecutar en la Terminal
 
**sudo pppoeconf** (Si no encuentra el comando ejecuta: sudo apt-get install pppoeconf)
 
Se abre una Interfaz, donde automáticamente detecta la placa de red que está conectada al modem, y te va guiando paso a paso (debés utilizar el teclado para avanzar e ir llenando los campos requeridos, el mouse no hace click aquí, si en algo tenés dudas, dejá seleccionada la opcion por defecto, y dale [enter]), luego te pide el usuario para conectarte a speedy, despues la contraseña, y los DNS, aunque no los puse nunca aquí, los configuré en la placa antes como te describí al principio.
 
Ahora te pregunta si querés conectarte YA, luego te pregunta si querés que Autoconecte al arrancar Ubuntu (yo le puse que no), y te da los comandos para conectarte y desconectarte (anotalos por las dudas), aunque en mi caso aparecen accesos directos para esto (después que reinicies Ubuntu) arriba a la derecha donde está el iconito de 2 pc's haces un click y en Conexiones... (no me acuerdo el nombre del menu) vas a encontrar 2 opciones, conectar por modem y desconectar (creo que ese es el nombre, luego corrijo, perdón por los errores), pero en esa parte están, seguro que los encuentras, pero solo despues de reiniciar Ubuntu.
 
Bueno, espero que te sirva de algo esta improvisada guia de memoria.
 
Saludos.

---

### Post by BiTFx on 2007-12-08
> **Mauro22 said:**
> Fiajte si sirve
 
[http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810](http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810)
 
Hola, creo que esa guía es para el **Huawei MT810 [COLOR=red]USB[/COLOR]**, y nandazo tiene un [COLOR=red]**Ethernet**[/COLOR].
 
Ahora ya tienen las 2 posibles soluciones, via USB o Ethernet.
 
Un saludo.

---

### Post by nandazo on 2007-12-10
> **BiTFx said:**
> 
 
Ahora en la ventanita que se abre desmarcá la opción que aparece arriba a la izquierda (de la ventanita) y [COLOR="Red"]Seleccioná en la lista desplegable IP Fija, poné la ip que te proporciona speedy (en mi caso es 192.168.1.10)[/COLOR], Mascara de subred (hace click y se pone automaticamente 255.255.255.0) en puerta de enlace yo pongo 192.168.1.1
 
Ahora en la solapa de la derecha (Propiedades) colocá los DNS que te dieron, los mios son: 200.51.211.7 y el secundario es 200.51.212.7. 
 


Hola BiTFx gracias por la guia se ve muy entendible, pero hay un problem, speedy me da ip dinamico, es decir tengo un ip distinto cada vez q me conecto y me conecto atravez de un icono de speedy en el escritorio doble click y todo el asunto ese y tampoco me dieron ningun DNS y bueno ese es el asunto q no puedo solucionar igual grcias por la ayuda y si no lo entendi bien disculpa. bye

---

### Post by BiTFx on 2007-12-10
Hola nandazo, te cuento, en mi caso también, cada vez que me conecto tengo ip dinámica.
 
La configuracion que propongo de tu placa de red (192.168.1.10) es porque esta se conecta con el modem ethernet, que en mi  caso (el modem) trae la ip por defecto 192.168.1.1.
 
Hay casos en que tienen configurado el modem como router, y en este caso le ponen en la configuracion de tu placa de red "Obtener IP Automáticamente", o mas precisamente DHCP (ahora tengo Ubuntu sin funcionar y no lo reinstalo, y no me acuerdo el nombre exacto de la opcion, pero es algo así, la idea es que obtenga la ip automáticamente), entonces todo quedaría de forma automáticamente, y si el modem está en modo router, él ya tiene configurado los DNS y todo eso, así que debería conectarse sin problemas.
 
En todo caso probá la configuracion que te pasé, seguramente te funcionará (yo soy de San Juan), y no creo que haya drama.
 
***Por favor alguien que conozca más del tema que me corrija cualquier error, ya que soy novato***
 
Perdón por la demora en al respuesta.
 
Contanos como te fue.
 
Un saludo.

---

### Post by jotix on 2007-12-12
yo tengo el mismo modelo de modem y speedy tambien.

SmartAX MT880 de Huawei, S.O. Ubuntu 7.10 amd64

Lo único que hice para que funcionase es seguir las instrucciones del manual del modem para ponerlo en modo PPPoE y funciona sin ningun inconveniente. Ubuntu reconocio desde el primer dia la conexion a internet, no tuve que tocar absolutamente nada en el sistema operativo.

---

### Post by cool-bits on 2007-12-22
Mira..hace unos 5 dias que toy con ubuntu definitivamente..despues de bajar montones de live cds de distros y probar y ver cual era la que mas me gustaba.

tengo modem ZyXEL P-660 por ethernet y speedy.

lo que lei por la net y me sirvio y lo uso asi es lo siguiente:

abris la consola (aplicaciones/accesorios/terminal)

escribis " sudo pppoeconf" sin las comillas obviamente,te pide la contraseña con la que te logueas en el sistema,si esta todo instalado te abre el programita de consola para configurar la conexion.

Lo primero que hace es detectar en la/s placas de red donde ta conectado el modem,una vez que lo detecta directamente te pone para que pongas tu nombre de usuario (en mi caso 4237**@speedy2m),el arroba lo haces con la tecla ALT Gr + Q o ALT Gr + 2.

Despues de eso te pide la contraseña que usas vos para conectarte,le pones y le das a aceptar..despues te pregunta unas cosas..vos dale a todo que si o aceptar segun te corresponda.


En teoria ya estas conectado,pero que pasa si te queres desconectar y volver a conectar?.

Haces lo siguiente:

abris la consola como puse arriba y tipeas primero que nada el comando sudo plog o plog solo depende como estes logueado y ahi te tira toda la data de la conexion,es decir, si esta conectado..los dns..las ips y demas..es para informacion nomas.

Ahora ponele que ya estas conectado y te keres desconectar tecleas "sudo poff" o "poff" (sin comillas siempre).Ahi te desconectaste,para ver si es cierto tecleas devuelta el comando "plog" y te va a decir.

Ahora se te ocurrio conectarte devuelta?

en consola (todo en consola) tecleas "sudo pon dsl-provider" o "pon dsl-provider" depende como estes logueado y ya estas conectado.

Le das unos segundos y en la consola tecleas devuelta el comando "plog" para ver el estado y tendria que estar conectado.


Espero que te sirva,cualquier cosa pm o postea aca.

PD: mi primer post jeje :)

salu2 comunity

---

### Post by faktorqm on 2007-12-23
es 1000 veces mas facil activar el modo router en ese modem, (es el que tengo yo) y olvidarte de cualquier software. si sabes como se hace postealo sino lo hago yo y les libro recursos de pc a varias personas..... si tenes un hardware que lo hace, por que lo va a hacer tu microprocesador? salu2!

---

### Post by BiTFx on 2007-12-24
> **faktorqm said:**
> es 1000 veces mas facil activar el modo router en ese modem, (es el que tengo yo) y olvidarte de cualquier software. si sabes como se hace postealo sino lo hago yo y les libro recursos de pc a varias personas..... si tenes un hardware que lo hace, por que lo va a hacer tu microprocesador? salu2!
 
 
Buenísimo!!!
 
Si podés publicalo, a mi me sería muy útil, y no sería el único.
 
Gracias por tu ayuda.

---

### Post by Nikolopulus on 2010-09-12
Buenas, tengo el modem zyxel p-600 intenté configurar la red con pppoeconf pero me dice que "se consultaron las interfaces pero no respondieron" ¿alguna idea de como continuar?
Gracias

---

### Post by mdqman on 2010-09-13
Hola a todos. hace poco que estoy activo en este foro y estoy recorriendo los treads Veo que este tema se inicio hace varios años, pero parece que para algunos que van llegando a Linux siempre es problema la conexión a internet, como en este caso Nikolopulus.

La solución para la conexión a internet con Speedy no podría ser mas fácil y funciona con cualquier módem que entrega Speedy.  

Teniendo placa de red conectada y conexión ethernet con IP dinámica, simplemente hay que comunicarse con la ayuda del servicio técnico de Speedy, decirle que usas Linux y pedirle que te configuren el módem como router, Ellos te guían paso por paso y el módem se conecta automáticamente cuando se enciende la PC, sin necesidad de tocar mas nada se conecta al arrancar con cualquier sistema operativo y cualquier versión de linux.

Se que parece una obviedad escribir esto que es muy básico y viejo, pero mucha gente que llega a Linux se desespera cuando no se puede conectar rápidamente a Internet. 

Saludos

---

