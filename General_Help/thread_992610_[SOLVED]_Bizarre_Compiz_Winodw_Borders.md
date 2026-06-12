---
title: "[SOLVED] Bizarre Compiz Winodw Borders"
date: 2008-11-24
forum: General Help
---

### Post by crazyness003 on 2008-11-24
Hello. Not really a big problem, but i've noticed this since 7.10 and just passed it off...till now.
Okay, take a look at the attachment.

You'll notice the top two screenshots are of the windows border, and the program running  is OOo3

Now observe the rest of the screenshots. That's kinda weird.

I dont know if anyone else has these anomalies, but im not quite sure what causes them, and if it is a bug, how do i go about reporting this? and Where?

It only heppens when running compiz with the GTK Window Decorator. Whevever i turn compiz off...everything runs normally. And if I used Emerald with compiz...again, normal.

Im open to any suggestions regarding cause. I do think that its the size of memory that a windows uses affects this...but gnome-terminal? It does it with that too (and im assuming therminal dosnt take too much ram space). It dosnt happen with the GIMP tho (at leased i'v never noticed it), so yeah, my theory may be wrong.

And i know, i can always turn compiz off, or run it with emerald....but wheres the fun in that?

Thanks in advanced.

---

### Post by crazyness003 on 2008-11-26
bump?

---

### Post by Usufruct on 2008-11-26
Are you using an nVidia display driver?  It looks suspiciously like the title bar display bug that was fixed in the recent nVidia beta driver release.

---

### Post by crazyness003 on 2008-11-26
Yes I am (geForce 6800 on my desktop, and 6150 on my laptop). 
Its a driver issue? whoa!
which driver fixes this, I got the 177 right now.

But wait. I dont get this kinda behaviour when i use the Clearlooks* window border. Strange. Maybe it dosnt like a certain derivative...

Thanks for the info

---

### Post by crazyness003 on 2008-11-28
nobody has anything else to ad?

---

### Post by mosimea on 2008-11-28
What Usufruct said, it's likely an Nvidia driver-related problem.

Take a look at this:

[http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html]("http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html")

---

### Post by Usufruct on 2008-11-28
> **crazyness003 said:**
> Yes I am (geForce 6800 on my desktop, and 6150 on my laptop). 
Its a driver issue? whoa!
which driver fixes this, I got the 177 right now.

But wait. I dont get this kinda behaviour when i use the Clearlooks* window border. Strange. Maybe it dosnt like a certain derivative...

Thanks for the info

There were a few of the window borders that didn't display the bug for me.  The worst was Dust, it bugged out almost every time.  

I'm running the 180.06 beta driver, and since installing that I have not had any issues.

---

### Post by crazyness003 on 2008-11-28
> **mosimea said:**
> What Usufruct said, it's likely an Nvidia driver-related problem.

Take a look at this:

[http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html](http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html)
Thanks. I read the article and it appears that someone left a comment on there saying that if do somethign wrong. You get a tanked system.
This behavior annoys me, but not that much. Im just gonna wait it out till nvidi releases a complete driver.
Again thanks for all y'alls help.

EDIT: Im gonna mark this as solved, but im not gonna try the fix for obvious reasons
Anyone else can use at their own risk. Have funz

---

