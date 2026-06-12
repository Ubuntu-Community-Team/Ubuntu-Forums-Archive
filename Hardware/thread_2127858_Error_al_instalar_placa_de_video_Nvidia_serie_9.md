---
title: "Error al instalar placa de video Nvidia serie 9"
date: 2013-03-21
forum: Hardware
---

### Post by PeTTi on 2013-03-21
Tengo esta placa:
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9500 GT] (rev a1)


Bajé de la página de Nvidia los drivers que terminan en .run, lo abro con la termina y me da este error:

 nvidia-installer must be run as root 

Por lo que entiendo tengo que abrirlo como root, pero ya ni me acuerdo cómo se hacía.

¿Cómo se hace?
Gracias.

---

### Post by albandy on 2013-03-21
Tienes que poner sudo delante de la instrucción.
De todas formas no te recomiendo en absoluto la instalación manual de los drivers, mejor utiliza la herramienta que te proporciona Ubuntu para este fin.

Si estás en 12.04 la herramienta se llama jockey-gtk
En versiones superiores si no me equivoco está en la parte de configuración de los repositorios.

> **PeTTi said:**
> Tengo esta placa:
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9500 GT] (rev a1)


Bajé de la página de Nvidia los drivers que terminan en .run, lo abro con la termina y me da este error:

 nvidia-installer must be run as root 

Por lo que entiendo tengo que abrirlo como root, pero ya ni me acuerdo cómo se hacía.

¿Cómo se hace?
Gracias.

---

### Post by gmunioz on 2013-03-24
Para instalar los driver Nvidia desde su archivo .run es necesario que:
Presiones Ctrl+Alt+F1 para entrar en una terminal, donde deberás loguearte con tu nombre de usuario y contraseña
Para luego ejecutar en esta terminal
> 
sudo su
service lightdm stop
cd /home/usuario/Descargas
chmod +x nvidia-xxxx-xxxx.run
sh nvidia-xxxx-xxxx.run
reboot


---

### Post by PeTTi on 2013-03-28
> **gmunioz said:**
> Para instalar los driver Nvidia desde su archivo .run es necesario que:
Presiones Ctrl+Alt+F1 para entrar en una terminal, donde deberás loguearte con tu nombre de usuario y contraseña
Para luego ejecutar en esta terminal
[IMG]http://i.imgur.com/8exIAf6.png[/IMG]

Me da es error, ¿qué podrá ser?

---

### Post by gmunioz on 2013-03-28
Debes matar las X
No puedes instalar en modo gráfico

> sudo su
service lightdm stop
O inicia en modo recuperación, subopcion root

---

### Post by PeTTi on 2013-03-28
> **gmunioz said:**
> Debes matar las X
No puedes instalar en modo gráfico


O inicia en modo recuperación, subopcion root
Use la opción de service lightdm stop... y se me quedó borró todo, quedó el fondo de pantalla y quedó así. Tuve que reiniciar y ahí intenté todo pero sin esa linea de service...

---

### Post by EnriqueK on 2013-03-30
Te la voy  dejar muy simple
1.- crea una carpeta de nombtr NVIDIA en tu carpeta personal y allí pones el controlador descargado del sitio oficial, pero modificando el nombre dejandolo así
NVIDIA.run
2.- Ejecuta en un terminal
sudo gedit /usr/local/bin/aaasss
se abre un archivo de texto vacío y allí pones lo siguiente
#!/bin/sh
 service lightdm stop
 nvidia-uninstall
 apt-get --purge remove nvidia*
 rm /etc/X11/xorg.conf
 bash /home/usuaeio/NVIDIA/NVIDIA.run
 service lightdm start

Guardas, cierras y cierras terminal
3.- Abre terminal y pones 
gedit 111
pones lo siguiente

#!/bin/sh
 echo 'blacklist nouveau' > /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
 echo 'options nouveau modeset=0' >> /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
update-initramfs -u
 init 6


guardas, cierras y cierras terminal
4.- Abre terminal y pones
sudo su
luego de introducir tu contraseá ejecuta en ese terminal
bash 111
Esta operación la debes ejecutar una sola vez
5.- cuando reinicie el equipo  . pones 
Ctrl + Alt + F1
si la tty no aparece con F1, prueba con F2
Luego de introducir tu login y contraseá, ejecuta
sudo bash aaasss
Acepta todas las opcopnes , los cambios de opciones lo logras pulsando la tecla Tab
Ante un cambio del kernel, del xorg o si quieres poner una versión mas moderna del controlador, solo debes aplicar el punto 5.-

---

### Post by PeTTi on 2013-03-31
> **EnriqueK said:**
> Te la voy  dejar muy simple
1.- crea una carpeta de nombtr NVIDIA en tu carpeta personal y allí pones el controlador descargado del sitio oficial, pero modificando el nombre dejandolo así
NVIDIA.run
2.- Ejecuta en un terminal
sudo gedit /usr/local/bin/aaasss
se abre un archivo de texto vacío y allí pones lo siguiente
#!/bin/sh
 service lightdm stop
 nvidia-uninstall
 apt-get --purge remove nvidia*
 rm /etc/X11/xorg.conf
 bash /home/usuaeio/NVIDIA/NVIDIA.run
 service lightdm start

Guardas, cierras y cierras terminal
3.- Abre terminal y pones 
gedit 111
pones lo siguiente

#!/bin/sh
 echo 'blacklist nouveau' > /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
 echo 'options nouveau modeset=0' >> /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
update-initramfs -u
 init 6


guardas, cierras y cierras terminal
4.- Abre terminal y pones
sudo su
luego de introducir tu contraseá ejecuta en ese terminal
bash 111
Esta operación la debes ejecutar una sola vez
5.- cuando reinicie el equipo  . pones 
Ctrl + Alt + F1
si la tty no aparece con F1, prueba con F2
Luego de introducir tu login y contraseá, ejecuta
sudo bash aaasss
Acepta todas las opcopnes , los cambios de opciones lo logras pulsando la tecla Tab
Ante un cambio del kernel, del xorg o si quieres poner una versión mas moderna del controlador, solo debes aplicar el punto 5.-

Llegue hasta el ctrl alt + F1 (funcionó con F1) pero se apagó todo, lo dejé un rato pero el monitor no reaccionaba, a&#347;i que tuve que reiniciar.

---

