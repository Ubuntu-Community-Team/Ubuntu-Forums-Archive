---
title: "problems installing tkresolver"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by higashi on 2009-03-08
I heard about tkresolver and want to try it out. it sounds pretty kool and something that would be fun to play around with... so i tried installing it.,   the install.sh  didnt work, i get the error 

> me@my-desktop:~/Desktop/tkresolver-0.6.2$ '/home/me/Desktop/tkresolver-0.6.2/install-sh' 
/home/me/Desktop/tkresolver-0.6.2/install-sh: no input file specified.

so i tried installing it manually with the ./configure and make comands.  ./configure went well, but when i do the make command, i get 

>  make: *** No targets specified and no makefile found.  Stop.

in the directory, there are 2 makefiles: makefile.am and makefile.in ... dont know how to use these :\
help?

---

### Post by Partyboi2 on 2009-03-09
You probably got 
>  			 				 make: *** No targets specified and no makefile found.  Stop. 			 		
because ./configure did not finish. Run ./configure again and check the last few lines to see if there is any errors or missing packages.

---

