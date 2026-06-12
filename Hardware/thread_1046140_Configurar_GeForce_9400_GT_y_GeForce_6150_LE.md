---
title: "Configurar GeForce 9400 GT y GeForce 6150 LE"
date: 2009-01-21
forum: Hardware
---

### Post by Kabezon on 2009-01-21
Buenas, me compré una GeForce 9400 GT para actualizarme y poder jugar juegos de PC modernos (en Windows). Como ya sabrán, usar ciertas placas nVidia en Hardy no se puede; este es el caso de la 9400 GT. Por algún motivo, el nuevo Kernel de Intrepid no se lleva muy bien que digamos con mi PC: Ya sea con mi placa onboard (GeForce 6150 LE) o con la nueva placa, no puedo tener video como Dios manda. Después de instalar sus respectivos drivers y hacer reboot, me salta con que encuentra pantallas pero ninguna está configurada, o algo por el estilo... (Quedo clavado en Shell o en recovery mode)

Ese problema no me preocupa, ya que la nueva placa la compré con el único fin de usarla bajo Windows, por lo cual si no funciona en Ubuntu me es indiferente, de todas formas con la 6150 Compiz corre 10 puntos. El problema es que yo pensé que si cambiaba el enchufe del monitor de placa a placa cada vez que bootee un SO, iba a caminar... Pero no, no camina (Quizás sea algo muy obvio el porqué, pero yo no sé!)

Entonces, quería saber si hay que configurar algo dentro de Ubuntu, Windows, el Bios o qué sé yo, para poder poner a Ubuntu sólo con la 6150LE y a Windows sólo con la 9400GT, de esta forma teniendome que ahorrar el dolor de cabeza que implacaría lidiar con el problema de Intrepid y el video. 

Si no se puede hacer lo que quiero, entonces no me quedará otra que profundizar más en cómo arreglar lo de Intrepid u.u Aunque, desde ya les digo, que aparentemente soy el único ser en la faz de la tierra al que Intrepid+nVidia le trae problemas de este tipo -.-

---

### Post by guillermodl on 2009-01-21
la version 177  de los drivers a mi me trajo problemas, proba descargar la version beta 180 de nvidia.

despues tenes que ejecutarla para recompilar el kernel desde el bash, no sin antes detener el entorno grafico

sudo /etc/ini.d/gdm stop
sudo ./NVIDIA-Linux-x86-180.xx-pkg.run
sudo /etc/ini.d/gdm start

el tema es que cada ves que actualices el kernel vas a tener que ejecutarlo nuevamente

suerte

---

### Post by Kabezon on 2009-01-22
> **guillermodl said:**
> la version 177  de los drivers a mi me trajo problemas, proba descargar la version beta 180 de nvidia.

despues tenes que ejecutarla para recompilar el kernel desde el bash, no sin antes detener el entorno grafico

sudo /etc/ini.d/gdm stop
sudo ./NVIDIA-Linux-x86-180.xx-pkg.run
sudo /etc/ini.d/gdm start

el tema es que cada ves que actualices el kernel vas a tener que ejecutarlo nuevamente

suerte

Ya probé con la 180.22, es exactamente lo mismo. Voy a tener que esperar a que saquen Kernel nuevo :S

---

