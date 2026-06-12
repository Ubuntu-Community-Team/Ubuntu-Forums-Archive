---
title: "Installing and Running Crack"
date: 2008-11-18
forum: General Help
---

### Post by serlex on 2008-11-18
Hi

I did not know exactly where to put this; I installed a program called Crack through apt-get install Crack, however i have no idea how to run it

any ideas?

---

### Post by oldos2er on 2008-11-18
Type "crack" in a terminal.

---

### Post by serlex on 2008-11-18
ok thanks, go inside the c50a folder, type Crack <passwordfilename>, will run on the background, type ./Reporter to see results

---

### Post by pdwerryhouse on 2008-11-18
I could be wrong here, but Crack was bit old and crusty, last time I tried it, and couldn't handle shadow files that used md5 (of course, it might be updated now).

There's a better program for doing this - John the Ripper. Install it with:

```
sudo apt-get install john
```

---

### Post by serlex on 2008-11-19
Thanks, Crack can handle shadows now; however its abit tricky to setup. I have tried JTR, thats old too...

---

