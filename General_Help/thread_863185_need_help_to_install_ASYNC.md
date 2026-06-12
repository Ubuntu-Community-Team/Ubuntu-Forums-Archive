---
title: "need help to install ASYNC"
date: 2008-07-18
forum: General Help
---

### Post by luxubuabac on 2008-07-18
hi all, i just started with Ubuntu .. so just consider im a newbie. Here is my problem:
I'm currently working on my project which is related to programming in Linux and GPS devices. I downloaded ASYNC packet (coz i need to use it to get the info from GPS device) but I dunno how to install or make use of it >"< ... 
i tried to install gcc by "sudo apt-get install gcc build-assential" ... but when i use "gcc async_1_23.c" ... it showed up errors like:
undefined reference to 'floor'
undefined reference to 'sqrt' 
etc
PLEASE help me out .... T_T:confused:

---

### Post by alxlabs on 2008-07-18
Most likely you are missing some includes, i.e. sqrt requires #include <math.h> etc..

---

### Post by Taxman415a on 2008-07-18
Repeat after me, google is my friend. :) I'm not a programmer, but after a minute with google and your error message I found a link to this:
[http://c-faq.com/fp/libm.html](http://c-faq.com/fp/libm.html)
Now if I were you I'd do some more reading on linking and compiling on Linux, but that's just me.

---

### Post by luxubuabac on 2008-07-18
i checked the source code ... there is no missing of include libraries ...
T_T ...
the source code file i downloaded from 
[http://artico.lma.fi.upm.es/numerico/miembros/antonio/pd/](http://artico.lma.fi.upm.es/numerico/miembros/antonio/pd/)

---

### Post by luxubuabac on 2008-07-18
thx Taxman ... as i mentioned ... i just started with Linux ... 
so i dun really noe anything about programming in linux ... T_T
n yet my problem is still unsolved

---

### Post by luxubuabac on 2008-07-18
.... T_T .. no1 can really help me ??? 
i dunno wat to do with my project if i cannot install ASYNC .. T_T

---

### Post by Taxman415a on 2008-07-18
Ok, I downloaded the file from the link you sent and indeed the instructions I linked solve the problem. Make sure to read the whole thing.

There's nothing wrong with being new, but knowing how to look for what you want will save you lots of headaches. Spending some time upfront compiling some resources and reading them will help too. That way you will know about programming on linux.

---

