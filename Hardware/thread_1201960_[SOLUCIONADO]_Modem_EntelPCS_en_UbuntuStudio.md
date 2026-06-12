---
title: "[SOLUCIONADO] Modem EntelPCS en UbuntuStudio"
date: 2009-07-01
forum: Hardware
---

### Post by cojeda on 2009-07-01
Tengo el modem SonyEricsson MD300 de EntelPCS, y tal como indica la página del proveedor configurado y funcionando en Ubuntu 9.04, funciona en perfectas condiciones.

Por otros motivos debo usar UbuntuStudio 9.04, y al realizar la misma operación no puedo conectarme, investigando me di cuenta que esta distro no viene nm-connection-editor baje del repositorio y no puedo instalarlo pues faltan unas librerias, las instaló y me arroja el error de no poder abrir la libreria compartida.

Alguien sabe como habilitar el md300 en UbuntuStudio, la forma wvdialEntelPCS.conf requiere del applet nm-connection-editor, por lo tanto necesito urgente otra forma de conectarme.

Por la ayuda muchas gracias.

Ubuntero nuevo pero sin retorno !!!

---

### Post by moreback on 2009-07-02
Hay una guía que está en el foro de hardware que tiene información como habilitar ese modem (incluso salió post de la semana). Lo que necesitas es network-manager y nm-applet en versión 0.7, lo raro es que deberían venir con Ubuntu Studio.

---

### Post by cojeda on 2009-07-02
Pablo, llegue a la misma conclusión, e procurado instalar pero no lo consigo, pues dispongo de los .deb respectivos pero siempre me reclaman alguna libreria.
Hoy intente con el wvdial_1.60.1+nmu2_i386.deb y tambien me reclama otras librerias, que aunque las instalo inidca que ya estan en uso.
Otra alternativa explorada es ndiswrapper y usar los driver windows, al final lo que espero es conectarme y actualizar desde los repositorios, pero no lo he conseguido.
Gracias por tu sugerencia

Cristian

---

### Post by Carlos C on 2009-07-02
cojeda, tengo una duda. La única vez que he tenido que instalar Ubuntu Studio recuerdo que el paquete network-manager viene instalado, por ese lado tengo la misma impresión que moreback. ¿Intentaste el método que moreback te propone?

[http://ubuntuforums.org/showthread.php?t=1188209](http://ubuntuforums.org/showthread.php?t=1188209)

Si no te resulta podrías decirnos qué es lo que te falla. En el caso de que lo que te falle sea la instalación de applet, por favor copia el error exacto.

Saludos!

---

### Post by asterix77 on 2009-07-02
Acá hay otra posible solución (creo que no necesitas el NM)

1) Instruciones   [http://www.niclabs.cl/entel/MD300/UbuntuDebian.html](http://www.niclabs.cl/entel/MD300/UbuntuDebian.html)
2) Link de descarga   [http://www.niclabs.cl/entel/MD300/UbuntuDebian_files/md300config_1-1ubuntu2_all.deb](http://www.niclabs.cl/entel/MD300/UbuntuDebian_files/md300config_1-1ubuntu2_all.deb)


Saludos y suerte

---

### Post by cojeda on 2009-07-02
Amigos gracias por sus respuestas pero sigo sin solución. Previo a ello "suponer" no es una palabra a considerar.

Efectivamente EntelPCS tiene una guía de como instalar el modem y un .deb pero que adolece de "suponer", en ubuntu 9.04 wvdial no viene por defecto, por ende el deb se cae y se debe copiar a mano los archivos de configuración.

Otra certeza es que en ubuntu 9.04 viene nm-applet y nm-connection-editor por defecto y que bastan dos click y ya está. El modem funciona perfecto

Pero !!!

En Ubuntu Studio 9.04 no viene instalado wvdial, nm-applet y nm-connection-editor, el sitio poco aporta, recopilando sus sugerencias, verificada la existencia del dispositivo en la puerta, identificado el "vendor" y el "product" (tal como viene en los archivos de Entel) y luego de resetear el udev con el comando

$sudo /etc/init.d/udev restart

Concluyo que solo me falta el dialer, pero no lo tengo, ok, consegui uno el
wvdial_1.60.1+nmu2_i386.deb
Al instalarlo me reclama problemas con las dependencias y nada, procedo manualmente y consigo el siguiente mensaje:

libuniconf.so.4.4 no puede ser compartida.

Si alguien conoce otro dialer que me permita ejecutar el script wvdial-EntelPCS. conf creo podria resolver el problema.

Gracias por la ayuda y orientación

---

### Post by moreback on 2009-07-03
Network-Manager tiene su propio dialer, ¿intentaste crear una cuenta de Banda Ancha Móvil en él? Yo uso otro modem, pero con las configuraciones que tiene el NM para Entel PCS conecta sin problemas.

---

### Post by cojeda on 2009-07-03
Si me cree una cuenta e ingrese los valores de discado , user password entre otros pero no me conecta, ahora intento con habilitar el wvdial, no pude instalarlo desde el deb pues reclamaba una dependencia.

Copie cada archivo en los destinos descritos en el deb pero al ejecutar

$ sudo wvdial o

$ sudo wvdial-EntelPCS.conf

me arroja el siguiente error:

wvdial: error while loading shared libraries: libwvstreams.so.4.4: cannot shared object file: no such file or directory.

Pero este archivo está en /usr/lib

Al igual que libwutils.so.4.4 y libwvbase.so.4.4 (permisos y owner verificado)

No he determinado que me origina este error aparentemente me falta algún archivo.

Si sabes cual te lo agradeceré

---

### Post by moreback on 2009-07-03
> **cojeda said:**
> Si me cree una cuenta e ingrese los valores de discado , user password entre otros pero no me conecta, ahora intento con habilitar el wvdial, no pude instalarlo desde el deb pues reclamaba una dependencia.

Que raro que tengas que ingresar los datos de discado, estos ya vienen por defecto y funcionan, sólo tienes que escoger el proveedor correcto en el asistente.

No te va a funcionar el wvdial que bajaste ya que la forma que se hace en Ubuntu para instarlarlo es usar el comando

```
sudo apt-get install wvdial
```

Saludos.

---

### Post by cojeda on 2009-07-03
SOLUCIONADO:

En rigor todas las ideas propuestas ayudaron a resolver el problema.


[LIST]
[*]La configuración de MD300 era conocida, probada y funcionaba con Ubuntu 9.04 en perfectas condiciones.
[*]La distro Studio no contiene por defecto network-manager-gnome.
[*]Las instalaciones apt-get no son efectivas y tal como uno de ustedes señaló no queda bien instalado.
[*]Entonces como se resolvió:
[/LIST]
[INDENT]
[LIST=1]
[*]Conecta tu equipo a internet via cable (eth0)
[*]Instalar network-manager-gnome
[*]Reiniciar el equipo
[*]Instalar el md300config_1-1ubuntu2_all.deb (disponible en EntelPCS)
[*]Ejecutar nm-connection-editor
[*]Crea una conexion banda ancha movil para Entel
[*]Configura en propiedades el Nº de discado, pues dice *99# y debe decir *99***1#
[*]AL cerrar veras el applet pestañando y conectando.
[/LIST]
Gracias a todos.
[/INDENT]

---

### Post by Carlos C on 2009-07-04
Excelente, edito el título y lo señalo como solucionado. Gracias cojeda por el feedback, la solución está completa y clara, servirá a otros.
Saludos.

---

### Post by moreback on 2009-07-05
> **cojeda said:**
> Configura en propiedades el Nº de discado, pues dice *99# y debe decir *99***1#

Esto no es necesario, se debe dejar tal cual, ya que Network-Manager hace esa sustitución solo.

---

### Post by Pottian on 2009-07-09
Tengo ubuntu 9.04

Yo tengo el Vodafone negro de entel creo que el ultimo, la cosa es que viene con un software de instalacion el cual instale con wine ¿primer error?.
Cuando lo conecto no abre el software vodafone y por ende no me puedo conectar, pero si tomo el antiguo de entel uno blanco se me conecta sin problemas.

gracias

---

