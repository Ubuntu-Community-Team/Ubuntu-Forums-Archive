---
title: "[SOLVED] Makefile troubles"
date: 2008-07-13
forum: General Help
---

### Post by upchucky on 2008-07-13
I have a little project I am trying to get working.

it is to set up a keypress for ventrilo, I got it untarred but I don;t know enough about make to go further, the instructions are vague, or i just dont know enough to understand the install. could someone be kind enough to look at it and write step by step instructions please.

---

### Post by pauper on 2008-07-18
First, install compiler tools:

```
sudo apt-get install build-essential
```

Now, let's assume ventriloctrl-0.3 directory located on ~/Desktop

Change directory to Make file location:

```
cd ~/Desktop/ventriloctrl-0.3
```

There is no Configure script, so proceed to compiling:
```

make
```

README states that installing is not yet implemented.

To run the program:

```
./runctrl.sh
```

---

### Post by upchucky on 2008-07-19
Thank you very much, I was in the wrong directory when i was trying to make it.

---

