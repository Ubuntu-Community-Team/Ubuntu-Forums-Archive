---
title: "Black screen after bootscreen"
date: 2014-05-04
forum: Hardware
---

### Post by wamgx on 2014-05-04
Hey everybody,

Another problem with Lubuntu, for no apparent reason, I have now a black screen when booting up (the GUI doesn't load apparently). Everything is fine until the blue lubuntu bootscreen with the dots, after that, nothing ...

I managed to go in the terminal with Ctrl + Alt + F1 and tried to launch a few applications:
```
paeschli-desktop login: paeschli
Password:
Last login: Sun May 4 13:57:34 CEST 2014 on tty4
Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.13.0-24-generic i686)

 * Documentation: https://help.ubuntu.com/

paeschli@paeschli-desktop:~$ libreoffice
Failed to open display
paeschli@paeschli-desktop:~$ leafpad
leafpad: Impossible d'ouvrir l'affichage :
paeschli@paeschli-desktop:~$ lxterminal

(lxterminal:1450): Gtk-WARNING **: cannot open display:
paeschli@paeschli-desktop:~$ 
```
I have a 19" TFT LCD Protek monitor with model number PT1901 (LM19T)

Can someone help me get the GUI back?

TIA

---

### Post by ajgreeny on 2014-05-04
What happens with command **startx** after logging in at the command line?  What hardware have you got, in particular the graphic card?

Command ```
sudo lshw -c display
``` will tell you if you don't know.

By the way you can not run any gui applications from the tty you get with Ctrl+Alt+F1/6;  there has to be a graphic display first and that is what's missing for you at the moment.

---

