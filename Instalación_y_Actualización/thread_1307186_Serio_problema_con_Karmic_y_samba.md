---
title: "Serio problema con Karmic y samba"
date: 2009-10-30
forum: Instalación y Actualización
---

### Post by moFeta on 2009-10-30
Muy buenas.
Acabo de instalar karmic, instalacion nueva en un equipo que tenía Jaunty previamente. Tengo otro PC con Jaunty, que las oficia de servidor de impresión y depósito de archivos, todo mediante el uso de samba para hacerlo accesible además a un note con mala-Vista.
El detalle es que desde Karmic no hay caso que pueda conectarme al PC, y por ende, no puedo configurar una impresora. El mensaje es que no puede acceder al listado de compartición. Todo estaba funcionando muy bien desde Jaunty, y sigue funcionando muy bien desde Vista, no se ha tocado nada en el servidor.
Al parecer hay un "issue" en Karmic al tratar de integrarse a una red con samba...
Si alguien tiene alguna idea o le ha pasado lo mismo...

Gracias

---

### Post by moreback on 2009-10-31
- Instalaste los paquetes de samba?
- Configuraste el smb.conf?
- Revisaste las contraseñas con smbpasswd?
- Saludos.

---

### Post by Carlos C on 2009-11-02
Si, también creo que faltan algunos datos para no sugerir cosas que para ti son evidentes. Lo que tienes en tu smb.conf es importante, lo mismo lo que te da el comando "[testparm]("http://blockdeubuntu.blogspot.com/2008/07/verificando-la-sintaxis-del-archivo-de.html")" para verificar que no sea un problema de sintaxis en ese archivo. Puedes también verificar los servicios de samba que están corriendo. Lo puedes ver [aquí]("http://blockdeubuntu.blogspot.com/2008/07/cmo-verificar-la-disponibilidad-y.html").

Saludos.

---

### Post by moFeta on 2009-11-04
Disculpen la demora, pero estaba buscando y probando otras soluciones que encontré por ahí, y el problema en definitiva no es la configuración de samba.
Esta ya estaba funcionando perfectamente en el servidor desde hace unos cuantos años, actualmente aún con Ubuntu 9.04, este es 'visto' y accesible sin problemas desde Vista, y desde Jaunty.
El problema estaba definitivamente en la instalación nueva de Karmic, y según entiendo, no necesito instalar samba en el cliente, para poder acceder a recursos en el servidor, solo necesito tener smbclient y este viene por defecto. Sin embargo, cada ves que ejecutaba "smbtree" decía lo mismo:> Enter ubuntu's password: 
HOGAR
	\\HADES          		hades server (Samba, Ubuntu)
cli_start_connection: failed to connect to HADES<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

Por las dudas, agregué a /etc/hosts la dirección IP de hades, con el mismo resultado.
Finalmente di con una solución parcial: deshabilitar el firewall de ubuntu
```
sudo ufw disable
```y el resultado es que ahora la salida de smbtree es:> Enter ubuntu's password: 
HOGAR
	\\HADES          		hades server (Samba, Ubuntu)
		\\HADES\respaldo       	
		\\HADES\directorio        	
		\\HADES\deskjet-3500   	hp deskjet 3500
		\\HADES\HP-LaserJet-P1005	HP HP LaserJet P1005
		\\HADES\print$         	Printer Drivers
		\\HADES\IPC$           	IPC Service (hades server (Samba, Ubuntu))

Es decir, no está configurado adecuadmente el firewall de modo de permitir el acceso a los recursos de red mediante samba.
¿Alguien sabe como se hace eso? Para no tener totalmente deshabilitado el firewall.

---

### Post by Carlos C on 2009-11-04
Creo que la configuración que buscas está acá:

[http://ubuntuforums.org/showthread.php?t=1225549](http://ubuntuforums.org/showthread.php?t=1225549)


Saludos.

---

### Post by endbyte on 2009-11-05
amigos cualquier problema con samba en ubuntu 9.10 no es realmente problema del OS sino un problema de comunicacion mas que todo porque a mi mepaso lo mismo que a varios de ustedes por lo cual detallo de donde se origina todo esto:

ubuntu 9.10 ya trae instaldo por defecto el smbclient y solo tendriamos como agregado ke instalar el samba desde el centro de software de ubuntu y con eso seria suficiente para ke podamos visualizar la red windows desde ubuntu y ademas compartir carpetas e impresora instalda en ubuntu, el unico problemilla que trae esta nueva implementacion es que dentro de la configuracion del servidor samba el workgroup esta digitado en minusculas y debe estar en mayusculas para que todo funcione a la perfeccion y para esto solo ban a: sistema / administracion / samba / preferencias / configuracion del servidor y donde dice "workgroup" solo cambienle a "WORKGROUP" y eso es todo.

para los ke han instalado samba server desde terminal y winbind les recomiendo purgar todo esto y kitarlo por completo y en synaptyc simplemente revisar ke esta instalado smbclient y el samba ke desde luego recuerden deben hacerlo desde centro de software con solo eso t todos los problemas de red y comparticiones estaran solucionados, espero ayudarles con esto porke yo pase un infierno de dos dias leyendo foros y probando soluciones y nada jajaja y realmente el unico probelam ke existe es el del workgroup por WORKGROUP jaja espero haberme dado a entender, suerte a todos.

---

### Post by alfplayer on 2009-11-06
Se puede compartir una carpeta con windows haciendo click con el botón secundario del mouse en la carpeta que se quiere compartir. Si no está instalado samba como en las instalaciones nuevas de 9.10 (que es necesario para crear la carpeta compartida con windows), el asistente pregunta si se quiere instalar, solo hay que seguir los simples pasos de instalación que no requieren conocimiento técnico.

---

### Post by moFeta on 2009-11-09
> **Carlos C said:**
> Creo que la configuración que buscas está acá:

[http://ubuntuforums.org/showthread.php?t=1225549](http://ubuntuforums.org/showthread.php?t=1225549)


Saludos.

Gracias.
Funciona la primera vez, reinicio y ya no funciona más.
Puede acceder al directorio compartido poniendo la dirección completa en nautilus, pero explorar la red, ni hablar. Smbtree además no muestra acceso al árbol.
Seguiré buscando.

---

