---
title: "Escaladao de frecuencia en Celeron M5XX(Acer 5310)"
date: 2008-08-21
forum: Hardware
---

### Post by z37a on 2008-08-21
Buenas gente, es la primera vez que posteo por aca, normalmente voyy de lado en lado rompiendo las bolas a ver si se solucionan mi problemas jaja, bueno no es asi, tambien ayudo a veces y espero poder ayudar!!!

Desde el principio que tuve muchos problemas con mi laptop, una Acer Aspire 5310, al principio con ubuntu 7.10 llegue a tener el problema de tener wifi o sonido!!!!(no funcaban los 2 juntos), por suerte para cuando estaba por darle a la solucion salio el 8.04 y me lo habian solucionado ahi, asi que ese ubuntu me detecto todo menos la wifi(que con madwifi funco de 10). Pero tengo un problema serio con el procesador, se trata de un Celeron M520, el mismo no me realiza el escalado de frecuencia para ahorrar corriente y bajar la temperatura, lo loco es que mi desktop tiene un chipset mas nuevo un micro mas nuevo y anda de 10 esta funcion, pero en la laptop no y esto me come cruda la bateria.

Alguna idea de que puede ser, que debo toquetear para que me baje las frecuencias automaticamente al micro?

---

### Post by niko_3100 on 2008-08-22
Tenes que instalar el paquete indicado, no se cual es pero desinstala a el paquete powernowd y en synaptics pone intel cpu a ver que sale, y anda probando. Igual te digo... yo tenia una amd y funcionaba con el escalado de frecuencias y no me gustaba para nada y no gastaba mas bateria, por ahi... 15 o 20 minutos menos me duraba pero la maquina me andaba mejor. Que placa wifi tenes? una atheros?

---

### Post by z37a on 2008-08-23
> **niko_3100 said:**
> Tenes que instalar el paquete indicado, no se cual es pero desinstala a el paquete powernowd y en synaptics pone intel cpu a ver que sale, y anda probando. Igual te digo... yo tenia una amd y funcionaba con el escalado de frecuencias y no me gustaba para nada y no gastaba mas bateria, por ahi... 15 o 20 minutos menos me duraba pero la maquina me andaba mejor. Que placa wifi tenes? una atheros?

de Wifi tiene una Atheros AR5007EG, hay un parche de madwifi para que funcione sin problemas.

Ahora con lo del escalado, lo hize eso, lo hize sin problemas, pero el problema esta que al cargar el modulo correspondiente me dice que no detecta el dispositivo("No such device"), esto me pasa con el modulo p4clockmod y speedstep-centrino, ambos me dicen que no encuentra el dispositivo, pero probe tambien con un live de fedora9 y tampoco me funciona el escalado. El problema parece estar en el driver del escalado de velocidad, el modulo no esta adaptado para el Celeron M5XX.

---

