---
title: "OpenGL &amp; 3D acceleration"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by saygin on 2007-01-30
Hi, 
I have searched the forum but couldn't find the solution.

I have ubuntu edgy installed on my computer and transgaming cedega. And my graphics card is Nvidia GeForce 4 MX 4000. Nowadays, cedega doesn't open "warcraft III". I ran the test on it and it says there is no OpenGL and 3d acceleration on my graphic card. The funny part is it used to work well and it is the first time it fails on OpenGL and 3D acceleration Test. 

I installed nvidia driver again as it is told at [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29") 

it still fails on those tests. I don't know what to do. How can I configure my cards OpenGL and 3D Acceleration settings? please help.

(NOTE: I have beryl installed and it works well. I don't know if you will need this information.)

thanks.

---

### Post by K.Mandla on 2007-01-30
I can't help much with the Cedega side of the fence, but if you're running Beryl with all the flash, then you definitely have video acceleration running. 

Could something be broken within Cedega?

---

### Post by saygin on 2007-01-30
maybe cedega is broken. however, when I write "glxinfo | grep direct" in terminal, it says "direct rendering: No".
so, what can I do? do you have any other ideas?

---

### Post by dreadhead90 on 2007-02-03
i have the same problem! (although i have a nvidia 7600, and i have 3d acc, but no opengl, and when i run that comand, i also get "no")
please help us if you know anything :confused:

---

### Post by dreadhead90 on 2007-02-04
i "solved" my problem atleast..
are you running like Xgl at the same time? try if so log in with GNOME and try again..

hope you solve it..

---

### Post by TheOmegaMan on 2007-02-14
After playing around with a pile load of linux distro's (OpenSuse 10.2, Sabayon 3.26(official beryl distro based off of gentoo), Simply MEPIS 6.0 (based off of ubuntu and debian), ubuntu edgy/feisty, Freespire 1.0.13 (debian based)) I could only  get two distro's to give me all the 3d support which is Freespire and MEPIS but unfortunatly Freespire has a stupid click and run crap that makes it's very slow and usless. Synaptic or Adept or even emerge is such better tools to use and u can get synaptic for Freespire but I don't know I guess it was a little lack luster.

MEPIS is extreamly reliable and works with ubuntu repositories and the ATI or Nvidia installer in that distro is the best. Simple get into the config utility found under Control Center, System Administration and sorry but I can't remember the tool's name but there are two extra icons there one gives you access to the Nvidia driver tab and there you just check the box and click apply, it downloads the driver and does all the config for you. Restart X (ctrl-alt-backspace) and all is good with 3D Acceleration and OpenGL working in cedega and I have and ATI card, hell I even enabled composits and well I can say this, ther is a reason composits are not supported by ATI in linux... slooooooooowness. The only problem I had with MEPIS is that some of the apps are a little old and my girlfriend is using kubuntu edgy and I found that the newer versions have many more features over the old ones. 

Now many of you uber linux guys are probably thinking that "Why doesn't this guy just compile the latest code".... simple, every tme I do it I get a screen full of errors and the apps half works at best. I'm new to programing and don't get the whole dependencies and lib/source files needed to get things working properly. Sorry I'm no uber linux god but at least I'm not using windows and to me that should be enough to avoid the noob wrath of uber lords of linux.


Currently I'm using Kubuntu feisty and are still trying to get things going properly but at the moment I can only get OpenGL working properly which is also detected by cedega. I would really like to know what that mepis tool actually does to get 3D acceleration working.... bah GRRR pffft! Damn it I will figure this out.

Weird side note the strange thing about ubuntu/kubuntu is that following this wiki [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) is this. I follow the ubuntu way and opengl doesn't work. Now if the drivers are installed and working and I run the last command which is supposed to be used to undo what the instructions above had done "sudo apt-get install --reinstall libgl1-mesa" and I restart X again OpenGL works.... doesn't make sense I thought I'm supposed to use the mesa that the ATI driver provides but I guess not.

I know you are using nvidia but I'm not sure if this trick will work for you it worked for me and I'm using ATI so if I can do it, it might just work for you.


Anyway I've babled enough, let me know if this works

---

