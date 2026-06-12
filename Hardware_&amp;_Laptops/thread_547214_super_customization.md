---
title: "super customization"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by Eagleon on 2007-09-09
Ubuntu is my favourite distro for two reasons: 1) hardware compatibility and 2) the huge package repositiores. Well, there are many other reasons as well, but these two are the two biggest reasons. 

I know how to get most of what I want done through the shell, so the user-friendlyness is not of much use to me. So what I don't need much is the flashy stuff.

What I want to do is either (a) strip ubuntu of all the stuff I dont need (perhaps install the alternate-cd version, and build it up to my needs) or (b) get another distro that has similar harware compatibility or better but less stuff i will not use. Ive been looking at fluxbuntu for example, since this is somewhat what I wil do in choice (a)... but since I dont know so much about all the distro's out there... i was hoping someone could point me to a system with just as much compatibility as ubuntu and just as many packages.. but lighter. Id be more than happy with just a console and ill install fluxbox on it myself. 

I am a web programmer mostly, but one with very little patience. I need my system to be extra responsive. I wouldn't even mind using DSL-linux if it had the hardware support for my machine...

My primary programming machine is a Toshiba Portege M400 tablet. Does anyone know if there is a distro that completely supports this laptop? So far ubuntu has been the best from a few ive tried.. but even with ubuntu, my SD flash card reader, my tablet hot-key panel and finger-print stuff don't work. Also, the butt of the tablet pen works as a eraser in windows (on ms-paint), but in linux, it just writes just like the tip (only tried it on GIMP). 

Any help will be greatly appriciated...

Thank you in advance,
Antony

p.s. one more thing... I was wondering if anyone could help me understand the difference of compiling a linux distro on ur machine vs using the ISO's. Also, does this give you any boost in performance at all (even if it is very little), and how could I compile ubuntu or another linux distro if I wanted to. I want to customize everything in a way that the system has only what I need -- no unnecessary modules, dameons etc.. i tried google on this one as well, but no luck.. not sure what to search for. If someone could point me to some tutorials -- it would be great! thanks...

---

### Post by geraldm on 2007-09-09
There are so many other distros out there, each with some special objective.
The problem can be that the builder is set adrift from a community, so look for one that
has community.  Some that come to mind are based on Rock Linux, a fairly spartan distro.
[http://dl.exactcode.de/t2](http://dl.exactcode.de/t2) (rock)
[http://www.linuxfromscratch.org](http://www.linuxfromscratch.org) - builds system as distro, more of a learning exercise,  
No X, as that can be added later.  

Compiling a linux kernel is a simple process.  Know the hardware on the target computer.
Go through the complete option configuration answering the questions.
then make, and install the modules and the kernel.  Reboot.

I would suspect that the process would be an education, and that you would come away with
a renewed appreciation of the work that does go into Ubuntu.  Perhaps look into a Ubuntu
basic install, where only the needed programs are choosen, and let users add to the basic 
as they wish.  That way you would benefit from the Ubuntu work, while trimming your 
use to minimalistic.

Gerald

---

### Post by Eagleon on 2007-09-09
grealdm, thank you for your response! I really appriciate it. First, i must apologize if I sounded a little unapreciative of ubuntu -- quite the opposite. I have been a linux user for only a few months.. since Feb 2007 to be exact and ubuntu was my first real linux distro. ive used Red hat in the past, but i lost interest in that distro pretty quick. despite what people say about ubuntu not being the best distro if you want to learn about linux, i have learnt everything I know about linux thanks to ubuntu. In fact, i have learnt more about computers overall  thanks to ubuntu. I love ubuntu... but school is already here and I have a lot of programming to do. I need to run virtual machines that have windows (for visual studio and C++ and C#) while im running linux and so on, and im desperate for anything that will help my dual core run even faster than it already does. 

thank you a lot for the advice.. im really excited to try out the linux from scratch idea.. and also.. the basic install option (but I might go even further and attempt recompiling the kernel and whatever else an expert here could suggest me with ) :)

thanks again...

---

### Post by RedSquirrel on 2007-09-10
I can recommend the minimal install idea. Here are a couple of guides to help you with that:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

I use something similar to this and then build Fluxbox from the latest SVN code. ;)

---

### Post by Eagleon on 2007-09-13
thank you.. very helpful! :) i appriciate the help

---

