---
title: "Log in menu reappears when I try to log in, cant get in"
date: 2008-08-31
forum: General Help
---

### Post by raakken on 2008-08-31
After I have typed my password and hit enter, the screen goes black and then the log in menu reappears. I have no idea what to do. It is possible to log in terminal, but when i try to start a program, it only says that there is something wrong with the display/ or I should reconfigure DISPLAY. I have a lap top Toshiba Portege s100 with a nVidia GO 6200TE 64mb graphics card. Im using Kubuntu 8.04. I tried and boot into recovery mode which is usually the second choice from the grub and use the xfix option to correct my display, but this didnt work either... Pleas help me, Im completly lost, and I really need my lap top for school tomorrow...

---

### Post by ellgor on 2008-08-31
Hi,I'm sorry I haven't got the definite answer but I do know that it is the KDM manger that is the cause (been there) I found out later that it gets stuck in a loop and keeps presenting the login screen, knoowing this you can look around for a specific fix, or, take a look at the Kdm settings in:
/etc/kdm/init.d/conf
hope this helps.

Regards, Ellgor

---

