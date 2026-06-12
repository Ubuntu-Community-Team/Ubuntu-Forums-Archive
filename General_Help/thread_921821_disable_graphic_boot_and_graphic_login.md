---
title: "disable graphic boot and graphic login"
date: 2008-09-16
forum: General Help
---

### Post by linex on 2008-09-16
hi,
i just installed xubuntu. i would like to get rid of the graphic boot and the graphic login. i would like to see what's going on during the boot, text only. once xubuntu boots up, i want to login via the prompt. 

i'm hoping i can start xfce using xwindow once i login.

my second question is, how do i add more colors to my terminal. i tried out linux mint. in linux mint the terminal had three or four colors. my username was one color, the system name was a different color, diffrent types of outputs were different colors. how do i enable this?

thanks

---

### Post by Pro-reason on 2008-09-16
You can get rid of the graphical splash screen by changing the option in /boot/grub/menu.lst.  Removing the usplash and splashy packages would probably do it too.

I imagine that if you just deleted GDM, Xubuntu would drop you into a log-in prompt at start-up.  It would have no other choice.

You can set colours in ~/.bashrc.  I believe that the code to do so is already there, commented out.

---

