---
title: "display dying? weird problem"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by Caligula on 2007-06-15
Hello all,
I've noticed a weird problem with my display. 
I left my laptop (dell Inspiron 1501 with Ubuntu Feisty) for about one hour, and when I came back I was (un)wellcomed by a black screen that just refused to be anything other than black. I tried changing tty's, and all that kind of stuff, but the only thing that worked was to switch it off with the power button.

I have a ATI Radeon Xpress 1150 256MB HyperMemory (integrated) graphics card and run XGL & Beryl, don't know if that should matter.

I thought maybe somehow the X server has crashed, because it's the same symptom, but I have no idea. 
My worst fear is that it's a hardware issue, it's a new laptop.... could it be a problem with the fglrx drivers or something?

Please tell me it's not a hardware problem :(

Thanks for any reply.

---

### Post by fabertawe on 2007-06-15
I'm having a problem with ttys being offset about a third of the way down (and off) the screen which I think are down to the latest Nvidia driver (it's the only change to my system recently). Restarting GDM from one of these ttys results in a loss of signal to my monitor, which then goes to sleep, necessitating a reboot via the button on the front of my case. You're obviously not using the Nvidia driver but maybe our two instances are related somehow.

Paul

---

