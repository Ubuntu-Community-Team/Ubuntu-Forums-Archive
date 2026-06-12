---
title: "compiz --replace &amp;&amp;"
date: 2008-09-12
forum: General Help
---

### Post by frogotronic on 2008-09-12
Hello,

  I'm running Ubuntu 8.04.1 Gnome, and compiz works well.  I've seen where using the command

```
compiz --replace &&
```

eliminates issues with flickering videos, google earth, etc.

My questions are the following:

1) What does that command do?

2) How do I undo (reverse) it if it doesn't work/buggers the system?

- CH

---

### Post by BlackLLama on 2008-09-12
its just restarts compiz

---

### Post by EnGorDiaz on 2008-09-13
it restarts compiz

compiz is the main 3d effects compisite manager give you all those cool effects that you cant get on vista and mac

---

### Post by oobe-feisty on 2008-09-13
> **EnGorDiaz said:**
> it restarts compiz

compiz is the main 3d effects compisite manager give you all those cool effects that you cant get on vista and mac

he knows what compiz is

---

### Post by sayakb on 2008-09-13
This replaces the existing window manager with compiz. For example, if you had been using metacity, doing **metacity --replace &** would bring metacity back.

---

### Post by frogotronic on 2008-09-13
> **LinuxIsInnovation said:**
> This replaces the existing window manager with compiz. For example, if you had been using metacity, doing **metacity --replace &** would bring metacity back.

Okay thanks.  I was impressed with a friend's laptop where this command eliminated the flickering video issues.  Although he is using an nVIDIA card.

What's the difference between the single amperstand "&" and the double "&&" ; or have I got that wrong and it should be a single only?  I suspect this is a linux/debian related question as opposed to a compiz question.

- CH

---

### Post by frogotronic on 2008-09-14
Hello,

Okay, i got most of compiz figured out. The fusion button is really nice.

Two more questions:

1) Is there a workaround for the flickering issue on ATI cards? And what is the purpose of installing xserver-xgl in addition to FGLRX?  Whenever I try to install that package, the FGLRX driver doesn't load and I have no acceleration.  The fglrxinfo tells me MESA drivers.

2) I get window border corruption after suspend or hibernate.  Is there a fix, or workaround for this?

- CH

---

