---
title: "Fatal error need help..."
date: 2008-11-21
forum: General Help
---

### Post by alpinesmu on 2008-11-21
I tried downloading mythtv and for some reason I get an error saying that it can't read line 54. I have no idea what this means. All I want to do is uninstall the program or reinstall ubuntu but I don't know how to do either. I'm a newb when it comes to linux. I just started using it 2 days ago so I still want to give it a try.

---

### Post by adult swim on 2008-11-21
how did you install mythtv?

---

### Post by alpinesmu on 2008-11-21
I used 
[http://mythtv.org/modules.php?name=Downloads&d_op=viewdownload&cid=1](http://mythtv.org/modules.php?name=Downloads&d_op=viewdownload&cid=1)
thats all I really know

---

### Post by alpinesmu on 2008-11-21
It was probably my fault, I didn't know what I was doing .. trial by error. I have no clue how to fix it though.

---

### Post by adult swim on 2008-11-21
did you ever run anything like ./configure, make, or make install?
can you currently use your ubuntu installation?

---

### Post by Kain000 on 2008-11-21
acording to the link you gave us, and when I click the main download link, the file you downloaded was a .tar arcive, which means that in order to install it you would first have to unpack, (extract. un-zip ect..) 
you would of done that either by downloading the file to some location... /user/home or whatever....

or by default you could of used the archive mannanger.     Now either way unless you un tared AND started building the program you shouldnt have changed anything.




can you tell me exactly what you did from the download?

and what do you do that give you the error?


until you use the commands

./configure

make
makeinstall

nothing has (or should have) been installed on your system.

---

### Post by alpinesmu on 2008-11-21
I used the config in the folder I downloaded and I can't use the add /remove section. I can use ubuntu for most things still but I can't add anything

---

### Post by alpinesmu on 2008-11-21
I can't really say much because I didn't even know how to install it until the next day but I did extract itand then I used the archive mannagee. I clicked on the option I thought I needed to install I read somewhere that it needed prerequisit files but I didn't dl anything else. Isn't there a way just to start ubuntu from scratch

---

### Post by adult swim on 2008-11-21
can you post the exact error you are getting?

---

### Post by Kain000 on 2008-11-21
> **alpinesmu said:**
> I used the config in the folder I downloaded and I can't use the add /remove section. I can use ubuntu for most things still but I can't add anything

ahh alright....


so let me get the story thus far.


you downloaded the archive,

have you extracted the archive or are you viewing the files with the archive mananger?



when you double clicked the configure "file" (it's really a shell script (command) that tells your system to start to build the myth tv program from the low-level programing language that people can understand into a language that the computer can understand, a process called compiling.)

so when you clicked the config script it would of prompted you to do one of four things.

1 run in terminal

2 display (text editor)

3 cancel

4 run



what one did you choose?

---

### Post by alpinesmu on 2008-11-21
I ran it in the terminal

---

### Post by alpinesmu on 2008-11-21
I'm not on my computer right now but it didn't give me a number error just that it could not read line 54 and to type in some stuff I'm the terminal but that didn't help it wouldn't give me permision.

---

### Post by Kain000 on 2008-11-21
alright and did you go and install all the programs listed in the read me text before you did that?    

if not your terminal should of started some sort of compile process where lots of words scroll by but stopped with an error because the listed programs werent installed.

basicly you did right by looking into the README file first as in linux unlike other os's you actually need to read them!!!  lol



alright so IF there wasnt an easier way to do this you would have to look in the README file and download form either the terminal
using the sudo apt-get install (name of program) command

or easier for the non-geek just use the synaptic software manager to search for and download them. 


then you would in the terminal 

cd (stands for change directory)   and type the path to the file where the configure script is


so cd/home/sean/Desktop/mythtv

and then ./configure

after it's all done right 


make    

make install

and finally 

make clean



*******************     HOWEVER    **************


there is a much easier way to install myth tv i just found out.......



go to system   >   admin   >   synatpic    

search for mythtv

look down the list for myth tv and click add  

this will add ALL THE PROGRAMS YOU WILL NEED automaticly.    there may be some extra plugins to find on your own, but they should also come up with the mythtv search.

PHEW sorry that was a bit long winded

hope this helps

let me know how it goes.

---

### Post by Kain000 on 2008-11-21
> **alpinesmu said:**
> I'm not on my computer right now but it didn't give me a number error just that it could not read line 54 and to type in some stuff I'm the terminal but that didn't help it wouldn't give me permision.



ohh and by the way, anything that needs permision it's wanting you to prove that you have the permission form the admin  (in this case you)  to install and or change important system things....


for that you will need to put  sudo  infront of the comand


so like 
```
sudo ./configure
```
it will ask for your admin password, (your logon password...... assumeing that you installed the system and set the passwords)

---

### Post by alpinesmu on 2008-11-21
thanks for the help I'll give it a try in the morning I'll let you know how it goes the only thing is I can't use the add section because I did this all wrong . I'll know to dead the read me files first next time more carefully

---

### Post by Kain000 on 2008-11-21
> **alpinesmu said:**
> thanks for the help I'll give it a try in the morning I'll let you know how it goes the only thing is I can't use the add section because I did this all wrong . I'll know to dead the read me files first next time more carefully

cool good luck.

---

### Post by alpinesmu on 2008-11-21
Hey I'm still having problems I read the read me files to install the required software but I can't get into the synaptic for some reason

---

### Post by alpinesmu on 2008-11-21
I get nothing when I type in
 sudo ./configure

---

### Post by adult swim on 2008-11-21
if you cant get into synaptic package manager it sounds like an update got interrupted.  go to a terminal and run ```
sudo dpkg --configure -a
``` then see if the synaptic package manager.  if it works, you dont need to compile mythtv, you can install it from there.

---

