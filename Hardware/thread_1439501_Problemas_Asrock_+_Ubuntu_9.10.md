---
title: "Problemas Asrock + Ubuntu 9.10"
date: 2010-03-26
forum: Hardware
---

### Post by krakc on 2010-03-26
Hola gente

algunos recordaran este post : [http://ubuntuforums.org/showthread.php?t=1237729&highlight=ubuntu+arranca+con+fx5200](http://ubuntuforums.org/showthread.php?t=1237729&highlight=ubuntu+arranca+con+fx5200)

pues abro este para decirle que me pasa exactamente lo mismo pero ahora es con ubuntu 9.10 karmic....

trate de usar la misma solucion que use con el 9.04 pero no funciono... ( poner en /etc/modprobe.d/blacklist una linea "blacklist intel_agp"

pero no funciono, segui leyendo y resulta que ahora el archivo donde deberia ir es /etc/modprobe.d/blacklist.conf, pues bueno lo hice y tampoco funciona...

alguien me puede decir si se puede o no, o cual es el truco para hacer que mi ubuntu 9.10 arranque con mi aceleradora FX5200 en mi board asrock p4i45gv

cuando pongo en la bios que arranque desde la aceleradora, se pone la pantalla con barras negras y blancas y se cuelga... si me voy por la parte "no grafica", me dice algo como "kernel panic -not syncing: attempted to kill init"...

recibo sugerencias, es que regale el dvd del 9.04 y lo dañaron y no tengo internet en mi casa para bajarlo de nuevo.

---

### Post by EnriqueK on 2010-03-26
Primero que nada, debes entrar al BIOS y hacer la instalación básica con  la tarjeta de video integrada, no voy a tocar el tema. Una vez instalado la distro, editar como root el archivo /etc/modprobe.d/blacklist, agregar las siguientes líneas:

#Inhabilitar Intel AGP
blacklist agpgart
blacklist intel_agp

Guardar y cerrar el editor, reiniciar con la tarjeta gráfica externa (entrando previanente al BIOS para cambiar la selección), es probable que el servidor gráfico no arranque, iniciar en modo de recuperación para reparar el servidor gráfico, esto instalara el driver "vesa" en xorg.conf, no habrá aceleración gráfica, iniciar el administrador de hardware, este debiera instalar el driver para nVidia.
Por último, mi recomendación es que en cuando puedas, te cambias de Mobo por que este es muy problemático en la parte gráfica por usar AGI en vez de AGP.

---

### Post by krakc on 2010-03-26
> **EnriqueK said:**
> Primero que nada, debes entrar al BIOS y hacer la instalación básica con  la tarjeta de video integrada, no voy a tocar el tema. Una vez instalado la distro, editar como root el archivo /etc/modprobe.d/blacklist, agregar las siguientes líneas:

#Inhabilitar Intel AGP
blacklist agpgart
blacklist intel_agp



estamos hablando de 9.10 o de 9.04???, lo digo por el nombre del blacklist, que no se si sera blacklist o balcklist.conf 

el SO ya lo tengo instalado pero no puedo iniciar desde la AGI de mi mal**ta board que es una pesadilla pero como no hay dinero para cambiarla tengo que tratarla con cariño (por ahora).

PD: no compren asrock, compren asus o msi o cualquier otra menos asrock.

---

### Post by guillermolisi on 2010-03-26
Para 9.10 el archivo a usar es /etc/modprobe.d/blacklist.conf

---

### Post by lddm on 2010-07-23
Perdon que reviva este post después de tanto tiempo. Yo tengo la misma motherboard, también instale Ubuntu 9.10 y estuve intentando configurar una fx5200 AGP sin exito. Agregué esas lineas al archivo /etc/modprobe.d/blacklist.conf y aún así cuando quiero abrir el Ubuntu la pantalla queda negra con lineas verticales blancas. No se me ocurre mucho más que hacer,¿podrían subir el contenido del xorg.conf para ver si tengo que modificar alguna opción ahí también?
Muchas gracias
Luis

---

### Post by atari130xe on 2010-07-23
Mmm la pesadilla de Asrock, me pasó lo mismo hace unos meses cuando traté (sin éxito) de instalarle Ubuntu 9.04, 9.10 Mandriva one etc. en su PC con mother Asrock, tenía una Intel Graphics con 64MB AGI (un invento de Asrock) que al intentar agregarle una Nvidia 6200 AGP 256MB no quiso arrancar ni ahí, pero.. siempre hay un pero pude exitosamente instalarle Linux Mint en modo compatibilidad y funcionó perfecto, hoy disfruta de Linux con Compiz activado y todo. (La placa madre es una Asrock 775i65G)

De todas maneras te paso este Link de Ubuntu-es de una persona que pudo finalmente hacerlo:
[http://www.ubuntu-es.org/node/72609]("http://www.ubuntu-es.org/node/72609")

suerte!

---

### Post by EnriqueK on 2010-07-23
Inicia el equipo con un  LiveCd anterior que te permita arrancar, desde allí usando Firefox vas al sitio oficial de Nvidia que correpomde a tu caso
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Recomiendo que al archivo .run lo descargues en la carpeta de usuario de tu instalación en DD .
Completada la descarga de, NVIDIAxxxxx.run en tu carpeta de usuario, reinicias el equipo entrando a la instalación del 10.04 pero en Recovery Mode, cuando termine la rutina te muestra varias opciones, elige la última creo se llama netroot, te va a iniciar una terminal de root , luego escribes
nano /etc/modprobe.d/blacklist.conf
le agregas 
#Inhabilitar Intel AGP
blacklist agpgart
blacklist intel_agp
guardas los cambios y finalmente
bash NV
pulsa la tecla Tab y se va a autocompletar el nombre del controlador, pulsa Enter y comienza la instalación, durante el proceso debes aceptar todas las opciones que te muestra aunque por defecto te muestre que NO , con la tecla TAB cambias las opciones, cuando termine la instalación pones reboot y reinicias en modo normal-

    * editar
    * responder

---

