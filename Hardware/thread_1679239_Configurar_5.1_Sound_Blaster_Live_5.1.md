---
title: "Configurar 5.1 Sound Blaster Live 5.1"
date: 2011-01-31
forum: Hardware
---

### Post by anarko on 2011-01-31
Hola gente después de un par de meses de escuchar "torcido" el sonido me puse con el método de prueba y error a ver como hacer para conf. un 5.1 y que ande bien con una SB Live en 10.10. Busque por internet pero no encontré una manera "user friendly" y que no sobreescriba con archivos de dudosa procedencia los paquetes alsa.

La cosa viene masomenos asi : 
En el administrador de sonido del pulse elegir "Analog Envolvente 5.1 Output + Estereo Analogico Input" ( como se ve en la imagen adjunta ) 
En el alsa mixer dejarlo como se ve en la imagen otra adjunta ( asi se escucha bastante bien y balanceados los volumenes de los 6 parlantes ) 
Y las conexiones en la placa estan explicadas en la otra^2 imagen adjunta.

Los conectores Rosa y Azul se usan para sus funciones "originales" Mic In y Line In respectivamente. 

Posteo esto porque no encontre como dije antes ninguna manera sensilla de conf. el 5.1 en la SB Live si esto no va en esta seccion que algun admin lo mueva donde corresponde, disculpen las desproligidades. Creo que la explicacion es sesilla y facil de entender. Lo pongo mas bien como recordatorio.

Saludos

---

### Post by Pablo33 on 2011-09-12
Gracias por tu post, Tengo una tarjeta SB live! 5.1 como la que comentas y un amplificador que lleva los 6 conectores de entrada analógica. Solo un par de notas que espero sirvan de aclaración a otros usuarios.

Para los que hayan instalado el paquete "gnome-alsamixer", evidentemente han obviado el mensaje de "fuentes desconocidas y sin verificar, etc, etc". Ojo, repito, para este tipo de instalación en la que se requieren de los 6 canales analógicos, dispondrán de una interfaz en la que deben desactivar la opción "SB Live Analog/Digital Output jack" que es el correspondiente a los altavoces central y subwoofer. En caso contrario, éstos no se escucharán, pues conmuta con el modo digital. (adjunto el pantallazo)  Lo notaréis porque en algunas películas se escucha la música y no se escuchan las voces, ya que solo son enviadas por el altavoz central.

Otra inquietud que tenía, era la forma del conector nº3, (este mismo del que estoy comentando) pues la clavija "jack" no entra hasta el fondo como las otras. No pasa nada, es así, no sé porqué, pero es así, tendréis que conectar una clavija jack de 3.5mm estéreo como las otras para los altavoces frontales y traseros.

Una vez más agradecer tu post. :)

Saludos.

---

