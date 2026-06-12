---
title: "Laptop waiting time! grrrrr!"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by Thumper! on 2007-12-16
Right having a little trouble with ubuntu  on my laptop!

Ok, first i will post up specs that System monitor gives me -

Software -
OS - Ubuntu 7.10 (Gusty)
Linux Kernel - 2.6.22-14-generic
Gnome version - 2.20.1

Hardware -
Memory - 471.5 MB 
Processor - Intel Pentium 4 2.00GHz

Laptop -
Compaq Presario 1500


As this is not my laptop, i do not know any more, sorry guys.
Right now to the problem -

When i start the laptop up, it will start normally then after the Ubuntu logo a black screen comes up (normal) but the abnormal part is that it stays like that for about 2 minuets?? 

Don't know if this is normal but my older, less powerful DESKTOP pc don't have this problem.

Any help would be gratefully received :KS

Thanks, Tom

---

### Post by dasunst3r on 2007-12-16
Your hardware looks pretty decent, but what graphics card do you have?

---

### Post by Thumper! on 2007-12-17
any idea where i could find it out? it's not in system monitor... 

Like i say, tis isn't really my laptop, i'v got a bloody quad core, 3GB RAM, Nvidia 8600 beast stareing right at me under the christmas tree lol

---

### Post by Craigus on 2007-12-17
[http://ubuntuforums.org/showthread.php?t=581075]("http://ubuntuforums.org/showthread.php?t=581075")

---

### Post by fvds on 2007-12-17
I had something similar. It appeared to be fsck not being able to check a volume. Perhaps browsing the /var/log/messages file will shed a light.

In my case I had to change a line in the /etc/fstab file..

---

