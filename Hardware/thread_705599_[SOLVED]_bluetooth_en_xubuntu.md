---
title: "[SOLVED] bluetooth en xubuntu"
date: 2008-02-23
forum: Hardware
---

### Post by andy_91 on 2008-02-23
bueno tengo un problema con el bluetooth 

lo que pasa es que instalo el kbluetooth y no puedo recibir archivos solo enviar

instalo el bluetooth de gnome y puedo recibir pero no enviar

y si instalo ambos el kbluetooth no funciona


alguien me da una mano con esto?


desde ya gracias

---

### Post by User21 on 2008-02-25
Para enviar y recibir archivos via Bluetooth en Xubuntu 7.10

Instala los siguientes paquetes desde Synaptic o via apt-get !

bluetooth
bluez-utils
libbluetooth2
gnome-bluetooth
libgnomebt0
libopenobex1

Debe aparecer un icono de  "Bluetooth File Sharing" en la seccion de Accesorios en la seccion Sistema.

Podes crear un icono onda ENVIAR A para el Bluetooth en Thunar usando las instrucciones que se detallan en:
[http://thunar.xfce.org/pwiki/documentation/sendto_menu](http://thunar.xfce.org/pwiki/documentation/sendto_menu)

SUERTE CON ESO! Decinos si te funcionó! 

                                                               __________________

---

### Post by User21 on 2008-02-25
Script "Enviar a Bluetooth" para Thunar (gnome-obex-send) 
 
 Esto le permitirá enviar archivos de su PC a su teléfono (o de otro dispositivo Bluetooth usando OBEX push). 
 
Guardar el siguiente script en un archivo llamado "gnome-obex-send-generic.desktop" en ~ / .local / share / Thunar / sendto / (crear el directorio si no existe ya): 
 ```
[Desktop Entry]
Type=Application
Version=1.0
Encoding=UTF-8
Name=Bluetooth OBEX Recipient
Icon=internet-mail
Exec=/usr/bin/gnome-obex-send %f
``` Esto le permite seleccionar de una lista de posibles receptores de Bluetooth. 
 
Si ya tiene un dispositivo fijo al cual desea enviar y quiere evitar tener que seleccionarlo cada vez, puede hacer lo siguiente. En primer lugar, es necesario averiguar el destinatario del dispositivo Bluetooth: su dirección mediante *hcitool*. Luego personalizar el fichero mediante la inserción de la dirección Bluetooth donde dice INSERTAR DIRECCION BLUETOOTH : 
 ```
[Desktop Entry]
Type=Application
Version=1.0
Encoding=UTF-8
Name=My Bluetooth Device
Icon=internet-mail
Exec=/usr/bin/gnome-obex-send -d INSERTAR DIRECCION BLUETOOTH %f
```

Espero te sea de utilidad! :)

---

### Post by andy_91 on 2008-02-25
gracias ya esta!!!!!!!!!!!!!!!!!!!!

salio bien me habia faltado poner Thunar con mayuscula

---

### Post by picharras on 2008-08-10
Que tal.

Bien pues he hecho todo lo que citan anteriormente al pie de la letra, pero no puedo enviar de la computadora al telefono celular en Xubuntu 8.04.

Si me envian algun archivo desde el telefono lo recibo sin problemas, pero no  puedo enviar y el **gnome-obex-send** no aparece por ningun lado como si no lo tuviera instalado, el **gnome-obex-server** si lo tengo. Supuestamente estos dos se encuentran en el paquete gnome-bluetooth y lo tengo instalado. Lo mismo me pasaba en Xubuntu 7.10. Les vuelvo a comentar he hecho todo al pie de la letra, paso por paso.

¿Alguien me puede decir como instalar el gnome-obex-send?:confused:

Desde ya gracias por su ayuda.

---

### Post by santiagoward2000 on 2008-10-16
Hola gente!
Revivo este thread porque tengo una duda, y ya que estoy quiero agregar algo.
Primero, a partir de Hardy no hay más **gnome-obex-send**, por lo que ahora hay que poner:
```
Exec=bluetooth-sendto %F
```
Puede que ahí haya estado el problema del post de arriba (más vale tarde que nunca :)).
Ahora mi duda: ¿cómo hago para **bajar** algo de mi cel a la compu? Si voy desde el cel a la foto (por ejemplo) que quiero bajar, le mando enviar via Bluetooth y selecciono mi compu, el celu dice: > Servicio no soportado ¿Alguien me ayuda? GRACIAS

_EDIT:_
UPS! Me faltaba instalar **bluetooth** y **gnome-bluetooth**.
Ya está! :)
Gracias User21!

---

