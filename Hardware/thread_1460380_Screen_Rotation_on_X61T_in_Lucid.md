---
title: "Screen Rotation on X61T in Lucid"
date: 2010-04-22
forum: Hardware
---

### Post by jbiggs12 on 2010-04-22
Hello world!!

So I'm trying out Lucid, and all is going well, but the main problem that I'm having is that I can't install wacom-tools; apparently it doesn't exist anymore or has fallen into obsolescence. I've set up screen rotation as per this guide: [https://help.ubuntu.com/community/X61T#Setup%20the%20Tablet%20Rotate%20Button]("https://help.ubuntu.com/community/X61T#Setup%20the%20Tablet%20Rotate%20Button"), and while I'm able to rotate the screen, I'm unable to rotate the orientation of the actual digitizer that records the location of the stylus, making me unable to move the mouse with my stylus while the screen is rotated.

When I type something in the termial like "autorotate" or "rotatenormal" the screen will rotate just fine, but it'll spit out an error saying that it "Cannot find device 'stylus'." I'm pretty sure this would be fixable if wacom-tools were installed, but unfortunately it won't install for my platform because it "Breaks existing package 'xserver-xorg-input-wacom' conflict: wacom-tools (<= 1:0.8.4.1-0ubuntu4)".

Can somebody help me out here?

---

### Post by jbiggs12 on 2010-04-25
...bump? It's been really disruptive and I might have to switch back to Windows if this keeps up... :(

---

### Post by Fraggy_the_undead on 2010-04-28
Have you had a look at the corresponding page of the [Thinkwiki(Link)]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_an_X61_Tablet")?

---

### Post by memckimmy on 2010-04-30
I'm having this problem too on my "new" x61. The Thinkwiki page is (currently) very inaccurate - my guess is that it hasn't been updated by anyone actually trying to make this work with the final version Lucid.

Any help would be greatly appreciated! Thanks!

---

### Post by jbiggs12 on 2010-04-30
Unfortunately, that doesn't help either. I've created all of those scripts, rebooted, but unfortunately whenever I rotate my computer into tablet mode nothing happens. Am I supposed to type a rotate command into a terminal or something??

---

### Post by dino99 on 2010-04-30
searching "wacom" into synaptic, there is xserver-xorg-input-wacom

si i guess its installed on your system and maybe need to be reconfigured:

sudo dpkg-reconfigure xserver-xorg-input-wacom

[http://www.uluga.ubuntuforums.org/showthread.php?t=1415676](http://www.uluga.ubuntuforums.org/showthread.php?t=1415676)

---

### Post by jbiggs12 on 2010-05-01
Still not rotating... I wonder if there's a way to install wacom-tools onto Lucid. Wouldn't that fix the problem?

---

### Post by Favux on 2010-05-01
Hi,

> I wonder if there's a way to install wacom-tools onto Lucid.
Not that I'm aware of.  The xsetwacom commands were rebuilt for xf86-input-wacom.  They are installed.  So what rotation script are you using?

What's happened is they are using a new naming convention.  Instead of stylus, eraser, and touch (if you have it) are longer more descriptive names.  So you need to change stylus to the new "Device Name" (with the quotes) in the script, etc.

To see the new names enter 'xinput --list' into a terminal.

---

### Post by jbiggs12 on 2010-05-01
I'll see if I can remember where I did it the first time... I undid it to do the mod that Fraggy suggested. p:

---

### Post by Favux on 2010-05-01
The [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") has scripts.  Method 1 scripts should work for you once you change the names.  Also Method 3's wacomrotate.

---

### Post by koukasio on 2010-05-04
Hi my friend,
here is what I did on my X61 tablet:

[LIST]
[*]I installed wacomrotate:[https://launchpad.net/~thjaeger/+archive/tabletpc](https://launchpad.net/~thjaeger/+archive/tabletpc)
[/LIST]

[LIST]
[*]Then, I am modifying the page of this guy: [https://help.ubuntu.com/community/X61T](https://help.ubuntu.com/community/X61T)
[/LIST]

First create a file to store the current rotation  data 

```
sudo gedit /usr/bin/rotationmode
```fill this file with: 

```
0
```and make it editable, but not executable 

```
sudo chmod 666 /usr/bin/rotationmode
```Now we will write the script to rotate the screen 

```
sudo gedit /usr/bin/rotatebutton
```And fill it with: 



```
mode=`cat /usr/bin/rotationmode`
if test 0 = $mode
then
echo 1 > /usr/bin/rotationmode
xrandr -o right
fi
if test 1 = $mode
then
echo 2 > /usr/bin/rotationmode
xrandr -o inverted
fi
if test 2 = $mode
then
echo 3 > /usr/bin/rotationmode
xrandr -o left
fi
if test 3 = $mode
then
echo 0 > /usr/bin/rotationmode
xrandr -o normal
fi
```
 
Make it executable: 
```
sudo chmod +x /usr/bin/rotatebutton
```
Now typing rotatebutton in terminal should  go through all of the rotations 
To  map the command to the button go to System>Preferences>Keyboard  Shortcuts, click the Add button at the bottom, name it whatever you want  and use the command rotatebutton. Then bind the key by  clicking in the shortcut column and pressing the tablet rotate key.

PS: I prefer only to have normal and inverted rotation in my button,
in which occasion you can modify the script to something like:

```

mode=`cat /usr/bin/rotationmode`
if test 0 = $mode
then
echo 1 > /usr/bin/rotationmode
xrandr -o inverted
fi
if test 1 = $mode
then
echo 0 > /usr/bin/rotationmode
xrandr -o normal
fi

```

Hope you'll be fine with that...

---

### Post by jbiggs12 on 2010-05-04
So you gave me the rotation script to rotate the screen, but does it rotate the orientation of the stylus along with it? Just making sure before I get started.

---

### Post by koukasio on 2010-05-08
You should install wacomrotate first, following the link I sent you above.That is exactly what I did on my x61 tablet... I can't imagine you will fail, since i am doing my job just the way i should... I did check for spelling mistakes, but my mini tutorial comes with no official warranty :)..

---

### Post by lifeflaw on 2010-05-09
Worked perfectly. Thanks.

---

### Post by jbiggs12 on 2010-05-10
Solved it! I appreciate your help. You'd think they'd publish this on the wiki or something... Oh well. At least it's on the internet now.

---

### Post by koostudios on 2010-05-10
Hi, most of the solutions to your problems appears on this wiki [https://help.ubuntu.com/community/X61T](https://help.ubuntu.com/community/X61T). I found it useful for 9.10. Perhaps other X61T users could update it for 10.04. I love my X61T and I've used that guide to get the most out of it.

---

### Post by ndiosque on 2012-04-08
hola... gracias por la solucion. 
yo tengo esta notebook, con ubuntu 11.10 instalado
hice tal y como explican y funciona bien en la orientacion "normal" e "invertida", todo bien incluso utilizando el stylus.

PROBLEMA:
Pero en las posiciones "rigth" y "left" rota la imagen pero el stylus funciona invertido, cuando voy arriba el cursor va abajo y asi con todas las direcciones.
lo mismo pasa con los botones Left, Right, Up, and Down Tablet Buttons 

Cual sera el problema?... que puedo hacer?...

Gracias!!!!

---

### Post by Favux on 2012-04-08
Hi ndiosque,

Both Natty (11.04) and Oneiric (11.10) have a bug in their version of xf86-input-wacom.  Portrait (right and left) orientations are reversed.  So cw and ccw in scripts have their meaning reversed.  Either swap cw and ccw in your script or update xf86-input-wacom.

The [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") part II. tells you how to update xf86-input-wacom.

---

### Post by ndiosque on 2012-06-19
Hola Favux,

Muchas gracias por la respuesta. voy a intentar hacer lo que me dices. aunq ahora ya actualice a 12.04 , voy a probar de nuevo los script (por q dejaron de andar en la actualizacion) y tu sugerencia a ver si funciona. despues escribo por aqui q pasa .

Saludos y Gracias de nuevo... :)

---

