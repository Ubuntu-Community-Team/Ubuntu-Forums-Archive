---
title: "Fans not working after ubuntu 8.04 install"
date: 2008-09-18
forum: Hardware
---

### Post by fondupot on 2008-09-18
Hi im a relatively new user to ubuntu, so forgive me of any ignorance.

I have installed Ubuntu on my Dell Inspiron e1705, for a change of pace from windows xp. Installed fine and everything runs great, except for my system fans. 

When i use my laptop for an extended period of time it gets really hot, this is when i noticed the fans were not coming on. So i immediately shut down my system. I have a fan pad that i use when my laptop is in on my desk, but if i take my laptop to class, i dont wanna haul that thing with. So i need to figure out how to get the system fans working again.

Any suggestions. Thanks a lot.

Some more info about my laptop

Dell Inspiron E1705
2gb dual channel ram
Intel Core duo processor or might be intel core 2 duo, cant remember on the top of my head. 

160gb hard drive, (partioned half/half for windows xp and ubuntu.)

---

### Post by G-Dub on 2008-09-18
You can try updating your BIOS. That tends to fix quirky problems like that. Just an idea, i'm not really sure what the problem would be.

---

### Post by handaxe on 2008-09-18
As G-dub wrote, a bios upgrade might do it, but maybe not.

See if i8k-utils is installed and if not, if it can help. Although old and another model see if [http//ubuntuforums.org/showthread.php?t=396018]("http://ubuntuforums.org/http//ubuntuforums.org/showthread.php?t=396018") and [http//ubuntuforums.org/showthread.php?t=877611]("http://ubuntuforums.org/http//ubuntuforums.org/showthread.php?t=877611")  help.

The above refers to [http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)

HA

---

### Post by fondupot on 2008-09-18
both those links do not work....

---

### Post by fondupot on 2008-09-18
and im 99 % sure that the bios is updated to its latest.

---

### Post by NoWayBill on 2008-09-18
The http has been doubled in them.
Let the page fail then delete one of the http's in the addy to make a proper address.

---

### Post by fondupot on 2008-09-18
ok saw that, when i take the http out it just brings me to a google search.... so yea.

on the third link there i downloaded the dellfand .9, but how do i install it? i have the file extracted to the desktop and theres a bunch of files inside, but i dunno which installs.

on the page i downloaded it from, it says i have to:

Build with

    cd dellfand-0.9; make 


thats the exact phrase...what does that mean?

---

### Post by fondupot on 2008-09-18
ok i installed i8k-utils instead, i found it on another site.

how do i access the program once installed tho?

---

### Post by handaxe on 2008-09-19
[http://ubuntuforums.org/showthread.php?t=877611](http://ubuntuforums.org/showthread.php?t=877611)

[http://ubuntuforums.org/showthread.php?t=396018](http://ubuntuforums.org/showthread.php?t=396018)

Both these links provide guidance. Dunno why they crapped out like that.  Copy paste the above if need be but they work for me (now :-))

To compile, you need to install via synaptic / apt-get the package "build-essential".

Also, why did you install i8k-utils from another site? It too is available in synaptic etc, as long as the universe repository is enabled.  Ie. in Synaptic, go to settings -> repositories and select the universe tick box.

HA

---

