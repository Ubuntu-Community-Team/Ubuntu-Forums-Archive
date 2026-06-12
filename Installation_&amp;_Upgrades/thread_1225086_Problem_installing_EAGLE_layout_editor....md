---
title: "Problem installing EAGLE layout editor...??"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by deveshsamaiya on 2009-07-28
Hey..everyone
i need to install eagle layout editor on my machine..but i didnt find any command that can do it. i used one as
~$ sh eagle-lin-5.6.0.run
i downloaded the file eagle-lin-5.6.0.run from cadsoft website.
If anyone can help me installing this...plz .
Thank you

---

### Post by wojox on 2009-07-28
You want to move to the directory the application is in and use

```
sudo sh ./eagle-lin-5.6.0.run
```

---

### Post by deveshsamaiya on 2009-07-28
i did as suggested by you..but  is not working. I have the .run inside desktop directory.
it showing error like 
sh: Can't open ./eagle-lin-5.6.0
plz help
thank you

---

### Post by wojox on 2009-07-28
Ok 
Find the .run file in the File Browser (Nautilus)
Right-click the file and select properties
Under permissions tab make sure the Allow executing file as program is ticked and press close.
Double click the .run file to open it. A dialog box should appear.
Press run in terminal to run the installer
A terminal window willl open.
Follow any instructions on screen.

---

### Post by deveshsamaiya on 2009-07-28
thank you very much..eagle is noe working on my machine

---

### Post by lavadisco on 2009-08-01
I did the same thing and it appeared to install just fine, however there is no Eagle in my program menu now. Where is it?

---

### Post by anibalismo on 2009-08-07
Hi, guys! TY all for your support! I'm beginning like right now (with linuxMint) and I had a little problem installing eagle, since I step on this forum. TY again...
Im  translating this, so other users, also, could use it:


Hola, lo que sigue es una explicacion paso a paso para poder instalar el eagle en tu sistema ubuntu. hay dos formas, la segunda es la mejor:
recuerden que soy noob, si digo algo muy obvio o muy tonto, porfis, no me linchen...
PRIMERA:
0)busca un vasito de ron... 
1) ve a la pagina [http://www.cadsoft.de/download.htm](http://www.cadsoft.de/download.htm) y descarga el .run de windows
2) cuando se complete la descarga, busca el archivo, hazle click derecho, luego ve a permisions, y habilita "allow executing..."
3)dale doble click al archivo, y te va a salir un instalador, igual al de del sistema operativo de las ventanitas ;)
4)brinda con tu ron!!! acabas de instalar el eagle... si buscas en Home, va a haber una carpeta llamada eagle-5.6.0... si la abres, y le das click a la carpeta bin, y luego click al icono que dice "eagle" se va a abrir el programa, pero no va a aparecer en tu lista de aplicaciones... 

SEGUNDA:
5)para eso yo use un programa que se llama synaptics (que ya venia instalado con el linuxMint) y en la barra de buscar escribi "eagle" eso me enseno  unos packages de eagle
6)dale a los hitboxes (las cajitas cuadradas de seleccion)
7)y dale al boton de apply... y brinda otra vez!!! :popcorn:

te va a preguntar si lo quieres instalar... le das que si y voila! ya deberias de tener eagle 100% instalado en tu ordenador!
Espero que esto les haya servido de ayuda! :D
Cualquier cosa, me escriben al correo

---

### Post by andyzammy on 2009-08-10
Since this is a fresh thread i thought i'd use this one rather than make a new one:

I had no trouble installing EAGLE, and i also installed pcb-gcode, but when i try to make a new project it gives me a Permission Denied error when it tries to create a folder.

Is there a way to use eagle without having to run it as root?

---

### Post by andyzammy on 2009-08-26
bump this please.

---

### Post by andyzammy on 2009-09-08
are people seriously having to type in their passwords in order to use eagle bump?

---

### Post by andyzammy on 2009-09-15
bump, would love to hear other people's solutions to this. because it's a gui program am i better off using gksudo over sudo? doesn't seem to make any difference either or but i know gksudo's the norm for gui's.

---

