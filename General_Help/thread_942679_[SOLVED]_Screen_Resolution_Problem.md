---
title: "[SOLVED] Screen Resolution Problem"
date: 2008-10-09
forum: General Help
---

### Post by DougieFresh4U on 2008-10-09
Well me being me, couldn't leave well enough alone.
I was going through screen resolution list and trying different sizes, well one of them certainly wasn't meant to be used on my machine as when I clicked apply screen came back with just background color and nothing else. I can not get nothing to come up .
I rebooted and Log in screen appeared as well as password screen. I can choose session and I can get the 'Fail Safe Terminal'
Can some one please provide a code or some thing I can use in the 'Fail Safe Terminal' so I can reset resolution to the one it should be?
I also have Live-CD but do not know how to repair using it. 
Hopefully the 'Fail safe Terminal' can fix it.
Thanks, and really need the help soon so I can get back project I was working on.

---

### Post by Legend28469 on 2008-10-09
May I ask what version of ubuntu you are using, and it seems to be that the problem is that your stuff is still there its just not visible... try setting to the biggest resolution and pulling them back together... also try, to right click on the ubuntu desktop and click i think its "clean or auto arrange or something" thats off the top of my head.. so i don't know...

what you can also try doing because this causes resolutions problems... is a proper shutdown.. i don't know about you but i don't have a shutdown button so if thats also your case then you can do this in Terminal

```

sudo halt -p

```

and put your password in ...:popcorn:

this will shutdown your computer... but.. either way.. let me know what version of linux you are using.. because i know .. sometimes i play around with my screen res and somethings stay off the screen.. and the screen doesn't scroll like its supposed to and i have to take a guess as to how to come back to it... i dont wanna get off topic... so.. maybe try getting the latest updates... could be a bug..

---

### Post by DougieFresh4U on 2008-10-09
> **Legend28469 said:**
> May I ask what version of ubuntu you are using, and it seems to be that the problem is that your stuff is still there its just not visible... try setting to the biggest resolution and pulling them back together... also try, to right click on the ubuntu desktop and click i think its "clean or auto arrange or something" thats off the top of my head.. so i don't know...

what you can also try doing because this causes resolutions problems... is a proper shutdown.. i don't know about you but i don't have a shutdown button so if thats also your case then you can do this in Terminal

```

sudo halt -p

```

and put your password in ...:popcorn:

this will shutdown your computer... but.. either way.. let me know what version of linux you are using.. because i know .. sometimes i play around with my screen res and somethings stay off the screen.. and the screen doesn't scroll like its supposed to and i have to take a guess as to how to come back to it... i dont wanna get off topic... so.. maybe try getting the latest updates... could be a bug..

Thanks
I am using Intrepid. I was trying different resolutions and most were working but the last one I tried is what messed it up. Also, can not even see cursor any where on screen. I have also gone into recovery mode and tried **'sudo dpkg-reconfigure xserver-org'** and it comes back with** xserver-org is not installed** what is up with that? Everything was working fine until I started changing screen resolutions.

---

### Post by DougieFresh4U on 2008-10-09
I gotta bump
PLEASE, some one help me get my desktop back :(

---

### Post by daahli on 2008-10-09
try entering the following and then rebooting:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by DougieFresh4U on 2008-10-09
> **daahli said:**
> try entering the following and then rebooting:

sudo dpkg-reconfigure -phigh xserver-xorg

Ran that in fail safe terminal, said some thing about possibly over writing. Re-booted and Log in screen came up, logged in and still get blank white screen, not even cursor shows up

---

### Post by DougieFresh4U on 2008-10-09
Please Help

---

