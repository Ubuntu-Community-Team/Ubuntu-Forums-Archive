---
title: "Laptop - CPU Temperature - How to change FAN-ON threshold?"
date: 2010-10-21
forum: Hardware
---

### Post by zxMarce on 2010-10-21
Hi, noob post.

Been using Ubuntu 9.10 since 2009, then upgraded to 10.04 in May. Machine is a Toshiba Satellite L305-S5919:

[LIST]
[*]Celeron 585 (single core)
[*]2GB RAM
[/LIST]
I noticed that, when my fan starts, the air that comes out is pretty hot. Always had the laptop rest on a flat surface (normally a table) at the office or at home - NEVER ON CLOTH.

Hunted hi & lo (Google, these here forums), finally got a temp applet. The fan triggers at 80°C; way too hot IMHO.

So, my questions are:

[LIST]
[*]Is there a way to fiddle with the trigger temperatures, so the fan would start spinning at -say- 50°C? How do I do that?
[*]Can anyone list all the temperature triggers for the fan, and/or where are these trigger values fetched from? I mean Turn-On Low speed, Turn-On Hi speed, and Turn-Off.
[/LIST]
TIA,
zxMarce.

---

### Post by P4man on 2010-10-21
THis might help:
[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

But not all laptops support it. Often the bios takes care of it and you have no control over it, but its worth trying.

---

### Post by zxMarce on 2010-10-28
Been reading, could not make heads nor tails from it :confused:
Way over my (still Windozed) brains :eek:
Will continue trying, tho. It will have to fit in sometime!

Thanks for the fish,
zxMarce.

---

### Post by P4man on 2010-10-28
Not as difficult as it looks, once you get over the "terminal fear" :)

Essentially you copy/paste those commands in a terminal (applications | accessories | terminal). The first commands are "cat" which simply shows the contents of a file. 

In linux, everything is a file. Even if its not residing on a physical medium like a harddrive, its part of the filesystem. Running processes, devices, etc, they are part of this filesystem. So if your machine supports these instructions, there will be a file you can just check the contents of, and some others to edit to change its behavior.

If you prefer, you can do so graphically with the file browser too, just go places | select anything, click on "filesystem" in the left and drill down the folder structure and double click to open those "files". Though its not quite the same, think of it as regedit in windows.

IMportant: at some point the link I gave tells you to "sudo kate blahblah". Dont do that, kate is a text editor for KDE (Kubuntu) and you wont have it installed.  Replace 'kate' with 'gedit' the default gnome text editor. Also dont use sudo (which you put before a command to run it with root permissions) but **gk**sudo which is the same, but for graphical apps, rather than terminal apps.


Last hint: to paste something a terminal, just click on the middle mouse, or press shift+control+v. Let me know if you get stuck anywhwere.

---

