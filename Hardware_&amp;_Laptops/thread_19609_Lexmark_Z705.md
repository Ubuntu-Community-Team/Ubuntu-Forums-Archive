---
title: "Lexmark Z705"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by occy8 on 2005-03-12
Hello,
has anyone got a driver for the Z705 or know how to configure it?
I'm using Hoary. The printer is recognised as Z705 but I can not select it on the list.
it only has Z11, and some other low numbers.

cheers

---

### Post by occy8 on 2005-03-14
hello
I found something myself, but I need help!!!

can anybody tell me how I can use or convert the stuff from here:
[http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)

thanks

---

### Post by bored2k on 2005-03-14
[QUOTE=occy8]hello
I found something myself, but I need help!!!

can anybody tell me how I can use or convert the stuff from here:
[http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)

thanks[/QUOTE]
 Its not 100% it might work , but grab the requirements needed [mostly on synaptic] and build-essential, download the source .rpm they have there.

in a terminal 
alien -d filename.rpm

after that is done
dpkg -i filename.deb

if it needs some dependencies it should tell, then you can search them up in synaptic.

You can compile wich is more secure but it is harder -a lot harder-.

---

### Post by occy8 on 2005-03-14
hi thanks,
another problem - I'm still not on the internet with hoary. working on it too
so I have to get those files through windows.
do I need just those 4 or lots more because of dependencies and what are they exactly called, maybe I should wait ?

---

### Post by bored2k on 2005-03-14
[QUOTE=occy8]hi thanks,
another problem - I'm still not on the internet with hoary. working on it too
so I have to get those files through windows.
do I need just those 4 or lots more because of dependencies and what are they exactly called, maybe I should wait ?[/QUOTE]

bored@noir:~$ apt-cache search enscript
enscript - Converts ASCII text to Postscript, HTML, RTF or Pretty-Print

-didnt find magic on apt

-cups u should already have it

-kernel i imagine they mean kernel headers
for this u download headers of the kernel your hoary is on 


I have hoary PRE and my kernel is  2.6.10-4-686 [i upgraded to 686, default should be  2.6.10-4-386] I think.


I think that should do it

p.s. I dont know the deal with internet connection and hoary for some of you. Luckily i have a static ip so its manual and it never fails :D

---

### Post by occy8 on 2005-03-14
Thanks again 
I have Hoary pre too and a D-link DSL200 ](*,)  and a long thread at eciadsl and I'm waiting for a day to get a call back from my ISP
But I'm sure I get through, in the next few days.

cheers

---

### Post by bored2k on 2005-03-14
[QUOTE=occy8]Thanks again 
I have Hoary pre too and a D-link DSL200 ](*,)  and a long thread at eciadsl and I'm waiting for a day to get a call back from my ISP
But I'm sure I get through, in the next few days.

cheers[/QUOTE]
 [D-Link DSL-200 Rev B DSL modem -- success!!](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=250110&highlight=DSL00)
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=203560&highlight=DSL00](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=203560&highlight=DSL00)

Good luck [be sure to get build-essential before that ]


[http://home.pacific.net.au/~twhitema/linux_adsl.html](http://home.pacific.net.au/~twhitema/linux_adsl.html) < not that useful


edit - when did this became a router thread :P . internet is more important than printing IMHO.

---

### Post by occy8 on 2005-03-14
I tried all that connected o.k. but don't get a response to ping
my thread at eciadsl if you are interested
[http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=2819&sid=1eed8928a6afb191693a3bb260f31e37](http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=2819&sid=1eed8928a6afb191693a3bb260f31e37)
or I started one here as well, but htought its more a eciadsl problem, now it looks like a ISP config problem [http://ubuntuforums.org/showthread.php?t=19241](http://ubuntuforums.org/showthread.php?t=19241)

---

### Post by bored2k on 2005-03-14
[QUOTE=occy8]I tried all that connected o.k. but don't get a response to ping
my thread at eciadsl if you are interested
[http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=2819&sid=1eed8928a6afb191693a3bb260f31e37](http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=2819&sid=1eed8928a6afb191693a3bb260f31e37)
or I started one here as well, but htought its more a eciadsl problem, now it looks like a ISP config problem [http://ubuntuforums.org/showthread.php?t=19241](http://ubuntuforums.org/showthread.php?t=19241)[/QUOTE]
 Oh so its a hard one ... weird that developer hasnt found a solution.

---

### Post by occy8 on 2005-03-14
SUCCESS

I got the following files
z700llpddk-2.0-1.i386.rpm
lexmark-z700-cups-driver-1.1.1-1.i586.rpm

from this site

[http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)

this file
enscript_1.6.4-6_i386.deb

Cups is already in Hoary

and the other file " magic " I was told not to worry about which I did
converted the rpm's with alien
installed it rebooted ( don't know if that was neccessary) and selected the new printer
I don't use the colour so only checked black and white but its perfect

So if you guys from Ubuntu want to add this in somewhere I think its worth iy because it supports a lot of Lexmark printers

---

### Post by starNIX on 2005-08-04
This worked flawlessly for me.

[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

---

