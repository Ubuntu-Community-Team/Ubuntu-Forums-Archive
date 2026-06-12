---
title: "Auxilio para configurar video en 9.04"
date: 2009-07-05
forum: Hardware
---

### Post by varcom on 2009-07-05
Hola, gente....no soy nuevo en Ubuntu , soy super archi novatisimo.
Instale una Pc con Ubuntu 9.04 y todo funciono bien , solo que no puedo mejorar la resolución a mas de 800x600.
Por lo que estuve viendo y leyendo y haciendo, no esta cargado el driver de video (de paso: de donde lo saco?)
Entre en el xorg y no aparece ni monitor , ni nada.
Hice un lpci y ahi aparece el video, que es Via/S3 Unichrome Pro, es onboard 
en una madre Biostar Celeron 2.6 con 500 de Ram.
Preciso de su ayuda, para saber paso a paso, detalladamente como instalar el driver y configurar el video bien.

Muchas Gracias desde ya.

---

### Post by staar on 2009-07-05
mirá, lamento informarte que las placas VIA carecen de un buen driver en linux, el que provee el fabricante es muy malo, y la única alternativa pasable es usar el driver genérico VESA (que supongo es el que estás usando ahora) con el que no es posible usar aceleración 3D (no vas a poder activar los efectos de compiz), lo lamento...

pero igualmente se puede hacer algo para arreglar lo de la resolución, posteá las características de tu monitor (en especial las frecuencias de sincronización horizontal y vertical, que las encontrás en el manual), la resolución que querés usar y el contenido del archivo /etc/X11/xorg.conf

saludos

---

### Post by pablo.s on 2009-07-06
Esto me hace recordar
de un desafío adquirido
a resolver antes de Octubre.

---

### Post by guillermolisi on 2009-07-06
Que por ahora voy ganando.

Por las dudas recomiendo repasar ese thread ya que ahi se establecen las condiciones que hacen de este tema algo valido. El que avisa no es traidor :)

---

### Post by pablo.s on 2009-07-06
La verdad verdadera
es que no pude conseguir
una máquina con esa placa.
Pero tengo serias intenciones
de echarle un guante.
Faltan unos meses de todas
maneras. 
Y si, por ahora vas ganando...

---

### Post by varcom on 2009-07-07
Gracias por la respuesta, lo que me dices  es lo que he leido en general, buscando en la web.
Ya consegui mejorar la resolucion, colocando el controlador Vesa, copiando un post  que daba todas las resoluciones con monitor generico.
Muchas gracias.
Ahora lucho con el Audio, es que tirando en comando lpcia, no sale ningun controlador de audio.
La mather es una Biostar P4m80-M4 con audio realteck AC97 algo asi.
Si podes ayudarme con algo de eso te lo agradecere.
Lo importante es que pueda aprender como ver las configuraciones, asi como  en el panel de control de win.
Desde ya muchisimas gracias.

---

### Post by guillermolisi on 2009-07-07
Por favor, si el tema de video esta resuelto y tenes otras cuestiones para preguntar, abri un hilo/thread especifico con cada una.

---

