---
title: "Driver video Compaq Presario 2500"
date: 2008-09-04
forum: Hardware
---

### Post by GGsalas on 2008-09-04
Hola, acabo de instalar (y actualizar) Ubuntu 8.04 en una [compaq presario 2500]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=en&cc=us&product=425567"). Todo funciona bien. Necesito activar OpeGL en la placa de video, para eso intent'e instalar el driver de video de la placa ATI y no lo he logrado. 

Desde agregar programas, instale el driver de ATI y nada sucedio.

Desde Envy nstale el driver de ATI seleccionando la unica verdion que me dejo y solo consegui desconfigurar el teclado, por eso ahora no pongo acentos.

Gracias por la ayuda.
Saludos.

---

### Post by niko_3100 on 2008-09-04
En windows te anda bien la placa?? que raro que en "controladores restringidos" te haya hecho algun conflicto, nunca tube ati me gusta mas nvidia por eso, lo unico que te sugiero es que desde controladores restringidos desintales y vuelvas a instalar.

---

### Post by GGsalas on 2008-09-04
> **niko_3100 said:**
> En windows te anda bien la placa?? [...] te sugiero es que desde controladores restringidos desintales y vuelvas a instalar.

En Win. funcionaba bien, aunque no se con total seguridad si esa placa tenía aceleracion 3d y OpenGL. 

En Ubuntu no funcionan los efectos de escritorio, tampoco la aceleracion OpenGL y los videos de internet (flash) se ven muy mal.

Gracias.

---

### Post by sajnox on 2008-09-04
Lo del teclado me suena a que se desconfiguro el xorg.conf, ya me lo hizo alguna vez

poste la salida del comando cat /etc/X11/xorg.conf

---

### Post by GGsalas on 2008-09-04
> **sajnox said:**
> Lo del teclado me suena a que se desconfiguro el xorg.conf, ya me lo hizo alguna vez

poste la salida del comando cat /etc/X11/xorg.conf

Gracias. Entre las muchas pruebas que hice, eso se soluciono medianamente bien. Me preocupa mucho no poder instalar el driver adecuado a mi placa de video.

Saludos.

---

### Post by sajnox on 2008-09-05
Probaste con el Driver libre de Ati? 

Fijate en esta pagina si tu placa esta soportada 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

En caso que lo este en mi experiencia el driver libre funciona mejor que el que proporciona ATI. Si ya instalaste envy con utilizar la opcion de desinstalar el driver deberia alcanzar.

Con un Live CD como funciona la placa??

---

### Post by faktorqm on 2008-09-05
es verdad, hay problemas con esa placa... encima vi en un monton de foros que preguntan y en vez de contestarle el problema, le sugieren la instalacion de fedora, suse o mandriva que anda "sin tocar nada".... cuanta ignorancia que anda dando vueltas por ahi! cero filosofia de nada... lo pongo me anda listo, no importa el resto. GGGRRR

Mirate este link [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) que es un wiki no oficial de ati, pero a mi me parece que va. no lo lei en realidad si decia algo con respecto a tu placa pero yo creo que algo bueno tenes que sacar. Salu2!

---

### Post by GGsalas on 2008-09-07
faktorqm, justo iba a comentar que probé el live CD de Mandriva y funcionan los efectos compiz (es decir, tengo openGL funcionando) y probé una resolución mayor a 1024x768 y aparentemente no hay problemas, o sea que linux reconoce mi placa el problema es ubuntu, gracias sajnox.

Los datos que mandriva ve de mi placa son:

Radeon IGP 330M/340/350
VGA compatible controller
BUS PCI nº 1
ID fabricante: 0x1002
ID dispositivo: 0x4337
Sub ID fabricante: 0x103c
Sub ID dispositivo: 0x0850

CARD ATI RADEON 9250 AND EARLIER

Voy a probar la insalación que me proponés a ver que pasa y también me voy a bajar el live de fedora a ver si tambien lo reconoce.

Quiero aclarar que para quienenes somos principiantes en linux, o en realidad no poseemos conocimientos para configurar desde consola, el "instalar y funcionar" es muy importante. Ubuntu, en mi opinion, es una de las distribuciones que más ha contribuido en eso, al instalarlo me reconoce todo el hardware sin que yo haga nada, y salvo algunas excepciones reconoce scanners e impresora sin instala nada. Esto es una enorme ventaja respecto de cualquier sistema operativo incluso win. Despues, si uno quiere modificar partes de sistema a mano, tambien lo puede hacer. 

Saludos.

---

### Post by GGsalas on 2008-09-07
Necesito ayuda. Luego de varias horas de probar encontre varios tutoriales pero no logro podeer instalar los drivers libres de video para la targeta ati, supuestamente de esa manera poria activas la aceleracion en 3D.

[ATI/Radeon_(Del_modelo_8500_al_9250)]("http://doc.ubuntu-es.org/ATI/Radeon_(Del_modelo_8500_al_9250)")

[mucho mas en google ]("http://www.google.com.ar/search?hl=es&client=firefox-a&rls=com.ubuntu%3Aes-AR%3Aunofficial&hs=6nP&q=instalar+driver+libre+ati+radeon+9250+%22ubuntu+8.04%22&btnG=Buscar&meta=")

Confirmo que tanto en los liveCD de  mandriva como de fedora tengo puedo poner compiz y funciona sin problemas.

Saludos.

---

### Post by Hei Ku on 2008-09-07
Yo tengo esa placa y funciona con el driver radeon, con aceleracion 3D. Es el driver libre, que me instalo Ubuntu solito. No hace falta usar el driver privativo para que ande bien.

Desinstala todo lo relacionado con fglrx e instala el paquete xserver-xorg-video-ati

Despues postea tu xorg.conf

---

### Post by GGsalas on 2008-09-22
He reinstalado Ubuntu  la aceleración gráfica funciona bien con el driver original. Sucede que no puedo activar los efectos d escritorio. No se si eso se debe a que no es compatible con OpenGL o a que. No me voy a hacer problema por eso, lo importante es que funcione bien Blender, Inkscape y demás programas gráficos.

Gracias.

---

