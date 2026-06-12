---
title: "Instalando Creative Zen X-Fi"
date: 2009-05-11
forum: Hardware
---

### Post by cor_stellae on 2009-05-11
Hola gente:

Encontré este fabuloso [tutorial]("http://www.forosuse.org/forosuse/archive/index.php/t-10100.html") para tratar de que Ubuntu reconozca mi Creative Zen X-Fi, el problema es que sigo siendo novata y me quedo pegada en un paso.

Logro hacer que la consola haga todo lo que debe hacer, lo que no logro es añadir la línea que ahí se sugiere modificada para que reconozca mi Zen. Deduzco que ese es un archivo que debe abrirse de alguna manera, en un editor adecuado. ¿Alguien puede decirme cómo abrirlo para poderlo modificar? :confused:

Un millón de gracias.

---

### Post by staar on 2009-05-12
primero que nada, esa guia en muy vieja (no es necesario que compiles, ni amarok, ni gnomad2, con solo instalar este último desde synaptic, ya está bien) encontrás una más actualizada [http://www.mossroot.com/worlds/2008/11/22/connecting-the-creative-zen-x-fi-to-linux/]("http://www.mossroot.com/worlds/2008/11/22/connecting-the-creative-zen-x-fi-to-linux/") (en inglés)

básicamente, es esto:

1- instalar las librerías necesarias: ```
sudo aptitude install libmtp7 mtp-tools
```

2- editar el archivo /etc/udev/rules.d/45-libmtp7.rules ```
sudo gedit /etc/udev/rules.d/45-libmtp7.rules
``` (sudo para obtener permisos de root, gedit es el nombre del editor de textos, el resto es la ubicación del archivo) este archivo tiene dos secciones, en la primera, llamada LABEL=&#8221;libmtp_usb_rules, agregar esto:```

# Creative Zen X-fi
ATTR{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```
en la segunda sección, llamada LABEL=&#8221;lib_usb_device_rules&#8221;, agregar esto otro:```

# Creative Zen X-fi
ATTRS{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```

las dos líneas son casi idénticas, pero difieren en que la primera dice ATTR, y la otra ATTRS.

3- después, editar el archivo /etc/udev/rules.d/45-libnjb.rules ```
sudo gedit /etc/udev/rules.d/45-libnjb.rules
``` y agregar:```

# Creative Zen X-fi
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4162", GROUP="plugdev", MODE="0660"
```

4- reiniciar

5- conectar el mp3, abrir gnomad2, y transferir!

notas: podés usar cualquier programa que soporte mtp para transferir, no sólo gnomad2, amarok (un excelente reproductor de audio) también soporta el protocolo, banshee (otro) también, el reproductor de audio de ubuntu rhythmbox también (hay que activarle un complemento), etc.
hay dos números que se repiten en todas esas líneas que tenés que agregar, 041e y 4162, son los id del fabricante y del producto, respectivamente, asegurate previamente de que esos números son los que corresponden a TU dispositivo, corriendo un ```
lsusb
``` y fijándote, en la línea del dispositivo, luego de las letras 'ID', si los números separados por un ':' son los mismos que los que usaste, 041e y 4162, sino suplantá ambos números, en las 3 líneas que tenés que agregar por los que correspondan a tu dispositivo...

saludos

---

