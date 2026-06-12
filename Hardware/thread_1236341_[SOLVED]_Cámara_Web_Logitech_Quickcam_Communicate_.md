---
title: "[SOLVED] Cámara Web Logitech Quickcam Communicate STX"
date: 2009-08-10
forum: Hardware
---

### Post by jpoeta on 2009-08-10
Amigos del Loco Team Argentina,
tengo problemas con esta camara al tratar de usarla en Skype, se vuelve verde distorciona y termina cerrando el Skype. Con el Cheese no muestra problema alguno, alguien tiene idea que puede estar pasando.

Saludos su Amigo

Jpoeta:popcorn:

Cámara Web Logitech Quickcam Communicate STX

---

### Post by milovan1971 on 2009-08-12
A mi me pasa lo mismo con una Creative webcam... funciona en Cheese, y en Skype aparece todo negro con rayitas verdes nomas. Parece ser un problema de Skype.

---

### Post by jpoeta on 2009-08-13
Hoy solucioné todos los problemas con mi cámara en Ubuntu
aquí les explico paso a paso cómo si es que ha alguien le sirve

Primero abrimos la terminal he introducimos lo siguiente:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Luego:

sudo apt-get remove skype
sudo apt-get install skype

Asi se acabaron is problemas de Video con Skype

Pero todavía tenía el molestoso problema audio 
aqí la solución

En terminal

    cd

    rm -rf .Skype/

En skype en las configuraciones de sonido elige los siguientes dispositivos :

    Sound in: XXXXX(hw:XXXX, 0)

    Sound out: pulse

    Ringing: pulse

En el archivo de configuración de pulse-audio /etc/pulse/daemon.conf agregamos las siguientes lineas al final:

high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5

resample-method = src-sinc-best-quality

Guardamos el archivo y listo

Tenemos nuestro skype :) finalmente perfecto

Jpoeta:guitar::popcorn::lolflag:

---

