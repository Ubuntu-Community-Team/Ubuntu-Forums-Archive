---
title: "code to enable wireless on startup?"
date: 2008-09-06
forum: General Help
---

### Post by jimmgunnz on 2008-09-06
i have an odd situation, maybe someone can help.

ubuntu plain old locks up on me upon login... when networking.
if i have an ethernet cable plugged in when starting up...
it locks up.
if my wireless drivers are enabled while starting up....
it locks up.

so... i basically blacklisted all of my potential wireless drivers for startup, which prevents my lockup on startup problem.  
but each time upon restart, i need to open a terminal and enter sudo modprobe <module> to re-enable my wireless.

it's not THAT big a deal, but i'm wondering if there is something i can do to my /boot/grub/menu.lst possibly, or somewhere else even that will allow me to automatically enable the wireless after startup but not during startup??

or am i just stuck with my re-enabling step every time??

help is appreciated!!

---

### Post by jimmgunnz on 2008-09-06
okay, so i just created a launcher on my desktop.
i guess that'll do.
but since it's a command that requires sudo, i needed to create the launcher for an application in terminal.  
then i just need to pop in my password and my wireless is there.

so... it there any way to modify the launcher code so that i can sudo and get the password in there in one motion??

thanks for help!!

---

### Post by borobudur on 2008-09-25
Why don't you write a shell script and give it the execute permission?

---

