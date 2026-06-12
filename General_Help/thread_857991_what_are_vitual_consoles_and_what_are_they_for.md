---
title: "what are vitual consoles? and what are they for?"
date: 2008-07-13
forum: General Help
---

### Post by boblemur on 2008-07-13
they all, i was wonderin what virtual consoles are....

as in ctrl + alt + f1 - f12 (useing ctrl + alt + f7 to get back to normal)

my questions:

1) what are virtual consoles
2) why are some of them system logs?
3) why is 7 my normal gnome one?
4) what use are they??
5) can i have diffrent X11 sessions running on them and different things?
6) any other info or a link to any other info would be nice :)


thanks in advance

---

### Post by p_quarles on 2008-07-13
> **boblemur said:**
> 1) what are virtual consoles
They are the basic interface that each user logs into on a UNIX or Linux system.
> 2) why are some of them system logs?
They might show these, but they are not the logs themselves. 
> 3) why is 7 my normal gnome one?
Because that's what Debian and Ubuntu use as the default tty for the X session. 
> 4) what use are they??
They allow you to create more than one user session on the same computer.
> 5) can i have diffrent X11 sessions running on them and different things?
Yes. 
> 6) any other info or a link to any other info would be nice :)
Not sure what else there is to know, actually.

---

### Post by coffeecat on 2008-07-13
> **boblemur said:**
> 4) what use are they??

One use:

Sometimes (rarely) you get a freeze-up on your desktop, or an application goes out of control such that the GUI becomes unresponsive. So long as the system is still detecting your keyboard you can Ctrl-Alt-Fx into a virtual console and 'top' to see what's going on and then kill rogue processes. As a last resort you can 'shutdown -h now' or 'shutdown -r now' to do a clean shutdown or reboot.

---

### Post by boblemur on 2008-07-13
ok thanks :) how can i start  an X11 session on one of them using ssh...

i got as far as setting up ssh on my test box ( the one i wana connect to)

and then i went to the other window like ctrl + alt + 2 and i wanted to start a gnome session... but i need an x session first?? because gnome says cannot find display...

---

### Post by p_quarles on 2008-07-13
> **boblemur said:**
> ok thanks :) how can i start  an X11 session on one of them using ssh...

i got as far as setting up ssh on my test box ( the one i wana connect to)

and then i went to the other window like ctrl + alt + 2 and i wanted to start a gnome session... but i need an x session first?? because gnome says cannot find display...
[http://ubuntuforums.org/showthread.php?t=858024](http://ubuntuforums.org/showthread.php?t=858024)

---

