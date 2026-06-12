---
title: "[SOLVED] Testing an individual process for multi-core use"
date: 2008-08-28
forum: General Help
---

### Post by jvincent08 on 2008-08-28
I just compiled a program from source and enabled an option (when running ./configure) that supposedly enabled multi-threading support (I chose POSIX.. that's what I was supposed to, right?). Now I know you can run top to see the total CPU usage for all your cores, but I was wondering if there was a way to test an individual process to see if it's actually multi-threaded. Is there anything like this in the plethora of Linux tools? Thanks in advance. :)

---

### Post by Predator106 on 2008-08-28
Alright, I think this is the command you are looking for, I just uncovered it after some digging with the terminal.

ps aux -L | grep pidgin

To find the threads for pidgin. I think this is what it is, but not entirely sure :).

---

### Post by jvincent08 on 2008-08-28
> **Predator106 said:**
> Alright, I think this is the command you are looking for, I just uncovered it after some digging with the terminal.

ps aux -L | grep pidgin

To find the threads for pidgin. I think this is what it is, but not entirely sure :).

Hmm.. well, I executed that with the program in question, xchat, and it printed two copies of xchat. That sounds right, because I have two cores, so if multi-threading were enabled, it should spawn two threads. However, I tested it on firefox, and I got several copies, at least 5. That doesn't sound exactly right to me, but according to man, -L *does* "show threads." :confused:

---

### Post by Predator106 on 2008-08-28
Noo noo nooo no, you're confusing the amount of cores you have (physical processors) with the amount of threads a process has. 

A process can have 50,000 bajillion threads, that doesn't mean that you need to have that many cores to run it. 

Threads are a way of a process breaking itself up into sections. A process running on one thread, especially one that deals with networking or immense I/O would be very slow. That is also why certain badly programmed-programs you see, when you click download or save it will freeze up and not respond at all(typically with windows). 

Multi-threaded applications allow one part of a process to do it's work, say UI, and another handle the I/O (networking, etc.). That way the program is still left responsive.

The operating system itself will evenly divide(depending on Niceness value) each thread of the process, and each process of the stack, amongst the CPU time. You can have one core, but still have a ton of threads for one process, because the operating system splits this up, executing only an instruction (or a handful of) at a time. 

This way it is displayed the "illusion" of multi-tasking. Remember, computers don't actually multi-task all that well, better than humans, but that is because they can balance it efficiently. 

True multi-tasking would be performing multiple (instructions) at the same EXACT time. This is not possible (yet) with computers, although they are immensely efficient at it(especially linux :) ).

---

### Post by jvincent08 on 2008-08-29
> **Predator106 said:**
> Noo noo nooo no, you're confusing the amount of cores you have (physical processors) with the amount of threads a process has. 

A process can have 50,000 bajillion threads, that doesn't mean that you need to have that many cores to run it. 

Threads are a way of a process breaking itself up into sections. A process running on one thread, especially one that deals with networking or immense I/O would be very slow. That is also why certain badly programmed-programs you see, when you click download or save it will freeze up and not respond at all(typically with windows). 

Multi-threaded applications allow one part of a process to do it's work, say UI, and another handle the I/O (networking, etc.). That way the program is still left responsive.

The operating system itself will evenly divide(depending on Niceness value) each thread of the process, and each process of the stack, amongst the CPU time. You can have one core, but still have a ton of threads for one process, because the operating system splits this up, executing only an instruction (or a handful of) at a time.
Ohh, I thought that there were only as many threads as there were cores. So if the process reports that it has two or more threads, I can be sure that it's taking advantage of both my cores, right? This is what I'm looking for.

> **Predator106 said:**
> True multi-tasking would be performing multiple (instructions) at the same EXACT time. This is not possible (yet) with computers, although they are immensely efficient at it(especially linux :) ).
I thought that multicore systems could do this. Even though you have multiple processors, the computer can't perform two things at once? One action using the first core, and the other action using the second? I thought that was the whole point in multicore processors..


While we're on the subject, is GCC multi-threaded? When performing large software compilations, top reports only about 50% CPU usage.

---

### Post by Predator106 on 2008-08-29
Yes, if it has at least the amount of threads that you have cores, then it is taking advantage of it. 

Well with a multi-cored system, you do still have to wait for access times to/and from memory, without conflicting with the other core. In other words, it has to wait it's turn in line to access data that is stored. This is typically where the cache L1 and L2 caches come into play, faster and each core get's one (I think). For instance, if you try to say... uhm convert a movie file to a different format while simultaneously copying a movie from a very fast hard drive (faster than the one that is being copied to). You will notice that your CPU will not be used very much, and the HDD is maxed out in I/O demands. When you try this with a fast hard drive to a fast hard drive, your CPU would be used more frequently.

Most of the CPU requests, when not able to go through their own caches have to make requests to the Northbridge. And to top it all off, the CPU will make requests to the Northbridge to send/receive data to the Southbridge (PCI, Ethernet, etc.)


If it seems to be capped at 50% , it probably isn't using both cores.

---

### Post by jvincent08 on 2008-08-29
> **Predator106 said:**
> Yes, if it has at least the amount of threads that you have cores, then it is taking advantage of it. 

Well with a multi-cored system, you do still have to wait for access times to/and from memory, without conflicting with the other core. In other words, it has to wait it's turn in line to access data that is stored. This is typically where the cache L1 and L2 caches come into play, faster and each core get's one (I think). For instance, if you try to say... uhm convert a movie file to a different format while simultaneously copying a movie from a very fast hard drive (faster than the one that is being copied to). You will notice that your CPU will not be used very much, and the HDD is maxed out in I/O demands. When you try this with a fast hard drive to a fast hard drive, your CPU would be used more frequently.

Most of the CPU requests, when not able to go through their own caches have to make requests to the Northbridge. And to top it all off, the CPU will make requests to the Northbridge to send/receive data to the Southbridge (PCI, Ethernet, etc.)

If it seems to be capped at 50% , it probably isn't using both cores.

Many thanks for the information, everything makes sense now :)

---

### Post by Predator106 on 2008-08-30
Your welcome.

---

