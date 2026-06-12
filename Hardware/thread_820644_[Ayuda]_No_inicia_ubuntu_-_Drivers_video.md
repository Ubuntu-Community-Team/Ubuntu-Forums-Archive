---
title: "[Ayuda] No inicia ubuntu - Drivers video"
date: 2008-06-06
forum: Hardware
---

### Post by delmicio on 2008-06-06
Soy nuevo en Ubuntu y nuevo en Linux pero aprendo rápido. ;)

El tema fue asi:

Después de instalar Ubuntu 8.04 - Hardy Heron - en *Sistema > Administración >  Controladores de Hardware* habilite los driver de mi placa de video, que es una ATI Radeon HD 2400 pro, y tba de lujo, funcionaban todos los efectos de escritorio de 10, pero no había probado con juegos, así que instale un juego (Secret Mayoro Chronicles) y cuando entro se me titilaba la pantalla y era molesto para jugar: Entonces fue a la web de Ati para buscar mis drivers ([http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)) seleccione *Linux x86 > Radeon > HD 2400* los descargue y los instale con la consola. Reinicie y paff! ](*,) no iniciaba linux, a que me refiero con esto, enciende la pc y me da para elegir el sistema operativo y elijo ubuntu y de ahí no pasa nada queda la pantalla negra. entonces pienso :-k y esto ya me había sucedido.

ahora estoy en Ubuntu pero sin los drivers habilitados. ¿Como lo hice?:?:  Entro al otro ubuntuenla lista de sistemas operativos (no es otro kernel es una opcion como de pruebas o arreglar) toque y proceso y reinicie y entro pero ahora habilito de nuevo los drivers y me pasa lo mismo.

probé desinstalando del Gestor de paquetes Synaptic 2 cosas que decian Ati y crei que podian ser los que descargue pero nada.

Me pueden ayuda? es que me encantó Ubuntu, me encanta ser LIBRE :guitar:
y ahora no se com solucionar esto.

Gracias.

---

### Post by anarko on 2008-06-06
Te fijastes si tienen una opcion --uninstall los drivers de la pagina de ati?
En el archivo que bajaste de la pagina de ati, abri una consola y poner ./ati-driver-bla.superbla --help y te da todas las opciones

Sino tenes la opcion "anarko" que es ir a /lib/modules/{version de kernel} y borrar el fglrx.ko apartir de ahi muere el driver de ati. Despues volvelo a habilitar desde la opcion de controladores restringidos.

No vas a conseguir mejor performance con los de la pagina, son la misma basofia.

---

### Post by ariel on 2008-06-06
> **delmicio said:**
> Soy nuevo en Ubuntu y nuevo en Linux pero aprendo rápido. ;)

El tema fue asi:

Después de instalar Ubuntu 8.04 - Hardy Heron - en *Sistema > Administración >  Controladores de Hardware* habilite los driver de mi placa de video, que es una ATI Radeon HD 2400 pro, y tba de lujo, funcionaban todos los efectos de escritorio de 10, pero no había probado con juegos, así que instale un juego (Secret Mayoro Chronicles) y cuando entro se me titilaba la pantalla y era molesto para jugar: Entonces fue a la web de Ati para buscar mis drivers ([http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)) seleccione *Linux x86 > Radeon > HD 2400* los descargue y los instale con la consola. Reinicie y paff! ](*,) no iniciaba linux, a que me refiero con esto, enciende la pc y me da para elegir el sistema operativo y elijo ubuntu y de ahí no pasa nada queda la pantalla negra. entonces pienso :-k y esto ya me había sucedido.

ahora estoy en Ubuntu pero sin los drivers habilitados. ¿Como lo hice?:?:  Entro al otro ubuntuenla lista de sistemas operativos (no es otro kernel es una opcion como de pruebas o arreglar) toque y proceso y reinicie y entro pero ahora habilito de nuevo los drivers y me pasa lo mismo.

probé desinstalando del Gestor de paquetes Synaptic 2 cosas que decian Ati y crei que podian ser los que descargue pero nada.

Me pueden ayuda? es que me encantó Ubuntu, me encanta ser LIBRE :guitar:
y ahora no se com solucionar esto.

Gracias.

te sugiero:

Hace un backup de xorg.conf, por las dudas
```
cp /etc/X11/xorg.conf ~/xorg.conf.backup
```

Ctrl-Alt-F1 (consola)
loggeate y hace:
```
sudo dpkg-reconfigure xserver-xorg
```

Y segui las instrucciones. Vas a poder elegir el driver, te va a ofrecer por default el driver opensource que funciona.

por ultimo

```
sudo reboot
```

---

### Post by delmicio on 2008-06-07
Gracias por responder pero no me funcionó. he decidido reinstalar ubuntu.

Yo tengo una home aparte en otra particion y ahora quiero instalar ubuntu 64bit me va a funcionar esa home?

---

