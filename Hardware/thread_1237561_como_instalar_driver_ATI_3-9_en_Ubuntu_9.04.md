---
title: "como instalar driver ATI 3-9 en Ubuntu 9.04 ?"
date: 2009-08-11
forum: Hardware
---

### Post by lms58 on 2009-08-11
Hola todos, estoy tratando de instalar el "ati-driver-installer-9-3-x86.x86_64.run" en Ubuntu 9.04 jaunty jackalope , para una radeon 1600 series, aun no puedo :( , si alguien lo logro instalar podria dar alguna informacion de lo que hizo? 
Tambien instale envy, muestra un solo driver ati 8.600-0ubuntu2 , no es compatible ni recomendado, despues de tanto probar sistema/administracion/controladores de hardware me muestra una lista vacia.
No puedo habilitar los efectos de escritorio.
cualquier dato se agradece, saludos!

---

### Post by Hei Ku on 2009-08-11
Ese driver no sirve para esa placa. Tenes que usar el driver libre, Radeon.

---

### Post by lms58 on 2009-08-12
hola key ku, gracias por tu respuesta, pero la idea es que alguien comente si pudo instalar el driver y como lo hizo para darnos una idea. Respecto a si corresponde o no el driver con el modelo(radeon 1600series) ,podes fijarte en esta pagina:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

Llegas ahi desde cualquiera de estos dos buscadores ingresando el so y modelo de placa

[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&contentType=GPU%20Download%20Detail](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&contentType=GPU%20Download%20Detail)

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Me llevan directo al driver 9.3, el tema es que la extension es .run y no se como se instala.
PD: ya probe con Envy, la idea es tratar de instalar este controlador , se puede?? Por ahi lei que si instalaron, pero no explican bien como, no pude seguir lo que hicieron. 
Saludos!!

---

### Post by Hei Ku on 2009-08-12
El driver no te sirve, porque hubo cambios en el X Server que no son compatibles con el driver. El driver de ATI que es compatible es el 9.04, pero ya no tiene soporte para esas placas.

Si de todas maneras queres instalarlo y romper tu instalacion, el comando es asi. Desde una terminal en la carpeta donde esta el archivo:

sudo chmod +x <nombre de archivo>

sudo ./<nombre de archivo>


Suerte!

---

