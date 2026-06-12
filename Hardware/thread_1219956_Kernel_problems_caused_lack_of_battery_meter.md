---
title: "Kernel problems caused lack of battery meter?"
date: 2009-07-22
forum: Hardware
---

### Post by AICollector on 2009-07-22
I don't know a lot when it comes to the kernel, other then it's worth a few billion pounds, would take a single man 30,000 years to do by himself and includes more drivers in it then anything else on earth. 

I've recently found out, however, that a 'regression' (which I still don't understand) was the cause of why my battery works with Kubuntu 8.04 (and, oddly, Mandriva One 2009 Spring) but not with most other distros.

As this is my laptop that is going to see some heavy use very soon away from powerpoints, can anyone tell me if they experience similar problems and if there is a fix in the works? I heard something about the .30 release sorting it, but I've never been able to find the bug again to confirm. :/

---

### Post by irv on 2009-07-22
Under power manager there is a option to always show:
[ATTACH]122010[/ATTACH]

---

### Post by AICollector on 2009-07-22
Ah, I think I did not make myself clear.


After using many distros, (all of which display a power meter as they all detect this laptop as being a laptop) none can read it. They can tell me if I'm on a powerpoint or not, either way, they will say 'no battery'.


In this situation, I would revert to Kubuntu 8.04, but it cannot connect to my wireless network (it dosent seem to even be able to SEE wireless networks or hardware)

---

### Post by irv on 2009-07-22
> **AICollector said:**
> Ah, I think I did not make myself clear.


After using many distros, (all of which display a power meter as they all detect this laptop as being a laptop) none can read it. They can tell me if I'm on a powerpoint or not, either way, they will say 'no battery'.


In this situation, I would revert to Kubuntu 8.04, but it cannot connect to my wireless network (it dosent seem to even be able to SEE wireless networks or hardware)

What kind of laptop to you have? I am using a dell Inspiron 1521 and it does a good job showing the battery life.
I also had problems with wireless with version 8.10, but with the upgrade to 9.04 this problem was fixed.

---

### Post by AICollector on 2009-07-22
Found it. 

It's been patched and should be with us for Karmic.
[http://bugzilla.kernel.org/show_bug.cgi?id=11884](http://bugzilla.kernel.org/show_bug.cgi?id=11884)

---

### Post by irv on 2009-07-22
> **AICollector said:**
> Found it. 

It's been patched and should be with us for Karmic.
[http://bugzilla.kernel.org/show_bug.cgi?id=11884](http://bugzilla.kernel.org/show_bug.cgi?id=11884)

I take it you have a HP EliteBook 2730p?

---

### Post by AICollector on 2009-07-22
Nope, ASUS X50GL.

---

