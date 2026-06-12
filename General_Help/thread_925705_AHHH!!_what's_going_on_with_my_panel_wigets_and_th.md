---
title: "AHHH!! what's going on with my panel wigets and the panel?"
date: 2008-09-20
forum: General Help
---

### Post by Hyper Tails on 2008-09-20
Help! my laptop runs vista and hardy and i installed kde 4.1 over 4.0 and while updrading the panel got messed up and  the clock won't move it just stays in the middle and i accadently deleted that panel and now it's on the top and now i can't get them back!!

Could someone help please

thank you

---

### Post by Hyper Tails on 2008-09-21
..........................................................................................................................................................................................................................................
.............................................................................................

---

### Post by awakatanka on 2008-09-21
rename your .kde4 to somthing else and the ctrl-alt-backspace it may help but you need to reconfigure all.

---

### Post by Hyper Tails on 2008-09-21
how do i rename my .kde 4?

---

### Post by Tyl3r on 2008-09-21
rm -rf /$HOME/.kde4

---

### Post by SuperSonic4 on 2008-09-21
Wouldn't that remove KDE4? I'm not sure if the OP [who has an inherently awesome username btw] wants that.

I suggest you make a backup of .kde4 first although I don't know how to use the terminal to backup. What does resetting X do? Also what graphics card do you have? If it's nvidia you might have to disable a secondary screen if applicable

---

### Post by nowshining on 2008-09-21
i believe the .kde4 folder in /home/username is where all the kde4 config files are...

---

### Post by Hyper Tails on 2008-09-22
> **nowshining said:**
> i believe the .kde4 folder in /home/username is where all the kde4 config files are...
I checked there and i don't see it

any more help that i can use in konsole?

---

### Post by awakatanka on 2008-09-22
I hate typing commands so i always use mc in konsole for that kind of things. Very handy prg and used it also in my dos time ( norton commander ;-)

Dolphin >> view >> show hidden files                Right click on .kde4 >> rename

---

### Post by Hyper Tails on 2008-09-22
my wigets and panels are still the same when i renamed it

any other advice?

---

### Post by benerivo on 2008-09-22
Log out of kde, then do Ctrl+Alt+F1. Then log in as yourself and do```
mv .kde .kdeBACKUP
```then Ctrl+Alt+F7 and log back in.

---

### Post by Hyper Tails on 2008-09-22
all that did was reset my desktop effects

what else can i do to reset my panel and panel wigets?

---

### Post by awakatanka on 2008-09-23
> **Hyper Tails said:**
> Help! my laptop runs vista and hardy and i installed kde 4.1 over 4.0 and while updrading the panel got messed up and  the clock won't move it just stays in the middle and i accadently deleted that panel and now it's on the top and now i can't get them back!!

Could someone help please

thank you

Try to unluck widget with right click desktop. Then right click panle and go in panel settings, drag it to where you want it. For the plasmoid if you hover above it then you see option to use.

Rename /.kde4 also resets the panel and plasmoid it will be put back to default state

---

### Post by semitone36 on 2008-09-23
> **Hyper Tails said:**
> the clock won't move it just stays in the middle and i accadently deleted that panel and now it's on the top and now i can't get them back!!


Okay.  This seems like a pretty easy fix.  Right click the clock on the panel and if "lock to panel" is checked, uncheck it.  This will allow you to move the clock to any other position on the panel you want (so long as the other icons on your panel are also unlocked).

As far as getting your panel back (i dont have my comp on me at the moment so I cant test this) I believe that if you still have at least one panel you can right click the panel, select "preferences" and somewhere there should be an option to add another panel back to your desktop. Hope this helps

---

### Post by awakatanka on 2008-09-23
> **semitone36 said:**
> Okay.  This seems like a pretty easy fix.  Right click the clock on the panel and if "lock to panel" is checked, uncheck it.  This will allow you to move the clock to any other position on the panel you want (so long as the other icons on your panel are also unlocked).

As far as getting your panel back (i dont have my comp on me at the moment so I cant test this) I believe that if you still have at least one panel you can right click the panel, select "preferences" and somewhere there should be an option to add another panel back to your desktop. Hope this helps
Add panel is possible if widget are unlocked with a right click on the desktop and then right  click on desktop again and the otion to add panel is there also.

---

