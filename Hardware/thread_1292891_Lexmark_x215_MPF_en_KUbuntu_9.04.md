---
title: "Lexmark x215 MPF en KUbuntu 9.04"
date: 2009-10-16
forum: Hardware
---

### Post by Blackaiser on 2009-10-16
**Hola, hace poco decidi cambiarme completamente a Linux bajo la version de Kubuntu y ha sido como volver a cuando era niño... volviendo a empezar... bueno.. mi problema es mi impresora, tengo una Lexmark x215 y no la reconoce, esta instalada por USB. busqué en San Google y encontre esto:**

**[Lexmark X215 funcionando con Ubuntu 8.04]("http://nideaderedes.urlansoft.com/2008/08/27/lexmark-x215-funcionando-con-ubuntu-804/")**

 Agosto 27th, 2008 Posted in [ubuntu]("http://nideaderedes.urlansoft.com/category/ubuntu/") 
    				¡Casi no puedo ni creerlo! He conseguido que funcione una Lexmark X215 con Ubuntu 8.04. Después de varios meses sin intentarlo de nuevo (y casi a punto de desterrar esta multifunción a tareas de simple fotocopiadora) lo he conseguido.
 La pista me la dieron aquí:
[http://foros.ubuntu-cl.org/viewtopic.php?p=30637](http://foros.ubuntu-cl.org/viewtopic.php?p=30637)
 Sabiendo que la Lexmarxk X215 funciona igual que una Samsung scx-4×16 rebusqué un poco y encontré la solución aquí:
 [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)
 Los pasos que seguí fueron:
 1) [Descargar el driver de Samsung]("http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=&subtype=&model_nm=CLP-550N&language=&cate_type=all&mType=DR&dType=D&vType=L&cttID=209194&prd_ia_cd=06010200&disp_nm=CLP-550N"). Es posible que haya una versión nuevo, sólo es cuestión de buscar.
 2) Lo descomprimí en la carpeta ‘/home/gorka/cdroot’.
 3) Abrí una consola y tecleé:
 cd /home/gorka/cdroot
sudo chown -R root:root *
sudo ./autorun
4) Este último comando abre un asistente de instalación. Como no me autodetectó la impresora cancelé la configuración en cuanto me pidió que indicara el puerto al que estaba conectado la impresora.
 5) Abrí el asistente de impresoras de Ubuntu: Sistema->Administración->Impresoras.
 6) Seleccioné: Impresora nueva.
 7) Buscó las impresoras y la encontró conectado al puerto LPT1 (sí, sí, está conectada a ese puerto y no al USB en este PC). Seleccioné la impresora y click en siguiente.
 8 ) En la lista de controladores seleccioné el de Samsung.
 9) De la lista de impresoras de Samsung escogí la “SCX-4×16&#8243;.
 10) Siguiente, aplicar y listo. Pedí que imprimiera la página de prueba y ¡Tacháaan! Salió perfecta.
 He de decir que es posible que en algún momento tengas que reiniciar el ordenador, por ejemplo si ves que la lista de impresoras de Samsung no aparece, o que no se detecta la impresora Lexmark.
 Suerte, que creo que sois unos cuantos con éste problema.
 Como nota final diré que esta ha sido la primera Lexmark que me he comprado y será la última.

SITIO:
[http://nideaderedes.urlansoft.com/2008/08/27/lexmark-x215-funcionando-con-ubuntu-804/](http://nideaderedes.urlansoft.com/2008/08/27/lexmark-x215-funcionando-con-ubuntu-804/)

He seguido los pasos y no pasa nada, incluso encontre unos post donde decian que se debia editar el archivo autorun y en la primera línea cambiar el SH por BASH y nada... 
Estoy claro que despues de mucho analisis el drama es de capa 8, por eso solicito su ayuda.
De antemano gracias.

---

### Post by Carlos C on 2009-10-17
Puedes partir mirando la información que tenemos en el foro sobre las impresoras Lexmark:

[http://ubuntuforums.org/showthread.php?t=1224963](http://ubuntuforums.org/showthread.php?t=1224963)

[http://ubuntuforums.org/showthread.php?t=1282983](http://ubuntuforums.org/showthread.php?t=1282983)


Saludos.

---

### Post by themasterdark on 2009-10-18
fijate bien si cambiaste "sh" por "bash" en el archivo autorun

en las dos lineas que debes hacerlo no solo en la primera

fijate

“ #! /bin/**sh**
BASE='dirname $0'
exec **sh** $BASE/Linux/install.sh”

deberá quedar asi:

“ #! /bin/**bash**
BASE='dirname $0'
exec **bash** $BASE/Linux/install.sh”

puse en negrita lo que se debe modificar... 
Saludos

---

### Post by Blackaiser on 2009-10-18
no la cambié... gracias.. probare de inmediato

Me dice

Bash : autorun : orden no encontrada

"desde la consola, dentro de la carpeta que contiene los archivos, pongo "autorun" y ejecuto pero me sale ese mensaje...

adjunto el contenido de autorun, la direccion del install tambien la modifique.

#! /bin/bash
BASE=`dirname $0`
exec bash $BASE/Documentos/driver/Linux/install.sh

---

### Post by themasterdark on 2009-10-19
lo estas ejecutando de esta forma **sudo ./autorun**

eso en una consola?

saludos...

(Ademas me fije que la informacion q lees para instalar la impresora dice, que no le sirvio de nada ejecutar el autorun porque abrio un asistente de configuracion para detectar la impresora, pero no se la detecto)

vee si te resulta, el **sudo ./autorun** en caso q no resulte saltate ese paso y continua y cuenta que ocurrio.

Saludos (ahora si xD)

---

### Post by Blackaiser on 2009-10-19
Bueno actualizo info.

Siguiendo el hilo, con el autorun no paso nada, finalmente me encontre unos drivers unificados de Lexmark que instala un asistente para las impresoras... bastante genial, pero no esta mi modelo, asi que quede en la misma... ahora me encuientro probando una por una a ver si algun driver de ellos me funciona.

Tambien encontre info donde dicen haberla instalado con los drivers de la Samsung scx4x16 pues baje los famosos drivers unificados  de samsung y encontre los famosos *.ppd y procedi a instalarla de forma manual, pero tampoco responde.... la unica diferencia es que yo la tengo conectada por usb y la persona que la hiso funcionar la tenia por paralelo, bueno, esos cambios he de probarlos ya mañana... almenos agradesco que sigan el tema... cualquier sugerencia y opinion es agradecida.:popcorn:

---

