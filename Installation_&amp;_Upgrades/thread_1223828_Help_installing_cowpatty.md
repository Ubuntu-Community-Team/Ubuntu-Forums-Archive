---
title: "Help installing cowpatty"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by skorea2131 on 2009-07-26
hi, i downloaded the cowpatty tar to "andrewo@andrewo-laptop:~/tools" and then i made the directory cowpatty-4.2 there... all the files are in there but i dont know how to run or install them... HELP!!!

---

### Post by redspider on 2009-07-26
open terminal type "make --help" 
make is your friend.

---

### Post by skorea2131 on 2009-08-04
That didn't help...

---

### Post by serejj on 2009-11-25
code # sudo apt-get install checkinstall -y

now when compiling cowpatty do this:

code # cd /cowpatty* 

code # make

code # sudo checkinstall "a window will open, just accept the defaults"

now you must have one cowpatty*.deb inside the paste cowpatty, so:

code # dpkg -i cowpatty*.deb

or you just can do this:D:

code # sudo gedit /etc/apt/sources.list

and add this line:
deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/

code # sudo apt-get update
"don't worry about the gpg key error"

code # sudo apt-get install cowpatty

give some feedback please

remember this: §erejj is your friend but google is your best friend

by §erejj

---

### Post by Johnny2good on 2009-11-25
or you just can do this:D:

code # sudo gedit /etc/apt/sources.list

and add this line:
deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/

code # sudo apt-get update
"don't worry about the gpg key error"

code # sudo apt-get install cowpatty

give some feedback please

-----------------------------------------------------------------------------------------------------
Hi [serejj]("http://ubuntuforums.org/member.php?u=494291") i did what you said and it went in Applications/Other/  now i can see Cowpatty when i open it i get >>>  
There was an error creating the child process for this terminal

Im new to Ubuntu but learning every day so if you can help me here with this would be nice. Thanx

---

### Post by serejj on 2010-01-14
hi dude...

in my system everything works fine...

post this console output:

code# sudo cowpatty
code# locate cowpatty
code# whereis cowpatty

by the way in my opinion it's better to compile from the source code but in that case you have to install kernel headers and the required development libs, try this:

code# sudo apt-get install checkinstall

and it will install most of the required packages. Then when you are compiling pay attention to the "make" output and install the required development libs.

a tip: for example you have a "libssl" error, so, go to synaptic and search for "libssl" and install the "libssl-dev" or in a console:

code# sudo apt-get install libssl-dev

i hope you're not confuse, but if so say something...or download the package that i compile for 32 bits. [http://sites.google.com/site/serejj/](http://sites.google.com/site/serejj/)

remember this: §erejj is your friend but google is your best friend

---

