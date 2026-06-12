---
title: "Bloatiness"
date: 2008-08-16
forum: General Help
---

### Post by Unanimated on 2008-08-16
I've noticed recently that my computer has been running slowly (mainly in games), so I opened System Monitor and lo and behold, about 230MB of my 750MB processor is being taken up, even when I'm just looking at the desktop with nothing (except Tracker and gnome-panel) running. I know you're going to need more information to help me, and I don't know the command to list out all the processes. So... yeah. I really want that number to go down.

---

### Post by iaculallad on 2008-08-16
> **Unanimated said:**
> I've noticed recently that my computer has been running slowly (mainly in games), so I opened System Monitor and lo and behold, about 230MB of my 750MB processor is being taken up, even when I'm just looking at the desktop with nothing (except Tracker and gnome-panel) running. I know you're going to need more information to help me, and I don't know the command to list out all the processes. So... yeah. I really want that number to go down.

You could post whatever displays when you issue the command below on your terminal so we could take a look at what application/process are eating your CPU/memory resources.

```
top
```

---

### Post by p_quarles on 2008-08-16
The main thing to remember here is that memory management in Linux is dynamic compared to Windows. The fact that 230 MB of memory are being used at any given time is neither a problem nor an explanation of why certain programs are running slowly. 

You could try, of course, killing some background processes and seeing if game play speeds up, but I doubt that will do much. You are more likely looking at sub-optimal performance from your graphics card.

---

### Post by Unanimated on 2008-08-16
Attached is an image of my output, because it changed too much to be able to copy it.

@quarles: I don't think it's my graphics card, because before I reinstalled Windows and formatted my Ubuntu installation (X.X), I had the Tremulous graphics settings almost maxed out, and it ran fine on most occasions. While that might be the problem, I don't think it is.

NOTE: I had Amarok, Firefox, and Tracker running when I put in the command.

---

### Post by danwood76 on 2008-08-16
To find out how much memory is acrtyually free its best to use:
```

free

```

This command gives output on ho much memory is free, cached, and swapped.
If you see a lot of swap this could be a problem with not enough RAM (unless you are doing something that hits a lot of memory)
A lot of cached memory is normal and helps speed up the system.

---

### Post by Unanimated on 2008-08-16
[FONT="Courier New"]             total       used       free     shared    buffers     cached
Mem:        775280     347876     427404          0       6696     188092
-/+ buffers/cache:     153088     622192
Swap:      1277128     199512    1077616
[/FONT]

There's my output.

---

### Post by Unanimated on 2008-08-16
bump

---

### Post by Unanimated on 2008-08-16
bump

---

### Post by fragos on 2008-08-16
I think you are assigning meaning to the numbers that may not be correct. Games in particular can be real power hogs.

---

### Post by p_quarles on 2008-08-16
> **Unanimated said:**
> bump
Don't do that: it's rude.

---

### Post by dexter on 2008-08-16
Did you install a graphic driver (nvidia/ati/...) for your system?

---

### Post by Unanimated on 2008-08-16
Yes.

---

