---
title: "Interesting laptop problem"
date: 2005-11-14
forum: General Help
---

### Post by izzydahedgehog on 2005-11-14
I have an older (had it for the past 4 years or so) Dell Inspiron 8200 (specs coming later, I'm typing this while at work doing an English paper) with a very interesting problem.

After it's been on for more than an hour or so, it starts slowing down A LOT.  When it slows down, the fans start running full blast, and the fans don't run at all before it does this.  This leads me to believe that the problem is with the system overheating.

One of my friends suggested that it could be a memory leak in Kubuntu, so I installed FreeBSD where it does the same thing.  While they are both using KDE, I don't think the problem is in the desktop environment.  I'll try some other distributions to see if installing them fixes the problem, but I'm doubtful.

Has anyone else experienced this kind of problem?  Anyone have any ideas?

---

### Post by 23meg on 2005-11-14
Try typing "ps aux" in a terminal to see if any processes are eating up close to full CPU power when the slowdown occurs.

---

### Post by nim278 on 2005-11-14
I have had a similar problem before that turned out to be caused by having too much swap space. How much RAM do you have vs. how big is your swap drive?

Maciej

---

### Post by Sloth on 2005-11-14
You need to clean your fan nd/or heatsink.  Here's what is happening:

As you are using your machine, your CPU is heating at.  At some point, the CPU will start to get too hot and the fan will come on to reduce the temps.  Because of blockage on your heatsink or fan, that's not working and eventually your CPU is going into thermal overload and is starting to slow waaay waaaay down in order to avoid burning itself out.

This has nothing to do with Ubuntu, really, except maybe it's using more CPU so you are getting there more quickly.

Just take a vacuum to the fan and heatsink.  I bet you find a big old dust bunny in there.

---

### Post by mlomker on 2005-11-14
Sloth is right on.  My Emachines laptop had poor ventilation and would actually shut itself off due to a lack of cooling...popping out the keyboard and cleaning the vents took care of it.

They also make [fan bases]("http://www.topmicrousa.com/byalnoco.html") for laptops...I have one even though it isn't necessary with my new laptop.

---

### Post by izzydahedgehog on 2005-11-16
Thanks everyone.  There *was* quite a bit of dust in the heatsink and fans.  However, after putting it back together it won't turn on.  :-(  It was mostly a guinea pig computer at this point anyway.

---

### Post by Butterfly on 2005-11-17
Open it again and make sure everything is connected properly. 

I have a laptop that was not working after I opened it.  Turns out a card was not pushed in enough.  so check the cable and the card to make sure there is no play when you push them.  You might be able to save your guinea pig :)

---

### Post by kairu0 on 2005-11-17
[QUOTE=mlomker]My Emachines laptop had poor ventilation...[/QUOTE]

You have an e-machines laptop? I can no longer respect you as an "ubuntu master roaster" lol

---

### Post by mlomker on 2005-11-18
[QUOTE=kairu0]You have an e-machines laptop? I can no longer respect you as an "ubuntu master roaster" lol[/QUOTE]

Did you notice that was past tense?  :D

---

### Post by joshuapurcell on 2005-11-18
I had an older Dell Inspiron laptop, and the thing slowed down noticeably (and fans started up if they wern't already) when updatedb began.

---

