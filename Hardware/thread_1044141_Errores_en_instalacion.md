---
title: "Errores en instalacion"
date: 2009-01-19
forum: Hardware
---

### Post by Nikolopulus on 2009-01-19
Hola, soy nuevo en ubuntu y en el foro, me compre una máquina hace unos dias y cuando le quiero cargar ubuntu me es imposible.

Al principio de tiraba este error:
/sbin/sh: can't access tty; job control turned of
(initransf)
Busque por muchos foros y encontre 15 soluciones, de las cuales ninguna me sirvió, la mayoria era para casos en los que ya tenes instalado el SO

La solucion que me hizo llegar más lejos es una en la que, antes de instalar apretaba F6 y reemplazaba "splash--" por "brak=top" en la consola que se abre y, cuando me tiraba el error de mas arrbia ingresaba "modprobe piix".
Después de hacer eso supuestamente se reiniciaba la máquina y andaba todo bien.
Bueno, a mi me tiró el siguiente error:
CP:unable to open 'root/var/log'
mount:Mounting /root/dev on /dev/.static/dev failed
Mounting /sys on/root/sys faild failed
Mounting /proc on/root/proc faild failed
target file name does not have /sbin/init

Por favor, necesito que me ayuden a independizarme de windows.
Gracias

---

### Post by sergiom99 on 2009-01-19
Hola, bienvenido!
vamos por partes:
1. que versión de ubuntu estas tratando de instalar?
2. Como lo bajaste? Usaste la opcion de comprobar disco que trae el instalador?
3. Podes arracancar con el LiveCD y ver si detecta todo el hardware de tu PC?
4. Si podes hacer lo anterior, entra en una terminal y tipea los comandos:
```
 lspci
lsusb
```
y postea en este foro los datos que te devuelve la consola.
5. Si no podes hacer esto, por favor postea lo mas detallado que puedas las especificaciones del hardware de tu PC.

Esperamos tus respuestas para seguir ayudandote a aprender.

---

### Post by Nikolopulus on 2009-01-19
Version 7.04, tengo el CD original. Se que anda porque hace unas semanas lo usó un amigo. Estoy tratando de conseguir una version más nueva, pero como no tengo internet en casa se me complica
No puedo arrancar con live CD
La maquina tiene un AMD X2 de 5200, 2 GB de RAM con mobo MSI k9A2GM-F V3. No tengo ninguna placa agregada.

---

### Post by sergiom99 on 2009-01-19
es una version muy vieja, capaz que no reconoce parte del hard y por eso no arranca el liveCD.
Te recomendaria que trates de conseguir un CD de 8.04 u 8.10 para ver si funciona como LiveCD y si detecta todo.

por donde vivis? capaz tenes algun otro miembro cerca y te puede facilitar una copia.

---

### Post by guillermolisi on 2009-01-19
> **Nikolopulus said:**
> Version 7.04, tengo el CD original. Se que anda porque hace unas semanas lo usó un amigo. Estoy tratando de conseguir una version más nueva, pero como no tengo internet en casa se me complica
No puedo arrancar con live CD
La maquina tiene un AMD X2 de 5200, 2 GB de RAM con mobo MSI k9A2GM-F V3. No tengo ninguna placa agregada.
Dame una pista de donde sos y tal vez podamos combinar que te hagas de un CD de la 8.10 desktop 32 bits, asi podes probarla como Live CD y no extrañar mucho Internet (cosa que despues seria conveniente consigas para instalar las actualizaciones).

---

### Post by Nikolopulus on 2009-01-20
Vivo en almagro, en Yrigoyen y Maza. Ya pedí un CD a Canonical, pero va a tardar un toque.
Si alguien me hace la gamba y me pasa un CD sería genial, laburo a la mañana y, hasta que arranque la facu, tengo casi toda la tarde libre.
Gracias

---

### Post by Nikolopulus on 2009-01-22
Bueno, gracias a guillermolisi que me pasó el liveCD de Ubuntu 8.10, ya soy oficialmente usuario linux.
Ahora empieza la parte donde tengo los mil millones de problemas que no puedo solucionar.
Arranco por dos faciles:
Tengo un aviso que dice que el controlador gráfico FGCRX privativo para ATI/AMD está deshabilitado. Le doy a habilitar, me pide la contraseña pero no me lo habilita ¿que puedo hacer? Windows reconoció mi placa como una ATI Radeon 2100.
El otro tema es de donde puedo bajar los plug-ins para reproducir .mp3 y demás formatos que no están incluidos en Ubuntu.
Una vez más, gracias por toda la ayuda

---

### Post by guillermolisi on 2009-01-22
> **Nikolopulus said:**
> Bueno, gracias a guillermolisi que me pasó el liveCD de Ubuntu 8.10, ya soy oficialmente usuario linux.
Ahora empieza la parte donde tengo los mil millones de problemas que no puedo solucionar.
Arranco por dos faciles:
Tengo un aviso que dice que el controlador gráfico FGCRX privativo para ATI/AMD está deshabilitado. Le doy a habilitar, me pide la contraseña pero no me lo habilita ¿que puedo hacer? Windows reconoció mi placa como una ATI Radeon 2100.
El otro tema es de donde puedo bajar los plug-ins para reproducir .mp3 y demás formatos que no están incluidos en Ubuntu.
Una vez más, gracias por toda la ayuda
Es que cuando habilitas los controladores privativos para la ATI lo que sucede normalmente es que intente bajar la ultima version desde Internet. Como no estas conectado, pasa lo que observaste.

Los CODECS los podes bajar de .... Internet, mas precisamente de los repositorios de Ubuntu.

Hay forma de bajar paquetes en una maquina que posee conexion, copiarlos a (por ejemplo) un pendrive y luego instalarlos en la PC que no esta conectada a la Net, pero tal vez te resulte mas facil llevar la maquina hasta algun lugar con conexion, actualizar ahi (ojo que lo que tenes instalado no esta actualizado. Hay una buena cantidad de actualizaciones para aplicarle) y dejarla funcionando, todo de una vez (y con algo de tiempo segun la conexion a Internet que logres conseguir prestada).

---

