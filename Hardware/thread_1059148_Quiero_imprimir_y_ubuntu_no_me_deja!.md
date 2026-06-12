---
title: "Quiero imprimir y ubuntu no me deja!"
date: 2009-02-03
forum: Hardware
---

### Post by Mauro22 on 2009-02-03
Hola!!


Tengo un asunto y ojala puedan ayudar...


Necesito imprimir desde mi laptop con ubuntu en la HP que esta conectada a la pc de escritorio con XP.

+ PC de escritorio: 

Tiene compartida la HP 1350, que es USB.
La PC esta conectada al router wifi por cable.
El nombre es Garage y el Grupo de trabajo es CASA.

+ Notebook Con Ubuntu/Vista:

Esta conectada al router por wifi
Modifique samba para que esten dentro del mismo grupo.
Desde Vista, encontró, instaló e imprimió lo mas bien.

+ Punto de Anclaje:

Voy a Menu -> Sistemas -> Administracion -> Impresoras
Selecciono SAMBA, le doy navegar y aparece en la lista.

El problema viene al darle en 'Verificar' Con o Sin autorizacion, Ponga Guest, Invitado, Papo o ubuntu, no me deja conectarme a la impresora.

+ Error:

La impresora compartida esta inaccesible.


+ Adjunto imagen



Desde ya gracias y espero que se les ocurra algo.


Edito:

Compre otra impresora por usar por ahora, Solved temporal, pero lo dejo por si alguien se le ocurre o le pasa lo mismo.

---

### Post by biale on 2009-02-06
Esa es una prueba que no hice, pero igual voy a intentar (humildemente) ayudar...
Te cuento que la impresión en modo remoto esta plagada de pequeños detalles que suelen complicar el tema, el acceso a archivos siempre es mas facil. Solo repasemos las generales de la ley:

Supongo que la PC de escritorio tiene instalado WXP SP2 o SP3.

Para una primera prueba, la impresora debería estar compartida al grupo "Todos" y para acceder desde Linux usaría una cuenta mas fuerte que la cuenta de Invitado. Concretamente la cuenta de "Administrador", con clave. Si por algún motivo no tiene clave hay que ponerle una.

El nombre de la impresora y su share no deberían incluir espacios. Por las dudas evitaría que el nombre tenga mas de 8 caracteres "universales". Igual probaría acceder a la impresora usando la dirección de IP de la PC servidor para evitar el tema de la resolución de nombres.

Un vistazo al "visor de sucesos" de Windows puede ayudar a detectar algo.

Supongo que la firewall de la notebook no esta molestando (?)

Al menos bajo Windows, la responsabilidad de los drivers corre por cuenta y riesgo del equipo cliente y si el servidor detecta algo que no le gusta no deja imprimir. Si la computadora cliente fuera windows, en principio el servidor pide/ intenta forzar la instalación de los drivers adecuados. Entonces, y siempre pensando en Windows a veces conviene hacer una instalación de la impresora como si fuera local para generar el soporte adecuado. Siguiendo el razonamiento conectaría la impresora por un momento a la notebook en forma local, instalaría lo que fuera y probaría imprimir algún docuemento. ¿Lo habías hecho?

A lo mejor el comando smbclient ayuda.

Espero que algo de esto sirva. Saludos.

---

### Post by Mauro22 on 2009-02-06
> 
Supongo que la PC de escritorio tiene instalado WXP SP2 o SP3.

Windows Xp sp2
> 
Para una primera prueba, la impresora debería estar compartida al grupo "Todos" y para acceder desde Linux usaría una cuenta mas fuerte que la cuenta de Invitado. Concretamente la cuenta de "Administrador", con clave. Si por algún motivo no tiene clave hay que ponerle una.

Chequeado y no funciona con ninguna cuenta, con o sin pass
> 
El nombre de la impresora y su share no deberían incluir espacios. Por las dudas evitaría que el nombre tenga mas de 8 caracteres "universales". Igual probaría acceder a la impresora usando la dirección de IP de la PC servidor para evitar el tema de la resolución de nombres.

el nombre es hp1350s asi que no habria problema
ping hace, asi que ahi el problema no esta
> 
Un vistazo al "visor de sucesos" de Windows puede ayudar a detectar algo.

No hay nada raro
> 
Supongo que la firewall de la notebook no esta molestando (?)

El vista en la notebook no hubo problemas, imprimio lo mas bien
En Ubuntu, el iptables no esta negando nada.
> 
Al menos bajo Windows, la responsabilidad de los drivers corre por cuenta y riesgo del equipo cliente y si el servidor detecta algo que no le gusta no deja imprimir. Si la computadora cliente fuera windows, en principio el servidor pide/ intenta forzar la instalación de los drivers adecuados. Entonces, y siempre pensando en Windows a veces conviene hacer una instalación de la impresora como si fuera local para generar el soporte adecuado. Siguiendo el razonamiento conectaría la impresora por un momento a la notebook en forma local, instalaría lo que fuera y probaría imprimir algún docuemento. ¿Lo habías hecho?

Si, conecte el USB directamente a la notebook con Ubuntu y en 4 minutos estaba imprimiendo, pero no es la solucion.
> 
A lo mejor el comando smbclient ayuda.

No sabria que hacer con ese comando.
> 
Espero que algo de esto sirva. Saludos.

Primero, gracias por tomarte el tiempo en responder :D
Segundo, el tema lo sigo dejando e iré probando lo que me den para asi llegar a una solucion que le puede servir a otro.

---

### Post by faktorqm on 2009-02-09
Hola, yo en casa tengo una hp igual que vos y me anda barbaro. Sino hace la gran, logueate como administrador y listo! (primero seteale un pass, si no no podes) si no podes ahi, descartas problemas de permisos.
Anda al xp, habilitale todo lo de compartir carpetas e impresoras y listo. 

Y si no podrias probar de habilitar IPP en la pc que tiene la impresora e imprimir por ahi. Siempre IPP es una opcion.

Taz super seguro que el firewall no te esta tapando nada? Salu2!

---

### Post by biale on 2009-02-12
Si querés probar una vez mas con la impresión usando la cadena "cupsys+Samba", te paso algunos detalles a tener en cuenta.

Conviene verificar la resolución Netbios en ambas direcciones haciendo ping, no con las direcciónes de IP sino con las nombres de los equipos. Las direcciones resueltas deberían estar en el mismo segmento de red:

Desde Windows	Ping  netbios_name_ubuntu
Desde Ubuntu	Ping  netbios_name_wxp

La mejor manera de verificar el funcionamiento de Samba es acceder (leer, escribir) desde la notebook a un archivo en WXP. También la viceversa, es decir leer y escribir un archivo en la notebook desde WXP. 

Si llegaste hasta acá bien, verfica el archivo /etc/samba/smb.conf La linea de la sección global "printing = cups" debería estar activa y si no lo esta, agregala. ¿Como comfiguraste Samba? ¿A manopla? Ahora acordate que hay que reiniciar samba. Recuerdo haber tenido que reiniciar la máquina completa (?).

El archivo /etc/samba/smbusers esta  OK?

Para definir la impresora en la notebook, parece que lo mejor es usar la interface web de Cups: [https://localhost:631](https://localhost:631)
Si ya tenes la impresora definida proba en cambiar alguna pavada para que regenere la definición completa. La uri tiene la forma:

smb://user:passwd@ip_pc_win/impresora
user:  Es el nombre de un usuario del sistema Windows.
password: Es la contraseña de dicho usuario.
ip_pc_win: Es la dirección IP del equipo Windows que comparte la impresora.
impresora:  Es el nombre que le dimos a la impresora al compartirla en el equipo Windows 

También se podría poner así:
smb://username:password@WORKGROUP/WINDOWSNETBIOSNAME/printersharename
smb://username:password@WINDOWSNETBIOSNAME/printersharename

Recomiendan reniciar a Cups. Yo verificaría ademas que la linea anterior haya quedado bien codificada en el archivo de definición de impresoras:
En  /etc/cups/printers.conf
Es la linea "DeviceURI smb://user:password@..."
O sea que la clave de Administrador queda visible! Alguna vez vi escrito "administrador" con minúsculas, sospecho que es un error.

Si te decidis a hacerlo conta como te fué. Saludos.

EDIT: El emoticon que aparece en realidad es un ":"

---

### Post by Mauro22 on 2009-02-12
OK, gracias a los 2 por sus respuestas.


Lamentablemente, (como era de esperarse) la PC con Xp empilchó hacia el mas alla, dejando a la impresora sin host.


Ni bien logre hacerla andar, voy a probarlo.


Gracias, nuevamente!

---

