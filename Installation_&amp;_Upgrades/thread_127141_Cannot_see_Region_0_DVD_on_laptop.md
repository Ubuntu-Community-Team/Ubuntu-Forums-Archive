---
title: "Cannot see Region 0 DVD on laptop"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by eiffel on 2006-02-08
hi - i wonder if anyone can help me with a small problem I've been having since buying a new laptop.

The DVD drive is a QSI DVDRW 041 and plays DVD region 2 discs (I'm in Britain) just fine.  However, if I put a Region 0 disc (legally bought from a British high street shop) in there I can't even see it, let alone play it.

I've tried setting the drives region to 0 using regionset but that doesn't seem to work, and anyway would seem like a bad solution as it limits the number of changes to 5.

The disc plays fine on my workstation with the same software setup.

---

### Post by jimbob on 2006-05-08
According to the /usr/share/doc/regionset/README file there is no such thing as region 0.  Maybe that is why it wouldn't take.

Looks like you can use the regionset command to determine where your drive is currently set without it counting as one of your 5-allowed changes as long as you exit before executing.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by FrancoNero on 2006-07-08
> **jimbob said:**
> According to the /usr/share/doc/regionset/README file there is no such thing as region 0.  Maybe that is why it wouldn't take.

Looks like you can use the regionset command to determine where your drive is currently set without it counting as one of your 5-allowed changes as long as you exit before executing.
&#65279;

crap. I also need a program that would effortlessly trick my DVD drive into any region beyond those 5 changes

---

