---
title: "japanese keyboard"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by cjm on 2005-04-21
hi... i'm pretty much a complete newbie, so please bare with me...

i've freshly installed ubuntu 5.04 on a machine with a japanese keyobard.

unfortunately, the ] key returns a \ instead.  i guess this is something to do with the keyboard not being set with the correct key mapping, but i'm not sure how to go about fixing it.

oh, and i've installed it on a total of three different machines with japanese keyboards and all do the same.

can anyone help,

thanks in advance.

---

### Post by Sam on 2005-04-21
I'm not really sure that it's the answer. When I installed Ubuntu I set my keyboard layout during the installation. When entering gnome, it was back to the default one. I had to set it again in the keyboard preferences window. Maybe it's the same problem.

---

### Post by cjm on 2005-04-21
cheers sam... you were dead on.  changed the listed 105-key setting to the correct 106-key one.  guess i should have figured out that one by myself.

a big thanks!

---

### Post by Sam on 2005-04-21
You're welcome ! :-P


BTW welcome to the Ubuntu forum.

---

### Post by an9n on 2005-07-18
[QUOTE=cjm]hi... i'm pretty much a complete newbie, so please bare with me...

i've freshly installed ubuntu 5.04 on a machine with a japanese keyobard.

unfortunately, the ] key returns a \ instead.  i guess this is something to do with the keyboard not being set with the correct key mapping, but i'm not sure how to go about fixing it.

oh, and i've installed it on a total of three different machines with japanese keyboards and all do the same.

can anyone help,

thanks in advance.[/QUOTE]
 If you are not running gnome you might benefit from the doing the following;
(I am running fluxbox, en_US-UTF8, japanese Happy Hacking Keyboard and constantly switch to and from swedish keyboard layout)

setxkbmap -model MODEL_NAME -layout LAYOUT_NAME


In fluxbox, I have setup the following keykommands for switching between keyboards:

.fluxbox/keys:
Shift F11 :ExecCommand /usr/X11R6/bin/setxkbmap -model pc105 -layout se
Shift F12 :ExecCommand /usr/X11R6/bin/setxkbmap -model jp106 -layout jp


 I hope this helps someone.

---

