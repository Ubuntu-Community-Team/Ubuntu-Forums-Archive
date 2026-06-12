---
title: "Login window administration will not open"
date: 2008-08-15
forum: General Help
---

### Post by onesojourner on 2008-08-15
I am trying to edit some things in my login window manager System>Administration>Login Window and it seems to be broken. The window pops up for a spilt second. bottom bar and says Starting administration and starting Login Window. Does any one have any Idea what would cause this kind of behavior?

Trying sudo gdmsetup also fails. The window pops up but only for a split second.

---

### Post by RealPSL on 2008-08-15
Have you tried ```
gksu gdmsetup
``` in a terminal. It might just show you what is causing the failure in the terminal window.

---

### Post by aysiu on 2008-08-15
It should be *gksu gdmsetup* and not *sudo gdmsetup*, but that won't solve the problem.

Can you paste this command in the terminal and then paste the output back here? ```
gksudo gdmsetup
``` If there's no error message, does it hang after the command or give you the next command prompt line?

---

### Post by frank392 on 2008-08-16
Hi I have the same problem, when I try "sudo gdmsetup" i get the error segmentation fault
with "gksudo gdmsetup" i get no error messages, but will not work, but I get the next command prompt line
please help

---

### Post by frank392 on 2008-08-17
Problem solved! I have install KDE 4.1 and it got fix, do not ask me how but is working now :)

---

