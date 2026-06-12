---
title: "Problemas instalando awn-extras"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by mmannuell on 2009-03-30
Hola

Recientemente estaba instalando awn-extras-applets. Después de poner en la consola el comando "./configure", puse "make". Sin embargo me salió el siguiente error:

make  all-recursive
make[1]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6'
Making all in src
make[2]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src'
Making all in libawn-extras
make[3]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras'
Making all in .
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras'
make[4]: No se hace nada para `all-am'.
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras'
Making all in bindings
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings'
Making all in python
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings/python'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings/python'
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings'
make[5]: No se hace nada para `all-am'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings'
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings'
make[3]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras'
Making all in affinity
make[3]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity'
Making all in affinity-preferences
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/affinity-preferences'
make[4]: No se hace nada para `all'.
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/affinity-preferences'
Making all in data
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data'
Making all in actions
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/actions'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/actions'
Making all in 16x16
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/16x16'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/16x16'
Making all in 22x22
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/22x22'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/22x22'
Making all in 24x24
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/24x24'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/24x24'
Making all in 48x48
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/48x48'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/48x48'
Making all in scalable
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/scalable'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/scalable'
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data'
make[5]: No se hace nada para `all-am'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data'
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data'
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity'
make[4]: *** No hay ninguna regla para construir el objetivo `applet.lo', necesario para `affinity.la'.  Alto.
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity'
make[3]: *** [all-recursive] Error 1
make[3]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6'
make: *** [all] Error 2
manuel@dell-desktop:~/Software/awn-extras-applets-0.2.6$ make
make  all-recursive
make[1]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6'
Making all in src
make[2]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src'
Making all in libawn-extras
make[3]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras'
Making all in .
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras'
make[4]: No se hace nada para `all-am'.
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras'
Making all in bindings
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings'
Making all in python
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings/python'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings/python'
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings'
make[5]: No se hace nada para `all-am'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings'
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras/bindings'
make[3]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/libawn-extras'
Making all in affinity
make[3]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity'
Making all in affinity-preferences
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/affinity-preferences'
make[4]: No se hace nada para `all'.
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/affinity-preferences'
Making all in data
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data'
Making all in actions
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/actions'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/actions'
Making all in 16x16
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/16x16'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/16x16'
Making all in 22x22
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/22x22'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/22x22'
Making all in 24x24
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/24x24'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/24x24'
Making all in 48x48
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/48x48'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/48x48'
Making all in scalable
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/scalable'
make[5]: No se hace nada para `all'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data/scalable'
make[5]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data'
make[5]: No se hace nada para `all-am'.
make[5]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data'
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity/data'
make[4]: se ingresa al directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity'
make[4]: *** No hay ninguna regla para construir el objetivo `applet.lo', necesario para `affinity.la'.  Alto.
make[4]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity'
make[3]: *** [all-recursive] Error 1
make[3]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src/affinity'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/manuel/Software/awn-extras-applets-0.2.6'
make: *** [all] Error 2


¿Qué puedo hacer?

---

### Post by sharkbaitbobby2 on 2009-04-08
Hola,

me parece que estás usando awn-extras-applets 0.2.6. Recomendamos usar 0.3.2.1. Sin embargo, necesitas awn 0.3.2 para awn-extras-applets 0.3.2.1. Puedes obtenerlos en [https://launchpad.net/awn/+download](https://launchpad.net/awn/+download) y [https://launchpad.net/awn-extras/+download](https://launchpad.net/awn-extras/+download). Pero, si estás usando Ubuntu, debes usar [https://launchpad.net/~awn-core/+archive/ppa](https://launchpad.net/~awn-core/+archive/ppa) en vez.

(Lo siento si mi español es mal; estoy apendiendo. :)

---

