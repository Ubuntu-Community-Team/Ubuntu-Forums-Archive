---
title: "montar disco rigido en red. problemas con permisos."
date: 2009-05-09
forum: Hardware
---

### Post by granjero on 2009-05-09
hola, no quería preguntar por aca pero ya agoté google y los foros...  ):P :-k

tengo 2 pcs.

**en la pc1**
2 discos rigidos 1 de 20gb con el SO (xubuntu 8.04)
                 1 de 80gb(formateado en ext3, vacío, disco que va a ser compartido)
1 placa de red con la ip fija 10.0.0.2

en esa pc en el fstab monta el disco de 80 en /media/disco80gb

la linea del fstab la arme así

```
/dev/sdb1 /media/disco80gb ext3 user,sync,rw 0 1 
```

en el archivo /etc/exports agregue la linea:

```
/media/disco80gb 10.0.0.1(rw)
```

**en la pc 2**

SO ubuntu 8.04 y 2 placas de red una por donde entra la inet y otra con la ip fija 10.0.0.1 conectada a la otra pc con un cable de red cruzado.

monto con este comando pero no logro escribir en el disco montado
```
sudo mount 10.0.0.2:/media/disco80gb /home/jm/disco80gb
```

supuestamente cuando en el archivo /etc/exports (de la pc que tiene el disco de 80)le pongo sin espacio despues de la ip (rw) estoy dando a esa ip los derechos de lectura y escritura, pero al montar no puedo crear carpetas ni nada...

donde estoy pifiando?

gracias de antemano.

---

### Post by guillermolisi on 2009-05-09
Tengo algo hecho en casa y en el laburo.
Te muestro como lo tengo hecho en casa, que es mas simple y pareceria coincidir con el entorno que mencionas.
En la maquina que publica los recursos tengo ```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home/guille/downloads  90.0.0.0/255.255.255.0(sync,rw)
```De esa forma dejo libre que cualquier maquina de la red mencionada pueda "ver" ese recurso (fijate que menciono la red y su mascara, luego los permisos en forma similar a como vos lo hiciste).

En la PC que monta los recursos publicados via NFS, tengo en /etc/fstab:
```
ubuntu804server:/home/guille/downloads /media/ubuntuserver/downloads nfs user,noauto,atime,auto,rw,nodev,exec,nosuid 0 0
``` Asi como lo montas vos es posible que solo permita que un superuser o root puedan escribir en ese disco.
Esto lo podrias comprobar si accedes al recurso compartido montado con un sudo antepuesto a un mkdir o similar (para que confirmes si crea algo o no en ese disco).

Proba y comenta como te fue.

---

### Post by granjero on 2009-05-09
guillermo agradezco tu pronta respuesta, pero te quiero preguntar una cosa.

¿en tu caso la pc que monta, lo hace al iniciarse? o sea ¿tenés siempre prendido el host que comparte?

yo voy a montar desde consola o con un script cuando este prendida la pc que publica el disco rígido...

y no termino de entender la línea que pones del fstab.

¿por que dice ubuntu804server en vez de la ip que corresponde?  

ahora voy a hacer unas pruebas y te cuento como va saliendo la cosa...

gracias

---

### Post by guillermolisi on 2009-05-09
> **granjero said:**
> guillermo agradezco tu pronta respuesta, pero te quiero preguntar una cosa.

¿en tu caso la pc que monta, lo hace al iniciarse? o sea ¿tenés siempre prendido el host que comparte?

yo voy a montar desde consola o con un script cuando este prendida la pc que publica el disco rígido...

y no termino de entender la línea que pones del fstab.

¿por que dice ubuntu804server en vez de la ip que corresponde?  

ahora voy a hacer unas pruebas y te cuento como va saliendo la cosa...

gracias
Si, lo hace al iniciarse y para ello la otra ya tiene que estar encendida, asi publica el recurso.
En mi casa las maquinas estan siempre encendidas, no las apago nunca salvo por cuestiones de mantenimiento (cambios en el hard y/o limpieza) o cortes de energia electrica.

ubuntu804server es el nombre del host que publica el recurso via NFS. Lo hice asi porque si en algun momento le cambio la IP o uso IP dinamica (via DHCP) resuelve el cambio via DNS interno o actualizando el /etc/hosts.

Si montas a mano o via script no cambia la cosa. la linea del mount deberia ser siempre lamisma (la que te funcione y sirva a los fines perseguidos).

---

### Post by sebastianabate on 2009-05-09
Qué permisos tiene el directorio /media/disco80gb? posteá la salida del comando

ls -ld /media/disco80gb

Si mal no recuerdo, NFS aplica los permisos más restrictivos entre file, directory y export; por lo que si el usuario de tu pc con ip 10.0.0.1 no tiene permisos de acceso sobre ese directorio, no va a poder escribir ni leer nada.

También tenés que tener en cuenta que NFS chequea los permisos de usuario a nivel UID, por lo que si tenés el mismo usuario creado en las dos máquinas, pero tienen distino UID, vas a tener un lindo quilombo para setear los permisos.

---

### Post by granjero on 2009-05-09
```
jm@xubuntu-jm~$ ls -ld /media/disco80gb
drwxr-xr-x 3 root root 4096 2009-04-29 01:46 /media/disco80gb/
```

lo que más me llama la atención es que si comparto un directorio cualquiera del otro disco si tengo permisos....

---

### Post by sebastianabate on 2009-05-09
Justamente el problema son los permisos, fijate que el disco que estás compartiendo tiene permisos de escritura únicamente para el usuario root, y tiene permisos de lectura y ejecución para el grupo root y para other (o sea todos los demás). Es por eso que no podés crear ningún archivo o directorio ni desde la propia máquina que tiene el disco ni desde la otra máquina cuando usás otro usuario distinto de root.

Ejecutá este comando en la máquina que tiene el disco de 80:

sudo chmod 777 /media/disco80gb

y volvé a probar crear un archivo o directorio desde la propia máquina que tiene el disco, y después desde la otra máquina, y te tiene que funcionar sin problemas. Lo que hace este comando es dar permisos de lectura, escritura y ejecución a todos los usuarios.

Si ya tenés archivos en ese disco, y querés setearle los mismos permisos a todos, podés ejecutar el mismo comando con el modificador -R así:

sudo chmod -R 777 /media/disco80gb

pero tené en cuenta que así estás cambiando los permisos a TODOS los archivos del disco, [COLOR=Red]y no hay forma de deshacer esta acción.[/COLOR]

---

### Post by granjero on 2009-05-09
un dia escribí ```
sudo chomd 777 /
```

y después foramtié...

ahora pruebo y te digo...



el disco está vacío, recién formateadito... sólo le apareció una carpeta que se llama "lost&found que imagino es normal...

garcias!

---

### Post by granjero on 2009-05-09
con chmod 777 funciona....

eso no me hace vulnerable el disco????

gracias!

---

### Post by sebastianabate on 2009-05-09
No del todo, porque al único que le pusiste permisos 777 es al directorio raíz de la partición; cuando cualquier usuario crea un archivo o directorio se setean los permisos que se quieran, pudiendo hacerlos tan seguro como uno quiera.

Por ejemplo, vos ahora tenés el directorio /media/disco80gb con permisos 777, pero si ejecutás este comando:

sudo touch /media/disco80gb/test

te va a crear un archivo "test" con los situientes permisos:

-rw-r--r-- 1 root root 0 2009-05-09 21:19 /media/disco80gb/test

Fijate que el archivo no tiene permisos 777, tiene a root como owner, a root como group y tiene permisos rw sólo para root, y r para el grupo y para others. Este archivo lo van a poder ver todos, pero sólo lo va a poder modificar o borrar root (ni siquiera lo va a poder modificar o borrar otro usuario que pertenezca al grupo root).

Si vos queres que nadie pueda ver ese archivo ejecutás:

sudo chmod 600 /media/disco80gb/test

y aún teniendo el / de la partición con 777, nadie excepto root va a poder acceder a ese archivo, porque va a quedar con permisos rw sólo para root, y ningún permiso para el grupo o para others.

---

### Post by z37a on 2009-05-10
Al igual que guillermo yo tambien lo monto via nfs, aparte te permite utilizar buffers de lectura escritura!!!

Lo que si quiero aclarar es algo que me mande y me parecio muy interesante que es el usar un DHCP en mi ubuntu server y no en el router, de esta manera le asigno ips estaticas mediante la mac address, y cuando quiero realizar un cambio en la seguridad del nfs lo hago todo desde el server y no maquina por maquina!!!

con el nfs tambien podes montar en el momento que quieras la unidad, solo deberia tener en cuenta que la carpeta que compartas debe tener los mismos privilegios que el usuario que lo va a usar, o mejor dicho tienen que ser el mismo dueño, pro ejemplo, en la desktop y el server el usaurio dueño seria "z37a"(UID=1100), lo unico recorda que SIEMPRE se le da bola al UID mas que al nombre de usuario, asi que ambos usuarios()e server y desktop) deberan tener el mismo UID!!!

---

### Post by granjero on 2009-05-11
gracias a todos por la ayuda...

una pregunta... que pasa si yo agrego en mi fstab
```
10.0.0.2:/home/jm/disco80gb /mnt/disco80gb ext3 **noauto**,sync 0 1
```

esto haría que lo monte cuando le doy click? 
y si no esta prendida la pc que comparte me dará un error y si esta prendida lo monta?


salud!

---

### Post by sebastianabate on 2009-05-11
Con la opción noauto el recurso no se monta en el arranque (ni con un "sudo mount -a"), pero queda disponible para que, cuando vos hagas un "sudo mount /mnt/disco80gb", se monte tomando todas las opciones de montaje del fstab

Pero esta opción no te deja ningún ícono en el escritorio para que vos le des doble click.

---

