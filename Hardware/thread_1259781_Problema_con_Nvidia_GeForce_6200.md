---
title: "Problema con Nvidia GeForce 6200"
date: 2009-09-06
forum: Hardware
---

### Post by Don King on 2009-09-06
Hola, soy medio nuevo en Ubuntu, pero hasta ahora me las habia podido arreglar viendo foros y demas.

Hace dos semanas intente instalar ubuntu, y siempre daba con errores. LLegue a la conclusion de que era algo del Hardware, y decidi hacer la prueba sacando mi placa de video (Una GeForce 6200 AGP). A los 15 minutos estaba andando en internet en Ubuntu.

Hoy decidi probar si podia ponerla ahora. Desgraciadamente no. El primer intento fallo. Trate de entrar desde el Recovery Mode y me aparecia un error diciendo "Init: pcS main process (770) killed by SEGV signal.
/bin/sh: 6: /sbin/sulogin main process(1532) terminated with status 127.

Tambien probe desde el CD de instalacion y nada. Probe en modo grafico seguro, y en el modo que pones los drivers (puse el CD con los drivers de la tarjeta). Nada.

En todos los casos es igual, aparecen los errores, y despues puedo escribir, incluso puedo poner Alt+f2, f3, f4... pero en ningun caso responde a ningun comando.

Decepcionado, saque la placa de video. Arranque ubuntu perfectamente. Busque algunos paquetes para Nvidia (sudo apt.get install nvidia-glx), pero me dice que no estan y que son reemplazados por otros.

Alguna Recomendación?

---

### Post by staar on 2009-09-06
que dicen exactamente los errores? esa placa anda bien en otro SO? sobre que motherboard la estás usando?

saludos

---

### Post by sajnox on 2009-09-09
Si tenes una placa nvidia instalada y podes arrancar en una terminal te diria que pruebes con lo siguiente

```
sudo apt-get install envyng-gtk
```

Y despues ejecutas 

```
sudo envyng -t
```

Y ahi le das para instalar el Driver que te recomiende, despues reinicias y fijate si anda

Saludos

---

### Post by gmunioz on 2009-09-09
Hola don...:

Prueba con lo siguiente:

Edita el archivo /etc/X11/xorg.conf

En una terminal (Aplicaciones - Accesorios - Terminal)

ejecutas el comando:

sudo gedit /etc/X11/xorg.conf

Busca la seccion Device y la dejas asi:

Section "Device"
	Identifier	"Default Device"
	Driver	"vesa"
EndSection

Guardas el archivo.

Cierras gedit y la consola

Pulsas: Sistema - Preferencias Pantalla

Y la configuras a 800 x 600

Aplicas.

Cierras el sistema

Colocas la tarjeta nvidia

Al reiniciar deshabilitas la tarjeta onboard

desde el setup del ordenador

Y teóricamente debería iniciar Ubuntu, con un

aspecto gráfico espantoso pero bastante legible

Luego pulsando Sistema - Administración - Controladores

de hardware, podrás aplicar los drivers adecuados

a tu tarjeta.

---

### Post by PabloGNU/LINUX on 2009-09-12
Tengo el mismo problema con Nvidia 5200. 
La unica diferencia es que ami no me salta el cartel de error directamente se tilda cargando de todos los modos posibles el SO hasta desde el CD para reintalar. 

Nos mantenemos informado si alguno lo resuelve.
saludos

---

