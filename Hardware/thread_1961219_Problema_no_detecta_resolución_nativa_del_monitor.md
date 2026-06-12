---
title: "Problema: no detecta resolución nativa del monitor"
date: 2012-04-18
forum: Hardware
---

### Post by kidonaipe on 2012-04-18
Buenas gente, espero que este sea el lugar indicado para realizar este tipo de consultas, la cosa es así:

Tengo un monitor LCD Samsung SyncMaster 2233Plus de 21.5', conectado a una placa de video ATI Radeon 5670 Sapphire por medio de un adaptador DVI a VGA (Ya que el monitor solo posee una entrada VGA y la placa de video solo salida DVI y HDMI) por lo tanto fue la única manera factible de conectarlo.

En Windows tuve un par de q********s por el mismo tema, no me reconocía la resolucion nativa del Monitor, hasta que despues de 500 mil intentos anduvo.

Probando en Ubuntu (fresh install o live), tanto en versiones como 10.10, 11.10, 12.04 no me reconoce el monitor y mucho menos las resoluciones nativas de éste.

Buscando por foros, taringa, etc. encontré una manera de hacerlo andar mediante tres comandos del xrandr.
Helos aqui:
[LIST]
[*]xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync 
[*]xrandr --addmode VGA1 1920x1080_60.00 
[*]xrandr --output VGA1 --mode 1920x1080_60.00
[/LIST]

Al realizar eso con los drivers libres ( los que vienen x default al instalar ubuntu o al ejecutarlo desde el live cd ) el tema se arreglo, y la resolución quedo seteada correctamente ( a la fuerza ).

Ahora bien, contento de la vida, decidí instalar los drivers propietarios de la web de ATI/AMD que poseen aceleración 3D ya que la necesito para diversas cuestiones.
Luego de realizar la instalación, mi resolucion full hd desapareció, el monitor sigue siendo detectado como "Desconocido" y me aparecen diversas resoluciones (la mas alta 1600x1200) pero no son las nativas del monitor, y la 1920x1080 no aparece.

Alguien me podrá dar una mano? quiero tener mi resolución al mango con el driver que posee aceleración 3D.

PD: también pobre agregando el modeline a mano en xorg.conf pero no pasa nada. A lo máximo que he llegado es a reiniciar y que la pantalla no pendria, y se queda en negro el monitor con la luz del encendido parpadeando.

Si no quedó muy claro me avisan que contesto a la brevedad, y desde ya muchisimas gracias por leer

EDITO: me olvidaba, el driver libre reconoce a mi monitor como DVI-0(ya que esta conectado x dvi mediante el adaptador), sin embargo al instalar el driver privativo lo reconoce como un monitor CRT.

---

