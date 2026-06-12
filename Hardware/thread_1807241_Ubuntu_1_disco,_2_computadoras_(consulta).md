---
title: "Ubuntu: 1 disco, 2 computadoras (consulta)"
date: 2011-07-18
forum: Hardware
---

### Post by alejandrounqui on 2011-07-18
Buenas, empezé a usar Linux hace unos días, instalé todo perfectamente en una maquina con video Nvidia. Lo que me gustaría saber es si en Ubuntu 11 se puede instalar mas de un driver de video a la misma vez. ¿Por qué? porque mi máquina en realidad no tiene acceso a internet. Instale Ubuntu en un HDD que puedo sacar y llevar al trabajo donde si tengo acceso. Mi maquina tiene una placa Ati 7670. 
El sistema funciona muy bien en ambas. pero por ahora solo instalé el video de Nvidia. Cuando booteo en la máquina con Ati me dice que hay un driver para la placa disponible.

¿conviene instalarlo sin sacar el driver anterior? 

Extra: en la máquina con Nvidia ya corrí Compiz a full, pero tengo algunos pantallazos blancos, y no funcionan las consolas de F1 hasta F6, tampoco el atajo a la terminal (Ctrl+Alt+T estando ya configurado) antes de la pantalla de bienvenida se "desactiva" el video (monitor sin señal).

En la máquina con Ati, Compiz está "desactivado", calculo porque no tiene soporte 3D.

"Levanté" el sistema en un 3ra máquina con video Intel, y no pude instalar el driver. 

Estoy sorprendido de que un OS corra con tnta facilidad en hardware tan doferente (adulacion ON).

La duda concreta:
¿Se puede correr el mismo Ubuntu en varios sistemas, con todo configurado?

Desde ya agradezco cualquier ayuda, comentario o simplemente la lectura de este thread.

---

### Post by juancarlospaco on 2011-07-19
Teoricamente si, no deberia exitir conflicto entre ambas, 
si solo se deberia cargar el modulo que se necesita usar automaticamente.

---

### Post by alejandrounqui on 2011-07-22
Buenas otra vez, gracias antes que nada, el sistema operativo funciona de maravilla, es increíble, tengo solo dos inconvenientes, uno de ellos relacionado con lo anterior, el otro no tanto.

En la maquina con video nvidia había instalado el driver sin problemas y usaba compiz sin problemas salvo por algunos pantallasos blancos, cada tanto lo pasaba a metacity de última. Al conseguir instalar el driver de la placa Ati, el driver de nvidia desapareció.

¿hay forma de "renombrar" (o algo parecido) los drivers o su ubicación para que uno no "pise" al otro?


La otra consulta tal vez deba formar parte de un nuevo thread. Es acerca del driver de la intel gma x4500, consegui en internet un supuesto codigo fuente del driver

[http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.11.0.tar.gz](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.11.0.tar.gz)

pero luego de descomprimirlo al ejecutar ./configure realiza unas cuantas operaciones y luego muestra en el terminal lo siguiente:

[COLOR=Magenta]checking for XORG... configure: error: Package requirements (xorg-server >= 1.6 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/COLOR]

¿Tengo que instalar algo mas o el archivo está mal? Gracias de nuevo y suerte.

---

