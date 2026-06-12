---
title: "Does Ubuntu recognise 1GB memory?"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by arunsub on 2005-08-09
I read somewhere in the forum that Ubuntu doesn't recognize 1GB or greater memory and we have to use smp kernel. Is that true? If so, What's the memory limit for Ubuntu with default kernel?

---

### Post by DJ_Max on 2005-08-09
[QUOTE=arunsub]I read somewhere in the forum that Ubuntu doesn't recognize 1GB or greater memory and we have to use smp kernel. Is that true? If so, What's the memory limit for Ubuntu with default kernel?[/QUOTE]
 Where did you hear this from (what thread)? The smp is for multiple processors. I don't think there is a restriction on memory.

---

### Post by Saru san on 2005-08-09
AFAIK 32 bit machines have 4GB of addressable memory, 64 bit machines have about 2TB

---

### Post by PeP on 2005-08-09
yep 1 have 1Gb and 'only' 896 MB are used because I use a ubuntu kernel compiled with default options

smp kernel is for multiple processors IIRC.

you can recompile your kernel and enable support for larger ram, you will find many infos on how to do that the debian way on the net.

I personally do not care cause a larger memory in the kernel require a larger indexing so it is not sure that the 100 more Mb will be a real gain compared to the current solution: default kernel and restricted modules (driver for my graphic card and wifi) easily upgradable through apt-get)

---

### Post by Saru san on 2005-08-09
Odd... well for what it's worth here's the output of free from the 2.6.10-5-686-smp kernel```
$ free
             total       used       free     shared    buffers     cached
Mem:       1036008     917740     118268          0     107192     652140
-/+ buffers/cache:     158408     877600
Swap:       522104       2752     519352
```

The machine has 1Gb installed btw

---

### Post by luca_linux on 2005-08-09
You don't need the SMP kernel, but the 686 one, instead of the 386 you're surely running (aren't you?).

---

### Post by az on 2005-08-09
Yes, that is the max for the 386 kernel.  If you are running a box that can only run that kernel, you would only be able to install that much memory anyway.

Install the k7, 686 or smp kernel, whichever suits your cpu (686 is intel, k7 is amd)

---

### Post by N'Jal on 2005-08-09
I found that after installation of the 686 kernel my P4 system just locks up, i think that for some intel processor's there is a bug in the 686 kernel, perhaps it's version's before hyperthreading, since my P4 can't hyperthread.

---

### Post by Juergen on 2005-08-09
> perhaps it's version's before hyperthreading, since my P4 can't hyperthreadI have such an old thing, too ;-)
The 686 Kernel runs fine here, though.

---

### Post by arunsub on 2005-08-24
[QUOTE=azz]Yes, that is the max for the 386 kernel.  If you are running a box that can only run that kernel, you would only be able to install that much memory anyway.

Install the k7, 686 or smp kernel, whichever suits your cpu (686 is intel, k7 is amd)[/QUOTE]
How do I compile K7 kernel? Can you point me to the guide?

---

### Post by Ride Jib on 2005-08-24
[QUOTE=arunsub]How do I compile K7 kernel? Can you point me to the guide?[/QUOTE]


just use synaptic.

---

### Post by arunsub on 2005-08-24
[QUOTE=Ride Jib]just use synaptic.[/QUOTE]
How safe is that? How good are the chances that the system will reboot without any problem after compiling? Just curious.

---

### Post by graigsmith on 2005-08-24
i use the stock k7 ubuntu kernel.  my system see's my whole gig of ram.

---

### Post by arunsub on 2005-08-25
What I would like to know is, WIll the system keep my current configurations, programs installed etc after installing K7 kernel? Do I have to do any setup after installing the kernel? I have Athlon 64 2800+.

Edit: I installed K7 kernel and it's headers and rebooted the machine without any problem. Thanks everyone for the help.

---

### Post by cfgtech on 2007-03-29
Speaking of  processors I have 8 Xeons processors I guess I need the SMP kernel then...
I d/loaded just the x86 version but do not see SMP.will look around some more

---

