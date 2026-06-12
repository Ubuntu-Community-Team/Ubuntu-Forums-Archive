---
title: "Nuevo driver de Nvidia problema para instalarlo en 8.04"
date: 2009-02-18
forum: Hardware
---

### Post by rojojuan on 2009-02-18
Corro Ubuntu 8,04, tengo una placa XFX 7300GS y el driver privativo 177 instalado; anda todo bien.
Quise actualizar al driver 280.29 de Nvidia (trae pure video, etc) y el problema que tengo es que, cuando corre el instalador de Nvidia, trata de buscar el kernel en el sitio de Nvidia y dice que no lo encuentra. Tengo Internet habilitada. Después sigue la instalación pero falta compilar el kernel adecuado. Podría ser que Nvidia no haya desarrollado la interfase para el último kernel? Tengo instalado el último 2,6,24-23. 
Aclaro que mucho no se sobre estas instalaciones, pero seguí las instrucciones de los foros: parar las X (etc/init.d/gdm stop) y luego correr el .run bajado.
Alguna idea?

---

### Post by josecuervo86 on 2009-02-21
Probaste con envy? A pesar de que te tendria que buscar los drivers solo, esta es una buena opcion

---

### Post by rojojuan on 2009-02-22
> **josecuervo86 said:**
> Probaste con envy? A pesar de que te tendria que buscar los drivers solo, esta es una buena opcion

Sí probé, pero el Envy busca el driver viejo, el 177....Tendría que salir una actualizacion del Envy, pero de todas formas lo que hace es conectarse a Nvidia y bajar el driver; en este caso, estaríamos igual. Me parece que el problema es de Nvidia.
Gracias.

---

### Post by josecuervo86 on 2009-02-22
Encontre [esto]("http://www.nvnews.net/vbulletin/showthread.php?t=128746") en el foro de Nvidia. Segun esto, el driver seria para la version de kernel rc4. Talvez sea este el problema

---

### Post by rojojuan on 2009-02-23
> **josecuervo86 said:**
> Encontre [esto]("http://www.nvnews.net/vbulletin/showthread.php?t=128746") en el foro de Nvidia. Segun esto, el driver seria para la version de kernel rc4. Talvez sea este el problema

Parece que sí, porque no encuentra la información necesaria para el Kernel. Esperaremos a ver si se soluciona. 
En otra máquina actualicé el driver para el SO de las ventanitas y anda de maravillas; se ve mucho mejor la salida para DVD. Ojalá lo mismo pase en nuestro Ubuntu.

---

### Post by luks911 on 2009-03-03
Llegué un poquito tarde al thread pero bueh...
Lo que hace el instalador de Nvidia es darte la opción de bajar un kernel precompilado de su sitio, puede que no lo encuentre si le decís que sí. Es lo que te pasa y me ha pasado a mí. No obstante, en ese caso o si le decís que no busque un kernel precompilado sino que lo compile en el momento, la instalación debería continuar. En tu caso, ¿qué pasa cuando te dice que no la encuentra?
Asegurate de que pueda compilar instalando los paquetes necesarios para esa tarea. Antes de ejecutar el instalador, en una terminal corré

```
sudo aptitude install linux-headers-$(uname -a) build-essential
```

con eso tenés lo básico para cualquier compilación. Avisá cómo sigue.

Saludos

---

### Post by rojojuan on 2009-03-04
> **luks911 said:**
> Llegué un poquito tarde al thread pero bueh...
Lo que hace el instalador de Nvidia es darte la opción de bajar un kernel precompilado de su sitio, puede que no lo encuentre si le decís que sí. Es lo que te pasa y me ha pasado a mí. No obstante, en ese caso o si le decís que no busque un kernel precompilado sino que lo compile en el momento, la instalación debería continuar. En tu caso, ¿qué pasa cuando te dice que no la encuentra?
Asegurate de que pueda compilar instalando los paquetes necesarios para esa tarea. Antes de ejecutar el instalador, en una terminal corré

```
sudo aptitude install linux-headers-$(uname -a) build-essential
```

con eso tenés lo básico para cualquier compilación. Avisá cómo sigue.

Saludos

Gracias por responder. 
El instalador termina de ejecutarse, pero como no tiene el nuevo kernel, me quedo sin acceso a las X.
Menos mal que el instalador tiene la opción de volver atrás y lo hace bien.
Leí que ese driver estaba preparado para el kernel nuevo 2.6.27...(no funciona para los más viejos).
En cuanto a compilar es una asignatura pendiente, nunca lo hice.
Build-essential lo tengo instalado via Synaptics.
Hardy Heron -que es el que uso- actualmente tiene el Kernel 2.6.24-23. 
Como todo anda bien puedo esperar que Nvidia resuelva la cuestión o cuando cambie a una versión nueva LST.

---

### Post by luks911 on 2009-03-04
Mmmm... acá está pasando otra cosa, porque viendo el Readme del 180.29 ([http://es.download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-02.html](http://es.download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-02.html)) veo que funciona con versiones del kernel desde la 2.4.7, siempre que sean estables. 
No sé como habrás hecho para instalarlo, pero yo traté y tuve un problema similar. No recuerdo los detalles porque fue antes de encontrarme con este thread. La cuestión es que tras instalar no cargaba el driver y decía algo acerca de una incompatibilidad entre versiones del kernel. Y me llamó la atención que cuando iniciaba, al cargar DKMS, hacía referencia al driver 177 y no al 180.
Lo que había pensado hacer y no hice todavía es entrar en recovery mode, desinstalar por completo nvidia-glx-177 y nvidia-177-kernel-source, y después sí tratar de instalar el 180.


Ah, y por compilar no te preocupes, en este caso el que compila es el instalador. Sólo que tiene que tener con qué.

---

### Post by rojojuan on 2009-03-04
> **luks911 said:**
> Mmmm... acá está pasando otra cosa, porque viendo el Readme del 180.29 ([http://es.download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-02.html](http://es.download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-02.html)) veo que funciona con versiones del kernel desde la 2.4.7, siempre que sean estables. 
No sé como habrás hecho para instalarlo, pero yo traté y tuve un problema similar. No recuerdo los detalles porque fue antes de encontrarme con este thread. La cuestión es que tras instalar no cargaba el driver y decía algo acerca de una incompatibilidad entre versiones del kernel. Y me llamó la atención que cuando iniciaba, al cargar DKMS, hacía referencia al driver 177 y no al 180.
Lo que había pensado hacer y no hice todavía es entrar en recovery mode, desinstalar por completo nvidia-glx-177 y nvidia-177-kernel-source, y después sí tratar de instalar el 180.


Ah, y por compilar no te preocupes, en este caso el que compila es el instalador. Sólo que tiene que tener con qué.

Mirá esta página del foro de Nvidia. Parece que tiene muchos problemas el driver 180.29 con el kernel actual de hardy heron. Algunos pudieron instalarlo y otros no.
Que opinás?

[http://www.nvnews.net/vbulletin/showthread.php?t=123858](http://www.nvnews.net/vbulletin/showthread.php?t=123858)

---

### Post by luks911 on 2009-03-04
Ahí leí el foro de nvidia. Cuando salió bien lo que hicieron fue primero esinstalar los drivers y luego instalar el nuevo, lo que se me había ocurrido. Prometo probarlo a ver qué onda. 
En el peor de los casos, si no va, se desinstala
```

sudo sh Nvidia-Linux-180.XX.XX.run --uninstall
```

y se instala el que funca

```
sudo aptitude install nvidia-glx-177
```

Por otro lado, está en los repositorios la 180 pero es una versión previa a la 180.29. También podés probar con esa.

Qué grande la gente de Nvidia haciéndonos las cosas fáciles :-P

---

