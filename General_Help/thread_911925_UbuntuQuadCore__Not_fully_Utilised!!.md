---
title: "Ubuntu/QuadCore : Not fully Utilised!!"
date: 2008-09-06
forum: General Help
---

### Post by jadhav333 on 2008-09-06
I tested a cpu intensive fluid simulation on Blender 2.47. While the operation was in progress, I checked the CPU usage. 

Of the 4 cpu cores at any given time only 1 cpu was utilised at 100%, the rest were utilised at between 8-15%

Why is that I am not utilising the full capacity  of each core?

What can I do to optimise the utilisation of my system capability?

Pls find my system spec in my signature.

Thanks

---

### Post by jadhav333 on 2008-09-06
Anybody?

---

### Post by txcrackers on 2008-09-06
Blender (and a vast majority of **all** programs) are not written with multi-CPU systems in mind. The OS's are multi-CPU capable (obviously), but in order for the programs to spread the load, they have to be written specifically to do that. Otherwise (as is your situation), a program will get "locked" to a single CPU/core for a period of time by the OS.

Of course, the nice thing is while Blender's maxing out one of your CPUs/cores, you have 3 others to do other things with at the same time...

---

### Post by jadhav333 on 2008-09-06
Is it so :(

and I was und the impr. that my quad core would give me blazing fast render performances. This is not so good :( . Feels like I have been cheated :P

---

### Post by cybrsaylr on 2008-09-06
The same thing has been going on with dual core PCs that also experience this and dual cores have been around longer than Quad cores and the new Tri cores.

---

### Post by Jimmey on 2008-12-29
There is an option in blender to specify the number of cores you want to use (I think on the render - F10 - Panel).
By clicking the "threads" button (far left) you can specify the minimum number of threads to use. Four should be fine on quad.

---

### Post by brucewestfall on 2009-02-21
So did that do the trick?  Have you tried the setting in blender telling it how many processors to use?

I would love to find out if it worked!

---

### Post by Maheriano on 2009-02-21
I read somewhere else on this forum that Linux doesn't yet have any support for quad cores, it's dual core maximum right now.

---

### Post by mcduck on 2009-02-21
> **Maheriano said:**
> I read somewhere else on this forum that Linux doesn't yet have any support for quad cores, it's dual core maximum right now.

That's nonsense. Normal Linux kernels supports 32 CPUs/cores on 32-bit systems, and 64 CPUs/cores on 64-bit systems. Of course this can be changed and Linux clusters scale up to thousands of processors.

The thing here is that your programs need to run in multiple threads to get any benefit from multiple processors/cores. And not all programs do this, or even can do it since many tasks simply cannot be divided into separate threads. Blender supports quad cores but only for rendering, just do what jimmey suggested to increase the number of threads used for rendering.

edit: the current worlds fastest supercomputer, Roadrunner, has 129600 cores and runs Linux.. ;)

---

