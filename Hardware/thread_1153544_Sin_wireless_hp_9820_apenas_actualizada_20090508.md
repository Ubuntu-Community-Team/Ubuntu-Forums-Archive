---
title: "Sin wireless hp 9820 apenas actualizada 2009/05/08"
date: 2009-05-08
forum: Hardware
---

### Post by pedregal on 2009-05-08
Hola! Resulta que hice un upgrade parcial de mi instalación del 9.04 y dejó de funcionar el wifi, hasta ahora había funcionado correctamente, incluso cuando pasé de la 8.10 a la 9.04, cuando clickeo en el ícono no aparecen las opciones de las redes (el ícono de la señal si se levanta) y cuando voy a configuración de redes me permite editarlas, pero no conecta. Un  detalle es que figura en la conexión que uso los minutos primero y ahora las horas desde la última vez que estuvo conectado. Alguna idea? gracias!

---

### Post by pedregal on 2009-05-12
Hola! Logré encontrar la solución "corriendo para adelante", en este sitio: [http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#wireless](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#wireless)

Ejecuté: 
sudo aptitude install linux-backports-modules-jaunty

sin blacklist y al reboot anduvo. 
Gracias y saludos!

---

