---
title: "HELP! Domain"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by nSTER on 2007-06-06
I tried putting a static ip on my computer and now, the domain on my computer changed to @none, the computer is running slow and I am unable to do anything but change it through the console back to my domain but I do not know the commands.

---

### Post by pbw on 2007-06-06
edit /etc/hosts and /etc/hostname

---

### Post by nSTER on 2007-06-06
Works, Thank You. I also had to remove the static ip for it to completely work. But what i am wondering is why did the OS become slow, was It because it was in a infinite loop searching for the static ip? I was amazed to find out something this small could "kill" your computer.

---

### Post by depele on 2007-06-09
set up dns on the slow pc! and all your problems will be fixed!

---

### Post by Alan O'Regan on 2007-06-12
Hi

I set the domain name on my new feisty implementation (hoping to use the internet at work) and not the computer takes 20 seconds even to open a terminal window - the system monitor recons the PC is idle (6% CPU) but it still takes and age.

Naturally I removed the domain name again, but the system remains slow.  Even rendering a a page on a local server (my Ruby app) is also taking 20 seconds a pop.  Although 'pop' makes it sound quick. . . . . 

Will this edit of etc/host & etc/hostname work in this case?  Or is there something else I need to do?

---

