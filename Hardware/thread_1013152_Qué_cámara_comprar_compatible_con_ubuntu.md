---
title: "Qué cámara comprar compatible con ubuntu?"
date: 2008-12-16
forum: Hardware
---

### Post by El Potro on 2008-12-16
Buenas, qué tal?

Estoy usando ubuntu en mi compu y necesito comprar una webcam de 2mpx genérica. Algún consejo? Alguien tiene una experiencia reciente?

No quiero usar windows, o sea, la idea es que sea 100% compatible con ubuntu 8.04 o 8.10.

Podrían orientarme? No quiero meter la pata!

Muchas gracias,

Mauricio

---

### Post by luks911 on 2008-12-16
La verdad es que no tengo mucha idea. Pero te paso un par de links que encuentro ahora medio a las apuradas:
[http://ubuntuforums.org/showthread.php?t=466870](http://ubuntuforums.org/showthread.php?t=466870)
[http://www.ubuntuhcl.org/browse/search+webcams?category=33](http://www.ubuntuhcl.org/browse/search+webcams?category=33)

Una conclusión apuradísima es que las Creative parecen ser una buena opción.

Seguro alguien pueda dar su experiencia. Saludos

---

### Post by El Potro on 2008-12-17
Gracias por colaborar lucks911, estuve viendo las páginas que pasaste.

Espero que algún usuario de ubuntu que se comunique por webcam y viva en Arg. "se cope" y postee su opinión, experiencia o testimonio, a ver cuál nos conviene comprar.

Yo busco alguna de 1.3 o preferentemente 2 megapíxels. De mayor definición creo q son mucho más caras, pero habría que ver.

Hay alguien?

---

### Post by fedeavila on 2008-12-17
Yo uso una marca Genius (común, sin megapixeles) con AMSN y me funciona perfectamente bien, mi prima usa una Genius también que es más avanzada pero no te podría especificar de cuantos megapixeles es... Redondeando, si es webcam no creo que tengas problemas con la marca Genius, son las más conociditas (a mi entender) y Ubuntu las debería "sentir" sin problemas.

Yo me voy a comprar [esta]("http://articulo.mercadolibre.com.ar/MLA-45539043-webcam-genius-messenger-310-notebook-lcd-pc-microfono-gtia-_JM"), a ese usuario no, pero ese es el modelo y me voy a arriesgar; si anda bien y sino mala leche... Para mi seguro anda, lo que no, quizás, el micrófono que viene incluído....

Saluditos

---

### Post by sajnox on 2008-12-17
Fedeavila,

Si queres esa webcam para usarla con Ubuntu te comento que por ahora no es tan facil hacerla andar.

Con Hardy no la reconocia y con Intrepid la reconoce, pero no por eso anda. Hay que darle un par de vueltas y la haces andar.

Si me queda claro que si no la hacen andar ahora en Intrepid para Jaunty seguramente ande.

---

### Post by andy_91 on 2008-12-17
para cuando la microdia, jaja

me habían pasado un tutorial, pero no entendí como se hace y tuve que desistir de mi webcam

---

### Post by luks911 on 2008-12-17
> **andy_91 said:**
> para cuando la microdia, jaja

me habían pasado un tutorial, pero no entendí como se hace y tuve que desistir de mi webcam

Para microdia hay un driver en desarrollo que podrías probar. Esta es la página del driver: [http://groups.google.com/group/microdia/?pli=1](http://groups.google.com/group/microdia/?pli=1) y esta otra es en la que se explcia la instalación: [http://groups.google.com/group/microdia/web/using-git-with-microdia](http://groups.google.com/group/microdia/web/using-git-with-microdia)

Pasado en limpio, para la instalación tendrías que seguir estos pasos:

1 ) Intalar lo necesario para la compilación y obtención del driver
```
sudo aptitude install cogito git-core linux-headers-$(uname -r) kernel-package build-essential libv4l
```

2 ) Bajar el código fuente (va a quedar en tu /home en una carpeta llamada microdia)
```
git clone http://repo.or.cz/r/microdia.git
```

3 ) Compilar el driver
```
cd microdia
make 
```

4 ) Cargar el módulo
```
sudo insmod ./microdia.ko
```

5 ) Para instalar el módulo y no tener que cargarlo en cada reinicio
```
sudo strip -g microdia.ko
sudo mkdir -p /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
sudo cp microdia.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
sudo depmod -a 
```

En la página hay un par de errores comunes. Y cualquier cosa preguntá. Aclaro que no lo llevé a la práctica, es probable que pueda dar una mano.

Saludos

---

### Post by andy_91 on 2008-12-17
a gracias por la traduccion, es que ni traducida al español es muy clara para mi voy a hacer la prueva y luego les digo

---

### Post by fedeavila on 2008-12-17
> **sajnox said:**
> Fedeavila,

Si queres esa webcam para usarla con Ubuntu te comento que por ahora no es tan facil hacerla andar.

Con Hardy no la reconocia y con Intrepid la reconoce, pero no por eso anda. Hay que darle un par de vueltas y la haces andar.

Si me queda claro que si no la hacen andar ahora en Intrepid para Jaunty seguramente ande.

uhhh! en serio?? ya intentaron con conectarla al puerto usb?

---

### Post by andy_91 on 2008-12-17
> no se encuentran libv4l cogito
***********************************************************************************************
andy@andy-desktop:~/microdia$ make
make -C /lib/modules/2.6.24-22-generic/build SUBDIRS=/home/andy/microdia modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /home/andy/microdia/microdia-usb.o
  CC [M]  /home/andy/microdia/microdia-v4l.o
  CC [M]  /home/andy/microdia/microdia-sysfs.o
  CC [M]  /home/andy/microdia/microdia-dev.o
  CC [M]  /home/andy/microdia/microdia-queue.o
  CC [M]  /home/andy/microdia/sn9c20x.o
  CC [M]  /home/andy/microdia/omnivision.o
  CC [M]  /home/andy/microdia/micron.o
  CC [M]  /home/andy/microdia/microdia-debugfs.o
  LD [M]  /home/andy/microdia/microdia.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/andy/microdia/microdia.mod.o
  LD [M]  /home/andy/microdia/microdia.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-22-generic'
make: ctags: No se encontró el programa
make: *** [ctags] Error 127

****************************************************************************************************
andy@andy-desktop:~/microdia$ sudo insmod ./microdia.ko
insmod: error inserting './microdia.ko': -1 Unknown symbol in module
*****************************************************************************************************

esos son los errores que me dio

---

### Post by luks911 on 2008-12-17
> **andy_91 said:**
> esos son los errores que me dio

Aparentemente el problema es que el módulo no queda donde debe. ¿Por qué? No tengo la menor idea. Dicen [acá]("http://doc.ubuntu-es.org/Instalar_c%C3%A1maras_Microdia")[0] que debería arreglarse con los pasos para la instalación del módulo que te decía antes, o sea.

1 )
```
strip -g microdia.ko
```

2 ) Copiar el módulo al directorio de módulos del núcleo
```
sudo cp microdia.ko /lib/modules/$(uname -r)/kernel/drivers/media/video/usbvideo/

```

3 ) Reconstruir las dependencias entre módulos
```
sudo depmod -a
```

4 ) Cargarlo con modprobe
```
sudo modprobe microdia
```

A ver qué pasa con eso.

[0] [http://doc.ubuntu-es.org/Instalar_c%C3%A1maras_Microdia](http://doc.ubuntu-es.org/Instalar_c%C3%A1maras_Microdia)

---

### Post by andy_91 on 2008-12-18
no todo salio igual que como decia la web y cheese no me la detecta.

el modelo exacto es 0c45:612a Microdia

---

### Post by El Potro on 2008-12-18
Parece que este thread al menos vino bien para aclarar dudas de usuarios. Lo que yo me pregunto es: ¿Habrá alguna cárama que no presente estos eventuales problemas de reconocimiento y de drivers?

Da la impresión de que es mucho pedir! Yo sólo quiero una webcam de 1.3 o 2 mpx (porque comprar una vga ya es un poco un atraso) que sea 100% compatible con Ubuntu y que pueda comprarla en suelo argentino.

Nadie tiene idea?

---

### Post by luks911 on 2008-12-18
> **andy_91 said:**
> no todo salio igual que como decia la web y cheese no me la detecta.

el modelo exacto es 0c45:612a Microdia

Viendo un poco más en la página que te pasé, resulta que justo ese modelo no lo soporta el driver. 
Buscando más encontré esto [http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=239&forum=3](http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=239&forum=3) que dice que funcionaría instalando el módulo gspca.sn9c110. Y acá ([http://blog.doutdex.com/2007/05/13/como-agregar-camara-web-webcam-a-ubuntu/](http://blog.doutdex.com/2007/05/13/como-agregar-camara-web-webcam-a-ubuntu/)) instrucciones para instalar gspca que pueden usarse para el módulo. Si querés probarlo.....

> **El Potro said:**
> Parece que este thread al menos vino bien para aclarar dudas de usuarios. Lo que yo me pregunto es: ¿Habrá alguna cárama que no presente estos eventuales problemas de reconocimiento y de drivers?

Da la impresión de que es mucho pedir! Yo sólo quiero una webcam de 1.3 o 2 mpx (porque comprar una vga ya es un poco un atraso) que sea 100% compatible con Ubuntu y que pueda comprarla en suelo argentino.

Nadie tiene idea?

Acá ([https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)) hay un listado de marcas que se desglosa en modelos. Capaz que no son muchos pero, busque una Genius en Mercadolibre y la encontré. Así que te puedde servir de guía.

Saludos :lolflag:

---

