---
title: "No veo nada"
date: 2009-06-03
forum: Hardware
---

### Post by FB91 on 2009-06-03
Ya tenía instalado desde hace mucho el driver para mi placa de video nvidia en Ubuntu... resulta que fui a administracion » controladores de hardware (creo que se llama así) y me saltó una instalación recomendada para instalar de unos drivers de nvidia.

Cuando los instalé se me habían ido los efectos visuales y no podía ponerlos !

Entonces intento instalar nuevamente mis viejos drivers que funcionaban bien y cuando termina la instalación y trato de volver al modo gráfico..


Veo la pantalla totalmente negra. 

Toque lo que toque sigue negra! ni idea que puede ser

Gracias por la ayuda :D

---

### Post by luks911 on 2009-06-03
¿Incluso si presionás Ctrl+Alt+F1 sigue negra o pasa a una terminal?
También contanos qué placa de video tenés y qué drivers tenías antes.

---

### Post by FB91 on 2009-06-03
No, no se abre la terminal...

Tengo una placa de video onboard GeForce 7025 y el driver no encuentro ahora el link exacto para pasarte pero lo descargué de la pag de NVIDIA y el archivo que me bajó se llama NVIDIA-Linux-x86_64-180.51-pkg2.run

gracias por la ayuda!

---

### Post by luks911 on 2009-06-03
Ok. Probá lo siguiente, en el inicio apretá Esc para ingresar a las opciones del Grub. Ahí elegí la primera opción que termine con (Recovery mode). Eso es el kernel más nuevo y te va a dejar en una pantalla de terminal.
Creo que pide que te loguees. Lo hacés y, conectado a internet, ejecutás

```
sudo aptitude install nvidia-glx-180
```

Si te hace alguna pregunta, decile que sí. Después reiniciá. A ver si con eso camina.

---

### Post by FB91 on 2009-06-03
> **luks911 said:**
> Ok. Probá lo siguiente, en el inicio apretá Esc para ingresar a las opciones del Grub. Ahí elegí la primera opción que termine con (Recovery mode). Eso es el kernel más nuevo y te va a dejar en una pantalla de terminal.
Creo que pide que te loguees. Lo hacés y, conectado a internet, ejecutás

```
sudo aptitude install nvidia-glx-180
```Si te hace alguna pregunta, decile que sí. Después reiniciá. A ver si con eso camina.

Puedo entrar en el recovery mode... pero el problema que una vez dentro me muestra un cuadro con opciones a elegir (arreglar problemas de graficos, problemas del disco, etc, etc) elijo cualquiera de esas opciones pero el problema sigue!

Nose como hacer para escribir una linea de comando una vez dentro del recovery mode... ese es mi problema :S

---

### Post by luks911 on 2009-06-03
Ah, me faltaba eso. La opción que tenés que elegir es una que te envía a una consola en modo root. Está en inglés y no recuerdo cómo es exactamente pero ice algo de "root shell".

Fijate con eso y avisá.

---

### Post by FB91 on 2009-06-03
Lo hice, no me tiró ningun error pero no modificó nada... es decir, sigo viendo la pantalla negra...

hay otra manera de solucionarlo? o me recomendás que lo instale desde 0 ? total no tengo nada que perder... lo instalé hace poco y no tengo casi ningun archivo que me sea util ahi dentro

---

### Post by luks911 on 2009-06-03
Mmmm...
No voy a ser el que te recomiende reinstalar :-P aunque tampoco tengo muchas ideas. 
Antes probá una cosa más. Lo mismo de antes pero en lugar de instalar el driver ejecutá
```
sudo dpkg-reconfigure xserver-xorg 
```

Y si llegás a reinstalar, el driver instalalo con el comando que te pasé antes o con el Administrador de Controladores de Hardware, de ese modo deberían evitarse problemas.

---

### Post by FB91 on 2009-06-03
hice lo que me dijiste y me salían unos carteles preguntandome cosas referidas al teclado entre otras cosas... yo le puse a todo que si. Pero no cambió nada...

Gracias por ayudarme! voy a seguir viendo si hay otra manera, sino de ultima reinstalo todo desde 0

---

### Post by luks911 on 2009-06-03
Bueh, teóricamente lo que hiciste debería haber reconfigurado el xorg.conf y sus opciones de video. Se me terminaron las pocas ideas, diría que hay algo con la configuración del monitor, pero me genera dudas el hecho de que antes funcionaba.
Seguro alguien te pueda dar algo más útil. 
Y si reinstalás, pensá que si antes instalaste con particiones aparte para / y /home ahora podés sólo formatear / y en 15 minutos tenés todo como antes.

---

### Post by FB91 on 2009-06-03
> **luks911 said:**
> Bueh, teóricamente lo que hiciste debería haber reconfigurado el xorg.conf y sus opciones de video. Se me terminaron las pocas ideas, diría que hay algo con la configuración del monitor, pero me genera dudas el hecho de que antes funcionaba.
Seguro alguien te pueda dar algo más útil. 
Y si reinstalás, pensá que si antes instalaste con particiones aparte para / y /home ahora podés sólo formatear / y en 15 minutos tenés todo como antes.

ahh eso no lo sabía... voy a probar con eso

Si alguien tiene algun tutorial para pasar se lo agradesco ;)

---

### Post by Mauro22 on 2009-06-03
No deberias tener una copia del xorg.conf cuando se actualizaron los drivers :S

Si es asi, solo tenes que hacer un par de pasos:


Entra a la consola como habias hecho antes.

```
cd /etc/X11
ls
```

deberia aparecerte entre muchos, el famoso xorg.conf y otros archivos con otra "extension" (ejemplo. xorg.conf.03062009 seria una copia hecha hoy) o tambien puede haber con .bak o algo por el estilo.

Si tenes, busca la copia mas actual y hace:

```
sudo rm xorg.conf
```

y despues usando el archivo de la extension mas larga hace (uso el de arriba como ejemplo)

```
sudo mv xorg.conf.03062009 xorg.conf
```


Si todo salio bien, intenta levantar la X


```
startx
```


Saludos!!

---

