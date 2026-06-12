---
title: "Parallel port device driver problem"
date: 2008-10-10
forum: Hardware
---

### Post by BogdanRosandic on 2008-10-10
Hi, 
I hope someone could help me with my problem... I have tested my  driver for some LEDs  without removing kernel modules like lp, parport_pc, ppdev, parport.. and it worked..Now the problem is that it doesn t work when I remove those modules. I didnt pay much attention to this untill i tried to implement API for interrupt handling..The problem is one of those module holds the interrupt line which I need..

THANK you in advance!!!!!!!!

---

### Post by iponeverything on 2008-10-10
> **BogdanRosandic said:**
> Hi, 
I hope someone could help me with my problem... I have tested my  driver for some LEDs  without removing kernel modules like lp, parport_pc, ppdev, parport.. and it worked..Now the problem is that it doesn t work when I remove those modules. I didnt pay much attention to this untill i tried to implement API for interrupt handling..The problem is one of those module holds the interrupt line which I need..

THANK you in advance!!!!!!!!

cat /proc/interrupts 

and you can see what is holding what.

---

### Post by BogdanRosandic on 2008-10-10
OK thanks but I already tried that... and it says that parport0 holds IRQ 7 which I need. When I remove parport_pc IRQ 7 is free and I can take it , but then nothing can be written in parallel port, my LEDs cannot light..That s actually a problem :)

---

### Post by BogdanRosandic on 2008-10-10
Is there a way to take away IRQ line from a module without removing it....Or setting that module to load without  IRQ line at boot time?

---

### Post by amnuwan on 2008-11-18
> **BogdanRosandic said:**
> Hi, 
I hope someone could help me with my problem... I have tested my  driver for some LEDs  without removing kernel modules like lp, parport_pc, ppdev, parport.. and it worked..Now the problem is that it doesn t work when I remove those modules. I didnt pay much attention to this untill i tried to implement API for interrupt handling..The problem is one of those module holds the interrupt line which I need..

THANK you in advance!!!!!!!!

I have the same problem. Exactly this one. I'm trying to understand what parport_pc do which my driver doesn't. But so far i have found nothing. This should be a problem of Ubuntu. Because i tried codes from the book "Linux Device Drivers 3rd Ed" and same thing happened. Dear kernel hackers please fix this bug or tell us the way.

---

### Post by BogdanRosandic on 2008-11-18
This is how i solved the problem..it's not a real solution but it works;)
i'll just type commands for starting module called timer.ko


2.rmmod lp *(needed for removing parport_pc)*
3.rmmod parport_pc  *(now nobody holds irq line)*
4.insmod parport_pc.ko io=0x378 irq=none  *(inserting parport_pc but irq line is free!!!)*
5.insmod timer.ko
6.rmmod parport_pc
7.insmod lp.ko    *(this include insmoding parport_pc but irq line is already taken by timer.ko)*[/I]

this should work,i tried it myself;)

---

### Post by amnuwan on 2008-11-19
BogdanRosandic, Tell me if you find a better solution than that, In your case you only needed an IRQ to be released from parport_pc. I need both 0x378 and IRQ 7 to be free. Because I'm developing something like parport_pc. Did above solution allow your interrupt handler to be called upon external interrupts. I'm curious about the thing this parport_pc do. You know , inb and outb consist with single assembly instructions, which means its guaranteed that they goes to CPU and start execution. So why the hell data doesn't come to the port.
                                  Nuwan

---

