---
title: "Proxy"
date: 2009-05-20
forum: Instalación y Actualización
---

### Post by Iced_R on 2009-05-20
Holas!! (Este nuevo foro es algo enredado, me gustaba más el antiguo... pero es interesante participar en la comunidad global de Ubuntu xD)

Tengo un pequeño problema. Me conecto desde la Universidad, y ahi tengo una maquinita con Ubuntu., Actualmente estoy trabajando con Jaunty. El problema es que ni Synaptic, ni apt-get, ni aptitude, ni dpkg se pueden conectar a Internet, por lo que no puedo descargar nada de los repositorios oficiales. He intentado colocar el proxy por separado en cada programa (no supe cómo ponerle un proxy a dpkg ni a apt-get, pero pude con Synaptic y aptitude), usé la herramienta Proxy de la Red, per no hay caso.

Si alguien me puede ayudar, se lo agradecería.

Saludos.

---

### Post by Patriciologico on 2009-05-20
Prueba lo siguiente:
```
export http_proxy=http://direccion:puerto
```
```
export ftp_proxy=http://usuari:password@ip_proxy:port/
```


Si hay usuario con contraseña
```
export HTTP_PROXY=http://usuario@contraseña:direccionIPdelproxy:puerto
```

y para comprobar
```
export
```

Para cambios permanentes,crear el archivo /etc/apt/apt.conf.d/proxy
y en este archivo ingresas lo siguiente:
```

Acquire::http::Proxy "http://usuario:password@direccion_del_proxy:puerto";
Acquire::ftp::Proxy "ftp://usuario:password@direccion_del_proxy:puerto";
```

[Puedes leer este hilo de la lista Ubuntu-es, para mas info]("https://lists.ubuntu.com/archives/ubuntu-es/2006-March/014146.html")

Saludos!

---

### Post by gmunioz on 2009-05-21
Hola ice....:

Generalmente con un proxy comun la configuración consiste en:

Editar el archivo   /etc/bash.bashrc

Poner las siguientes líneas al final de este archivo

        export http_proxy=http://username: [email]password@proxyserver.net[/email]: port/
        export https_proxy=http://username: [email]password@proxyserver.net[/email]: port/
        export ftp_proxy=http://username: [email]password@proxyserver.net[/email]: port/

Editar el archivo  /etc/environment

Poner las siguientes lineas al final de este archivo

   http_proxy=http://username: [email]password@proxyserver.net[/email]: port/
   https_proxy=http://username: [email]password@proxyserver.net[/email]: port/
   ftp_proxy=http://username: [email]password@proxyserver.net[/email]: port/

Editar el archivo /etc/apt/apt.conf

Poner las siguientes líneas al final del archivo:

Acquire::http:: Proxy "http://username: [email]password@proxyserver.net[/email]: port";
Acquire::https:: Proxy "http://username: [email]password@proxyserver.net[/email]: port";
Acquire::ftp:: Proxy "http://username: [email]password@proxyserver.net[/email]: port";

En Gutsy el archivo se debe crear en /etc/apt/apt.conf.d/proxy

Esto es para los proxys que soportan autenticacion.

Pero hay otros proxys, como el ISA server y algunos mas que usan 

autenticacion mediante NTLM.

Cuando se va a acceder a un recurso remoto el servidor que tiene el 

recurso debe autenticar a quien se conecta, para luego poder autorizarlo 

(o no) a acceder al recurso.

Dependiendo del sistema operativo del cliente, del servidor, si se está 

en grupo de trabajo o dominio y del tipo de dominio se utilizará el 

protocolo más seguro que sea admitido por las partes que interactúan.

NTLM significa NT LanManager

NTLM utiliza el método conocido como Challenge-Respose (Desafío-

Respuesta) variando solamente las funciones matemáticas utilizadas, 

longitudes de claves y algunos mecanismos internos. Está basado en la 

técnica de “Secreto-Compartido”. Si sólo dos conocemos un secreto y yo 

soy uno, el que me demuestre que conoce el secreto tiene que ser el 

otro”. Llevado a términos de inicio de sesión: Si el Controlador de 

Dominio conoce la contraseña del usuario “Usuario1”, quien diga ser 

“Usuario1” y conozca la contraseña correspondiente, debe ser el usuario 

“Usuario1”.

Si bien el firefox anda bien seteando el proxy con las medidas previas de 

esta autentificacion, la mayoría de las aplicaciones tipicas no, apt-get 

emerge wget, etc, etc,etc

Y marcan un error similar a:

ERROR 407: Proxy Authentication Required.

ntlmaps


¿Que ntlmaps? Es basicamente otro proxy que soporta la autenticacion que 

definimos al principio, y se configura seteando dominio, usuario, 

password, proxy y puerto, del proxy que usa autenticación NLM, para 

entonces autenticar contra el proxy NTLM y así generar un demonio que se 

queda escuchando conexiones en un puerto y nos permite salir a internet a 

traves de este demonio.

Para que funcione es necesario configurar la variable http_proxy, y todo 

lo aquello que necesite autenticacion de proxy a:

http//127.0.0.1:5865

5865 es el port por defecto del ntlmaps

Si no nos gusta lo podemos cambiar

Reiniciar NTLMAPS con 

sudo /etc/init.d/ntlmaps restart
    
Una vez instalado, configurado y reiniciado Ntlmaps

Debemos reemplazar en las líneas de los archivos mencionados al comienzo

[http://username: password@proxyserver.net: port](http://username: password@proxyserver.net: port)

por

http//127.0.0.1:5865

[B]Aclaración: no va separación alguna entre los dos puntos : y la p, lo que 

ocurre es que si los pongo como corresponde, se interpretan como smilies

y no puedo postear, porque exceden el límite permitido[/B]


Saludos

---

### Post by Patriciologico on 2009-05-21
> **gmunioz said:**
> Editar el archivo /etc/apt/apt.conf

Poner las siguientes líneas al final del archivo:

Acquire::http:: Proxy "http://username: [email]password@proxyserver.net[/email]: port";
Acquire::https:: Proxy "http://username: [email]password@proxyserver.net[/email]: port";
Acquire::ftp:: Proxy "http://username: [email]password@proxyserver.net[/email]: port";


En Jaunty no encuentro ese archivo, se debe crear?

[QUOTE=gmunioz]En Gutsy el archivo se debe crear en /etc/apt/apt.conf.d/proxy[/QUOTE]

No tenia idea que era sólo para esa versión. Me disculpo si llevé al error.

Gracias por tu completa información,

Saludos!

---

### Post by Carlos C on 2009-05-21
> **gmunioz said:**
> Hola ice....:


[B]Aclaración: no va separación alguna entre los dos puntos : y la p, lo que 

ocurre es que si los pongo como corresponde, se interpretan como smilies

y no puedo postear, porque exceden el límite permitido[/B]


Saludos
Una forma de evitar ese problema es seleccionar tu texto y luego hacer click en el botón "CODE" (símbolo "#"), así puedes escribir lo que quieras:
```
sin problemas para escribir :p
```

---

### Post by pagondel on 2009-05-21
> **Iced_R said:**
> , usé la herramienta Proxy de la Red, per no hay caso.


Mmmm, yo siempre uso esa herramienta... Hiciste click en "Aplica a todo el sistema" ???

Saludos!

---

### Post by gmunioz on 2009-05-23
Hola:


```
Editar el archivo /etc/apt/apt.conf

¿En Jaunty no encuentro ese archivo, se debe crear?

En Gutsy el archivo se debe crear en /etc/apt/apt.conf.d/proxy

No tenia idea que era sólo para esa versión. Me disculpo si llevé al error.
```

Todo es resultado de mi experiencia. Uso Ubuntu en mi trabajo, y estoy

conectado a internet mediante un servidor Suse con Squid.

Cuando cambié a Gutsy, perdí el acceso a internet y lo logré creando ese

archivo, cuando cambié a Hardy,[I] siempre hago instalaciones limpias 

formateando / y /home y conservado mis archivos en partición separada que

monto como /home/usuario/datos[/I], el archivo no me sirvió, creé el 

anterior /etc/apt/apt.conf y logré la conexión para actualizar el sistema 

sin problemas. Esto lo repetí en Intrepid y Jaunty y funcionaron sin 

inconvenientes, el archivo siempre lo tuve que crear. 

Estimo que nadie lo investiga, debido a que son pocos los que

actualizan como lo hago yo, en consola y mediante apt-get. Teniendo 

proxy, tanto a los navegadores como a synaptic, con simplemente ingresar

los parámetros del proxy en sus respectivos items, les basta y sobra.

Saludos.

---

### Post by Iced_R on 2009-05-25
> **pagondel said:**
> Mmmm, yo siempre uso esa herramienta... Hiciste click en "Aplica a todo el sistema" ???

Saludos!

Gracias por las respuestas muchachos...

Ahora, comienzo a responder. pagondel, apliqué esa opción de Aplica a todo el sistema, pero no pasó nada. Lo de export http_proxy, fue lo siguiente que probé, pero tampoco me funcionó. Ahora me falta probar la respuesta que me dio gmunioz, que será el siguiente paso, pero al parecer (si lo que ya he hecho funciona en teoría) todo me hace pensar que me restringieron el servidor de Chile por el proxy... lo que no me va a hacer feliz xD.

Si logro hacer funcionar mis actualizadores, se los haré saber.


Saludos, y reitero las gracias por las respuestas.

---

### Post by Iced_R on 2009-05-26
Aviso de último minuto: Sí era bloqueo por proxy. En la configuración del filtro del servidor estaba bloqueado el servidor de actualizaciones para Chile de Ubuntu, pero ya está solucionado. Con el simple hecho de marcar el proxy de la red en Gnome ya funcionaban las actualizaciones. Ahora, de forma más genérica, eso de export http_proxy para usarlo en otro tipo de entorno gráfico, pero cualquiera de las 2 funciona. Lo que posteó gmunioz, no alcancé a probarlo, no hubo necesidad.

Gracias a todos por las respuestas. Problema resuelto xD

Saludos.

---

