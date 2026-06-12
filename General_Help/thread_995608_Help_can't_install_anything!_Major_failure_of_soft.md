---
title: "Help can't install anything! Major failure of software management"
date: 2008-11-28
forum: General Help
---

### Post by 123456789mike on 2008-11-28
Well, this is only my second day with Ubuntu, but I am already having problems because of a stupid mistake ;(

Well, I tried installing Java yesterday, and it was going fine, I was doing this in Terminal. Then, It had went through a bunch of processes and it was at a blue screen in Terminal and it had Terms of use/agreement for Java.
At the bottom it said <ok> I tried clicking that and pressing enter, and nothing! So I exited Terminal...
Now, I can't install anything, I can't even go to Applications>add.remove without and error:
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I heard not to mess around with -f commands, so I tried the first one, it had all of the regular information with links etc, but at the end I get:

Fetched 126kB in 2s (52.1kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I don't quite know what to do. Well, thank you guys so much.

---

### Post by amauk on 2008-11-28
in the terminal, run
```
sudo dpkg --configure -a
```

---

### Post by adult swim on 2008-11-28
whenever you see the terminal turn blue and there are options at the bottom you can press tab to switch back and forth between options. press enter whenever you have the one highlighted that you want to choose.

---

### Post by 123456789mike on 2008-11-28
Hmm, thanks it says
     code:
Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 23 changed, 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up odbcinst1debian1 (2.2.11-16build2) ...

Setting up unixodbc (2.2.11-16build2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

can I exit now? Thanks!

---

### Post by adult swim on 2008-11-28
its safe to exit whenever it returns you to your prompt
username@computername:~$

---

### Post by 123456789mike on 2008-11-28
Even though I typed that code I still can't go to Add/Remove.
Should I try:
sudo apt-get update
then
sudo dpkg --configure -a
then
sudo apt-get install -f
? Thanks oh, and soemthing else strange is happening I can't type "C" or a capital c without hitting caps lock, nothing shows up unless I use caps ha. Well thanks, I really want to install a few things and I can't becasue of this software error ;(

---

### Post by adult swim on 2008-11-28
whats the error message that it says when you try add/remove
your best bet is to run sudo apt-get -f install and then sudo apt-get update
then see if it will work.

---

### Post by 123456789mike on 2008-11-28
During the install I got this message after the y/n question:
dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
But then it keeps on trying to install.. and then after it "finishes" it brings me to the blue screen again, I dont' want to close it out though, so what should I do this time?:
Operating System Distributor License for Java v1.1 (DLJ)                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618; 
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618; 
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618; 
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618; 
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618; 
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618; 
 &#9474;     form, any other machine readable materials including, but not         &#9618; 
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>      
Very strange... and I get the same error message form add/remove as before. Thanks.

---

### Post by adult swim on 2008-11-28
that is just the terms of service.  tab down and i think it will make ok turn red and then hit enter.  if you run sudo apt-get update does it return errors?

---

### Post by 123456789mike on 2008-11-28
YOU ARE GOD. Thank you so much, no errors... it finsihed the updating, well search or whatever, hehe. Thanks you so much! Now I know hit tab if there seems to be nothing to click ;)

Do you think anything can fix my problem with capital C, nothing shows up when I hit shift and "c"... hehe

---

### Post by adult swim on 2008-11-28
have you tried to use the other shift key, just for trouble shooting?  did you change anything in compiz lately?

---

### Post by 123456789mike on 2008-11-28
I have tried both shifts and both "c"s...
In compiz, I don't belive I have changed anything that would casue the C not to work...
The things I have set with shift+ a button are shift+control for water... shift+f9 for rain/f8 for wiper. and shift+leftclick(ing) for draw fire...

---

