---
title: "Compartir carpetas e impresora :("
date: 2008-05-15
forum: Hardware
---

### Post by valucha on 2008-05-15
[COLOR="DarkOrchid"]Hola chicos, estoy ahce unos días volviendome loca tratando de compartir algunas carpetas y la impresora entre todas las compu y la verdad que ya no sé qué más hacer...

Seguí el manual que te dan en el Wiki de Ubuntu, y no pasa nada, no puedo ver las carpetas de otras máquinas en ninguna máquina, y tampoco puedo ver la impresora desde las otras compus.

Después segui miles de manuales más en google y ninguno me da resultado.

La cosa es masomenos así:


Tengo una PC de escritorio con Ubuntu Hardy con una impresora usb HP.
Tengo una notebook con Ubuntu Hardy
Tengo otra notebook con Ubuntu Hardy y Vista (pero ni pienso meter a Vista en el medo, porque ni se usa, lo dejamos por la garantía)

Tengo FIbertel y comparto internet por un router Dlink DI-524

La PC se conecta por cable al router
Las notebooks se conectan de forma inalámbrica al router.

Lo que quiero es:
Poder ver ciertas carpetas entre las 3 máquinas, que todas las máquinas puedan imprimir en la HP. Y si es posible, que no haga falta poner un password para entrar.

Les dejo mi configuracion de smb.conf para que vean si me mandé alguna cagada ahi... Tengo la misma configuración en todas.

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the 
workgroup/NT-domain name your Samba server will part of
   workgroup = PACARUNA

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = SHARE

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

Edited: Con la PC puedo ver si entro a Lugares->Red lo siguiente:
Notebook 1
Red de windows
PC

Si entro a la Notebook 1, se me tilda y tengo que forzar el cierre
Si entro a Red de Windows, solo puedo ver las carpetas mias que yo quise compartir (osea, las mismas que están en este equipo, la PC).

Desde la Notebook 1, si entro a Lugares->Red veo: Red de WIndows y ahi adentro no veo nada...
CUando entro a Sistema->Administracion->Impresoras, me aparece una impresora de red con WIndows que tenía antes esa notebook, y si pongo "buscar" (para buscar mas impresoras) en el recuadrito solo me aparece NOTEBOOK 1: HP BLA BLA BLA..(que seria la misma impresora de esa notebook que no existe más que es la que pretendo cambiar)

La otra notebook todavia no la configuré quiero hacerlo con la Nobtebook 1 primero y después lo hago igual con la otra.




Espero no molestarlos, se que hay miiiles de posts al respecto, pero ninguno me sirvió, ni tampoco los tutoriales de internet, debe ser que hay algo implícito que no te dicen y no lo sé (??????)

Saludos, y gracias desde ya, Valen[/COLOR]

---

### Post by Mister X on 2008-05-15
Si vas a compartir carpetas entre maquinas con linux olvidate de samba y usá NFS!!!

---

### Post by Mauro22 on 2008-05-15
Primero lo primero:

* Proba si la red funciona OK, pingeando las otras pc.
O sea, haces ifconfig en una y te anotas la ip de esa maquina. Vas a otra y pones:
ping ip (ejemplo: ping 192.168.0.99)
y ver si "llegas" al otro lado.
* Verifica que todas las PC esten dentro de los mismos rangos de ip/mascara de sub red.
* Que esten todos en el mismo grupo de trabajo (workgroup)

---

### Post by valucha on 2008-05-15
> **Mauro22 said:**
> Primero lo primero:

* Proba si la red funciona OK, pingeando las otras pc.
O sea, haces ifconfig en una y te anotas la ip de esa maquina. Vas a otra y pones:
ping ip (ejemplo: ping 192.168.0.99)
y ver si "llegas" al otro lado.
* Verifica que todas las PC esten dentro de los mismos rangos de ip/mascara de sub red.
* Que esten todos en el mismo grupo de trabajo (workgroup)

[COLOR="DarkOrchid"]*1= OK
*2= ni idea qué es, pero en el ifconfig me dice en todas  Máscara:255.255.255.0
*3= OK[/COLOR]

---

### Post by faktorqm on 2008-05-16
No buscaste en el foro ¬¬ [http://ubuntuforums.org/showpost.php?p=4343317&postcount=3](http://ubuntuforums.org/showpost.php?p=4343317&postcount=3)

Configuración de la red para lo que querés hacer:

para que no te interfiera con lo que ya tenes, fijate en cualquier pc primero que IP tenés, de ese IP, en cada pc tenes que tener uno distinto del otro.

ejemplo: 

pc 1: 

direccion ip: 192.168.1.[COLOR="Red"]2[/COLOR]
mascara: 255.255.255.0
default gateway: 192.168.1.1

pc 2: 

direccion ip: 192.168.1.[COLOR="Red"]3[/COLOR]
mascara: 255.255.255.0
default gateway: 192.168.1.1

pc 3: 

direccion ip: 192.168.1.[COLOR="Red"]4[/COLOR]
mascara: 255.255.255.0
default gateway: 192.168.1.1

En los DNS es equivalente poner 192.168.1.1 o los de fibertel. 
Con el tema de la máscara, te lo explico mas o menos para que lo entiendas: cuando tu mascara es 255.255.255.0, la direccion de red esta determinada por los primeros 3 numeros de la direccion ip. siguiendo con el ejemplo, si tengo 192.168.1.1, la RED es la 192.168.1 y tal o cual pc es la 1 dentro de esa red. solo poder poner hasta 254. (en total te quedan 253 compus). En cambio, si tu mascara fuera 255.255.0.0, la red estaria determinada por 192.168, esto es, con la mascara anterior 192.168.1.4 y 192.168.4.8 son dos direcciones en distintas REDES, con esta mascara, ambas estan en la misma red. Si tu pregunta es, para que hacen esto, es para poner 253 compus en una red, si necesitas que más compus esten en la misma red cambias la mascara y podes 64000 y pico. (253 al cuadrado).

Espero que te haya servido, a pesar de ser un tutorial tentativo. Salu2!

---

### Post by valucha on 2008-05-16
[COLOR="DarkOrchid"]HU ese tutorial si lo encontré, pero pensé quehabías pegado lo mismo que decía en el wiki de Ubuntu, mil perdones por no leer bien...

Hoy lo hago, si queda todo bien, le doy por solved y les dejo de molestar :)

GRacias y saludos.


Edit 5 horas después: Bueno, hoy probé haciendolo como dice el manual y no puedo ver las carpetas desde ninguna máquina me dice:
"Error: falló al montar la compartición Windows. Seleccione otro visor e intentelo de nuevo".
Capaz lo que estoy haciendo mal es el tema de la dirección... porque tu manual me dice que ponga la dire de ip, y yo la saco desde la configuración del router, en ningún lado en el samba determine una ip especial (Y NI IDEA COMO HACERLO).

Y si lo estoy haciendo bien, entones no sé donde está el error... EL testparm me da todo bien al parecer.[/COLOR]

---

### Post by Mister X on 2008-05-16
Las impresoras tenes que podes verlas sin necesidad de samba, mediante CUPS. Desde el menú: Sistema->Administracion->Impresoras.
En la maquina que tiene la impresora conectada, tenes que tildar la opcion: "Compartir las impresoras publicas conectadas"
Y en las demas maquinas clikeas en Impresora nueva.

Con lo de compartir las carpetas, te dije de usar NFS (Network File System) porque es el modo "natural" de hacer eso en linux, pero si vos queres usar samba para aprender, adelante ;)

Saludos!

---

### Post by valucha on 2008-05-16
> **Mister X said:**
> **1)**Las impresoras tenes que podes verlas sin necesidad de samba, mediante CUPS. Desde el menú: Sistema->Administracion->Impresoras.
En la maquina que tiene la impresora conectada, tenes que tildar la opcion: "Compartir las impresoras publicas conectadas"
Y en las demas maquinas clikeas en Impresora nueva.

**2)**Con lo de compartir las carpetas, te dije de usar NFS (Network File System) porque es el modo "natural" de hacer eso en linux, pero si vos queres usar samba para aprender, adelante ;)

Saludos!

[COLOR="DarkOrchid"]1)HIce eso antes, hace un tiempo, después actualicé todas a Hardy y se perdió la configuración... Ahora desde las otras máquinas no puedo ni ver la otra impresora por más que en esta haya tildado las opciones necesarias en el panel de control de la impresora.

2)No no, me habían dicho que era más fácil y dada mi condición de novata decidí hacerlo con Samba...

Tengo una duda... para restaurar toda la configuración inicial de Samba (porque me parece que lo toquetié demasiado y eso es lo que me está trabando) es suficiente desisntalandolo completamente desde el synaptic? o eso no daría resultado y tnendría que hacer algo como dpkg reconfigure samba??


GRacias MIster X por tu respuesta y a los proximos respondientes (?) :)
[/COLOR]

---

### Post by Mister X on 2008-05-16
si, para eliminar la configuracion desde Synaptic es "Eliminar completamente" o sino desde la consola:
```
apt-get remove --purge
```

---

### Post by faktorqm on 2008-05-17
Las impresoras se comparten por CUPS, como decis vos, pero tengo entendido que esto se hace bajo samba.
La configuración original de samba no comparte nada, asi que bien podrias poner "nada" y listo. Mi tutorial te pareció dificil? Te pregunto para saber si necesito agregarle más cosas o si omiti cosas que capaz vos te terminaste encontrando en un problema.
NFS es otra solución, pero no es compatible con windows, es para compartir entre sistemas operativos Unix-like. Si lo haces con samba, aparte de compartir entre los linux, tambien podes compartir con los windows sin problemas. (o con mac os llegado el caso).
Y por el tema de la red fijate en cada pc el comando "ifconfig" a ver que ip te tira en cada una y listo.  Salu2!

---

### Post by Hei Ku on 2008-05-17
CUPS puede funcionar sin samba ni nfs. Es algo independiente. Yo lo tengo configurado asi en mi casa.
En la wiki de ubuntu-es hay un tutorial para compartir impresoras que a mi me sirvio para configurarla con CUPS.

---

### Post by Hei Ku on 2008-05-17
CUPS puede funcionar sin samba ni nfs. Es algo independiente. Yo lo tengo configurado asi en mi casa.
En la wiki de ubuntu-es hay un tutorial para compartir impresoras que a mi me sirvio para configurarla con CUPS.

---

### Post by faktorqm on 2008-05-17
mira vos no sabia. en el sitio de samba dice que se integra al 100% con cups, por eso. Salu2!

---

### Post by Hei Ku on 2008-05-18
es que samba debe aprovechar cups para compartir las impresoras con windows, pero si son todos equipos linux, no te hace falta. en mi caso fue dar de alta la impresora con el hp-setup y despues ir a la otra pc, borrar la que estaba, poner la ip de la maquina, seleccionar la nueva cola de impresion y ya esta.
El unico problema que tuve con esta impresora es que no anduvo bien cuando la di de alta por el asistente de CUPS, tuve que ejecutar el hp-setup. Fuera de eso, todo joya.

---

### Post by euzkoarima on 2008-05-18
Comentario informativo, casi OT, OSX y NFS van de 10, osx en el fondo es un BSD (FreeBSD para ser más exacto).

---

### Post by hexbase on 2008-05-18
Tengo el mismo problema. =(
Me dice nt_status_bad_network_name.

---

### Post by faktorqm on 2008-05-18
Creo que lo tuyo es por que samba solo admite nombres con ciertos caracteres, (no quiero decir cualquier cosa pero creo que solo acepta los que acepta nt4), pero 2k, xp, y vista te deja poner nombres con guion bajo, guion del medio, o ese tipo de cosas.
si les pones a todas, para probar, uno, dos, tres y asi capaz te salva el problema. Contanos como te fue.

val: y? lo solucionaste? necesitas ayuda x msn/irc? salu2!

---

### Post by margori on 2008-05-19
Valucha, agregaste los usuarios permitidos para samba.

Yo hice un pequeño "tuto" o "como" en mi blog [http://margori.wordpress.com/2008/05/01/como-compartir-carpetas-entre-windows-y-hardy-rapido-y-facil/](http://margori.wordpress.com/2008/05/01/como-compartir-carpetas-entre-windows-y-hardy-rapido-y-facil/)

Creo que la clave esta en "sudo smbpasswd -a <USUARIO>"

---

### Post by valucha on 2008-05-19
[COLOR="DarkOrchid"]No pude ni probarlo porque encima que no estoy teniendo tiempo, mi viejo necesita la notebook y no le puedo arreglar...

Disculpen creo que reinstalando todo y siguiendo 1 sola guía va a andar :)

Gracias igual[/COLOR]

---

### Post by hexbase on 2008-05-20
No, no es el nombre porque no tiene ningun caracter extraño. El error ya no aparece más, pero no puedo listar las computadoras que estan en la red... ese es mi mayor problema.

---

### Post by sergiom99 on 2008-07-29
> **margori said:**
> Valucha, agregaste los usuarios permitidos para samba.

Yo hice un pequeño "tuto" o "como" en mi blog [http://margori.wordpress.com/2008/05/01/como-compartir-carpetas-entre-windows-y-hardy-rapido-y-facil/](http://margori.wordpress.com/2008/05/01/como-compartir-carpetas-entre-windows-y-hardy-rapido-y-facil/)

Creo que la clave esta en "sudo smbpasswd -a <USUARIO>"

Gracias che! me habia olvidado de este detalle y estaba teniendo problemas.
No se porque no esta activada la medallita, sino te agradeceria el reminder.
Sergio

---

### Post by gefarion on 2008-07-30
Suponiendo q tu red esta bien configurada, proba configurar samba usando SWAT, es muy intuitivo y funciona muy bien. Pero antes de intentar configurar samba confirma que la red este bien configurada. Para esto puedes intentar hacer:

nmap -sP 192.168.1.*

donde 192.168.1.* seria la forma de las ip de tu red.

Recuerda que tambien puedes acceder a las compariticiones samba desde el explorador de archivos, poniendo en la barra de dirrecion "smb://xxx.xxx.xxx.xxx"

Saludos.

---

