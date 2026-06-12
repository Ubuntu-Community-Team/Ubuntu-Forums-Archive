---
title: "necesito el driver geforce 7025 para ubuntu 9.04"
date: 2009-09-28
forum: Hardware
---

### Post by diegote06 on 2009-09-28
Hola a todos instale a ubuntu por primera ves en mi pc anda todo perfecto menos la placa de video ya que tengo una geforce 7025 onboard y el problema que tengo es que se ve en 800 x 600 y quiero una resolucion mas alta 
en un post lei que podia instalar:

sudo aptitude install nvidia-glx-180
  
el tema es que la instale y cuando quiero abrir la pantalla me da un error: 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

quise reconfigurar el servidor x pero me reconfigura el teclado me baje de la pagina de geforce un archivo 

NVIDIA-Linux-x86-185.18.36-pkg1.run

pero no se como ejecutarlo la verdad es que necesito ayuda por que el pc lo utilizo para trabajar 

desde ya muchas gracias

---

### Post by gmunioz on 2009-09-28
Hola die....:

Tienes varios procedimientos.

1- El mas sencillo: 

Pulsa Sistema - Administración - Controladores de hardware

elige el sugerido - aplicar 

Luego de un tiempo prudencial, terminada la instalacion

al reiniciar estará instalado por completo y no parcialmente

como lo has instalado.

2- Pulsa Sistema - Administración - Gestor de paquetes Synaptic

En la ventana arriba a tu derecha elige para instalar envyng-gtk

tambien se instalará envyng-core, y dkms, terminada la instalación 

en consola ejecuta envyng -t y del menu emergente elige 1, 

terminada la instalacion, al reiniciar estará instalado el driver.

Estos dos procedimientos,  gracias a dkms, con cada actualización 

del kernel te actualizará el driver.

3- Este procedimiento lo debes ejecutar en cada actualización del

kernel.

Al iniciar pulsa escape. En el menu del Grub elige recovery mode

En el submenu emergente elige netroot. Iniciaras en consola como

administrador, ejecuta entonces en el directorio (carpeta) donde

se encuentra el archivo NVIDIA-Linux-x86-185.18.36-pkg1.run

chmod +x NVIDIA-Linux-x86-185.18.36-pkg1.run

NVIDIA-Linux-x86-185.18.36-pkg1.run

Espera que termine la instalación, reinicia y estará instalado.

---

### Post by mama21mama on 2009-09-29
[Aquí ]("http://mamalibre.eshost.com.ar/?q=node/30")te dice como.

---

