---
title: "[Emerald] Question about commands."
date: 2008-10-28
forum: General Help
---

### Post by AreonEpta on 2008-10-28
I'd like to know how to

1. Open a program without window decoration
2. Open a program maximized
3. Open a program in a specific desktop

all under ALT+F2. I'm trying to make it so that this stuff will open at bootup the way I want to.

---

### Post by AreonEpta on 2008-10-28
bump

---

### Post by loomsen on 2008-10-28
1)
Open ccsm --> window decoration
Klick the + under decoration window, chose and not and add the window you'd like to be undecorated.
For instance, I have got a desktop terminal, which I obv don't want to be decorated... So I added:
```

& !(title=descon)

```
To the end of the line. The exclamation mark means NOT. I match the window through its title, cause I do want other terminals I open up to be decorated. Otherwise you could specify 
& !(class=gnome-terminal)
for example to have any opened gnome-terminal window undecorated.

2+3)
CCSM -> Window Rules

Specify what you'd like to as explained above.
For example, mine looks like this:
[[img]http://img247.imageshack.us/img247/607/screenshot19uj2.th.png[/img]](http://img247.imageshack.us/img247/607/screenshot19uj2.png)

Pretty much self-explainatory I think.


*edit*
Still no use for an hourly bump.

---

### Post by AreonEpta on 2008-10-28
Thanks. That's alot of useful info I'm sure I can sort though. My question now is what do I append to a command in Sessions to make it execute in lets say, workstation 4 specifically? That way, when I boot, I know it'll be in workstation 4. I want to do this with terminal and ktorrent.

> *edit*
Still no use for an hourly bump.

Sorry. WAAYYY too used to 4chan. Yeah, I'm a /b/tard.

---

### Post by loomsen on 2008-10-28
You may specify such kind of rules through the window placement plugin.

[[img]http://img112.imageshack.us/img112/3781/screenshot20nd5.th.png[/img]](http://img112.imageshack.us/img112/3781/screenshot20nd5.png)

CCSM --> Window Management --> Place Windows

Then click on the 2nd tab, "fixed window placement"

Specify the rules as mentioned in the thread above in the second tab, Windows with fixed Viewports.

Y Viewport Position is only relevant if you use multiple desktops in vertical direction. So, assuming you have a cube with four desktops, this option has no effect for you. 

You may want to start your terminal with a specific title/profile, so that your matching is easier and unique, like for example

```
gnome-terminal --window-with-profile=deskterm4 --title=deskterm4
```  or sth like
```
gnome-terminal --role=deskterminal4
```

And then add for instance

title=deskterm4 or role=deskterm4

to your rules.

---

### Post by AreonEpta on 2008-10-30
Thanks! I got it working now. That helped alot. I really appreciate it. Two thank you's for you, my friend.

---

### Post by loomsen on 2008-10-30
Thank you too, and you're welcome :)

---

