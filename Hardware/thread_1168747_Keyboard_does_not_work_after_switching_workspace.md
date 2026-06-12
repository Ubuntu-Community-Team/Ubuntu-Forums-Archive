---
title: "Keyboard does not work after switching workspace"
date: 2009-05-24
forum: Hardware
---

### Post by Muppy on 2009-05-24
Dear all,

I have installed Hardy on different laptops (Acer TravelMate, ASUS R1F, and two other ASUS) and every laptop shows the same problem: after switching the workspace by clicking on the workspace switcher, the keyboard does not work anymore (compiz and metacity, no difference). The same is true when popup-windows (e.g. tooltips) appear: after they are gone, the keyboard won't work anymore. Minimizing the application or moving the window helps and the keyboard is working again. However, that's extremely annoying, especially when developing software in Eclipse where every few seconds such a popup window comes up (which I like and appreciate).

Today I have installed the alpha version of Karmic on the ASUS R1F, hoping that this problem disappeared, but, unfortunately, it hasn't.

The xorg.conf is on all laptops as it came "out of the box", no changes.

What can I do? This problem really bothers me.

Thanks for your help in advance!

Cheers,
Manfred

EDIT: I just found out that this problem only affects those windows that had the focus before. Selecting another window on the workspace also solves the problem. However, this finding still wouldn't make using Eclipse any better...

---

### Post by Muppy on 2009-05-25
Well, answering myself, found the solution and want to share it here, just in case someone runs across the same problem:
1. open a terminal
2. sudo aptitude install scim-bridge-agent scim-bridge-client-gtk scim-bridge-client-qt scim-bridge-client-qt4
3. sudo gedit /etc/X11/xinit/xinput.d/scim
4. change the line with GTK_IM_MODULE to:
   GTK_IM_MODULE="scim-bridge"
5. change the line with QT_IM_MODULE to:
   QT_IM_MODULE="scim-bridge"
6. save the file
7. reboot (or kill the X server with Ctrl-Alt-Backspace)

Credits for this solution go to: [http://sweemengs-tech-world.blogspot.com/2008/02/fixing-ubuntu-keyboard-problem.html](http://sweemengs-tech-world.blogspot.com/2008/02/fixing-ubuntu-keyboard-problem.html)

---

### Post by nerollo on 2011-07-10
this isn't working for me in 11.04, any other ideas?

---

