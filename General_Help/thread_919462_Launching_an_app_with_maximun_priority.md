---
title: "Launching an app with maximun priority"
date: 2008-09-14
forum: General Help
---

### Post by piousp on 2008-09-14
Hi everyone!
Just a quick a question (i guess):
**How do i lauch an app with a -20 niceness?**

Why you say? Well, the app i wanna nice its wow. Right now, i run it normally, and then i open a terminal, and renice the process with a -20.
My idea its to get a minor perfonce improvement. Now that i say it, does it work that way? MAN says it gets better scheduling, so i'm guessing i'll get that minor performance improvement i want, right?

Actually, this is how i open it:

```

nice -20 wine /home/piousp/Aplicaciones/World_of_Warcraft/Wow.exe -opengl

```
But when i check the niceness of wow, it has the regular 19. Any advice?

---

### Post by piousp on 2008-09-14
Bump!

---

### Post by piousp on 2008-09-16
Anyone? Any ideas?

---

### Post by bingoUV on 2008-09-16
For more priority, you need to be root. Try sudo. 

But then WOW might run as root, which you will not want. The following might work, assuming your username is piousp. If not, replace piousp with your username.
```

sudo nice -n -20 su piousp -c 'wine /home/piousp/Aplicaciones/World_of_Warcraft/Wow.exe -opengl'

```

The command that you ran earlier decreased the priority of the process to minimum. It was not the "regular" 19. 19 is the least priority.

Lastly, I don't think it will help you get better FPS unless there are many other activities happening on the PC which slow down WOW.

---

### Post by glotz on 2008-09-16
If you do renicing be careful. Should you use -20 as mentioned above, your system will lock up.

I suggest you rather install a light weight window manager like fluxbox and switch to it when you play to gain a much bigger improvement.

---

### Post by piousp on 2008-09-16
> **glotz said:**
> If you do renicing be careful. Should you use -20 as mentioned above, your system will lock up.

I suggest you rather install a light weight window manager like fluxbox and switch to it when you play to gain a much bigger improvement.

First of all, thanks for your answers.
I did try a niceness of -20 and i notice a slight improvement when there were a lot of stuff happening on screen. Otherwise, i could not notice any real difference.

> **bingoUV said:**
> For more priority, you need to be root. Try sudo. 

But then WOW might run as root, which you will not want. The following might work, assuming your username is piousp. If not, replace piousp with your username.
```

sudo nice -n -20 su piousp -c 'wine /home/piousp/Aplicaciones/World_of_Warcraft/Wow.exe -opengl'

```


Yay thanks, i'm gonna try it that way and i'll let you what happens.

I guess i'll have to go with a WM after all. Oh well.

Thanks again,

---

