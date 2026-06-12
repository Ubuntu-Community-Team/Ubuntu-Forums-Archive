---
title: "tecla FN Sony Vaio FZ 150 FE"
date: 2009-08-26
forum: Hardware
---

### Post by cr1571an on 2009-08-26
[LEFT]Hola!, soy novato. Instale la ultima version de Ubuntu 9.04. Tengo problemas con las teclas funcion, que son para bajar y subir el brillo de la pantalla.

encontré esto en internet, pero no entiendo mucho lo que hay que hacer para que todo quede funcionando ok.

[http://ubuntuforums.org/showthread.php?t=1004568](http://ubuntuforums.org/showthread.php?t=1004568)

cSaludos, Muchas Gracias!:guitar:
[/LEFT]

---

### Post by josecuervo86 on 2009-08-27
El tutorial parece claro.  Si necesitas traducción, avisa que te ayudo

---

### Post by ADICTOALMAXIMO on 2009-08-27
debes seguir lo que dice ese tuto que por cierto esta muy bien

---

### Post by cr1571an on 2009-08-27
hola, lo que pasa es que en si nose que hago para llegar al resultado. Nose ni que checkinstall ni cvs.

tube problemas en el paso 4:

  $ cd ~/apps/nvclock/nvclock 
  $ ./configure
  $ make
  $ sudo checkinstall 
mas precisamente cuando hago el make, me aparece:
make: *** No se especificó ningún objetivo y no se encontr ó ningún makefile.  Alto.

Luego de paso, si logran ayudarme con este problema.

el paso 5 no entiendo nada, no se que hay q hacer.

Saludos!

:)

---

### Post by Hei Ku on 2009-08-27
Cual es el resultado de correr ./configure? Me parece que te dió un error ahi.

---

### Post by cr1571an on 2009-08-27
cristian@cristian-laptop:~/nvclock/nvclock$ ./configure  
 checking for gcc... gcc  
 checking for C compiler default output file name... a.out  
 checking whether the C compiler works... yes  
 checking whether we are cross compiling... no  
 checking for suffix of executables...  
 checking for suffix of object files... o  
 checking whether we are using the GNU C compiler... yes  
 checking whether gcc accepts -g... yes  
 checking for gcc option to accept ISO C89... none needed  
 checking for g++... g++  
 checking whether we are using the GNU C++ compiler... yes  
 checking whether g++ accepts -g... yes  
 checking for a BSD-compatible install... /usr/bin/install -c  
 checking whether make sets $(MAKE)... yes  
 checking how to run the C preprocessor... gcc -E  
 checking for grep that handles long lines and -e... /bin/grep  
 checking for egrep... /bin/grep -E  
 checking for ANSI C header files... yes 
 checking for library containing getopt_long... none required  
 checking for sys/types.h... yes  
 checking for sys/stat.h... yes  
 checking for stdlib.h... yes  
 checking for string.h... yes  
 checking for memory.h... yes  
 checking for strings.h... yes  
 checking for inttypes.h... yes  
 checking for stdint.h... yes  
 checking for unistd.h... yes  
 checking getopt.h usability... yes  
 checking getopt.h presence... yes  
 checking for getopt.h... yes  
 checking for pkg-config... /usr/bin/pkg-config  
 checking for gtk+-2.0 >= 2.4.0... checking for x11... configure: error: "X11 required for nvcontrol support"  
 cristian@cristian-laptop:~/nvclock/nvclock$ make  
 make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.  
 cristian@cristian-laptop:~/nvclock/nvclock$ make  
 make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.  
 cristian@cristian-laptop:~/nvclock/nvclock$ sudo checkintall  
 sudo: checkintall: command not found  
 cristian@cristian-laptop:~/nvclock/nvclock$ sudo checkinstall  
 

 checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran  
            Este software es distribuído de acuerdo a la GNU GPL  
 

 

 The package documentation directory ./doc-pak does not exist.  
 Should I create a default set of package docs?  [y]: y  
 

 Preparando la documentación del paquete...OK  
 

 Por favor escribe una descripción para el paquete.  
 Termina tu descripcion con una linea vacia o con EOF.  
 >> nvclock 0.8.4  
 >>  
 

 ***************************************** 
 **** Debian package creation selected ***  
 ***************************************** 
 

 Este paquete será creado de acuerdo a estos valores:  
 

 0 -  Maintainer: [ root@cristian-laptop ]  
 1 -  Summary: [ nvclock 0.8.4 ]  
 2 -  Name:    [ nvclock ]  
 3 -  Version: [  ]  
 4 -  Release: [ 1 ]  
 5 -  License: [ GPL ]  
 6 -  Group:   [ checkinstall ]  
 7 -  Architecture: [ i386 ]  
 8 -  Source location: [ nvclock ]  
 9 -  Alternate source location: [  ]  
 10 - Requires: [  ]  
 11 - Provides: [ nvclock ]  
 

 Introduce un número para cambiar algún dato u oprime ENTER para continuar:  
 

 Installing with make...Installing with install...  
 

 ====================== Resultados de la instalación  =====================  
 make: *** No hay ninguna regla para construir el objetivo `install'.  Alto.  
 

 **** La instalación falló. Abortando la creación del paquete.  
 

 Limpiando...OK  
 

 Adiós.

---

### Post by Hei Ku on 2009-08-27
el ./configure te dio un error. te faltan los paquetes de desarrollo.

alguien sabe cuales son los de gnome-devel?

---

### Post by pablo.s on 2009-08-27
Perdón si estoy errado,
pero hay alguna razón 
por la que tengas que 
compilar nvclock?
El paquete está para ser
instalado en el repositorio
Universe.

---

### Post by josecuervo86 on 2009-08-27
Fijate aca [0]. Supuestamente te faltan dos paquetes:

```

sudo apt-get install xorg-dev
sudo apt-get install libgtk2.0-dev
```

[0] [http://ubuntuforums.org/showthread.php?t=1099115](http://ubuntuforums.org/showthread.php?t=1099115)

---

### Post by cr1571an on 2009-08-28
estoy medio complicado, lo que me dicen para mi es chino...

---

### Post by pablo.s on 2009-08-28
Es muy facil:

En una terminal escribes:

```
sudo apt-get install nvclock smartdimmer
```

y ya estaría hecho.

---

### Post by staar on 2009-08-28
el paquete que estás tratando de compilar está disponible en los repos, no hace falta que te gastes tratando de compilarlo, abrí Synaptic, buscá el paquete nvclock e instalalo, o más fácil ```
sudo aptitude install nvclock
```

saludos

---

### Post by pablo.s on 2009-08-28
Estamos sincronizados
con Staar hoy.

---

