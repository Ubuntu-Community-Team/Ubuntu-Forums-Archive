---
title: "[SOLVED] how do i create a link thats suppose to run with ./"
date: 2008-10-05
forum: General Help
---

### Post by bigdee973 on 2008-10-05
i have the game alien arena 2008...its in a folder and the way to run the game is by using the terminal and typing in ./crx,  the folder is in /usr/local/games and im getting sick of cd /usr/local/games/alienarena2008 and ./crx...everytime i try to create a link for crx and i double click the link i get nothing in response and if i try to create a launcher by giving it the command ./usr/local/games/alienarena2008/crx it doesnt do nothing neither..any ideas on how i can create a link for this CRX?

---

### Post by ad_267 on 2008-10-05
Don't put a . in front of your link. "." means the current directory. So the launcher should just run "/usr/local/games/alienarena2008/crx"

---

### Post by bigdee973 on 2008-10-05
> **ad_267 said:**
> Don't put a . in front of your link. "." means the current directory. So the launcher should just run "/usr/local/games/alienarena2008/crx"

i created a launcher with the command just like u told me and when i double click it it does nothing...:(

---

### Post by ad_267 on 2008-10-05
What happends if you go to a terminal (Applications - Accessories - Terminal) and then enter "/usr/local/games/alienarena2008/crx"

---

### Post by bigdee973 on 2008-10-05
> **ad_267 said:**
> What happends if you go to a terminal (Applications - Accessories - Terminal) and then enter "/usr/local/games/alienarena2008/crx"

i get this

~$ /usr/local/games/alienarena2008/crx
using /home/blankhead/.codered/data1/ for writing
using /home/blankhead/.codered/arena/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
recursive shutdown
Error: Couldn't load pics/colormap.pcx

---

### Post by cariboo on 2008-10-05
If your games has to run from a terminal you could create a script to keep from having to type the whole path. First open Applications-->Accessories-->Text Editor. Copy the script below, and paste it into gedit:

```
#!/bin/sh
# scritp to start alien arena 2008
/usr/local/games/alienarena2008/crx
```

Save the script as crx
close gedit, then in a terminal:

```
chmod +x crx
```

This will make the script executable. To run the script open a terminal and type:

```
./crx
```

Jim

---

### Post by ad_267 on 2008-10-05
> **bigdee973 said:**
> i get this

~$ /usr/local/games/alienarena2008/crx
using /home/blankhead/.codered/data1/ for writing
using /home/blankhead/.codered/arena/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
recursive shutdown
Error: Couldn't load pics/colormap.pcx


It sounds like it does need to be run from inside that directory then so the best thing to do would be create a script like cariboo907 said to run this and the script needs to change into the correct directory.

```
#!/bin/bash
cd /usr/local/games/alienarena2008/
./crx
```

Then make the script executable and you can use the script as the command to run for the launcher.

---

### Post by bigdee973 on 2008-10-06
> **ad_267 said:**
> It sounds like it does need to be run from inside that directory then so the best thing to do would be create a script like cariboo907 said to run this and the script needs to change into the correct directory.

```
#!/bin/bash
cd /usr/local/games/alienarena2008/
./crx
```

Then make the script executable and you can use the script as the command to run for the launcher.

THANKS MAN THATS EXTACTLY WHAT I DID AND IT WORKS GREAT. thank you guys for your help

---

### Post by vanwarantion on 2008-10-06
you can also create a link into /usr/bin/ to start it like any other program

to do that:
```
sudo ln -s /usr/local/games/alienarena2008/crx /usr/bin/crx
```
in terminal

---

