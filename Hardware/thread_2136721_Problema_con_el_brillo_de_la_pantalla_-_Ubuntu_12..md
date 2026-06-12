---
title: "Problema con el brillo de la pantalla - Ubuntu 12.04 LTS - Samsung NC110P"
date: 2013-04-18
forum: Hardware
---

### Post by mapa1988 on 2013-04-18
Hola a todos,

Mi nombre es Sebastián y estoy recorriendo mis primeros pasos en el mundo Ubuntu. Tengo una netbook ***Samsung NC110P*** corriendo Windows 7.

Particioné el disco para instalar la versión de ***Ubuntu 12.04 LTS*** y la instalación se terminó satisfactoriamente.

Hasta allí todo bien, pero cuando se reinició el equipo e inicié el SO, el brillo de la pantalla, que durante la instalación funcionó perfectamente, quedó seteado al mínimo.

Intenté varias formas de solucionarlo, instalé el xbacklight, el samsung-tools y el samsung-backlight pero no hay forma de modificar el brillo de la pantalla.

No es que las teclas Fn+Fxx no funcionan, de hecho, si presiono para subir o bajar el brillo, reconoce la indicación pero nada cambia en la pantalla.

Intenté también modificando  el rc.local, agregando la línea "echo 7 > /sys/class/backlight/acpi_video0/brightness".
Modifiqué el "grub" según encontré en un post en el foro pero tampoco funcionó.

La verdad es que todas las alternativas que encuentro por internet son similares a estas y con mis conocimientos, nulos, no se me ocurre que más probar.

Aclaro que todo parece funcionar correctamente, solamente no logro modificar el brillo de la pantalla de ninguna forma.

Gracias de antemano por su tiempo.

Saludos!

---

### Post by rojojuan on 2013-04-20
> **mapa1988 said:**
> Hola a todos,

Mi nombre es Sebastián y estoy recorriendo mis primeros pasos en el mundo Ubuntu. Tengo una netbook ***Samsung NC110P*** corriendo Windows 7.

Particioné el disco para instalar la versión de ***Ubuntu 12.04 LTS*** y la instalación se terminó satisfactoriamente.

Hasta allí todo bien, pero cuando se reinició el equipo e inicié el SO, el brillo de la pantalla, que durante la instalación funcionó perfectamente, quedó seteado al mínimo.

Intenté varias formas de solucionarlo, instalé el xbacklight, el samsung-tools y el samsung-backlight pero no hay forma de modificar el brillo de la pantalla.

No es que las teclas Fn+Fxx no funcionan, de hecho, si presiono para subir o bajar el brillo, reconoce la indicación pero nada cambia en la pantalla.

Intenté también modificando  el rc.local, agregando la línea "echo 7 > /sys/class/backlight/acpi_video0/brightness".
Modifiqué el "grub" según encontré en un post en el foro pero tampoco funcionó.

La verdad es que todas las alternativas que encuentro por internet son similares a estas y con mis conocimientos, nulos, no se me ocurre que más probar.

Aclaro que todo parece funcionar correctamente, solamente no logro modificar el brillo de la pantalla de ninguna forma.

Gracias de antemano por su tiempo.

Saludos!

La ayuda de Ubuntu indica:

Establecer el brillo de la pantalla
Puede cambiar el brillo de la pantalla para ahorrar energía o para hacer la pantalla más fácil de leer con luz brillante. También puede hacer que la pantalla se apague automáticamente cuando use la energía de la batería y que la apague automáticamente cuando no esté en uso.
Establecer el brillo
Pulse en el icono situado en el extremo derecho de la barra de menús y seleccione Configuración del sistema.
Seleccione Brillo y bloqueo.
Mueva el deslizador de Brillo para obtener un valor confortable.
Muchos teclados de portátiles incluyen teclas especiales para ajustar el brillo. Esas teclas tienen un símbolo que representa a un sol y se ubican por lo general en las teclas de función. Mantenga presionada la tecla Fn para usar estas teclas especiales.
Seleccione Reducir el brillo de fondo para hacer que el brillo se reduzca automáticamente cuando esté usando la batería. La luz de fondo de su pantalla puede consumir mucha energía y reducir significativamente el tiempo que durará la batería hasta que tenga que volver a cargarla.
La pantalla se apagará automáticamente después de que no la utilice durante unos minutos. Este apagado únicamente afecta a la pantalla y no implica que se apague el equipo. Puede ajustar el tiempo que debe permanecer inactivo el equipo utilizando la opción Apagar pantalla si está inactiva durante.

Probá para ver si te sirve

---

### Post by jankiev on 2013-05-14
Tengo el mismo problema con mi Netbook, ayer instale el Ubuntu 12.04 y experimenté lo mismo... Buscando por internet me encontré con una solución temporal el cual se tendría que ejecutar un comando por terminal. El comando es:

sudo setpci -s 00:02.0 F4.B=99

Bueno después del igual puedes poner entre 1 y 99 el brillo de la pantalla, pero es un fastidio estar haciendolo cada ves que queremos aumentar o disminuir el brillo.

Seguiré buscando a ver si encuentro algo útil para que las tecla de Fn funcione correctamente.

---

### Post by rojojuan on 2013-05-20
Hoy leí esto, fíjense si sirve.
Dejo el enlace:

[http://www.espaciolinux.com/foros/documentacion/como-controlar-brillo-inicio-ubuntu-t51471.html](http://www.espaciolinux.com/foros/documentacion/como-controlar-brillo-inicio-ubuntu-t51471.html)

---

