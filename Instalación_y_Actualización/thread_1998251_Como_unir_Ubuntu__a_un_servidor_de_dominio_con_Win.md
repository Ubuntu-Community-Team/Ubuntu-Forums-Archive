---
title: "Como unir Ubuntu  a un servidor de dominio con Windows server 2000?"
date: 2012-06-06
forum: Instalación y Actualización
---

### Post by pelaolinux on 2012-06-06
Hola amigos de Ubuntu chile, necesito ayuda con el siguiente requerimiento:
 
Tengo una red con un servidor de dominio con Windows Server 2000, el cual tengo varios usuarios registrados en el active directory. La prueba que deseo hacer es cambiar el sistema operativo a Ubuntu 12.04 en algunos computadores en  la empresa que trabajo. Estos pc  no  necesario que estén con Windows  ya que con los programas que trabajan en ellos están todos para Linux y funcionan perfectamente ya que los probé hace algunos días. 
Mi problema es el siguiente: necesito ver la forma de cómo puedo unir los equipo al dominio de la empresa y configurar  los usuario asignado en cada pc los cuales están registrado en el active directory. ¿Alguien puede ayudarme con eso?

Espero que puedan ayudarme con este tema, estaría muy agradecido.
Estaré atento a sus respuestas.


Saludos!

---

### Post by pelaolinux on 2012-06-11
Encontré la solución de mi problema y dejare el tutorial para que otras personas que tengan este problema puedan conectarse igual que yo.

Se debe verificar que el archivo /etc/resolv.conf tenga los dns del dominio.
en mi caso ejecutándolo en la consola como:
#sudo vi  /etc/resolv.conf 

Luego se debe instalar likewise o lo buscan como Join Domain 
para instalarlo desde la consola se coloca el siguiente comando:
#sudo apt-get install likewise-open

Se debe verificar que el nombre de la máquina sea el registrado en el dominio.
En mi caso cada PC de mi empresa están configurado con un nombre como TPC-01 , 02, etc...

Por último se ejecuta la herramienta para unir la máquina mediante línea de comandos.

#domainjoin-cli join dominio.cl administrador

Pedirá el password del administrador del domino y listo terminará mostrando el mensaje de:

SUCCESS
Iniciamos con el usuario del dominio al momento de iniciar el sistema de la siguiente manera
[email]usuario@dominio.cl[/email]

luego que esto se cumpla podremos entrar con un usuario que este en el active directory del servidor del dominio
 en mi caso todo esto lo hice con ubuntu 12.04 y el servidor de dominio de mi empresa esta con windows server 2000. 
ejemplos de los comandos aplicados fue el siguiente 
#domainjoin-cli join tunning.cl administrator
(luego me salia)
[email]administrator@TUNNING.CL[/email] password: *************************
(luego me salia)
SUCCESS
(luego inicia seccion con mi usuario del domini y mi password)
[email]pvergara@tunning.cl[/email]
(y password)
password: *********
y todo listo ya podía usar mi usuario del dominio con los mismos privilegios.

---

