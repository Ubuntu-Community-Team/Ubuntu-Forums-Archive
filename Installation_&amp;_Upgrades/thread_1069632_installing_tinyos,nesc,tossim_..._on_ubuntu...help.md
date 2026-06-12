---
title: "installing tinyos,nesc,tossim ... on ubuntu...help !!!"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by Dalal on 2009-02-14
Hello everybody
I NEED to work with tinyos  from a week and i got confused because of all different sites found 
 infact i do not have any prior known about  ubuntu  too
So i need help  to install tinyos   in the simplest way 
And if i can install tinyos graphically please give me the steps or a site talking about that .
For known we have downloaded  the tinyos 1.1.0  (we downloaded  three packeges with names :
tinyos-1.1.0.tar
tinyos-contrib-1.1.0.tar
task-tinydb-1.1.0.tar
)
And ubunto we have is ubuntu 8.10
Please if any body want to help me i will be very thankful
and  if u like to contact me by email this is it
fire_sprite092(at)yahoo (dot)com


sorry ,
but if anybody suggest to work with a newer version of tinyos please told me  how to download it and install it in my ubuntu  


REGARDS.

---

### Post by Partyboi2 on 2009-02-15
Easiest way to install it would be to add a 3rd party repo and install it using apt.
[http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html](http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html)

If you get stuck at any stage post the part where you are stuck :)

---

### Post by Dalal on 2009-02-15
thanks for reply 

in fact i have downloaded the rpm packeges from  somesite for tinyos 

but when i wanted to install them by rpm  
it said that the rpm packege itself not installed so where to get it from  
by the way i can not enter the net from within linux yet
 so I am working on windows xp to get packeges could that work ?

if not please give me a thread name of how to connect my linux to  a windows lan  for internet connection

Thanks for help ...again 


REGARDS

---

### Post by Partyboi2 on 2009-02-15
Ubuntu is debian based therefore you will need to find a deb package to install not a .rpm. If you go [[COLOR=Blue]here[/COLOR]]("http://tinyos.stanford.edu/tinyos/dists/ubuntu/pool/main/t/tinyos-2.1.0/") you can download the deb file. Once you have copied it over to your ubuntu installation you can install it by double clicking on it.
Then go [[COLOR=Blue]here [/COLOR]]("http://packages.ubuntu.com/intrepid/python-dev")and download python-dev package and copy it also over to your ubuntu machine and double click to install.

---

### Post by Dalal on 2009-02-15
i have read that i can convert an rpm into .deb file using alien package and i think i have installed it 
successfully so could i do that or what u suggest 


i tried to install the .deb file u  gave it but after a while the package installer pppear with red error 
[COLOR="Red"]
Error: Dependency is not satisfiable:tinyos is required [/COLOR]

i want to ask about jdk1.5 also ...please 
where to find it or if any body can send it to me by email:lol:

thanks .

---

### Post by ugm6hr on 2009-02-15
Are you online with Ubuntu?

If yes - follow the advice here [http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html](http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html) as suggested.

If you are not online, you will have to manually find all the relevant files  / dependencies.

---

### Post by Partyboi2 on 2009-02-15
> **Dalal said:**
> i have read that i can convert an rpm into .deb file using alien package and i think i have installed it 
successfully so could i do that or what u suggest 


i tried to install the .deb file u  gave it but after a while the package installer pppear with red error 
[COLOR=Red]
Error: Dependency is not satisfiable:tinyos is required [/COLOR]

i want to ask about jdk1.5 also ...please 
where to find it or if any body can send it to me by email:lol:

thanks .
You can go [[COLOR=Blue]here[/COLOR]]("http://tinyos.stanford.edu/tinyos/dists/ubuntu/pool/main/t/") and download the "tinyos-required" deb package. 

You can go [[COLOR=Blue]here[/COLOR]]("http://java.sun.com/javase/downloads/index_jdk5.jsp") to download java. Or you can install the deb from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/intrepid/sun-java5-jdk")

---

### Post by Dalal on 2009-02-16
thanks a lot everybody:)

i have add the new repository to my sources.list file and then  i typed

sudo apt-get install tinyos ...

it began to install every thing wanted for tinyos
and at last it writed 
*See attachment below*

and after that it went back to the shell prompt
 
so does  this mean that everything is done well  or what ?:confused:

IF IT IS OK  

how to add lines to the /.bashrc file by using terminal or what ?
because it is not saving the file after modifing it  .....

they said : i must do this  to add the environment variables at every startup 

 



thanks for help i really appreciate that .

---

### Post by ugm6hr on 2009-02-16
> **Dalal said:**
> and after that it went back to the shell prompt
 
so does  this mean that everything is done well  or what ?:confused
If it completed without errors - then yes - it has installed successfully.

```
how to add lines to the /.bashrc file by using terminal or what ?
because it is not saving the file after modifing it  .....
```

Try:
```
sudo cp /.bashrc /.bashrc.bkp
gksudo gedit /.bashrc
```

---

### Post by Dalal on 2009-02-16
> **ugm6hr said:**
> Are you online with Ubuntu?

If yes - follow the advice here [http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html](http://pjpramod.blogspot.com/2009/01/installing-tinyos-2x-in-ubuntu-intrepid.html) as suggested.

If you are not online, you will have to manually find all the relevant files  / dependencies.


thank u  the file u gave was very helpful and it confirm everything

but i use

 sudo gedit 


just to modify the file called  bash.bashrc 
do i need to modify any other .bashrc file  

or i need to initiate a new file and edit it ...?

i tried to compile the first example  in tinyos (Blink)and it did it successfully 
so what is the meaning of 

~/.bashrc  wrote ?





REGARDS ...REGARDS

---

### Post by ugm6hr on 2009-02-16
> **Dalal said:**
> thank u  the file u gave was very helpful and it confirm everything

Thanks are due to Partyboi2 who initially suggested it :)

---

### Post by Dalal on 2009-02-19
> **ugm6hr said:**
> Thanks are due to Partyboi2 who initially suggested it :)

oh! ;)sorry for this mistake  partyboi2 .THANKS ,I  appreciate your help . 


but infact this happened because i was online with windows xp(internet explorer) at first  and the link  give me a url  request error 
so i discarded it.
 
but the next time i  was online with ubuntu and i clicked the link ugm6hr gave and it opened ,

so i did not realize that this is the same link :o

 are there pages specific to linux or to firefox  or what happened here ? i have no prior idea about this:oops:

---

### Post by Partyboi2 on 2009-02-19
That is ok :p

---

### Post by Dalal on 2009-02-24
Hi...

I want to ask if u have work with tinyos before 
because me and my friend (year project group)
were thinking about using tinyviz with tossim in tinyos but:mad:

it seem as i found in many threads through the net that tinyviz don't work with the tinyos version 2.x 
it just work with 1.x so  can u please tell me where to find a repository for the .deb files for the version 1.x  

or if u have any helpful information  about tinyos generally ...please help
and really I appreciate your work .
thanks in advance .

REGARDS.

---

