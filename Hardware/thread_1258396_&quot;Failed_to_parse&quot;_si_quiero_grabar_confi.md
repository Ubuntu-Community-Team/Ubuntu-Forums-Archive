---
title: "&quot;Failed to parse&quot; si quiero grabar configuración de pantalla"
date: 2009-09-04
forum: Hardware
---

### Post by GerryEastwood on 2009-09-04
Hola. Tengo una nVidia y si quiero cambiar las preferencias de pantalla me manda al panel de control de nVidia. La cosa es que cambio la configuración pero cuando la quiero grabar me da el siguiente error:

```
Failed to parse existing X config file '/etc/X11/xorg.conf'!
```

¿Cómo puedo hacer?

Gracias.

---

### Post by pablo.s on 2009-09-05
Querés cambiar la resolución?

---

### Post by josecuervo86 on 2009-09-05
```
sudo nvidia-settings
```
Y desde ahi modificas los parametros ;)

---

### Post by GerryEastwood on 2009-09-05
Gracias.

Sí, me pone por defecto 1024 x 768 y yo quiero más definición, me permite cambiarla pero no me la graba.

---

### Post by GerryEastwood on 2009-09-05
No funcionó.
```
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".
```
:confused:

---

### Post by pablo.s on 2009-09-05
Fijate si [seguir estos pasos]("http://ubuntuforums.org/showpost.php?p=7667829&postcount=25")
te sirve. Está en ingles pero
creo que vas a entenderlo.

---

### Post by staar on 2009-09-05
después de instalar los drivers, tenés que correr el ```
sudo nvidia-xconfig
``` que recomienda, porque sino te pasa esto...

ese comando te modifica el /etc/X11/xorg.conf para que nvidia-settings pueda leerlo y modificarlo...

saludos

---

### Post by GerryEastwood on 2009-09-07
¡Andó! :lolflag:

Grazie tante \\:D/

No necesité reinstalar los drivers. Hice ésto:
```
sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup
sudo nvidia-xconfig
sudo nvidia-settings
``` 

Y después reinicié y todo bien.

Una pregunta de vago (si hay que buscar, busco, pero ya que estamos... ¿dónde encuentro un manual/listado de los comandos sudo?

Gracias.

---

### Post by pablo.s on 2009-09-07
> **GerryEastwood said:**
> 

Una pregunta de vago (si hay que buscar, busco, pero ya que estamos... ¿dónde encuentro un manual/listado de los comandos sudo?

Gracias.

El comando sudo da privilegios
de administrador a un usuario
común. Para que ese usuario
común pueda invocar sudo tiene
que estar en el archivo denominado
"sudoers".
Por lo tanto es un complemento y
no una serie de comandos. Se
utiliza para hacer configuración del
sistema sin tener que crear la cuenta
root, lo cual acrecienta la seguridad
del sistema.

---

