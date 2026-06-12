---
title: "[SOLVED] Howto scroll the top command?"
date: 2008-10-26
forum: General Help
---

### Post by jmjohn on 2008-10-26
Hey all,

Using the top command, I can't figure out how to scroll down.  Obviously there are many processes, that I can re-order, but how can I scroll through them?

thanks much
glass.dimly

---

### Post by john.nicholls on 2008-10-27
You should be able to scroll using either the scroll bar on the right of the terminal or by using the middle mouse button.

---

### Post by crtlbreak on 2008-10-28
> **john.nicholls said:**
> You should be able to scroll using either the scroll bar on the right of the terminal or by using the middle mouse button.

naah - i tried both and neither did it

---

### Post by Sam on 2008-10-28
Try [htop](apt://htop)...

---

### Post by geirha on 2008-10-28
As far as I know you can't. If you need a list of all processes, use ps or have top run one iteration and exit
```
ps -ef
top -b -n 1

```

---

### Post by oldos2er on 2008-10-28
Don't know about top, but with htop you can use PageUp and PageDown, and the Up/Down arrow keys as well.

---

### Post by Titan8990 on 2008-10-28
The point of the TOP program is to tell you which processes are using the most resources or are at the TOP of the list.

> By default, the processes are ordered by percentage of CPU usage, with only the "top" CPU consumers shown.


If you want to see the full process list you should use ps. 


ps aux


Also, it is popular to pipe ps aux through grep:


ps aux | grep firefox


Hope this helps.

---

### Post by Portmanteaufu on 2008-10-28
If you're not interested in a lot of the behind-the-scenes activity being run by the system and only want to see the programs that you've run yourself, you can use the following: 

top -u <username>

which will produce a much shorter list than just 'top' by itself and eliminate the need to scroll. Of course, if you're trying to see background system processes, that's significantly less helpful.

---

### Post by jmjohn on 2008-10-29
Thanks all!

To summarize, top doesn't scroll, just lists the "top" processes.

But.. $ top -b -n 1 gives a static print out of the top command to the scrollable termnial,  ...$ htop is a slicker top program with colors and scrolling, and the $ ps -ef | grep "processname" searches all processes for "processname".


Marking it solved,
glass.dimly

---

