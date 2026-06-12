---
title: "activar aceleración gráfica intel 945GM en ubuntu 9.10"
date: 2010-02-22
forum: Instalación y Actualización
---

### Post by 3nG3ndR0 on 2010-02-22
hola, instale ubuntu 9.10 en un notebook y no tiene aceleración gráfica, tiene vga intel.

hay muchas soluciones para 9.04 pero hay que modificar el xorg.inf, pero no hay en ubuntu 9.10

```
jorge@jorge-laptop:~$   lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
```

---

### Post by Carlos C on 2010-02-22
En [este enlace]("http://kaeltas.blogspot.com/2009/05/como-solucionar-problemas-de.html") te recomiendan añadir el siguiente PPA:

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Por supuesto las instrucciones del primer enlace son para Jaunty, pero en karmic sería tan fácil como usar el comando:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
```Luego habría que ver si la configuración de la sección Devices señalada funciona. Lamentablemente no tengo esa tarjeta, así que no puedo comprobarlo, sin embargo, nada de lo anterior es irreversible.

Saludos.

---

### Post by erickelrojas on 2010-03-19
No sé si es porque al descargar o al grabar el cd de ubuntu suele instalar mal el sistema.  Yo tengo un portátil Toshiba, Portage M400 al que le he agregado RAM, he cambiado el disco duro y el grabador de dvds con piezas genéricas
...quizá por esto si el cd no esta en perfecto estado a vecez al instalar el sistema he tenido problemas con que no me reconoce la gráfica o el sonido.  El instalar Karmic, Kubuntu, Xubuntu y Ubuntu netbook remix a sido a veces una odisea, pero si pruebas a volver a instalar una o dos veces suele instalarse bien. Porqué? Porque la versión del X.org si soporta esa tarjeta, sobre todo porque es Intel y el driver es libre.  Si no te reconoce la tarjeta prueba a activar todos los repositorios y hacer una actualización completa y al reiniciar verás como puedes tener aceleración gráfica para compiz.

Si necesitas ayuda en algo preguntame en mi página web [http://www.elleonplateadodeojosrojos.es](http://www.elleonplateadodeojosrojos.es)

---

### Post by CdK1 on 2010-03-21
Asegúrate que tengas el módulo cargado:

Caturra:/# lsmod | grep 915
i915                  217023  2 
drm_kms_helper         17183  1 i915
drm                   107507  3 i915,drm_kms_helper
i2c_algo_bit            3497  1 i915
i2c_core               12612  4 i2c_i801,i915,drm,i2c_algo_bit
button                  3598  1 i915
video                  14605  1 i915
Caturra:/#

Caturra:/# dpkg -l | grep intel
ii  libdrm-intel1                        2.4.18-3                                               Userspace interface to intel-specific kernel
ii  xserver-xorg-video-intel             2:2.9.1-2                                              X.Org X server -- Intel i8xx, i9xx display d
Caturra:/#

Luego:

sudo dpkg-reconfigure -phigh xserver-xorg

Y reinicias X...

---

### Post by 3nG3ndR0 on 2010-04-21
solucionado una instalación en limpio y me reconoció el driver de vídeo enseguida.

---

