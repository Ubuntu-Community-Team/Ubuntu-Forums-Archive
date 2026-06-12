---
title: "Problema -_- ATI Radeon 9200"
date: 2009-04-27
forum: Hardware
---

### Post by Cru1210 on 2009-04-27
Hola a todos, hace tiempo que se me presenta este problema, desde que me cambie al software libre, no puedo instalar el compiz, y no se si alguien podria ayudarme.
Pongo en terminal lspci y me tira esto:
[B]01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)[/B]
pruebo con:
Sistema> Administración> Controladores de Hardware y no encuentra nada.
Pruebo activando el compiz desde apariencia y nada, no puedo sacarlo de "efecto visuales: ninguno"
Si alguien puede ayudarme, se lo agradeceria muchisimo.

---

### Post by anarko on 2009-04-27
Seguramente el detector de Hard del coso es para drivers no conoce la 9200.
Baja el driver de la pagina de ati[1] e instala ese paquete.
A tener en cuenta antes de intentar instalar el driver que bajas de la pagina de ati,
abri una terminal y pone lo siguiente : 
```

sudo aptitude install build-essential linux-headers-`uname -r`

```

Con eso resolves las dependencias de compilador librerias y bla bla bla que necesita el driver de ATI para si correcta compilacion.
Todo esto para tener el driver "privatibo" de ati ( no se porque privativo yo no me privo de nada usandolo :p ), para esa placa te deberia andar sin preguntar el driver de Xorg ( Free ) eso lo podes probar instalando el paquete correspondiente :
```

aptitude install xserver-xorg-driver-radeon

```

y editando el archivo /etc/X11/xorg.conf reemplazando donde dice: Driver "XXXXX" donde XXXXX pude ser vesa ati o lo que sea,  reemplazas XXXX por radeon, quedando esa lina as : Driver     "radeon"

Espero haber sido claro, Saludos.

[1] [www.ati.com](www.ati.com)

---

### Post by pablo.s on 2009-04-27
Ver [este post]("http://ubuntuforums.org/showpost.php?p=1866190&postcount=103") que encontró una solución.

---

### Post by anarko on 2009-04-27
Ha mira vos, es bueno saberlo eso, igual si no tiene isntalado alguno de los 2 drivers fglrx ( Ati ), radeon ( xOrg ) tampoco va a poder levantar el compiz.
Esa solucion es solo para cuando tenes instalados los drivers.

Saluttes.

---

### Post by Hei Ku on 2009-04-29
Esta placa anda muy bien con los drivers libres. 

[https://wiki.ubuntu.com/RadeonDriverHowto](https://wiki.ubuntu.com/RadeonDriverHowto)

---

### Post by Cru1210 on 2009-04-29
les agradesco ..pero sepan disculpar mi estupidez...

[B]$ aptitude install xserver-xorg-driver-radeon
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
E: No se pudo abrir el fichero de bloqueo '/var/lib/dpkg/lock' - open (13 Permiso denegado)
E: Imposible bloquear el directorio de administración (/var/lib/dpkg/), ¿es superusuario?
[/B]
si alguien me puede decir de manera que alguien como yo que mucha idea no tiene.
[email]juancho_1210@hotmail.com[/email]
mi mail, para una comunicacion mas rapida.
Desde ya muchas gracias

---

### Post by josecuervo86 on 2009-04-29
pone "sudo" antes, te quedaria asi:

```
sudo aptitude install xserver-xorg-driver-radeon
```

---

