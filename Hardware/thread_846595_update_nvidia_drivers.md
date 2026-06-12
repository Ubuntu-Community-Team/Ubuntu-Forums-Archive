---
title: "update nvidia drivers"
date: 2008-07-01
forum: Hardware
---

### Post by Barasuishou on 2008-07-01
HOLA bueno soy nuevo en ubuntu, estoy tratando de instalar unos nuevos drivers de video que baje de la pagina de nvidia, pero cuando abro el archivo para instalarlo me dice que ya estoy corriendo un "X server" y qeu tengo qeu salir para instalar el nuevo driver, alguien me puede decir como hago, o hacer una miniguia, para actualizar los drivers???
aaa me olvidaba, probe con los controladores de hardware activados y desactivados, y es lo mismo :S,

---

### Post by atari130xe on 2008-07-01
> **Barasuishou said:**
> HOLA bueno soy nuevo en ubuntu, estoy tratando de instalar unos nuevos drivers de video que baje de la pagina de nvidia, pero cuando abro el archivo para instalarlo me dice que ya estoy corriendo un "X server" y qeu tengo qeu salir para instalar el nuevo driver, alguien me puede decir como hago, o hacer una miniguia, para actualizar los drivers???
aaa me olvidaba, probe con los controladores de hardware activados y desactivados, y es lo mismo :S,

teclas: Ctrl+Alt+F1
```
sudo /etc/init.d/gdm stop
```
luego
```
sudo sh /home/USUARIO/NVIDIA-Linux-x00-000-00-00-pkg0.run
```
a todo le decis "yes" o "si" no se si lo tenés en Ingles o castellano al Driver
en donde dice NVIDIA-Linux-x00-000 etc lo reemplazas por el nombre del archivo que bajaste (el driver claro está)

luego
```
sudo /etc/init.d/gdm start
```
y listo... espero te sirva :)

---

### Post by Barasuishou on 2008-07-03
HOLA, bueno hize eso y me anduvo de maravilla, pero ahora cada vez que inicia me tira como que no pudo detectar ni mi monitor y ni mi placa de video y me tira "inicio en baja resolución" o algo así,  :S, alguna idea???? osea mi monitor es un dell tiene reso 1680x1050, y la placa es una geforce 7100 osea la banca, pero ahora solo me figura como opciones 800x600, cuando habro el gestor de controladores de hardware, me tira que la placa de video está en uso, pero no esta habilitado, si lo habilito y reinicio me vuelve a tirar lo de antes de inicio en baja reso, :S, alguna solución???

---

### Post by Barasuishou on 2008-07-04
alguien plis ayuda que así no lo puedo ni usar :S

---

### Post by Hei Ku on 2008-07-04
postea tu xorg.conf

---

### Post by sdennie on 2008-07-05
Primero tenés que borrar el driver que viene con Ubuntu.  Asi que:

```

sudo apt-get remove --purge nvidia*

```

Después, podés usar las instrucciones de atari130xe y va a funcionar después de reiniciar.

---

### Post by Barasuishou on 2008-07-07
a ta :P voy a hacer ese purge, y por las dudas, como veo/abro el xorg.conf???, para postearlo

---

### Post by Barasuishou on 2008-07-07
hola, bueno hize eso del purge, y sigo en la misma solo que ahora en la parte de controladores de hardware restringidos, no me aparece la placa, osea antes no la tomaba, pero aparecia, ahora directamente no aparece :S, alguna solución???, no quiero usar tanto windows!!! T.T

---

### Post by GaBrIeEl on 2008-07-07
Yo eh solucionado el probleba ese bajando el nvidia-settings

> sudo apt-get install nvidia-settings

ejecutandolo

> sudo nvidia-settings

y cambiandole la resolución a 1280x960 y queda configurada correctamente .... nose si esto les servirá de algo. pero es lo que yo hice y ami me ha funcionado :)

---

### Post by faktorqm on 2008-07-08
¿Por que se la complican taaanto muchachos? No es tan dificil! Instalas el envy, te hace todo automatico y un problema menos! 

```
sudo apt-get install envy-ng
```

para ""el nuevo"": bienvenido al foro!! :KS

---

### Post by Barasuishou on 2008-07-11
me dice que no encuentra el paquete envy :S

---

### Post by faktorqm on 2008-07-13
Que version de ubuntu tenes?!?!

---

### Post by Barasuishou on 2008-07-14
la última hardy heron 8.04 :S

---

### Post by Mauro22 on 2008-07-14
en ubuntu 8.04 se llama EnvyNG-gtk

```
sudo apt-get install envyng-gtk
```

Si es Kubuntu:

```
sudo apt-get install envyng-qt
```

---

### Post by Barasuishou on 2008-07-15
bien ahora lo pude instaalar, pero sigue sin figurarme la placa de video :S, en esa pantalla vieron donde se le peude dar hablitar , la que está en administración, la abro y no me figura la placa :S, y me parece que si sigue así hago backup y lo reinstalo :(

---

### Post by Cristian CP on 2008-07-25
Barasuishou, pudiste arreglar tu problema ya que yo tengo el mismo. Si es así, podrías postear lo que hiciste? Saludos :confused:

---

### Post by luks911 on 2008-07-25
Llego tarde al hilo, pero trato de aportar algo. 
Para Cristian CP y Barasuishou: ¿Si revisan el archivo /etc/default/linux-restricted-modules-common, cómo está el parámetro DISABLED_MODULES?
Porque debería quedar así
```
DISABLED_MODULES="nv nvidia_new"
```
Eso es para que Ubunto no trate de cargar los drivers que vienen por defecto. No sé, en una de esas viene por ahí.
Para ver el archivo y poder modificarlo
```
sudo gedit /etc/default/linux-restricted-modules-common
```

---

### Post by Cristian CP on 2008-07-25
Gracias y a probar, yo por lo menos, en el archivo donde DISABLED_MODULES tenía " ". Tal cual. Después cuento.

---

### Post by Cristian CP on 2008-07-26
Uff, he resuelto los problemas con mi tarjeta nvidia 6200, no hice al final lo que dijiste luks911. Al final dejé los controladores restringidos que localiza el sistema a través del gestor. en mi caso dejó el driver 96.43.05, no es el último pero me está funcionando bien por ahora. el problema me parece era que tenía instalado el archico nvidia-glx-new en vez de nvidia-glx. Cuando los instalé se resolvieron los problemas. Luego hice 
sudo nvidia-settings
modifiqué resoluciones y tomó bien la configuración de xorg.

Cuando reinicié apareció el logo de nvidia. Listo.
Después como solucioné los problemas de compiz es otro tema que están documentados pero no son para poner acá.
Saludos.

---

