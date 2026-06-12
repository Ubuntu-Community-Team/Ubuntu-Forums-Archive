---
title: "Ayuda con problema de Video (Tarjeta Nvidia)"
date: 2013-04-26
forum: Instalación y Actualización
---

### Post by Kminari on 2013-04-26
Buenas, mi nuevo problema viene siendo que soy novato en lo que se refiere a Linux, instale Ubuntu 12.10 y tengo problemas con el video (supongo que por mi misera tarjeta NVIDIA Vanta/Vanta LT), mi pantalla esta casi dividida en dos y los textos esta inclinados (algo muy raro), como no puedo sacar captura de pantalla saque una foto con mi movil: [http://www.subirimagenes.cl/?di=4I4P](http://www.subirimagenes.cl/?di=4I4P)
Mas detalles: el fondo de pantalla se divide en dos, se ve la mitad izquierda (y se deforma) y la derecha esta en negro.
Las ventanas también se dividen en dos, lo que corresponde a la ventana completa se ve solo en la izquierda dificultando el hacer click en las opciones.
Los textos de los menus desplegrables se inclinan (solo visualmente, ya que para seleccionarlos el mouse se debe desplazar verticalmente).

Creo que el problema viene de la tarjeta gráfica, pero no se que archivo debo descargar para ejecutarlo desde un pendrive, ya que buscarlo desde ubuntu me es imposible (no logro guiarme con el ese lio visual y no se hacer todo con solo el teclado).

[SIZE=1]Problema anterior sin respuestas -.- : > Hola, soy nuevo en el foro y en Linux, tengo 3 PC's a mi cargo; uno de escritorio y 2 notebooks, todos con muy distintos recursos, por ello me gustaría pedir sus consejos respecto a que debo instalar en cada uno de ellos (Ubuntu, Kubuntu, Lubuntu, etc. Y que versión).
El pc de escritorio: Intel Pentium D CPU 2.80GHz, 1GB RAM, NVIDIA Vanta/Vanta LT
Notebook algo viejito: Intel Core Duo CPU T2350, 1.86GHz, 1GB RAM, mOBILE iNTEL 945GM Express Chipset Family
Y mi notebook: Pentium Dual-Core CPU T4400, 2.20GHz, 3GB RAM, NVIDIA GeForce 310M

Había descargado Ubuntu 12.10 pero no creo que corra bien en el notebook viejo y en el PC de escritorio, así que apreciaría muchísimo su ayuda en este tema.
Si este tema no va aquí me disculpo y pido que me indiquen las sección correcta (Ojala en español xD), cualquier link a tutorial o pagina para informarme mas del tema es bienvenido.[/SIZE]

---

### Post by Kminari on 2013-05-21
Ampliando la información: los problemas visuales solo empiezan después de iniciar sesión, ya sea como invitado o como admin.
Realmente no se que ocasiona el problema ni como arreglarlo, por favor, denme alguna idea de que puedo hacer.
---
Tengo otra duda, si me da por formatear las partes donde se instalo Ubuntu (lo hare si no arreglo el problema) iniciara normalmente con Win XP? (en el grub aparece primero ubuntu y despues win).
---
Logre sacar unas cap desde ubuntu pero no me las lee desde win y soy tan noob que no he podido encontrar la terminal para usar los comandos para actualizar soft. de nvidia -.-

---

### Post by Kminari on 2013-05-27
Logre pasar las capturas a windows, aqui les dejo los enlaces para q vean lo q tengo q sufrir, si no logro saber por q pasa esto tendre q formatear y eliminar ubuntu (sin siquiera lograr usarlo).
[http://www.subirimagenes.cl/upload/images/4C8F.png](http://www.subirimagenes.cl/upload/images/4C8F.png)
[http://www.subirimagenes.cl/upload/images/J6OM.png](http://www.subirimagenes.cl/upload/images/J6OM.png)
[http://www.subirimagenes.cl/upload/images/WA0O.png](http://www.subirimagenes.cl/upload/images/WA0O.png)
[http://www.subirimagenes.cl/upload/images/TAZZ.png](http://www.subirimagenes.cl/upload/images/TAZZ.png)
[http://www.subirimagenes.cl/upload/images/D68W.png](http://www.subirimagenes.cl/upload/images/D68W.png)

Ni siquiera he podido personalizarlo por q se ve así -.-
Por favor, alguien que me ayude.

---

### Post by asterix77 on 2013-05-27
Bastante antigua tu tarjeta, veamos si se puede hacer algo, no te prometo nada ya que no soy experto en ello pero veamos.

Una vez que instalastes ubuntu ¿instalastes algún driver gráfico?. ¿haz buscado "controladores adicionales" desde el dash?.

Para saber correctamente el modelo o chip en realidad, de tu tarjeta, escribe el resultado de la terminal del siguiente comando.

#sudo lspci | grep VGA.

Por otra parte, en el siguiente link [http://www.nvidia.com/object/linux_display_ia32_71.86.13.html](http://www.nvidia.com/object/linux_display_ia32_71.86.13.html)

se detalla el último driver para ese modelo de tarjeta por parte de nvidia, es el driver de 32 bit que me imagino que es tu arquitectura. Le das a download, aceptas el acuerdo y se descarga.

Una vez descargado, abres una terminal, te diriges hacia donde tienes el archivo descargado, escribes en la terminal para darle permiso de ejecución.

$chmod +x archivo.run

Seguido escribes en la terminal sh archivo.run

con lo anterior se instala el driver, y luego reinicias. Debiera funcionar...


Saludos

---

### Post by asterix77 on 2013-05-27
Acá encontré otro link donde se detalla la forma de instalar los driver.

[http://dmolinap.blogspot.com/2010/05/3d-con-nvidia-en-ubuntu-lucid-lynx.html](http://dmolinap.blogspot.com/2010/05/3d-con-nvidia-en-ubuntu-lucid-lynx.html)

Primero intenta desde la terminal instalar el paquete desde la terminal, en tu caso 

sudo apt-get install nvidia-glx-71

Y luego también desde la terminal

sudo nvidia-xconfig

y luego reinicias

---

