---
title: "How do I compile GTK?"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by grs on 2009-02-06
I'm trying to get ettercap running, when I try launching it I get:

GTK support not compiled in ettercap

How to go about setting this up?

---

### Post by Partyboi2 on 2009-02-06
You need to install ettercap-gtk package
```
sudo apt-get install ettercap-gtk
``` Or search for ettercap-gtk in synaptic.
Then start with
```
ettercap -G
```

---

### Post by grs on 2009-02-06
The first line of code you gave me did the trick.

Thanks

---

### Post by grs on 2009-02-06
I'm having trouble with the program now. When I start it up with

sudo ettercap -G -n 255.255.255.0

it start fine, select Sniff/Unified Sniffing then select the interface eth1. Nothing happens for a few moments then the windows fades to grey and seems to freeze.

Any ideas why this might be happening?

---

### Post by Partyboi2 on 2009-02-06
Is there any output in the terminal that might give any idea of what has happened?

---

### Post by grs on 2009-02-06
Just reads 

```
ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA
```

I am running Ettercap through the GUI so once the above appears the application opens in a different window.
The manual give advice on running it through terminal, but I can't seem to get anything  from it.

---

### Post by LHYX on 2010-04-10
> **grs said:**
> Just reads 

```
ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA
```I am running Ettercap through the GUI so once the above appears the application opens in a different window.
The manual give advice on running it through terminal, but I can't seem to get anything  from it.

I'm having the same problem.
did you solve it in the meantime ?
please help :)

---

