---
title: "Nvidia 7300 GS"
date: 2008-08-30
forum: Hardware
---

### Post by GambitCba on 2008-08-30
Hola gente!
Tengo instalada la version Hardy Heron 8.04 y no puedo subir la resolucion de mas que a 1024x768, tengo un monitor 19" se me ve todo muy grnade y no me copa. Estab instalados los controladores de Nvidia.
Alguien sabe como hacer para subir la Resolucion...

---

### Post by pol666 on 2008-08-30
1- anda a sistema>administracion>controladores restringidos
2- activa los driver, y espera a que descarguen
3- Reinicia la PC
4- Hace en una termina sudo apt-get install nvidia-settings
5- anda a sistema>administracion>NVIDIA x server settings.
6- Anda a la solapa que cambia la resolucion y elegi la que quieras.

---

### Post by GambitCba on 2008-08-30
> **pol666 said:**
> 1- anda a sistema>administracion>controladores restringidos
2- activa los driver, y espera a que descarguen
3- Reinicia la PC
4- Hace en una termina sudo apt-get install nvidia-settings
5- anda a sistema>administracion>NVIDIA x server settings.
6- Anda a la solapa que cambia la resolucion y elegi la que quieras.

Mil Gracias!!!!
Soy muy nuevo en Linux y todavia me cuesta un toco!!!!

---

### Post by pol666 on 2008-08-30
**Te cuento capas que cuando reinicias se te vuelve a la otra resolucion. Lo que tenes que hacer es para quedarte tranquilo...**


1- anda a sistema>administracion>NVIDIA x server settings.
2- Anda a la solapa que cambia la resolucion y elegi la que quieras.
3- Clickea en Save to X configuration File
4- y pone guardar[B]

Si te sale algo de que no puede escribir el fichero[/B]

3- Clickea en Save to X configuration File
4- Entra en Show Preview
5- Copia todo el texto
6- Abri una terminal y escribi sudo gedit /etc/X11/xorg.conf
7- Borra todo lo que este escrito y copia el texto de la preview.
8- Guardas y listo

**Consejo extra por si no sabias**

abri un terminal y escribi *sudo apt-get install compiz-settings-manager fusion-icon emerald*
Despues Podes activar los efectos de escritorio en sistema>preferencias<apariencia
y modificar los plugin en sistema>preferencias>configuracion avanzada de efectos de escritorio

Podes agregar en sistema>preferencia>sesiones  el programa fusion-icon, que te permite activar o dsactivar los efectos desde el systray y ademas te deja elegir entre emerald o metacity como bordes de ventanas.

---

