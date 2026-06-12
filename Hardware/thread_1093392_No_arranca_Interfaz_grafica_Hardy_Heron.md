---
title: "No arranca Interfaz grafica Hardy Heron"
date: 2009-03-11
forum: Hardware
---

### Post by Aristarlight on 2009-03-11
Lamentablemente decidi instalar manualmente el ultimo controlador nvidia para linux, [http://www.nvidia.com/object/linux_displ](http://www.nvidia.com/object/linux_displ)... siguiendo las instrucciones, pero no me funcionaba, entonces en un foro en ingles alguien respondio que no se podia instalar porque estaba activado gdm y xorg, asique empeze haciendo ctrl+alt+ f2 para salir de la interfaz grafica, despues seguin con sudo killall gdm, despues con sudo kill all xorg, a continuacion instale el driver asi sh NVIDIA-Linux-x86_64-180.29-pkg2.run, se abrio el instalador y le di a todo que si, aunque algunas cosas no las entendi porque estaban en ingles, igual termino la instalacion y cuando reinicie, ya no pude ver la pantalla de entrada ni nada, solo la linea de comandos, algo que me acuerdo del instalador es que dijo que nvidia tenìa que reacer un kernel o algo asi para poder continuar, yo le di a todo que si. intente hacer aparecer la interfaz grafica asi : sudo /etc/init.d/gdm start, me aparece una linea que dice gnome active o algo asi, como que si se cargo, pero sigue todo iguel, reinicio y siempre aparece la linea de comando, porfavor ayuda, no quiero tener que reinstalar todo otra vez, estuve instalando un monton de programas, juegos, etc, varios gigas, no quiero tener que formatear ni nada, bueno, muchas gracias por cualquier ayuda

---

### Post by anarko on 2009-03-11
Fijita que debes tener un archivo de nombre similar a : /var/log/Xorg.0.log
Ahi te dice que es lo que fallo al iniciar el X, son las lineas que empiezan con EE ( Error ) 

Tambien si te animas podes cambiar manualmente la conf. del X /etc/X11/xorg.conf 
Hay una linea deberia decir: Driver "nvidia"
Si dice eso es porque el driver nuevo no se instalo correctamente, lo que podes hacer es cambiar donde dice "nvidia" por "nv" y reiniciar. Y apartir de ahi usar el instalador de drivers del ubuntu. Todo eso simulando ser el usuario root.

Tip : sudo nano /etc/X11/xorg.conf
para editar desde la consola el xorg.conf

---

### Post by Aristarlight on 2009-03-11
sabes ya intente abrir nano para editar xorg.conf pero cuando entro no aparece ninguna linea de nada, esta vacio. asi que no puedo editar Driver "nvidia" por Driver "nv", porque no aparece nada. Solo la pantalla en negro.

---

### Post by Aristarlight on 2009-03-11
bueno acabo de intentar otra cosa y es restaurar el xorg sudo dpkg-reconfigure -phigh xserver-xorg pero me aparece lo siguiente: El paquete X no esta instalado y no hay ninguna informacion disponible. Utilize dpkg --info para examinar sus archivos y dpkg --contents para listar su contenido...y hasta ahi llegue. Sigo buscando como resolver el problema, ahora si me dijo que X no esta instalado que quiere decir? como puedo instalar Xorg si no esta en la maquina? por cualquier respuesta muchas gracias.

---

### Post by Aristarlight on 2009-03-11
bueno continuo con el informe de error a la hora de iniciar secion en ubuntu hardy :
 Loading, please wait...
usplash:setting mode 1152x864 failed
usplash: Using mode 1024x768
kinit: name_to_dev_t(/dev/disk/by-uuid/cea8b459-daa3-4b50-8951-a7d685a80212): s da6 (8,6)
kinit: trying to resume from /dev/disk/by-uuid/cea 8b459-daa3-4b50-8951-e7d685a80 212
kinit: no resume image, doing a normal boot
ubuntu 8.04.2 uauario-desktop tty1

  ****** no me voy a dar por vencido , no quiero instalar todo otra vez. tiene que haber alguna solucion, ojala alguien me pueda ayudar...thanks.

---

### Post by Hei Ku on 2009-03-11
eso anda todo ok.

Postea lo ultimo del archivo /var/log/Xorg.log

---

### Post by Aristarlight on 2009-03-12
mira lo ultimo del archivo less /var/log/Xorg.0.log es :
 Fatal Server Error Caught signal 11. Server Aborting.

---

### Post by Aristarlight on 2009-03-12
bueno, ya casi esta resuelto el problema, ya pude entrar a mi sesion de ubuntu con la grafica, lo que hize fue investigar un poco el error fatal del servidor 11...etc y entonces en otro foro en ingles  encontre la respuesta y es remover el conflicto que genera nvidia-glx new, asi que puse sudo apt-get --purge remove nvidia-glx new ...pero me decia que nvidia-glx no estaba instalado y que no podia encontrar el paquete new, entonces: sudo apt-get install nvidia-glx...listo, reinicie y ya puse entrar lo mas bien, pero compiz estaba deshabilitado, inicie sin ningun efecto activado, despues pense que debia hab¡litar el controlador de hardware, creo que fue otro error, porque decia  removiendo paquetes,etc, y luego reinicie, y ahora se abre una ventana antes de entrar en mi sesion que dice que se esta ejecutando una resolucion inferior 800x600...******! asi que despues pense en instalar el controlador nvidia desde enviNG, puse deteccion automatica instalar driver, lo hizo, reinicie y peor, la mitad de la pantalla no se veia, y la parte de abajo si, pero seguia en 800x600, asi que no pude hacer nada, porque encima estaba partida la pantalla, todo mal, sali con ctrl+alt+f2 y puse otra vez sudo-apt --purge remove nvidia-glx new  y otra vez decia que nvidia glx no estaba instalado, lo instale otra vez, y ahora ya se arreglo la pantalla, pero sigue en 800x600 y no puedo cambiar la resolucion, y no se que hacer, si tendria que reconfigurar xorg o tratar de borrar completamente cualquier vestigio del driver nvidia y volver a instalar o que...no se...espero solucionarlo pronto.

---

### Post by Aristarlight on 2009-03-12
ahora pude saber bien el cnflicto,  es porque aparentemente hay dos versiones distintas del driver nvidia el que me baje de la pagina oficial y es el que creo sigue instalado con todos sus componentes y el otro es el que usa ubuntu en la parte de hardware restringido, que cuando uno lo habilia borra el nvidia-glx new, pero al reiniciar mas de lo mismo, porque aparece la pantalla en 800x600 y toda la bola...lo que me gustaria hacer es remover completamente todo componente del driver bajado de la pagina oficial el driver es: NVIDIA-Linux-x86_64-180.29-pkg2.run, todo el problema por tratar de instalar ese **** driver oficial, la ****** de la lora. me gustaria borrarlo por completo, como puedo hacer, no funciona intentar borrarlo asi : sudo sh NVIDIA-Linux-x86_64-180.29-pkg2.run uninstall ( no funca) hay otra manera de purgar y hacer ****** todo vestigio de ese **** driver? pero por completo....

---

