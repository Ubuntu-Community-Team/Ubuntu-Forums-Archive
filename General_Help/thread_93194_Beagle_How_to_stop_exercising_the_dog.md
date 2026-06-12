---
title: "Beagle: How to stop exercising the dog?"
date: 2005-11-21
forum: General Help
---

### Post by pchachte on 2005-11-21
How do I turn off the beagle setting used to speed up indexing on beagle?

I tried:  

> export $BEAGLE_EXERCISE_THE_DOG=0

but beagle still seems to rev up every once in a while when I'm working (e.g., 80% of cpu).

Otherwise, it's working great!

---

### Post by ubuntu_demon on 2005-11-21
I moved this thread. Please don't post questions in the customization section!

I think this is going to work :

$ beagle-shutdown
$ export $BEAGLE_EXERCISE_THE_DOG=0
$ beagled

---

### Post by Jad on 2005-11-24
sorry but what's teh beagle exercise dog?

---

### Post by ubuntu_demon on 2005-11-24
[QUOTE=Jad]sorry but what's teh beagle exercise dog?[/QUOTE]
it's nice when you start beagled the first time. It dedicates more power to beagled.

---

