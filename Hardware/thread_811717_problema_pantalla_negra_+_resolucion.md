---
title: "problema pantalla negra + resolucion"
date: 2008-05-29
forum: Hardware
---

### Post by desestructurar on 2008-05-29
Hola,
     hace ya 2 dias vengo tratando de solucionar un problema con la resolución de pantalla debido a la pantalla negra en una sesión.
Somos 2 usuarios en Ubuntu y uno de ellos cambió su resolución a una no soportada y la pantalla se volvió negra y el monitor "Flatron L1750S" muestra un mensaje de configuración no soportada.
Traté de cambiar la resolución desde diferentes comandos en la consola pero sin lograr acceder a dichos archivos de configuración.
Si alguien sabe como hacerlo o ya hay algún Post que lo explique, lo agradecería.
Sin más, saludos.

---

### Post by sajnox on 2008-05-29
apreta ctrl + alt + f1 

Con eso te vas a modo texto, te loguea y escribis
```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

Lo que haces con esto es reconfigurar nuevamente el display, salvo que hayas hecho alguna configuracion my particular desde que instalaste no deberia de hacer nada raro

Espero te sirva,

Un plan mas limpio pero menos complicado es que arranques con un live cd y edites el xorg y lo reconfigures a mano, no es tan dificil como suena.

---

