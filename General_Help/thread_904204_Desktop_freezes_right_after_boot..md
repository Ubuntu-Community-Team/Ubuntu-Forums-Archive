---
title: "Desktop freezes right after boot."
date: 2008-08-29
forum: General Help
---

### Post by Briped on 2008-08-29
I can't access my ubuntu 8.04. Right after boot the desktop shows up and looks normal, but there's no response to mouse clicks. This means that I can't open the terminal or do anything at all. My top bar gadget showing processor and HD show activity for a few seconds and then flat line completely. My only way out is to turn it of is using the power button. A very quick touch, and the screen shows the following [http://pedersen.brygge.dk/skaerm2.jpg](http://pedersen.brygge.dk/skaerm2.jpg) and [http://pedersen.brygge.dk/skaerm1.jpg](http://pedersen.brygge.dk/skaerm1.jpg). Please excuse the blurred pics, I have to be somewhat quick on the 'trigger'.

 I have not altered any settings,  but for some weeks it has been oddly unstable. For example taking 1-2 minutes to give me the shut down screen after clicking 'quit', nautilus not reacting to certain commands ctrl + a nor shift + del, generally freezing up every now and then, but I don't know if these minor nuisances bear any relevance to my present major problem.

I run a dual boot, and my XP partition boots and works.

You probably need more details in order to diagnose the problem, but as I don't know which, please ask. Also, please be very explicit as I only understand newbie language.

It may be a bit pointless to add this, but I really would appreciate your help. I haven't found any thread dealing with a similar problem, but any link is greatly appreciated too, of course.

Thanks,
Britta

Added info: Documents on the desktop behave normally. It's only 'applications, places and sytem' as well as most other icons in the top bar I can't access - making the pc useless.

---

### Post by Sam Lars on 2008-08-29
So are you saying that the mouse moves fine but you can't click on anything?
Can you switch to a terminal with Ctrl+Alt+F1, restart X with Ctrl+Alt+Backspace, or reboot with Ctrl+Alt+Del?

---

### Post by Briped on 2008-08-29
> **Sam Lars said:**
> So are you saying that the mouse moves fine but you can't click on anything?

The mouse moves fine, yes. I can click on and open documents on the desktop, but none of the menus and only a few of the icons on the top bar react to clicks. 

> **Sam Lars said:**
> Can you switch to a terminal with Ctrl+Alt+F1,

I wasn't aware of that possibility, but will try when I get a chance in 3 hours time.

> **Sam Lars said:**
>  restart X with Ctrl+Alt+Backspace yes

> **Sam Lars said:**
>  reboot with Ctrl+Alt+Del? no

---

### Post by Briped on 2008-08-30
Yes, ctrl + shift + F1 does give me the terminal. I altered the thread title as the desktop is not as frozen as I thought initially. Can anybody tell me which command would help me find out what causes the problem?

Kind regards,
Britta

---

### Post by Sam Lars on 2008-08-30
Have you done anything with Nautilus scripts?  I heard that if you have a bad script in it, it will freeze like that.
Also, have you tried KDE or some other environment to see if it freezes, too?

---

### Post by Voorhees1979 on 2008-08-30
I had this and it was the panel, Try and open the terminal and type "killall gnome-panel" without the "

Then restart the panel as it will shrink on your desktop see if you can click the panel then

---

### Post by Briped on 2008-08-31
> **Sam Lars said:**
> Have you done anything with Nautilus scripts? 

I wouldn't even know how :confused:
 
 > **Sam Lars said:**
> have you tried KDE or some other environment to see if it freezes, too?

I wouldn't even know how :confused:

Honestly - I'm innocent. No messing about that would explain it. It worked sort of fine (apart from the before mentioned buggy behaviour) till suddenly one morning. Maybe some update messed up something? That's my theory.

Thanks,
Britta

---

### Post by Briped on 2008-08-31
> **Voorhees1979 said:**
> I had this and it was the panel, Try and open the terminal and type "killall gnome-panel" without the "

I 'killedall' gnome-panel in the terminal (alt + F2 didn't bring up the run dialog), switched back to the desktop which was now blank, except for top and bottom panel being faintly outlined, but empty too. Went back to the terminal, which didn't understand 'gnome-panel' to restart it, so rebooted, but it's status quo. I got my frozen panels back.

Much as I dislike this solution, I think I will have to re-install. I hate it because it doesn't teach me what went wrong and because I won't know how to avoid ending up in the same situation in the future.

Anyway, thanks for the help/suggestions to both of you.

Britta

---

