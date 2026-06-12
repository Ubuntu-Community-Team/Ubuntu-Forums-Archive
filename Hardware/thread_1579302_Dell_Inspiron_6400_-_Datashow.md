---
title: "Dell Inspiron 6400 - Datashow"
date: 2010-09-21
forum: Hardware
---

### Post by ppellet on 2010-09-21
Estimados

Cuando uso mi laptop Dell Inspiron 6400 (que tiene instalado Ubuntu 10.04) con un DataShow la imagen proyectada se mueve, vibra rápidamente, y finalmente, no se puede ver bien. Otra cosa que pasa es que, se cambia la resolución (baja) y aunque se puede ver, más o menos bien, pasa un momento y se va a negro la pantalla, luego vuelve, pasa un tiempo, y de nuevo a negro, así se lo pasa todo el rato (así tampoco es posible trabajar).

He probado en varios datashow (3) y en todos el mismo problema. Además, hice una prueba conectando un monitor externo (un antiguo SyncMaster 753dfx de Samsung) y ocurre lo mismo.

Debo agregar que, con las versiones anteriores de ubuntu no tenía este problema y podía trabajar con los mismos datashows que ahora no puedo usar.

Otra cosa. En esta versión de Ubuntu (10.04) que uso, me indica que el sistema no esta usando controladores privativos; en cambio, con la versión anterior (9.04), me daba la opción de activarlo o no.

Esto es recomplicado para mi, porque hago clases y toda la información la he trabajado con ubuntu desde hace varios años. Entonces, tener que cambiar las cosas sólo para esto... puaj! (no me gustaría, ya no sé ni usar el w. nuevo).

pd. busqué en varios lados, pero no dan cuenta del mismo problema.

¿Alguna sugerencia...?

---

### Post by themasterdark on 2010-09-22
Que tarjeta de video posees ?

si no lo sabes, pon en un terminal lo siguiente y nos lo pegas aquí.

lspci | grep VGA

Saludos =)

---

### Post by ppellet on 2010-09-22
> **themasterdark said:**
> Que tarjeta de video posees ?

si no lo sabes, pon en un terminal lo siguiente y nos lo pegas aquí.

lspci | grep VGA

Saludos =)

Estimado themasterdark

Esto me arroja el comando indicado:

ppellet@ppellet-laptop:~$ lspci | grep VGA
**01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400**


Muchas gracias de antemano.

---

### Post by Carlos C on 2010-09-24
Hoila. Al parecer no es un problema especifico de los datashow, sino, como bien tú dices, el problema se da con cualquier salida externa, ya sea monitor o data. Buscando por ubuntuforums di con un thread en el que resuelven tu problema instalando una nueva versión del kernel:

[http://ubuntuforums.org/showthread.php?t=1468484&page=4](http://ubuntuforums.org/showthread.php?t=1468484&page=4)

Dinos si eso te resulta.

Saludos!

---

### Post by ppellet on 2010-09-25
Carlos C

Leí el post que me indicas y me dió miedo realizar las operaciones que indican, sobre todo, porque muchos tuvieron problemas posteriores con su wifi (y yo no sé arreglar problemas como estos).

Sin embargo, dentro de los muchos links a que hacen referencia, hubo uno que me pareció más simple y cuya solución me pareció que podría afrontar en caso de generarme algún nuevo problema.

Acabo de realizar los pasos que indica y me _funcionó_:
[LIST]
[*]24.09.10 - Con un monitor LCD (de esos que son TV y se pueden usar para PC). Eso sí, la resolución es más baja, pero no para generarme problemas.
[/LIST]
[LIST]
[*]27.09.10 - Acabo de probarlo con mi viejo monitor Samsung SyncMaster 753DFX y también me funcionó.
[/LIST]
[LIST]
[*]27.09.10 - Estoy trabajando con un datashow y, finalmente, he solucionado el problema. La pantalla del data no se mueve, no vibra, y hasta puedo utilizar la función de configurar dos pantallas: en uno tengo el datashow con una presentación y en la pantalla de mi laptop estoy escribiendo este mensaje.
[/LIST]

Agradecido con todos y espero que esto le sirva a alguien más.



_El link en cuestión es el siguiente_ (está en inglés):
[http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card](http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card)

_Observaciones_:
- El autor dice que aplicó esto sobre una instalación nueva de Ubuntu 10.04, pero yo he agregado muchas aplicaciones sobre el ubuntu original y también funcionó.
- El tiene una tarjeta Mobility radeon x1600, pero en el link hay varios ubunteros que lo aplicaron en otras tarjetas, entre ellas la ATI Technologies Inc Radeon Mobility X1400 que yo tengo.

_Los pasos_ que indican son los que siguen:

[LIST]
[*]Abrir un Terminal y escribir:
[/LIST]
> gksudo gedit /etc/modprobe.d/radeon-kms.conf

[LIST]
[*]Se abrirá un archivo en blanco. Escribir lo siguiente:
[/LIST]
> options radeon modeset=0

[LIST]
[*]Salvar, exit y reboot.
[/LIST]

---

