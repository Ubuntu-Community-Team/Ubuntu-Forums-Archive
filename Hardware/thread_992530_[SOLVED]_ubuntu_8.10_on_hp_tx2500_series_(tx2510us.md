---
title: "[SOLVED] ubuntu 8.10 on hp tx2500 series (tx2510us)"
date: 2008-11-24
forum: Hardware
---

### Post by RodrigoRodrigues on 2008-11-24
I have a hp tx2510us tablet notebook, so far it can only run Vista...

I have tried to install 8.04 and it worked, I just didn't have time enough to find out how to install all drivers, the tutorial I followed had drivers for the touch screen and the tablet device but it didn't work for me... (it was for 2500)

I downloaded 8.10 and intalled, i had to disable acpi, as usual for tx series...

Running from the cd the installer runs normal after a long time trying to fix something in some device....

It install and reboot... but after that I can't boot from HD...

I edit the grub line and add "acpi=off" but it doesn't seems to care, it just doesn't work...

I verify the battery and keep trying to do something forever...

these are some related threads I found... can someone help me?

[http://ubuntuforums.org/showthread.php?t=792669](http://ubuntuforums.org/showthread.php?t=792669)
[http://ubuntuforums.org/showthread.php?t=987987&highlight=hp+tx2510](http://ubuntuforums.org/showthread.php?t=987987&highlight=hp+tx2510)
[http://ubuntuforums.org/showthread.php?t=845911&highlight=hp+tx2510](http://ubuntuforums.org/showthread.php?t=845911&highlight=hp+tx2510)
[http://ubuntuforums.org/showthread.php?t=972552&highlight=hp+tx2500](http://ubuntuforums.org/showthread.php?t=972552&highlight=hp+tx2500)
[http://backports.ubuntuforums.com/showthread.php?t=873188&page=2&](http://backports.ubuntuforums.com/showthread.php?t=873188&page=2&)
[http://ph.ubuntuforums.com/showthread.php?t=979236](http://ph.ubuntuforums.com/showthread.php?t=979236)

---

### Post by RodrigoRodrigues on 2008-11-24
Hmmmm

I tried "acpi=Off" with 'O' insted of 'o'
and the x kind of started...

I can see the busy cursor and it crashes...
the caps lock led starts to blink...

---

### Post by RodrigoRodrigues on 2008-11-24
It worked...

I had to use "nolapic acpi=Off"

I have no ideia of what nolapic means, but it solve the problem...

Some drivers are not working, but I belive now it's easy to solve

---

### Post by Bucky Ball on 2008-11-24
Well done! You fixed your problem. I sometimes find talking about it helps ...

Could you mark the thread as 'solved' from the Thread Tools menu, please. Then others with the same problems might get some help here. :)

---

### Post by RodrigoRodrigues on 2008-11-25
Done, it is marked...

If someone is having problems with audio in this model, follow the links in the first post, the solution linked there...

---

### Post by empty pockets on 2008-12-03
Actually, in 8.10 it is no longer needed to add the acpi=off tag.  I installed 8.10 on my TX 25xx and it went just fine without any modifications.  Until it came to connecting to wireless networks that is.

---

