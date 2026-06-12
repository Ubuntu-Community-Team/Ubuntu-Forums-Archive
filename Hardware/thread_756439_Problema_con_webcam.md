---
title: "Problema con webcam"
date: 2008-04-15
forum: Hardware
---

### Post by sartrejp on 2008-04-15
Hola, como les va? Escribo por lo siguiente.
Tengo una webcam minicam GE  H98657 que no logro hacer andar.

Bus 003 Device 001: ID 0000:0000  
[COLOR="Red"]Bus 002 Device 004: ID 0c45:6011 Microdia [/COLOR]
Bus 002 Device 005: ID 0458:0035 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Se que tiene un chipset microdia (aunque no se que signifique eso) y probé con todos los drivers que encontré por la web, con todos los que eran para microdia, con los de easy cam, etc. y llegué acá, donde vengo a solicitar su ayuda.
Para colmo la cámara es un regalo, sino a esta altura ya la hubiese hecho volar por la ventana.

Bueno, si alguno sabe o tiene una idea, les estaré eternamente agradecido.
Nos vemos

---

### Post by sajnox on 2008-04-15
[http://ubuntuforums.org/showthread.php?t=749943](http://ubuntuforums.org/showthread.php?t=749943)

Probablemente esto te ayude a desistir con la webcam, pero es lo que  hay

---

### Post by sartrejp on 2008-04-16
Efectivamente, ya lo había visto, lo instalé (por las dudas), pero no hubo caso.
Bue... ya veré como hago para hacerla andar, o entraré en el club del trueque (lástima que ya no esté más jejje)

Gracias, un abrazo.

---

### Post by sartrejp on 2008-05-09
Acá encontré la solución [http://ubuntuforums.org/showthread.php?p=4831129](http://ubuntuforums.org/showthread.php?p=4831129)
(por si a alguien le sirve)

---

### Post by User21 on 2008-05-09
No sabes a cuanta gente ayudas con eso! :D Podes editar el nombre del hilo como "Problema con webcam Microdia" ? 
Me tomo el tiempo de traducirlo al español! :D 

Una vez conectada la webcam al puerto usb, tipeen en terminal el comando lsusb. Entre los dispositivos enlistados, debe aparecer: 
```
Bus 001 Device 006: ID 0c45:6011 Microdia
``` (sin importar el numero de Bus o Device)
El dato que nos interesa es **0c45:6011**.  0c45 -cada fabricante tiene su propio ID en hexadecimal. 0c45 es para Microdia.
6011 - es el ID del producto. Hay muchos productos que contienen el chip Microdia. 

Para hacer funcionar la camara, es necesario compilar un modulo con un parche para gspca (gspca v1-2007 12 24). En terminal:

```
sudo apt-get install kernel-package linux-source build-essential
```Una vez instalado, descarga y extrae el parche, luego ingresa a la carpeta donde fue descargado:
```
wget http://www.cspath.com/gspcav1-20071224-0c45:6011.tar.gz
tar -zxvf gspcav1-20071224-0c45:6011.tar.gz
cd gspcav1-20071224/
```y compila el mismo:
```
make
```luego, antes de probar el modulo, haz lo siguiente:
     
      ```
sudo  modprobe fuse 
```     ```
 sudo modprobe videodev 
```     ```
 sudo modprobe compat-ioctl32 
```Luego, prueba el modulo con:
     
      ```
sudo insmod ./gspca.ko 
```Enchufa tu webcam y testeala. Mi webcam funcionó perfecto con Skype. Tambien puedes probarla con Cheese.
Si funciona bien, pues instala el modulo con:
     
      ```
sudo make install 
```Si te preguntas que hay dentro de tu cam:    
     **Bridge:** SN9C101
**Image sensor:** OV6650

Espero sea util y les funcione! Saludos!
Gracias a [Skretch]("http://ubuntuforums.org/member.php?u=493861") y a sartrejp ! :D

---

### Post by marcunix on 2009-01-23
Pues con la camara NGS spincam he probado varias cosas y nada, ahora estoyintentanto hacer este tutorial, pero no encuentro ya el archivo en [http://www.cspath.com/gspcav1-20071224-0c45:6011.tar.gz](http://www.cspath.com/gspcav1-20071224-0c45:6011.tar.gz)

He buscado en google si puedo descargarlo de otro sitio, pero no encuentro nada, si alguien aun lo guarda podria postearlo en algun sitio?

Gracias

---

### Post by sartrejp on 2009-01-23
Está acá [http://mxhaard.free.fr/download.html]("http://mxhaard.free.fr/download.html")
Igual a partir de intrepid ibex no hace falta, viene el módulo en el kernel (creo) y reconoce la webcam directamente.
Suerte

---

### Post by marcunix on 2009-01-23
Gracias, yo uso Intrepid y mi camara no la reconoce, por eso busco como solucionarlo.  Probare haber que pasa.

Gracias

Editado----------------

Pues lo he intentado y me tira estos errores.....

marcos@marcos-ubuntu:~/Escritorio$ ls
configuracion angel  gspcav1-20071224  gspcav1-20071224.tar.gz  Ubuntu
marcos@marcos-ubuntu:~/Escritorio$ cd gspcav1-20071224
marcos@marcos-ubuntu:~/Escritorio/gspcav1-20071224$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/marcos/Escritorio/gspcav1-20071224 CC=cc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/marcos/Escritorio/gspcav1-20071224/gspca_core.o
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No existe el fichero ó directorio
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c: En la función &#8216;spca5xx_ioctl&#8217;:
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c:2463: error: declaración implícita de la función &#8216;video_usercopy&#8217;
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c: En el nivel principal:
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c:2609: error: se especificó el campo desconocido &#8216;owner&#8217; en el inicializador
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c:2609: aviso: inicialización desde un tipo de puntero incompatible
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c:2611: error: se especificó el campo desconocido &#8216;type&#8217; en el inicializador
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c: En la función &#8216;spca50x_create_sysfs&#8217;:
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c:2769: error: declaración implícita de la función &#8216;video_device_create_file&#8217;
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c:2780: error: declaración implícita de la función &#8216;video_device_remove_file&#8217;
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c: En la función &#8216;spca5xx_probe&#8217;:
/home/marcos/Escritorio/gspcav1-20071224/gspca_core.c:4301: error: tipos incompatibles en la asignación
make[2]: *** [/home/marcos/Escritorio/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/marcos/Escritorio/gspcav1-20071224] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2


---------------------------------------


Yo ya no se x donde tirar para instalar la maldita cam....

---

### Post by sartrejp on 2009-01-23
Claro, pero si el módulo está en el kernell, no te va a servir ese.
¿Con que programa probaste la webcam? A mi me anda con cheese y con amsn (con los demás no). ¿El chipset es microdia? ¿que sale del comando lsusb?

---

### Post by marcunix on 2009-01-23
Hola.... esto es lo que me tira el lsusb

---------------

marcos@marcos-ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62b0 Microdia Audio (Microphone)
Bus 001 Device 002: ID 06b9:0120 Alcatel Telecom 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---------------

Yo uso Ubuntu Intrepid y Amsn, pero el cheese tampoco me la reconoce... La cam es una Ngs spincam y ya me tiene desesperadito....

---

### Post by sartrejp on 2009-01-23
Probaste este paquete? [http://debian-multimedia.org/pool/main/v/v4l2ucp/v4l2ucp_1.2-0.1_amd64.deb](http://debian-multimedia.org/pool/main/v/v4l2ucp/v4l2ucp_1.2-0.1_amd64.deb) Es para debian pero por ahí anda, sino descargando el tar.gz de [http://downloads.sourceforge.net/v4l2ucp/v4l2ucp-1.2.tar.gz?modtime=1142094286&big_mirror=0](http://downloads.sourceforge.net/v4l2ucp/v4l2ucp-1.2.tar.gz?modtime=1142094286&big_mirror=0) y compilándolo
Leí por ahí que les funcionó con una webcam similar

---

### Post by marcunix on 2009-01-24
Ese en concreto me daba error porque era la version 64 bits, me he bajado del mismo sitio la i386 y la he instalado sin problemas, pero sigue sin funcionar la camara, no se si igual tengo que hacer algo mas...

---

### Post by sartrejp on 2009-01-24
fiajte en la wiki de v4l a ver si aparece la solución, o si tiene lista de correo, porque la verdad me supera el asunto, la web [http://linuxtv.org/v4lwiki/index.php/Main_Page](http://linuxtv.org/v4lwiki/index.php/Main_Page)

Exitos

---

### Post by marcunix on 2009-01-24
Echare un vistazo haber que tal......... Gracias

---

### Post by inma on 2009-06-13
hola yo soy nueva en ubuntu, una novata vamos y tengo un asus a6000 series y tiene la camara integrada, tengo el disco partido entre windows y ubuntu y cuando instale los drivers lo hice en windows, la camara funciona pero la calidad de la imagen es mucho peor que cuando la uso en windows, alguien podria decirme por que puede ser?
gracias.

---

