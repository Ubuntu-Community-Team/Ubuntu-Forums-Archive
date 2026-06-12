---
title: "help"
date: 2008-08-10
forum: General Help
---

### Post by katabarwa on 2008-08-10
i just installed ubunt and after i typed in my password it told me to wright a command i did and it just kept saying "david@ubuntu:~$"
is their some sort of command I'm suppose to put int to get to the home page please help.

---

### Post by iaculallad on 2008-08-10
> **katabarwa said:**
> i just installed ubunt and after i typed in my password it told me to wright a command i did and it just kept saying "david@ubuntu:~$"
is their some sort of command I'm suppose to put int to get to the home page please help.

Homepage? You're already in your home directory as indicated by the ~ sign with a user mode ($) terminal. If you're trying to access the net, you could just navigate Applications->Internet->Firefox Web Browser.

---

### Post by loboc on 2008-08-10
you are at a prompt in a terminal and the screen is all black with white text?

---

### Post by zxscooby on 2008-08-10
Is the problem that the desktop/Graphical user interface is not loading and you are only getting a command prompt screen?
if so try typing startx and see what happens.

---

### Post by katabarwa on 2008-08-10
if thats the problem how do i fix it?

---

### Post by zxscooby on 2008-08-10
It could be any number of problems related to your configuration. Maybe with your graphics card driver. 
Does it give an error message?

---

### Post by katabarwa on 2008-08-10
when i had windows vista every thing worked fine.

---

### Post by zxscooby on 2008-08-10
What command does it tell you to type?
What happens when you type startx?

---

### Post by katabarwa on 2008-08-10
i used to have ubuntu  on my computer and every thing was goo but i rebooted the computer and it went away so i ordered a disk from the home page and they sent me 2 disks a brown one and a caramel color one so i installed the brown one and now their is a just a black screen with white letters and it keeps telling me "david@ubuntu:~$" is their any way to get to be normal. i don't know what to do because my brother was the one who installed it the first time know his not here.

---

### Post by katabarwa on 2008-08-10
when i typed that in it told me to install it then i tried then it said it can't find it.

---

### Post by Bucky Ball on 2008-08-10
When you type;

```
sudo apt-get install ubuntu-desktop
```

Does it tell you it is already installed? If it doesn't this command will load the desktop.

Did you install from Desktop GUI type installer or 'alternate' text based installer? In the text based version, you may have omitted to install the desktop (I have done that when first getting into it).

:)

---

