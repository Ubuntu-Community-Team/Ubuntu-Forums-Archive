---
title: "Scrambled video with OpenGL and ATI X1250"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by Vlafdi on 2008-02-28
SOLVED - kind of. New FGLRX -driver release fixed the problem so it isn't relevant anymore.

I have a HP 6715s Laptop with an integrated ATI X1250, Kubuntu 7.10 and the latest Catalyst drivers. The latest Catalyst drivers fixed hardlocking when switching tty:s and with a few workarounds I have also managed to fix hardlocking when logging out and disabling atieventsd now allows me to even do a X restart.

However, Xv obviously still doesn't work. With previous drivers I could watch videos using gl2 video output with only minor annoyances like a diagonal line sometimes seen on the screen. Unfortunately, the latest driver update caused another problem: when using Opengl the video output is scrambled like so:

[http://imageupload.com/~imageupl/show.php/78675_problem.jpg.html]("http://imageupload.com/~imageupl/show.php/78675_problem.jpg.html")

Cycling between full screen ja windowed mode eventually shows the video correctly but this is very annoying and cannot be done with some games that use OpenGL and so have the same problem. Is there any kind of workaround to fix this? I have tried googling this problem but haven't found anything.

Thanks in advance.

---

### Post by pir4 on 2008-03-04
Same problem, no solution yet ...

---

