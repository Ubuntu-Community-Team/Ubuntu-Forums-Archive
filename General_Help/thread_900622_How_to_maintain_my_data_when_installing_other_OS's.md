---
title: "How to maintain my data when installing other OS's?"
date: 2008-08-25
forum: General Help
---

### Post by maxmanapple on 2008-08-25
I'm about to migrate from Ubuntu to DSL and wanna know how can my data (userfiles, themes, etc.) can be called from Ubuntu to DSL. I'm planning to format after install but i have a second hard drive where my docs are.

How can I do this?

Any help...well, any help appreciated!

By the way, as stated I have second HDD, but I have to mount it manualy. How can I turn it into auto-mount?

---

### Post by aysiu on 2008-08-25
Let me get this straight.

So you have two hard drives.
Hard drive 1 has Ubuntu on it.
Hard drive 2 has data on it.

You want to make it so that...
Hard drive 1 has Damn Small Linux on it and
Hard drive 2 has data on it... and the data drive automounts at bootup?

---

### Post by maxmanapple on 2008-08-25
> **aysiu said:**
> Let me get this straight.

So you have two hard drives.
Hard drive 1 has Ubuntu on it.
Hard drive 2 has data on it.

You want to make it so that...
Hard drive 1 has Damn Small Linux on it and
Hard drive 2 has data on it... and the data drive automounts at bootup?

Not really.
HD 1 has Ubuntu
HD 2 has data

I want to make so that
HD 1 has DSL (now I'm headed to Dreamlinux too)
and
HD 2 has data.

Then I want to know how to make the OS automount HD 2 when I login.

How can I do it?

---

### Post by aysiu on 2008-08-25
Which OS do you want to have automount HD 2? Ubuntu? DSL? Dream Linux?

---

### Post by maxmanapple on 2008-08-25
On any of those, but, for now, Ubuntu

---

### Post by -Zeus- on 2008-08-25
no offense but you might get better support on the forum of the OS you are migrating *to*, not the one you are leaving. :-P  although you seem to be doing pretty well here.

---

### Post by maxmanapple on 2008-08-25
> **-Zeus- said:**
> no offense but you might get better support on the forum of the OS you are migrating *to*, not the one you are leaving. :-P  although you seem to be doing pretty well here.

I'm only trying to kill Ubuntu of my system because, the way i's working on my PC, you'd better call him Damn Slow Linux. I'm sure there's worse, but Ubuntu qualifies. Unless there is a Ubuntu flavor that is very small, there's no other chance.

---

### Post by -Zeus- on 2008-08-25
> **maxmanapple said:**
> I'm only trying to kill Ubuntu of my system because, the way i's working on my PC, you'd better call him Damn Slow Linux. I'm sure there's worse, but Ubuntu qualifies. Unless there is a Ubuntu flavor that is very small, there's no other chance.
xubuntu is very small.  try it; run this command
```
sudo apt-get install xubuntu-desktop
```

When it asks which login manager to use, pick xdm.  then log out and log back in and you should have much faster performance

---

### Post by aysiu on 2008-08-25
> **maxmanapple said:**
> On any of those, but, for now, Ubuntu
This might help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

