---
title: "Loop bug in the Terminal?"
date: 2008-07-16
forum: General Help
---

### Post by espressobeanies on 2008-07-16
Why is it that when you open the terminal and just type 'yes', the terminal will go into a continuous loop of the letter 'y'? Was some dev just trying to be funny?

---

### Post by dracayr on 2008-07-16
nope. It's a program in one of the most basic packages of GNU. It even has a manpage:
man yes
I only once had to use it: while configuring a package, I piped
yes ""
into the config questions :D

dracayr

---

### Post by espressobeanies on 2008-07-16
oh. okay. Thought it was an easter egg or something.

---

