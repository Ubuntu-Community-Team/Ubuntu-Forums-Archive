---
title: "gnome &quot;brown screen of LAGGGGG&quot;"
date: 2005-12-04
forum: General Help
---

### Post by Trab on 2005-12-04
ive asked this question before, but no one has been able to help me, probably because i didnt explain it well enough...


when i boot up my compter, it goes through the bios...
then it goes to grub, i select ubuntu and it starts booting...
it goes through the bot sequence just fine, sure its a bit slow, but not bad...
then it could do either of 2 things...
if i dont have auto login enable, it goes to the login screen... i select my user enter my password... and it goes to a brown screen.... and just sits for like... 5 minutes... i dunno wat its doing...
if i do have auto login enable, it does the same thing...
after about 5 minutes, it finally loads up everything, and runs fine...

if from the login menu i login as root (The only other user i have on my machine) it works fine...loads up instantly...

it lags if i hit ctrl+backspace to drop outta X and restart stuff too....


its very annoying, to the point of dreading rebooting my machine...like i need to do right now.....

it still does this despite a few reinstalls of ubuntu...

but my /home dir has not been changed, because its on a diff partition...
i think its something to do with my /home dir...

thanks
-Trab

---

### Post by Bachstelze on 2005-12-04
You're certainly right. Which filesystem is your /home partition ?

---

### Post by Trab on 2005-12-04
i beleive its ext3...
and its a "recent" issue (actually its probably a month old) but in the year or so ive had my home partition, its survived at least like 4 different linux systems (1 mandrake and 3 ubuntu...) and it just started randomly....(well probably not randomly, but i cant remember wat i did)
:-/

any way to check wtf its trying to do during that time?
i dont hear the machine thinking until RIGHT before it loads all the panels and background and stuff...

all i have is the brown screen, and the mouse... right click doesnt work...

switch to a terminal via ctrl+f1 works fine...

thanks

---

### Post by Trab on 2005-12-05
bump?

come on, this cant be something difficult, would someone please help me?

---

### Post by tlc on 2005-12-05
Got the same problem here. Just installed on an Opteron/nforce4 combo. Install went fine, get to the gdm login screen, select username/pwd and it just sits there forever.

Tried booting in safe mode, installed xfce4 but startxfce4 gets me the rat background and a blank panel/taskbar.

I'll try setting up a different user when I get home tonight, and see if logging in as root makes any difference.

---

### Post by neutronstar on 2005-12-05
[QUOTE=Trab]
when i boot up my compter, it goes through the bios...
then it goes to grub, i select ubuntu and it starts booting...
it goes through the bot sequence just fine, sure its a bit slow, but not bad...
then it could do either of 2 things...
if i dont have auto login enable, it goes to the login screen... i select my user enter my password... and it goes to a brown screen.... and just sits for like... 5 minutes... i dunno wat its doing...
[/QUOTE]

Select "Log out", then select "save session" before rebooting or shutting down.
Try doing this once, it worked with me.

---

### Post by tlc on 2005-12-05
Trouble is, you can't select anything at all when this happens. I might have found the answer though:

[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

I'll try it when I get home.

---

### Post by xmastree on 2005-12-05
[QUOTE=Trab]any way to check wtf its trying to do during that time?

switch to a terminal via ctrl+f1 works fine...[/QUOTE]Log in to that terminal, and run ```
top
```That will tell you what's running.

---

### Post by Trab on 2005-12-05
[QUOTE=xmastree]Log in to that terminal, and run ```
top
```That will tell you what's running.[/QUOTE]

doesnt ps -LA do the same thing?

ill try those 2 things...

thanks mates!

---

### Post by Trab on 2005-12-05
worked like a charm!


just wondering, do i have to have that checked every time i do it?

not that it matters....

but i already have my session start up stuff configed elsewhere, wanted to know if i should undo that first...


thanks

-Trab

---

