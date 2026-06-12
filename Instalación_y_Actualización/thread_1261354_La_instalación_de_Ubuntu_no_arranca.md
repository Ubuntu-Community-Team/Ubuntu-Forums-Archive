---
title: "La instalación de Ubuntu no arranca"
date: 2009-09-08
forum: Instalación y Actualización
---

### Post by Visente on 2009-09-08
Buenas.

Habñia decidido pasarme a ubuntu definitivamente y poner Virtualbox con XP para hacer algunas cosas que necesito de Windows, ojalá no tubiera que depender de M$.

He probado diversas veces Ubuntu con el instalador Wibu, y funcionaba perfectamente. Ahora he quemado un ISO de la última versión de Ubuntu y he intentado instalarla. El dico arranca y me pregunta qué quiero hacer; elijo istalar Ubuntu. Hasta ahí todo bien, pero empieza a cargar (Pantalla negra con el texto: "Loading, please wait...") y no pasa de ahí. Reinicio el equipo a la fuerza y compruebo que el disco no tenga errores.

Ahora vuelvo a probar, pero con las opciones de F6 activadas. Algo avanzamos, porque aparece el logo de ubuntu y la barra de carga. De nuevo vuelve a fallar: una vez carga del todo, la pantalla se vuelve negra y no dice nada más.

Tengo dos pantallas y en una dice "Imput not suported", la otra está negra, simplemente, y con la luz parpadeando.

Tengo 1GB de ram, unos 350GB de disco duro y un procesador Intel de doble núcleo.

Ahora mismo escribo con un portátil Ubuntu con la mitad de recursos... me parece un poco extraño que no funcione en este ordenador.

Por cierto, he descargado las dos últimas versiones de Ubuntu (8.10 y 8.04) y pasa lo mismo. También con Fedora y OpenSUSE (Después del GRUB se para y no carga la instalación respectivamente)

¿Aguien tiene idea de lo que pasa?
Agradecería vuestra ayuda, gracias.

---

### Post by AlexDDR on 2009-09-08
Hola, tienes que entregar más datos sobre tu  equipo, marca modelo , componentes de hardware, asi te podremos ayudar mejor

saludos

---

### Post by Visente on 2009-09-09
Pues a ver:

En cuanto a la marca: es un Medion sobremesa. No sé cuál es el modelo y no hay ninguna referencia en la torre.

El procesador es un Intel Core 2 a 2.13GHz
Tenog 1 GB de RAM
La gráfica es una NVIDIA GeForce 7650 GS

El OS principal es Windows Vista... por si sirve de algo.

No sé qué datos más pueden importar...

---

### Post by gmunioz on 2009-09-09
Hola vis....:

Mi sugerencia es que descargues la version

alternate de Jaunty amd 64

[http://cl.releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-amd64.iso](http://cl.releases.ubuntu.com/jaunty/ubuntu-9.04-alternate-amd64.iso)

La grabes con la opción grabar imagen a solo 24 X

E instales con este cd.

---

### Post by Visente on 2009-09-09
He probado con el alternate para la versión x32 y... ¡Ha funcionado! Ahora mismo escribo desde Ubuntu Jaunty.

Tengo algunos problemas con la gráfica, pero supongo que se solucionarán fácilmente con los drivers.

Gracias por la ayuda.

---

### Post by AlexDDR on 2009-09-09
te recomiendo que instales la version 185.xx que es mas avanzada que la que trae jaunty y que mas facil que desde repositorios


[http://ubuntulife.wordpress.com/2009/08/26/instalar-drivers-nvidia-190-desde-repositorios/](http://ubuntulife.wordpress.com/2009/08/26/instalar-drivers-nvidia-190-desde-repositorios/)

---

### Post by nopersona on 2009-09-10
Qué buena que lo solucionaste. Usa los drivers que te dice ALEXDDR, con esa nvidia el sistema te va a andar como seda.

---

### Post by colindo on 2009-09-22
hola ,,a mi tambien me aparece despues de instalar el ubuntu 9.04 desde cd -alternate x86   una pantalla negra con la ventanita:  out of range ,,les mando los datos de mi pc:Placa de video:	Intel 82945GZ Graphics Controller 0 [A-2]  Nombre código de la GPU: Lakeport-G        Aceleradora 3D   =                            Tipo de CPU	DualCore Intel Pentium E2140, 1600 MHz (8 x 200)         1,5 gb de RAM *******************************************************************    Intel GMA 950 =	Placa de video y Aceleradora 3D ,,,,,,por favor ayudenme .hace como 6 meses que no puedo ver mas que la barra anaranjada de ubuntu y luego la pantalla negra .Ni con el ubuntu 8.04  y el 8.10 ,,en este momento tengo en las particiones el ubuntu 9.04 desde un cd-alternate.  contestenme ¿que tengo que hacer?

---

### Post by Carlos C on 2009-09-22
> **colindo said:**
> hola ,,a mi tambien me aparece despues de instalar el ubuntu 9.04 desde cd -alternate x86   una pantalla negra con la ventanita:  out of range ,,les mando los datos de mi pc:Placa de video:    Intel 82945GZ Graphics Controller 0 [A-2]  Nombre código de la GPU: Lakeport-G        Aceleradora 3D   =                            Tipo de CPU    DualCore Intel Pentium E2140, 1600 MHz (8 x 200)         1,5 gb de RAM *******************************************************************    Intel GMA 950 =    Placa de video y Aceleradora 3D ,,,,,,por favor ayudenme .hace como 6 meses que no puedo ver mas que la barra anaranjada de ubuntu y luego la pantalla negra .Ni con el ubuntu 8.04  y el 8.10 ,,en este momento tengo en las particiones el ubuntu 9.04 desde un cd-alternate.  contestenme ¿que tengo que hacer?

Por favor evita publicar la misma pregunta más de una vez. Lo hiciste 4 veces, así que borré las otras. Antes de volver a postear recuerda leer las normas:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Saludos.

---

### Post by sesharrim on 2011-02-26
Hola, me parece que tengo el mismo problema

he descargado el ubuntu desktop 10.10, 9.04, 8.04 , ubuntu notebook 10.10 , ubuntu server 10.10 [i386] y ninguna me ha funcionado.

mi OS es windows 7
Intel(R) Pentium(R) Dual CPU E2180 @ 2.00 GHz 2.00 GHz
Memoria Ram 3.00 GB (2.49 Utilizable)
Tipo de Sistema: Sistema operativo de 64 bits(estaba 100% seguro de que era 32)

creen que el problema se revuelva si me descargo la version AMD 64 bits?

Gracias por su tiempo

Buen foro

---

