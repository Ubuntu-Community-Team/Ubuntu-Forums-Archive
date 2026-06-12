---
title: "Ubuntu no reconoce nueva unidad de DVD"
date: 2009-12-06
forum: Hardware
---

### Post by jose_rojas on 2009-12-06
Hola!
Hace algunos días compré una unidad de DVD (LG)para grabar mis películas favoritas :D
cambie los puertos del grabador de CD que tenia por el nuevo reproductor y grabador de DVD.
Al entrar a Windows reconoció inmediatamente la unidad e instaló los drivers a través del disco que venia con el producto.
En cambio cuando entré a Ubuntu, se paró y salieron muchas letras. Luego se arregló esto pero Ubuntu no reconoce la existencia de ningún dispositivo nuevo, existe una unidad de cdrom0, pero al ingresar un disco con el DVD sale el mensaje:
[FONT=Courier New]
mount: el dispositivo especial /dev/cdrom0 no existe[/FONT]

Busqué por ahi soluciones, pero ninguna satisface a mi problema. Creo que Ubuntu ni siquiera reconoce que existe una unidad. No sé que hacer para hacer que lo reconozca, hasta modifiqué muchas veces el fstab, pero si ni siquiera sabe que existe, entonces, para que servirá modificar el fstab :/
Eso, no quiero reinstalar ubuntu. Quién me ayuda?

Saludos!
José

---

### Post by moreback on 2009-12-06
No tienes por qué andar modificando el **/etc/fstab** para hacer que aparezca tu grabador, el sistema lo reconoce sólo. Un **dmesg** debiera informarte qué dispositivos reconoció el kernel, por ahí debiera aparecer un /dev/sr0 o algo similar:
```

[    1.182995] scsi 3:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
[    1.194417] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.194421] Uniform CD-ROM driver Revision: 3.20
[    1.194540] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.194607] sr 3:0:0:0: Attached scsi generic sg1 type 5

```

Yo en mi /etc/fstab sólo tengo las particiones importantes del sistema, como 7, /home y la swap.

¿Qué versión de Ubuntu? ¿modelo de tu grabador?

---

### Post by Carlos C on 2009-12-06
Verifica que no tega que ver con esto:

[http://blockdeubuntu.blogspot.com/2009/02/regionset-error-could-not-open-disc.html](http://blockdeubuntu.blogspot.com/2009/02/regionset-error-could-not-open-disc.html)

---

### Post by jose_rojas on 2009-12-20
> **moreback said:**
> No tienes por qué andar modificando el **/etc/fstab** para hacer que aparezca tu grabador, el sistema lo reconoce sólo. Un **dmesg** debiera informarte qué dispositivos reconoció el kernel, por ahí debiera aparecer un /dev/sr0 o algo similar:
```

[    1.182995] scsi 3:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
[    1.194417] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.194421] Uniform CD-ROM driver Revision: 3.20
[    1.194540] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.194607] sr 3:0:0:0: Attached scsi generic sg1 type 5

```Yo en mi /etc/fstab sólo tengo las particiones importantes del sistema, como 7, /home y la swap.

¿Qué versión de Ubuntu? ¿modelo de tu grabador?

Gracias por responder. 
Hice un **dmesg** y Arroja muchas lineas, pero en ninguna una referida a la unidad de grabación. 
instalé la última versiónd e Ubuntu (antes de cambiar el grabador de CD a DVD, la 9.10 y el grabador es un LG.

Con respecto a la sugerencia de más abajo, realicé lo pedido en el link y nada. Los más extraño, es que para UBUNTU la unidad no existe, es decir, por lo que pones, el kernel no reconoce la unidad de DVD o CD

---

### Post by CdK1 on 2009-12-20
Que te tira esto:

dmesg | grep DVD

---

