---
title: "how to change path of www"
date: 2008-09-27
forum: General Help
---

### Post by Cool Surfer on 2008-09-27
How can I change path of /var/www folder?

I have 60gb windows partition free/
is it possible to make the default location of /var/www on that windows partition?

If not then how can I increase the space of /www

---

### Post by dcstar on 2008-09-28
> **Cool Surfer said:**
> How can I change path of /var/www folder?

I have 60gb windows partition free/
is it possible to make the default location of /var/www on that windows partition?

If not then how can I increase the space of /www

Firstly, what application is using /var/www ? That is what you want to change.

Secondly, these things usually require full Linux filesystem security and permission support, which Windows filesystems may not provide.

---

### Post by Cool Surfer on 2008-09-28
I have installed almost everything I came across, just remembering 15yrs back, when I used to install every windows toolbar, screen savers etc to try ... lol.

But now I am installing various control panels, forums/scripts on localhost.

So i need more space for /www

I have one hdd 160gb > 
three partitions, linux partition being 16gb.

---

### Post by bigbrovar on 2008-09-28
u could make the real www in the windows partition and symlinkt it to /var/www idk if it would work but sound like a good idea to me .

---

### Post by Cool Surfer on 2008-09-28
Ya if it works it will save me a lot of space, as i can use wamp server directory (in windows) for the localhost /wwww

Dont have to copy GB's of data into linux all over.

Can anyone tell me how to do it? Something like we do in windows by right clicking on my documents and changing its storage path.

---

### Post by Cool Surfer on 2008-09-30
any help on this simple question pl... 

:guitar::guitar::guitar:

---

### Post by Causer1984 on 2008-09-30
I may have misinterpreted the question, but as I understand it, you want to sym link your Windows www directory to /var/www.... Is that right?

Basically, if your Windows directory is mounted as , say, /media/sda1 , and in Windows, the www directory is somwhere like c:\www, you could sym link it by

```

$ sudo -s
# cd /var
# mv www /tmp
#ln -s /media/sda1/www www
CONTROL-D

```

I moved your current /var/www directory as I have a real phobia about deleting stuff ;) Also, there is certainly a more elegant way of doing this, but I thought I'd give you a flavour of my own idiosyncratic style :)

If your Windows partion isn't mounted on startup, then it might prove a little trickier.....

---

