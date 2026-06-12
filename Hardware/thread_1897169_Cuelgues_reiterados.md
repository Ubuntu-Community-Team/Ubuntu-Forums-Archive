---
title: "Cuelgues reiterados"
date: 2011-12-18
forum: Hardware
---

### Post by mayin70 on 2011-12-18
Hola amigos, hace poco instale ubuntu 11.10 despues de haber usado durante años todas las versiones de windows y me encuentro con dos problemas:
- reiteradamente mi pc se cuelga (cosa que con Seven no sucedia) y debo resetearla y volver a arrancar.... 
Tengo una placa asrock n61p-s, 2GB Ram, micro AMD 64 X2 5200+Mhz y aceleradora GeForce 7300 GS (sin drivers privativos)

- segun el monitor de sistema, tengo normalmente menos de un 40% de ram en uso, pero en ocasiones y muy frecuentemente llego a un 99% de espacio ocupado (con poquisimas aplicaciones en uso) y ahi se vuelve extremadamente lenta como supondran....

me podrian dar una mano?  NO QUIERO VOLVER A SEVEN..!!!! :confused:

---

### Post by BC59 on 2011-12-18
La solucion es instalar los drivers privativos. Busca drivers adicionales y instala los NVIDIA.

---

### Post by guillermolisi on 2011-12-18
Suponiendo que la causa fuera el driver de video, vendria muy bien revisar el log /var/log/xorg.0.log

Suponiendo que este utilizando Ubuntu 64 bits, vendria muy bien revisar el log /var/log/dmesg.

Adicionalmente y como apoyo, la salida del comando ```
sudo lshw
``` tambien seria de utilidad.

---

