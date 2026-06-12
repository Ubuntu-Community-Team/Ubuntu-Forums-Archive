---
title: "Question about drivers"
date: 2008-08-12
forum: General Help
---

### Post by F4T4L FL4W on 2008-08-12
Well I put in a pci card ethernet card and it has an installation cd. Well I am new to ubuntu. I opened the cd and found the linux driver. It said to put it in the src folder but for someone reason my access is denied. I am the only person on my computer. Is there a way to get access to it? I just installed ubuntu today and I think I am admin. Or is there a simpler way to all of this?

---

### Post by benign on 2008-08-12
> **F4T4L FL4W said:**
> Well I put in a pci card ethernet card and it has an installation cd. Well I am new to ubuntu. I opened the cd and found the linux driver. It said to put it in the src folder but for someone reason my access is denied. I am the only person on my computer. Is there a way to get access to it? I just installed ubuntu today and I think I am admin. Or is there a simpler way to all of this?

Your not root (admin). You can do root commands from the terminal by typing "sudo" before the command, or "sudo su" and then entering your password, but it's only good for one terminal session.

Can you paste the instructions for installing the driver? I might be able to help you, but I don't really have a clue why you'd need to move it to the "src" folder.

---

### Post by Mgiacchetti on 2008-08-12
**WARNING** -- Please BE CAREFUL when following this, you can SERIOUSLY MESS UP YOUR SETUP if you dont know what your doing.

that being said

open a terminal
(accessories > terminal)

type
gksudo nautilus

hit enter.
type YOUR password and hit enter

YOU ARE NOW IN NAUTILUS AS THE ROOT USER  ---  DO NOT DELETE ANYTHING THAT YOU DO NOT KNOW WHAT IT DOES

that being said again.

you *should* now be able to follow the instructions to the end

WHEN YOU ARE FINISHED USING ROOT PRIVILIGES, CLOSE NAUTILUS AND TERMINAL

---

### Post by prankst3r on 2008-08-13
> **F4T4L FL4W said:**
> Well I put in a pci card ethernet card and it has an installation cd. Well I am new to ubuntu. I opened the cd and found the linux driver. It said to put it in the src folder but for someone reason my access is denied. I am the only person on my computer. Is there a way to get access to it? I just installed ubuntu today and I think I am admin. Or is there a simpler way to all of this?

Unless you are familiar with building from source, I would suggest you tread lightly. Certainly not discouraging you, just a word of caution.

---

### Post by F4T4L FL4W on 2008-08-13
I am just following the directions.

---

