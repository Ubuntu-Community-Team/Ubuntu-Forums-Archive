---
title: "Status of my machine via web"
date: 2008-07-28
forum: General Help
---

### Post by Xi0N on 2008-07-28
I have a smalll computer with ubuntu linux on it and i usually use ssh to manage anything.
Is there any program that i could use to monitor the system's load, disk capacity.. etc etc? The point is that i need something that cna be checked via web.... i dont really know if there exists such thing
Thanks!

---

### Post by djxcon on 2008-07-28
Why not use ssh (since it is already set up) from the remote location and then run a few commands like top or df?

---

### Post by Xi0N on 2008-07-28
> **djxcon said:**
> Why not use ssh (since it is already set up) from the remote location and then run a few commands like top or df?

Im trying to avoid this commands, actually, In my job, unfortunately, i usually use windows....... Ok, i can use putty (is what i actually use) but i want to try something different and more user-friendly

---

### Post by djxcon on 2008-07-28
Gotcha...I also use Putty from remote locations.  I like where you are going with this request so hopefully someone will have additional suggestions.

---

### Post by Xi0N on 2008-07-28
> **djxcon said:**
> Gotcha...I also use Putty from remote locations.  I like where you are going with this request so hopefully someone will have additional suggestions.

Yes.. something similar to open manage web interface for dell systems.... something u can use remotely to see the different status of the system memory, disk space.... gateways status...... any problems that could appear.............  I hope i find something good soon :)

Edited: [http://www.nagios.org/](http://www.nagios.org/)
I will have a look on this one... but if anyone knows something different/better it would be appreciated :)

---

### Post by djxcon on 2008-07-28
Good find.  Please let us know how this works out for you.

---

### Post by Archmage on 2008-07-28
I know that there are a few programs that make a html-page of the status.

MythTV has this, but that might be a little too much... ;)

---

### Post by Xi0N on 2008-07-28
Nagis works fine, but allways gives error when checking the ssh status....... (Maybe because i changed the default port?) anyway........ this is not exactly what i was looking for... looks really professional and for handling a lot of servers on the same time, but i was looking for something more graphical even.. something that can be similar to htop and iftop and that can give me the status of the partitions and stuf flike that... but more graphically....... nagios looks too complicated.......

---

### Post by cariboo on 2008-07-28
If you are running apache you could install webmin, it will monitor what you need. Have a look here:

[http://www.webmin.com/](http://www.webmin.com/)

there is a howto here:

[http://ubuntuforums.org/showthread.php?t=7507](http://ubuntuforums.org/showthread.php?t=7507)

Jim

---

### Post by Xi0N on 2008-07-28
Thanks!

---

