---
title: "hmm i have a question..dont really know how to explain it."
date: 2005-11-22
forum: General Help
---

### Post by SkillZero on 2005-11-22
[B]hi again , i seem to be a problematic user :P
ill try to explain myself the best i can.
so:

i am playing a game in linux , it's name is sof2.
now , to play it i have to do
"cd sof2"
"wine sof2mp.exe"

now , i want to make some file that will do this automatically when im double clickin on it.
(same as .bat file on windows)
thanks![/B]

---

### Post by Specialsauce on 2005-11-22
i would also like to know how to do this....

---

### Post by soulestream on 2005-11-22
its called a shell script

[linky]("http://www.freeos.com/guides/lsst/ch02sec01.html")

[linky2]("http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html")


soule

---

### Post by gapplewagen on 2005-11-22
[QUOTE=SkillZero][B]
i am playing a game in linux , it's name is sof2.
now , to play it i have to do
"cd sof2"
"wine sof2mp.exe"

now , i want to make some file that will do this automatically when im double clickin on it.
(same as .bat file on windows)
thanks![/B][/QUOTE]

You can create a launcher by right-clicking on the desktop and go to "Create Launcher".  Fill in Name as whatever you wanna call it and command is /path/to/wine /path/to/sof2mp.exe

---

### Post by SkillZero on 2005-11-23
the launcher doesnt work and the guides are SOOOOOO complicated

---

### Post by Pablo_Escobar on 2005-11-23
Go to notepad (gedit or kate or whatever).
Type in the stuff You type in terminar regularly (but remember to use the absolute paths f.e. cd /home/pablo/games/sof2   and not cd sof2)
F.e. in Your case: 
> cd **/home/pablo/games/**sof2
wine sof2mp.exe
Be wary that I don't know Your exact directory (in bold) so You have to change it Yourself.
Save the file f.e. at the desktop, filename is whatever.

Now 2 ways come in handy:
1. Right click the file, 3rd tab, enable the execute flag in owner group
or
2. open terminal, cd to the Desktop and type in
> chmod +x nameofthefileyoucreated

Now just doubleclick :) It'll bump out what to do with file, just select -> Run

VOILA :)

---

### Post by gapplewagen on 2005-11-23
[QUOTE=SkillZero]the launcher doesnt work and the guides are SOOOOOO complicated[/QUOTE]

What exactly did you input for the command for the launcher?

---

