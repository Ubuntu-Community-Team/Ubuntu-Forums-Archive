---
title: "Luz de adaptador wifi intermitente"
date: 2009-02-05
forum: Hardware
---

### Post by juan nicolas on 2009-02-05
Buenas, primera vez posteando en un furo y que mejor manera de empezar que haciendo consultas sobre ubuntu.
Recientemente estoy empezando a utilizar en mi Laptop HP dv2660se, el ubuntu como SO principal, hasta ahora no tuve problemas en la instalacion, configuracion de algunos soft, pero he aqui el motivo de mi contacto al foro: 
Desde hace unos dias noto que la luz de mi adaptador wifi se prende y se apaga constantemente, tengo conexion inalambrica a internet (mientras escribo este post se prende y se apaga, y cuando lo envie, seguira prendiendose y apagandose)
El adapatador wireless que tengo es un: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
Es normal que se prenda y se apague???
Muchas Gracias.

---

### Post by Hei Ku on 2009-02-05
En linux la configuracion por defecto es que la luz te muestre el trafico, asi que se prende y apaga, pero habia una manera de que quede prendida permanente, como es, si no me equivoco, en Win.

---

### Post by FlyerDie on 2009-02-05
> **Hei Ku said:**
> pero habia una manera de que quede prendida permanente
deja un ping corriendo... CUACK

No, hablando en serio, yo creo tener la misma placa en mi notebook Olivetti y siempre estuvo prendida, no titila.

---

### Post by sergiom99 on 2009-02-05
yo tengo una broadcom y esta siempre prendida, en Kubuntu y en win32.
Y cuando desactivo el wireless, pasa a naranja pero nunca titila.

---

### Post by luks911 on 2009-02-05
Capaz que se puede modificar para acomoddarlo a tu gusto. Habría que buscar un poco.
En mi caso, con una Compaq y una placa Atheros, usando Madwifi se puede cambiar. Originalmente, se queda naranja, pero puede modificar el archivo /etc/sysctl.conf para que muestre el tráfico o quede siempre azul. Lo mismo pasa en al menos un modelo de Acer. Aunque es imposible (hasta donde sé) cambiarlo usando el driver libre ath5k.
En todo caso, no te asustes que sólo muestra el tráfico. No va a explotar :lolflag:

---

### Post by marianom on 2009-02-05
Dell XPS 1330: en HH nunca se encendió. En II, está intermitente y me muestra la actividad del wireless como dijo Hei Ku anteriormente. Estaría bueno poder desactivarla para que no gaste batería (hace falta un Shaun en este thread).

---

### Post by luks911 on 2009-02-05
Busqué un poco y algunos lo consieran un bug porque no pasaba en Hardy. 
En este hilo ([http://ubuntuforums.org/showthread.php?t=964234](http://ubuntuforums.org/showthread.php?t=964234)) parece que encontraron una solución creando un script y haciendo que se ejecute al bootear.
Espero que sirva.

---

### Post by santiagoward2000 on 2009-02-05
> **marianom said:**
> Dell XPS 1330: en HH nunca se encendió. En II, está intermitente y me muestra la actividad del wireless como dijo Hei Ku anteriormente.

¿En serio? En mi 1330 con Intrepid está siempre prendida (mientras tengo la placa prendida), no titila...

---

### Post by marianom on 2009-02-05
> **santiagoward2000 said:**
> ¿En serio? En mi 1330 con Intrepid está siempre prendida (mientras tengo la placa prendida), no titila...

Aflojá con esos torrents... :) Ahora en serio, supongo que ese es el comportamiento por defecto pero la verdad a mi me distrae. Voy a ojear lo descubierto por luks911 para ver como lo puedo "arreglar".

---

### Post by juan nicolas on 2009-02-08
Agradezco a todos. Veré y probaré cada una de las respuestas que me dieron.
Nuevamente, muchas Gracias.

---

