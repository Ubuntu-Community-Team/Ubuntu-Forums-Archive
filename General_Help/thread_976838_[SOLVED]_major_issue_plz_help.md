---
title: "[SOLVED] major issue plz help"
date: 2008-11-09
forum: General Help
---

### Post by acegik on 2008-11-09
i im having a big problem with my ubuntu. i have ubuntu 8.10. 
my problem is: you when tou open limewire or amarok or pidgin and you close it they stay in the upper tray until you right click in them and close them, well i open those programs and they dont stay in the tray but they still open.
i already try to delete the panel and make a new one and it didnt work, this issue appear when i installed ubuntu 8.10.
does anyone has the same issue i have?
plz im going crazy how to find a fix for my problem plz help me ohh i also have compiz running but i already try to turn it off and it didnt fiz my problem.

ps: if you help me ill share a secret with well that is if you dont know it already is about how to download music from slacker.com

---

### Post by fooman on 2008-11-09
instead of clicking the x in the upper right corner to close the program use the quit command from within the program.

for example...open pidgin,  then to close it click on "buddies" in the toolbar and at the bottom you will see "quit".

in amarok,  click "engage" and quit will be at the bottom.

---

### Post by acegik on 2008-11-09
k thanx, but what i want is to fix the problem becauuse thanx to this issue i cant install compiz icon.

---

### Post by acegik on 2008-11-09
oh ive just have reinstall the gnome panelks from sypnatic package manager but it didnt fix the problem

---

### Post by soro2005 on 2008-11-09
*never mind, sorry*

---

### Post by acegik on 2008-11-09
k thanx no prob, i was able to find the solution by accident lol. if u ever get this problem just type in terminal this.

gconftool --recursive-unset /apps/panel && killall gnome-panel

---

### Post by acegik on 2008-11-09
wsell you thanx for answering in my need of help, if u r interested to know how to download music from slacker.com just let me know

---

