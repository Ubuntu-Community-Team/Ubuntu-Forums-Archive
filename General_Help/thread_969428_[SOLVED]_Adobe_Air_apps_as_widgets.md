---
title: "[SOLVED] Adobe Air apps as widgets?"
date: 2008-11-03
forum: General Help
---

### Post by lifestream on 2008-11-03
Mmm not sure if this is the right place, but:
How would I go about make Adobe Air run as Widgets? Could I possibly tell Compiz that any Adobe Air apps should behave as widgets?

If not, are there other ways? I'm loving Adobe Air :3 

Thank you :)

---

### Post by loomsen on 2008-11-03
I don't know adobe air, but compiz has a widget layer plugin.

Enable it and specify which windows you'd like to be handled by it.

[RegEx window matching](http://ubuntuforums.org/showthread.php?t=968859)
[example](http://georgia.ubuntuforums.com/showthread.php?p=6061456)

---

### Post by lifestream on 2008-11-03
Ack! 
Yeah, I knew of it, but I thought I would be too dummy to figure it out! All I really got to do it hit the (+), click my app, and it goes on the widget layer! Lovely!

Thank you!

---

### Post by lifestream on 2008-11-03
Grrr!
It seems I can only have ONE widget at the same time?


(class=Doomi)      --->    Shows the Doomi
(class=Cairo-clock)       --->    Shows the Clock
(class=Cairo-clock) & (class=Doomi)      --->     Shows none
(class=Doomi) & (class=Cairo-clock)      --->      Shows none


Pleh! What am I doing wrong? :P

---

### Post by loomsen on 2008-11-03
> (class=Doomi) & (class=Cairo-clock) 

If you speak it out loud it would read:

class is Doomi AND class is cairo-clock

Thats prlly not what you want. 

You'd want this:  (class= Doomi | Cairo-clock)

Would read:

class is doomi or class is cairo-clock

If you're linking two different regexes, like lets say for example all windows with title foo_bar and all dockbars

(title=foo_bar) | (type=dock)

meaning: 
all, where title is foo_bar or all of the type dock or both.

So, linking with a & creates another CONDITIONAL rule, you might want to use that if you want only windows with a special title to be ruled, but not all windows of the same type.

For instance, I have a deskterminal, tho, if I launch a terminal manually, through a launcher or such, I want it to be decorated.

Under decorated windows I'd add:
!(title=deskterm) & (class=gnome-terminal) 

Reading: decorate all windows, where the title is not deskterm but it's class is gnome-terminal.

Just read it out loud.

---

### Post by lifestream on 2008-11-03
Oh. I'm a dummy :P
You were right, Compiz put & there automatically, so I assumed it would know better ^^; 
Thank you so much, I will be sure to share should someone else ask.

---

### Post by Vadi on 2008-11-03
Ooh... great idea. AIR fan here too.

(but man that click-through bug is annoying)

---

