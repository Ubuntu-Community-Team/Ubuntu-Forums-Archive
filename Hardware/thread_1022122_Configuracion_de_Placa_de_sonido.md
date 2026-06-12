---
title: "Configuracion de Placa de sonido"
date: 2008-12-26
forum: Hardware
---

### Post by NickCis on 2008-12-26
Bueno, yo acabo de hacer una instalacion minima.
Estoy Ubuntu 8.10 con Openbox, el problema es que no se como instalar y/o configurar la placa de sonido.
Por lo que tengo entendido, lo que se usa es el alsa-sound.
Instale alsa-base y alsa-utils, pero al correr alsaconf, me devuelve: "bash: alsaconf orden no encontrada". Intente, abrir el alsamixer y me dice: "alsamixer: function snd_ctl_open failed for default: no such file or directory".
Si uso el comando alsa reload, la consola me devuelve este error: "/sbin/alsa: 219: cannot create /var/run/alsa/modules-remove: Permission denied".
Y si lo ejecuto en modo root: ```
unloading alsa modules: snd-es1938 snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-op13-lib snd-hwdep snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq snd-timer snd-seq-device.
Loading Alsa sound driver modules: snd-es1938 snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-op13-lib snd-hwdep snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq snd-timer snd-seq-device.
```

Si ejecuto el comando "lspi", lo que me devuelve, relacionado a la tarjeta de sonido, es : 01:05.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 audiodrive (rev 01).

El sonido, lo estoy probando con el programa emesene (el plugin Sound esta activado) y el tuxguitar, ya que no tengo programas para reproducir musica.

Saludos.

---

### Post by luks911 on 2008-12-26
Sólo encontré esto[0]. Ahí mencionan un howto pero el link apunta a la nada. Sin embargo está la instrucción para resolver el error que tenés.

[0] [http://alsa.opensrc.org/index.php/Es1969](http://alsa.opensrc.org/index.php/Es1969)

---

### Post by NickCis on 2008-12-28
No se cual es el directorio de los drivers del alsa (alsa-drivers directory). Cual es?
Yo instale el alsa por apt-get install, no lo compile. Los unicos paquetes que instale son alsa-base y alsa-utils tengo que instalar otros mas?

Saludos.

---

### Post by luks911 on 2008-12-28
> **NickCis said:**
> No se cual es el directorio de los drivers del alsa (alsa-drivers directory). Cual es?
Yo instale el alsa por apt-get install, no lo compile. Los unicos paquetes que instale son alsa-base y alsa-utils tengo que instalar otros mas?

Saludos.

Cierto, creí que el directorio estaba en algún lado, pero no. El script snddevices está en el directorio del código fuente de alsa-drivers. Lo que se me ocurre, si querés probarlo, es que lo bajes, lo descomprimas y ejecutes el script. Pero no sé cuán seguro será.
Para compilarlo como se debe instalá los paquetes necesarios para compilar si no los tenés
```
sudo aptitude install build-essential linux-headers-$(uname -a)
```
De acá[0] bajás las fuentes. Descomprimís con
```
bzip2 -dc alsa-driver-1.0.17.tar.bz2 | tar -xv
```  
Y después
```
cd alsa-driver-1.0.17
./configure
make
sudo make install
sudo ./snddevices

```

Insisto. No sé cuán seguro es. Aunque de todos modos no tenés audio. Espero que sirva de algo.

Saludos

[0] [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2)

---

