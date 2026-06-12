---
title: "Problema compiz actualizacion a HH"
date: 2008-07-15
forum: Hardware
---

### Post by Cristian CP on 2008-07-15
Hola gente, era mi último recurso escribir mi problema con mi tarjeta nvidia después de buscar y buscar. Tarjeta nvidia 6200. Actualizo a HH, problema con resolución. Instalo envy, de ahí los drivers actualizados, soluciono resolución. De ahí descubro que compiz no carga. Compiz en consola da esto: Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0221 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Se debe a la primera línea XGL? He realizado algunas pruebas y no doy con la solución. Si alguien se da una idea, desde ya gracias.

---

### Post by niko_3100 on 2008-07-16
proba bajandote la version de los drivers 96.algo yo tengo esos y anda de diez con mi geforce 6100 y antes tenia los ultimos drivers y me andaba mal.

---

### Post by Hei Ku on 2008-07-16
NVidia tiene 4 drivers distintos para linux, dependiendo del modelo de la placa. una belleza! :D

Tenes que probar cuál es el que te funciona a vos.

---

### Post by Cristian CP on 2008-07-16
Gracias, creo que el que decís es el driver 96.43.05, recién estuve fijándome en la página, aún no entendí bien cuáles son los drivers a buscar, pero por ahora probaré con este. Después cuento que pasó.

---

### Post by niko_3100 on 2008-07-16
Asi es, ese mismo driver tengo yo y es el que mejor me anda.

---

### Post by Cristian CP on 2008-07-21
Bueno, no he tenido mucha suerte con los drivers recomendados, renegué un rato y no logré hacerlos andar bien. La cuestión es que descubrí que en la configuración del otro usuario compiz anda sin problemas, lo cual me dejó así :confused:. ¿Alguna idea por dónde puede estar la diferencia?

---

