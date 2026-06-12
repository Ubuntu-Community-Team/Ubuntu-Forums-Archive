---
title: "Conexion a Speedy"
date: 2008-05-27
forum: Hardware
---

### Post by granadicto on 2008-05-27
Hola, este es mi primer mensaje.  Hace tiempo que queria probar Linux, pero no encontraba ningun producto relativamente intuitivo de usar (estoy acostumbrado desde chico al uso de Windows) hasta que comence a escuchar por todos lados: UBUNTU.

Me baje el Live CD y logre hacerlo andar. (al principio tube algun problemita que lo solucione googleando).


Estoy explorando Ubuntu mediante el CD, pero ahora quiero conectarme a internet, pero no se como.

Se que es un tema bastante pedido en el foro y estuve leyendo algunas respuestas pero no me han sido utiles ya que tengo 0 conocimiento de linux.

Para dejarles los datos de mi conexion contestare un formulario que esta en otro tema:
[B]
Compañía:[/B] Speedy 1 mega por telefono

**Version de Ubuntu:** 8.04 (live cd)

**más de una computadora interconectada al modem?** : No
[B]
¿Poseés placa de red por cable, inalámbrica, o ambas?[/B]  Fast Ethernet compatible VIA.

**¿Qué direcciones IP de DNS utilizás?**  No se bien a que se refiere la pregunta. Tengo entendido que Speedy me otorga una Ip distinta cada vez que me conecto.
[B]
¿Cuál es tu ubicación dentro de la Argentina?[/B] Lanus, Buenos Aires.
[B]
¿De qué marca y modelo es tu modem?[/B] Huawei . SmartAX MT880
[B]
¿Tiene conexión USB, Ethernet o ambas?[/B] Ethernet.



Les recuerdo que no tengo experiencias con Linux, asi que les pido que sean lo mas explicativos posibles.  

Espero me den una mano, asi termino de explorar este sistema operativo y sus potencialidades.

---

### Post by Mauro22 on 2008-05-27
Hola!!


Pasate por aca [http://ubuntuforums.org/showthread.php?t=779717&highlight=SmartAX+MT880](http://ubuntuforums.org/showthread.php?t=779717&highlight=SmartAX+MT880)

---

### Post by granadicto on 2008-05-27
Muchas gracias por tu respuesta. La verdad es que ya lo habia solucionado leyendo temas viejos de este foro de ubuntus 7, sumado a un poco de la intuicion y conocimientos previos.

No se como se manejan en el foro, pero si quieren pueden cerrar este tema y darlo por solucionado.

Me voy a crear otro tema, porque ya me convencio Ubuntus y ahora necesito ayuda para instalarlo ;)

---

### Post by pol666 on 2008-05-27
Abri una terminal y pone sudo pppoeconf
y ahi te salta un Asistente para que completes tus datos pone tu usuario, contraseña y lo demas todo "SI"

La conexion de red que este seteada en Dhcp y sin IP privada los DNS se agregan solos..de eso no tenes ue tocar nada

---

### Post by faktorqm on 2008-05-28
Hola, lo que podés hacer, ya que tenes conexión ethernet, es **no desperdiciar recursos de tu pc en marcadores como pppoeconf, ni en firewall's por software, teniendo un hardware que lo hace por vos**. Otra ventaja es que si lo configuras de esta forma, en la instalacion tambien vas a poder tener internet e instalar los paquetes de idiomas sin hacerlo despues, por que tenes conexion en todo momento.

Primero, pones la placa de red en ip automatica (o DHCP) y luego (segun el post al que te mandaron arriba) abris un explorador y pones la direccion [http://10.0.0.2/](http://10.0.0.2/) y ahora tenes que seguir este tutorial de como configurar el modem.

[http://www.adslayuda.com/Huawei_MT882RT-Configuracion_IP_Dinamica_PPPoE_Multipuesto.html](http://www.adslayuda.com/Huawei_MT882RT-Configuracion_IP_Dinamica_PPPoE_Multipuesto.html)

NOTAS IMPORTANTES:
1) si el usuario nos es admin admin, fijate en el manual de tu modem cual es.
2) CUANDO DICE "SELECCIONAREMOS VC EN EL CAMPO MULTIPLEX" ESTA MAL, Speedy usa LLC para multiplexar, asi que eso te tiene que quedar en LLC.
3) en login information, en service name pone cualquier cosa. (ejemplo: speedy), en user name deberias poner "tu_telefono@speedy", o sea el usuario que tuviste que poner cuando lo configuraste en windows. y en contraseña, la contraseña.

Una vez terminado el proceso, vas a tener internet y firewall sin "tocar" nada. Y si reinstalas lo mismo, el modem no cambia. Eso si, si vas a windows, tenes que poner a la placa de red en ip automatica y dns automatico tambien, sino cuando marques te va a decir que no puede.

Espero que te haya servido. Salu2!

---

### Post by michay on 2008-05-28
Buenas soy nuevo en ubuntu y tengo el mismo problema no se como conectarme a internet. tengo la misma coneccion lo unico que me varia es la version de ubuntu 7.10 y el modelo del modem **ZTE ZXDSL 831 series**.
Desde ya muchas gracias por la ayuda.
Advertencia: no tengo idea de S.O linux es la primera vez que lo uso.
Saludos

---

### Post by faktorqm on 2008-05-29
Bueno mirá, en speedy está eso, asi que voy a ""traducir"" el tutorial de ellos para linux. 

Primero, arriba a la derecha tenes un iconito con dos monitores, haces click y le das a "configuracion manual...", seguramente te va a pedir la contraseña, la ingresas y apretas en conexion cableada y apretas propiedades. Ahi te abre una ventana, le pones direccion IP estatica y en direccion IP pones: 192.168.1.4, en mascara de subred: 255.255.255.0 y en direccion de la puerta de enlace pones 192.168.1.1. Guardas todo y ahora si arrancas con este tutorial solo que en lugar de usar internet explorer vas a tener que usar firefox XDXD y obviamente ignorar la primera parte.

[http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132)

Cuando lo termines, ya vas a estar conectado. Ahora, no se como te conectaras en windows, pero deberias poner la misma configuracion que en linux, si no sabes como se hace, fijate en la primera parte del tuto de speedy :D 

Espero que te haya servido, salu2!

---

### Post by michay on 2008-05-29
Ok Faktoqm voy a ver que me sale, mi pregunta es yo tengo una sola pc es necesario routear el modem para tener internet, y la otra es que si configuro el modem en router para ubuntu tambien tengo que configurarlo para xp no?.
Disculpa que te moleste y sea muy novato en esto pero como veras ni idea de lo que estoy haciendo :)
Muchas gracias

---

### Post by faktorqm on 2008-05-29
No, no te lo queria decir para que tomes confianza con el linux, pero si lo haces desde windows es lo mismo, es decir, si seguis el tutorial de speedy de pe a pa desde windows, solo tenes que venir a linux y configurar la placa de red con la ip, la mascara y la puerta de enlace que te puse ahi y listo. (aunque en realidad, ahora que lo pienso un segundo mas, quiza ubuntu sin tocar nada de nada salga con internet de una, proba de abrir un firefox antes de configurar, si no anda, nada, a configurar la placa!)

Salu2!!

---

### Post by michay on 2008-05-29
Una masa Faktorqm estoy conectado y en ubuntu chau xp jeje, ahora tengo que configurar todo el resto como la gforce y no se que mas. cuales serian los pasos a seguir?? se que no es el post para esto pero donde encuentro respuestas de como instalar o que antivirus instalar en ubuntu, etc etc.
Muchas gracias

---

### Post by faktorqm on 2008-05-29
ja!! no tenes idea de lo que estas hablando men!! no existen virus para linux. ni spyware ni nada de todo eso. Busca un post aca en el foro que habla de todo eso y ahi lo explicamos bien.

Los drivers de la gforce, los tenes que instalar con envy. haces aplicaciones -> accesorios -> terminal y copias y pegas el comando:

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb
```

Cuando termina cerras y despues vas a Lugares -> carpeta personal, ejecutas el archivo que acabas de bajar. Ahi te lo instala y despues vas a aplicaciones -> herramientas del sistema -> envy.

esto es si tenes 7.10. si tenes 8.04 tenes que hacer aplicaciones -> accesorios -> terminal y copias y pegas el comando:

```
sudo apt-get install envyng-gtk
```

Espero que te haya servido. Salu2!!

---

### Post by michay on 2008-05-29
JEJE bueno che no te dije que soy totalmente nuevo en esto.
Primero: dodnde pongo code??? no entiendo
Segundo: no tengo Herramients del sistema en aplicaciones ni en ningun lado.
dame un empujoncito mas dale?.
gracias

---

### Post by sajnox on 2008-05-29
Te doy mi ayuda.

Code no lo tenes que poner en ningun lado, te esta diciendo que esa linea la tenes que ingresar en una consola.

---

### Post by michay on 2008-05-29
ok se complico lo baje  y cuando fui a instalarlo me dijo lo siguiente:
**error: dependency is not satisfiable: debhelper** y me explica lo siguiente:
Envy is an application written in Python which will download the latest ATI or NVIDIA driver or the Legacy driver (for older cards) (according to the model of your card) from ATI or Nvidia's website and set it up for you handling dependencies (compilers, OpenGL, etc.) which are required in order to build and use the driver. 
Alguna otra idea?.
gracias

---

### Post by sajnox on 2008-05-29
Me parece que leiste mal el post del amigo faktor, arriba en el thread dice que tenes 8.04 y por lo tal tenes que ejecutar el siguiente comando en la terminal: aplicaciones -> accesorios -> terminal

```
sudo apt-get install envy-gtk
```

Luego te lo tiene que dejar instalado en Aplicaciones -> Accesorios -> Envy

---

### Post by michay on 2008-05-29
no no lei mal mi version de ubuntu es 7.10. pero al instalarlo me tiro ese error.

---

### Post by faktorqm on 2008-05-30
Hola, el contenido de CODE lo tenes que pegar donde te dije, o sea, en la terminal. Terminal = consola = xterm = bash vas a encontrar esos nombres para la misma cosa, la terminal :P :P

si no te lo deja instalar, el wget es un "bajador" de archivos, es decir, te baja el archivo que vos le pedis. Cuando termina sin cerrar la consola pone esto:

```
sudo apt-get install debhelper
```

y despues cuando termina volve a darle doble click al archivo envy_0.9.10-0ubuntu10_all.deb. 

Si tenes 7.10 no instales el envyng-gtk, de todas maneras simplemente no pasa nada, por que no lo va a encontrar asi que no te preocupes. 


Recomendacion: por que no te pasas a 8.04 antes de instalar todo? es mejor, mas rapida y mas facil. Salu2!

---

### Post by patricio1977 on 2008-06-23
Hola!! estuve leyendo los post sobre la configuracion de speedy en ubuntu.Tambien tengo el moden ZTE ZXDSL 831 series, y por ahora estoy usando XP, y la idea es que convivan los 2 sistemas operativos, ya que es una pc que usan varias personas. Mi duda es la siguiente, si configuro el moden como se detalla más arriba, cuando se quiera usar XP, hay q volver a configurar algo o no tiene nada que ver una cosa con la otra?. No se si sirve como dato, pero la configuracion de la coneccion en XP la hice con el CD que te envía speedy. Bueno, quedo a la espera de la ayuda de alguien.
Gracias de antemano!

---

### Post by faktorqm on 2008-06-23
Hola, el cd de speedy lo podés usar de frisbi. Acá te explica como configurar tu modem [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=214&root=132) en modo router. Una vez que tengas eso, tanto ubuntu como xp van a tener internet sin tocar nada. Es mas, vas a tener internet aun reinstalando el sistema operativo (cualquiera de los dos) sin tocar nada. El soft de speedy para win lo tenes que desinstalar. Cualquier cosa pregunta. Salu2!

---

### Post by patricio1977 on 2008-06-23
Gracias por tu respuesta! voy a intentar hacer lo que me decis a ver si anda.

---

