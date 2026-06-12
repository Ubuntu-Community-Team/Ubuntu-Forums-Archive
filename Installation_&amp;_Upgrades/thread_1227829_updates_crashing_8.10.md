---
title: "updates crashing 8.10 ??"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2009-07-31
I am helping a friend with his laptop it has kubuntu 8.10, and is showing that there are 157 updates waiting to be done.

I try to do the updates (adept) and immediately the packages begin to come down, a crash occurs:

kde crash handler
the application adept updater (adept_updater) crashed and caused the signal 11 (SIGSEGV)

any suggestions please about what I should do?
tia

---

### Post by ajgreeny on 2009-07-31
Just use the terminal ```
sudo apt-get update
``` then ```
sudo apt-get upgrade
```However, it begs the question "why is adept crashing?" so perhaps it's worth trying to use adept first just to reinstall adept itself, or try ```
sudo apt-get install --reinstall adept
```then try using adept again to do the updates.

---

### Post by candtalan on 2009-07-31
Thank you for the response and suggestions.

I had tried these, although with adept, I used the synaptic gui method for the reinstall of adept, CL for the others.
However, unfortunately it did not change to problem.

I had to cut my losses and reinstall completely, and chose 8.04.3 for the friend. 

In fact he found Ubuntu simpler and easier to use than kubuntu, so that is what I installed.

Thanks again!

---

