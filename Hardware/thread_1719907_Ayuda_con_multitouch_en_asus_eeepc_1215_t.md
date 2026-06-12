---
title: "Ayuda con multitouch en asus eeepc 1215 t"
date: 2011-04-02
forum: Hardware
---

### Post by Gatillotuc on 2011-04-02
Quisiera consultarles por un problema que tuve al instalar UBUNTU en mi ASUS EEE PC 1215T. Probé varias distribuciones (32 y 64 bits de UBUNTU, KUBUNTU y la version netbook).
En ninguna de ellas pude hacer funcionar el multitouch de mi touchpad (en windows usa drivers synaptics, al igual que en linux)

Alguna idea?
Les dejo links de la compu:
[http://www.notebookcheck.net/Review-Asus-Eee-PC-1215T-Netbook.41488.0.html](http://www.notebookcheck.net/Review-Asus-Eee-PC-1215T-Netbook.41488.0.html)
[http://www.notebookcheck.org/Analisis-del-Netbook-Asus-Eee-PC-1215T.42728.0.html](http://www.notebookcheck.org/Analisis-del-Netbook-Asus-Eee-PC-1215T.42728.0.html)
[http://netbooksreview.net/asus/1215t-review/](http://netbooksreview.net/asus/1215t-review/)

---

### Post by Flechagorda on 2011-04-07
Gatillotuc, como te va....

Yo tengo una ASUS 1201PN con multitouch Synaptics tambien...

Desde el vamos ya me anduvo el multitouch pero con el scroll en la parte lateral.

Para pasarlo a "dos dedos" abri el gconf-editor desde la terminal.

Ahi anda a: /desktop/gnome/perhiperals/touchpad

Ahi tenes varias opciones, para el scroll donde dice "scroll method"

0 es para desactivarlo
1 es para lateral
2 es para "dos dedos"



Lo otro que no podia hacer andar es que cuando usas el navegador y queres abrir el link en otra pestaña en segundo plano haciendo click con dos dedos juntos, como emulando el boton central del mouse.

Si tiras en la terminal un: synclient -l
te sale toda la tira de parametros, la que yo cambie es esta:

TapButton1              = 1
TapButton2              = 3
TapButton3              = 2

le cambie el orden y quedo:

TapButton1              = 1
TapButton2              = 2
TapButton3              = 3

Y ahora en el Opera cuando le haces click con los dedos te lo abre en segundo plano.


El zoom del multitouch la verdad que no lo uso asi que todavia ni me fije como acomodarlo....


Se entiende algo????? porque hace rato que no entraba al foro...

Saludos

---

### Post by Flechagorda on 2011-04-07
Perdon, me olvidaba decirte que yo estoy con Ubuntu Netbook 10.10

---

### Post by RawthiL on 2011-06-08
> 
Para pasarlo a "dos dedos" abri el gconf-editor desde la terminal.

Ahi anda a: /desktop/gnome/perhiperals/touchpad

Ahi tenes varias opciones, para el scroll donde dice "scroll method"

0 es para desactivarlo
1 es para lateral
2 es para "dos dedos"

Sirve perfectamente para una Asus 1215p con ubuntu 11.04

Gracias!!

---

