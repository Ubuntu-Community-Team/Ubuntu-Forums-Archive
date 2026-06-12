---
title: "conecta el wifi pero no navega - ubuntu 12.04"
date: 2012-08-06
forum: Hardware
---

### Post by mano negra on 2012-08-06
Buenas,
   He instalado Ubuntu 12.04. Les escribo porque no puedo navegar con el wifi. Anque me reconoce todas las señales disponibles. La placa que tengo es una D-LINK DWA-525. He probado de todo lo que hay en la web, pero nada. Los controladores como los instalaba en ubuntu 10.10 no me los deja instalar. Aparece un error cuando instalo con make.
   Si alguno ya pasó por ésto y me puede dar una mano, se lo agradecería.

Saludos.
C.

---

### Post by rukiaEnix on 2012-08-06
¿Qué error te aparece con el make?

---

### Post by mano negra on 2012-08-06
> **rukiaEnix said:**
> ¿Qué error te aparece con el make?

Si, tendría que haber mostrado el error.
- Primero les muestro las últimas líneas de la compilación, que tira unas líneas de error:

/home/charles/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:1646:10: error: se especificó el campo desconocido ‘ndo_set_multicast_list’ en el inicializador
make[2]: *** [/home/charles/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/charles/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-27-generic»
make: *** [LINUX] Error 2


- Finalmente mando la instalación con "make install"
make -C /home/charles/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux -f Makefile.6 install
mkdir: no se puede crear el directorio «/etc/Wireless»: El archivo ya existe
make[1]: se ingresa al directorio «/home/charles/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux»
rm -rf /etc/Wireless/RT3060STA
#
#mkdir /etc/Wireless/RT3060STA
mkdir -p /etc/Wireless/RT3060STA
cp /home/charles/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/RT3060STA.dat /etc/Wireless/RT3060STA/.
install -d /lib/modules/3.2.0-27-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/3.2.0-27-generic/kernel/drivers/net/wireless/
install: no se puede efectuar `stat' sobre «rt3562sta.ko»: No existe el archivo o el directorio
make[1]: *** [install] Error 1
make[1]: se sale del directorio «/home/charles/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux»
make: *** [install] Error 2

Luego lo que hice (que nunca tuve problemas) fue escribir en /etc/modprobe.d/blacklist.conf: 

 blacklist rt2x00usb
 blacklist rt2x00lib
 blacklist rt2800usb

---

### Post by rukiaEnix on 2012-08-06
¿Esos controladores son los mismos que para el Ubuntu anterior?

Intenta bajando unos más actuales. Sino se puede entonces para darte otra posible solución. Pero el problema en si es este:

```

error: se especificó el campo desconocido ‘ndo_set_multicast_list’ en el inicializador

```

---

### Post by mano negra on 2012-08-06
> **rukiaEnix said:**
> ¿Esos controladores son los mismos que para el Ubuntu anterior?

Intenta bajando unos más actuales. Sino se puede entonces para darte otra posible solución. Pero el problema en si es este:

```

error: se especificó el campo desconocido ‘ndo_set_multicast_list’ en el inicializador

```

No, vengo de usar el 10.10. Lo voy a intentar y les cuento. Igualmente, repito, me reconoce las señales wifi y lo pongo como conectado y todo. LA placa está encendida (la luz que tiene se encuentra titilando). Ahora lo que no se es por que no interactúa con la red.

---

### Post by rukiaEnix on 2012-08-06
¿Entonces si logras conectarte a la red inalámbrica?

¿Puedes hacer ping al gateway?

---

### Post by mano negra on 2012-08-06
Ya me fijé. En la página de d-link siguen teniendo el mismo driver.

---

### Post by mano negra on 2012-08-06
> **rukiaEnix said:**
> ¿Entonces si logras conectarte a la red inalámbrica?

¿Puedes hacer ping al gateway?

Disculpame, no vi tu pregunta antes.
No, no puedo. Acá les pasó cuando probé con la pág. de la facultad:

charles@lesley-desktop:~$ ping [www.fi.uba.ar](www.fi.uba.ar)
ping: unknown host [www.fi.uba.ar](www.fi.uba.ar)

Te comento que en este momento estoy escribiendo desde una notbook con la misma red wifi, asi que no creo que sea un problema del router

---

### Post by rukiaEnix on 2012-08-06
¿Pero al hacer ping al gateway de tu red si responde? ¿Puedes hacer ping a otro equipo dentro de la LAN?

---

### Post by mano negra on 2012-08-06
> **rukiaEnix said:**
> ¿Pero al hacer ping al gateway de tu red si responde? ¿Puedes hacer ping a otro equipo dentro de la LAN?
  Eso ya no se cómo se hace. Lo mió era muy básico: 2 computadoras que toman señal de un router. A la de escritorio le puse una placa de red wifi y anduvo, nunca me puse a configurar nada. Solo la clave del router. Estoy al horno?

---

### Post by rukiaEnix on 2012-08-06
Sino sabes cual es la IP de tu gateway (que al parecer es la del router) ni la de otro equipo dentro de la red, no se puede apoyar mucho. Mínimo debes saber las direcciones de tu LAN...

---

### Post by mano negra on 2012-08-06
> **rukiaEnix said:**
> Sino sabes cual es la IP de tu gateway (que al parecer es la del router) ni la de otro equipo dentro de la red, no se puede apoyar mucho. Mínimo debes saber las direcciones de tu LAN...

A ver: en herramientas de red desde la notebook tengo que el ip es 127.0.0.1

---

### Post by mano negra on 2012-08-06
> **mano negra said:**
> A ver: en herramientas de red desde la notebook tengo que el ip es 127.0.0.1
en la pc con el problema me aparece el mismo ip:127.0.0.1

---

### Post by mano negra on 2012-08-06
> **mano negra said:**
> en la pc con el problema me aparece el mismo ip:127.0.0.1

Decidí instalar el controlador. Pero me es imposible compilarlo. Vi por ahí que hay que instalar "linux-headers 'uname -r'". Pero eso no me funciona, no instala nada o no se que.
Entonces fuí en busca del ndiswrapper. Instalo todo slos paquetes necesarios, bajo el controlador para wXP 64bits, busco el archivo .inf, pero al momento de instalarlo me sale un error diciendo que no encuentra la aplicación ndiswrapper. Sin embargo, en la pantalla de la aplicación gráfica del programa me aparece como que estaba el controlador instalado. 
Apago la máquina, sacó y vuelvo a colocar la placa, prendo la pc y ahora no reconoce ninguna red.
Finalmente saqué ese controlador. Si no puedo compilar no voy a poder instalar nada. 
Sino les quería preguntar que placa de red cuenta con soporte para instalar sus drivers en forma directa.
Saludos.
C.

---

### Post by guillermolisi on 2012-08-09
Lei rapidamente el hilo y decididamente no es problema de hardware ni de controladores. Es mas. ni siquiera deberia hacer falta compilar algo ni utilizar ndiswrapper.

Tengo toda la impresion que sencillamente es un problema de configuracion de la red, con direcciones IP adecuadas.

Todas las maquinas que posean una placa de red se identifican a si mismas como "localhost" en la direccion 127.0.0.1 pero esta direccion IP representa la misma maquina (es decir, la PC "habla" consigo misma a traves de esta direccion).

Coincido con que conocer/averiguar que direcciones IP se utilizan en la red es basico para sacar adelante este tema.

---

