---
title: "have 32-b, but system info is showing 64."
date: 2013-08-09
forum: Hardware
---

### Post by saadane_othmane on 2013-08-09
I m new to ubuntu
my laptop proc is 32-b (i was a windows user ), but now sys info says that it is 64-b. Is that normal ?
Ps : I m using ubuntu 13.04 .

---

### Post by Netstatus on 2013-08-09
Is '64-b' what is actually says?

---

### Post by sanderj on 2013-08-09
> **saadane_othmane said:**
> I m new to ubuntu
my laptop proc is 32-b (i was a windows user ), but now sys info says that it is 64-b. Is that normal ?
Ps : I m using ubuntu 13.04 .

Open a terminal, and type

```
uname -a

```
Post the output here.

---

### Post by ibjsb4 on 2013-08-09
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
lshw
```

The first line says:

description: Computer
    width: 32 bits

Which means Im running a 32bit operating system

Then a few lines down it reads ***-cpu**

and says

width: 64 bits

Which means I have a 64bit computer

Whats yours say?

---

### Post by Netstatus on 2013-08-09
My guess is that it'll say practically the same and was misread.

---

