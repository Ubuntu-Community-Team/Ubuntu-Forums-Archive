---
title: "AYUDA-vincular carpetas de windows con ubuntu"
date: 2010-07-25
forum: Instalación y Actualización
---

### Post by ruizse01 on 2010-07-25
Hola buenas...Lo que quiero hacer es vincular las carpetas predefinidas de Windows con las de Ubuntu. Ejemplo:

Users-->Docments-->Music     con /home/users/Música
Users-->Docments-->Imagenes  con /home/users/Imágenes
Users-->Docments-->Videos    con /home/users/Videos.

Así tengo el fstab:
[COLOR="RoyalBlue"]#Disco de Windws durante el inicio. 
###/dev/sdb1 /media/sergio 
/dev/sdb1 /media/sergio ntfs auto,ro,exec,users,dmask=000,fmask=111,nls=utf8 
/dev/sda1/ /media/seven ntfs auto,ro,exec,users,dmask=000,fmask=111,nls=utf8 

##/dev/sda1/Documents*and*Settings\casa\Music /home/sergio/Música ntfs auto,ro [/COLOR]

Como puedo vincular estas carpetas???.
Se puede montar directamente la carpeta Musica en Musica de Ubuntu??

Muchas Gracias

---

### Post by asterix77 on 2010-07-27
Si se puede, pero no entiendo el porqué quieres hacer eso, ya que desde ubuntu puedes perfectamente ver las carpetas de Windows a través del navegador (nautilus).

Puedes hacer acceso directos a las carpetas y dejarlas en el escritorio por ejemplo.

o puedes abrir nautilus,y arrastrar las carpetas a la columna de la izquierda y quedarán guardadas en "Lugares" para acceder directamente a ellas.

---

### Post by quixote on 2010-07-27
You probably want this so you don't have to synchronize the two sets of directories, right?

You'd set your Windows partition to mount automatically at bootup in fstab, as you have it:

/dev/sdb1 /media/sergio ntfs auto,ro,exec,users,dmask=000,fmask=111,nls=utf8 

Then you'd probably have to delete the existing Ubuntu /home/your-user/Music, /home/your-user/Pictures, and so on, because you can't turn an existing directory into a link.  (Make sure they're empty before you delete.)  Then make the links:```
ln -s /media/sergio/path-to-Docs-in-Windows/Music /home/your-user/Music
```and so on.

I'm not sure that answers your question, because my Spanish is not too great, but I hope it helps.

---

### Post by Sortega on 2010-08-02
Mira si tienes montada la partición de windows has lo siguiente (lo ideal es que se monte de forma automatica al inicio):
1. Abrir la carpeta home o cualquier otra carpeta
2. Click en Marcadores
3º Editar los Marcadores
4º Te van a salir las carpetas que tienes en el panel lateral, simplemente cambia el lugar a donde marca la carpeta que quieras cambiar y listo.

Saludos

---

