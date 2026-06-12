---
title: "Wine!!!!!"
date: 2008-08-25
forum: General Help
---

### Post by claymater on 2008-08-25
AHHH! Ok for some reason, WHATEVER I TRY, wine won't Open ANY program I throw at it! 

does anyone know why?!

---

### Post by Rhapsody on 2008-08-25
What applications are you trying, and how are you trying to open them?

---

### Post by Crafty Kisses on 2008-08-25
Depends on what programs, see a list of supported programs at < [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by insane_alien on 2008-08-25
psst! its because your meant to double click them, not throw them. not many people know that.

---

### Post by claymater on 2008-08-25
Well it is "[game maker]("http://www.yoyogames.com/gamemaker/")", I need to teach a class on game making (easy game making..) and I "need" that program. And I have installed it (using wine) and im opening it by going to "apps/wine/programs/Gamemaker7 and then clicking the "game maker exe file..

---

### Post by claymater on 2008-08-25
Any help?

---

### Post by claymater on 2008-08-26
Is there a reason everyone stoped posting? 


(sorry for triple posting.. but yea)

---

### Post by phidia on 2008-08-26
You might want to look at the winehq [documentation page]("http://www.winehq.org/site/documentation").

---

### Post by bankg3 on 2008-08-26
> **claymater said:**
> Well it is "[game maker]("http://www.yoyogames.com/gamemaker/")", I need to teach a class on game making (easy game making..) and I "need" that program. And I have installed it (using wine) and im opening it by going to "apps/wine/programs/Gamemaker7 and then clicking the "game maker exe file..

Run the program in Terminal and post the output you get.  If you don't know where the program is stored it is in your home directory under the .wine/ then drive_c and Program\ Files/
```
cd ~/.wine/drive_c/Program\ Files/
```
find the program you are looking for then run
```
wine (program name).exe
```
let us know what it says

---

### Post by bpl07 on 2008-08-26
Works fine on my system.  You probably have the default ubuntu version of wine installed (0.9.59).  You should get the [most recent version of wine]("http://www.winehq.org/site/download-deb") (1.1.3) and try again.  Run things in terminal so you can see if/when errors occur.

You might also try checking the [wine appdb]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2965") for help on installing your programs.

---

### Post by claymater on 2008-08-26
> **bankg3 said:**
> Run the program in Terminal and post the output you get.  If you don't know where the program is stored it is in your home directory under the .wine/ then drive_c and Program\ Files/
```
cd ~/.wine/drive_c/Program\ Files/
```
find the program you are looking for then run
```
wine (program name).exe
```
let us know what it says

Uhm.. well first, if my directory is 

/home/home/.wine/drive_c/Program Files/Gamer_Maker7


Where do I put that? (Im a BIG noob...) 


Thanks

---

### Post by bpl07 on 2008-08-26
Applications > Accessories > Terminal

---

### Post by claymater on 2008-08-26
> **bpl07 said:**
> Applications > Accessories > Terminal

? I know how to open to terminal.. im saying in the code you gave me, were do you want me to put that directory.

---

### Post by bpl07 on 2008-08-26
This is the exact command to run:

> wine ~/.wine/drive_c/Program\ Files/Game_Maker7/Game_Maker.exe

---

### Post by claymater on 2008-08-26
> **bpl07 said:**
> This is the exact command to run:
```

home@Ubuntu-desktop:~$ wine ~/.wine/drive_c/Program\ Files/Game_Maker7/Game_Maker.exe 
wine: cannot find '/home/home/.wine/drive_c/Program Files/Game_Maker7/Game_Maker.exe'
home@Ubuntu-desktop:~$ 

```

Thats what I get..

---

### Post by Rumpty on 2008-08-26
> **claymater said:**
> ```

home@Ubuntu-desktop:~$ wine ~/.wine/drive_c/Program\ Files/Game_Maker7/Game_Maker.exe 
wine: cannot find '/home/home/.wine/drive_c/Program Files/Game_Maker7/Game_Maker.exe'
home@Ubuntu-desktop:~$ 

```

Thats what I get..

Why does /home appear twice? Is that normal for your setup?

---

### Post by claymater on 2008-08-26
> **Rumpty said:**
> Why does /home appear twice? Is that normal for your setup?

Yea, its because my username is "home".. but here is a screen shot of it...

[IMG]http://i183.photobucket.com/albums/x23/coenat/Screenshot-2.png[/IMG]

---

