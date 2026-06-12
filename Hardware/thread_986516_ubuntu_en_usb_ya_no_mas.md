---
title: "ubuntu en usb ya no mas"
date: 2008-11-18
forum: Hardware
---

### Post by tsueseres on 2008-11-18
ya no puedo poner ubuntu en una usb lo he intentado del modo manual con ubuntu 8.04 y del modo automatico con intrepid ibex pero no bootea la usb

---

### Post by sajnox on 2008-11-18
Disculpame pero no termino de entender tu problema

No podes bootear una pc con un pen drive o no podes cargar el sistema en un pendrive

---

### Post by tsueseres on 2008-11-18
> **sajnox said:**
> Disculpame pero no termino de entender tu problema

No podes bootear una pc con un pen drive o no podes cargar el sistema en un pendrive

es que antes ya habia podido instalar ubuntu en un pendrive pero ahora ya no he podido lograrlo y he seguidolos mismos pasos (manualmente) y tmb con intrepid ibex 

(cargar linux mediante el pendrive)

---

### Post by c4d0rn4 on 2008-11-18
no te hagas más drama, buscá bien en intrepid que hay una herramienta para hacer ubuntu usb bootable.

te pondría una guia para hacerlo booteable, pero tengo entendido que esa herramienta puede inclusive hacer un linux booteable con la distro que tenés customizada. En pocas palabras, un pen drive con ubuntu, codecs, programas preferidos y actualizados.

Yo lo hice con remastersys, pero tengo entendido que en intrepid hicieron esa herramienta que te va a solucionar todo.

---

### Post by sajnox on 2008-11-18
Para hacer que el pendrive sea booteable, en intrepid tenes un creador de pendrives booteables

Sistema > Administracion > Create a USB Startup disk

Recorda que para que esto funcione es necesario que setees en el bios para que el arranque lo haga desde el pendrive, sino, no sirve de mucho

---

### Post by tsueseres on 2008-11-18
> **sajnox said:**
> Para hacer que el pendrive sea booteable, en intrepid tenes un creador de pendrives booteables

Sistema > Administracion > Create a USB Startup disk

Recorda que para que esto funcione es necesario que setees en el bios para que el arranque lo haga desde el pendrive, sino, no sirve de mucho

si ya lo intente con esa opcion (del intrepid ibex) pero no me la ace booteable, no se si ayan cambiado los archivos que descarga en la pagina de ubuntu y aiga algun bug

---

### Post by c4d0rn4 on 2008-11-18
debe tener mal el mbr el usb

si ya tenes lilo slatea esto
```
sudo apt-get install lilo
```

después, fijate cual es tu usb en 
```
sudo fdisk -l
```

y por último
```
lilo -M /dev/sdX
```
x es el que te diga fdisk que es tu usb

---

