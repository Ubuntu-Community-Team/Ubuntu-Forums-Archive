---
title: "&quot;Application in Terminal&quot; - How to Make Terminal Invisible or Exit on Completion?"
date: 2008-08-16
forum: General Help
---

### Post by OzzyFrank on 2008-08-16
Every now and again, I have to create an "Application in Terminal" launcher to a command or script, and while I'd prefer to just not have a terminal pop up to do the task, I'd settle for a way to have the terminal exit upon completion of the command or script. So, is there any command I can stick in the end of a script that will make the terminal exit? I gather I can't really do this with a launcher, but if this option exists, I assume it can be inserted into a script.

Also, if there is some way of getting the terminal to remain "invisible", or running in the background without actually appearing, please let me know. I gather this is not possible, but nothing would surprise me when it comes to Linux. Cheers.

---

### Post by Vivaldi Gloria on 2008-08-17
> **OzzyFrank said:**
> I gather I can't really do this with a launcher,


You can. Use a regular launcher with

```
gnome-terminal -x <command>
```

And in the second tab of the default profile settings of the gnome-terminal choose to exit after the command is executed.

---

### Post by OzzyFrank on 2008-08-17
Hmmm... mine's already set to that. Must be the default as i never changed that. Seems to be the same as making an "Application in Terminal" launcher, as the terminal shuts down both ways... after the program is closed or command finished. What I was hoping for was a way to either not have the terminal appear at all, or to make it exit once the program has been loaded.

I suppose I should clarify what I am trying to achieve here: I don't want it for a *command* as such, meaning some normal command that needs to be run in a terminal. I want to make a launcher for a GUI program that can't just be called upon in the usual manner, because **python** has to be called upon, so there is a *path, space, python, space, the-script-name*. In an open terminal it would be:

[COLOR="Indigo"]**cd ~/panelswitcher-read-only/source && python panelswitcher.py**[/COLOR]

Or the scipt I made:

[COLOR="DarkRed"][B]#!/bin/sh
cd ~/panelswitcher-read-only/source
python panelswitcher.py[/B]
[/COLOR]
with this command for the launcher to that script:

[COLOR="#8b0000"]**/home/ozzman/Scripts/./PanelSwitcher.sh**[/COLOR]

Also should clarify why this is important at all, as it may seem trivial to some. The reason is I often have 2 or more terminals open, so the less to get confused between, the better. The other reason is that occasionally I could accidentally shut down a terminal I thought I had finished with, only to see the GUI program it had loaded exit abruptly.

So, in a nutshell, what I want is to be able to load a GUI app via the terminal (or "Application in Terminal" launcher, actually) and have that terminal exit, but leave the program it loaded open.

**HEY!** Just figured it out, at least how to launch this program via the script I made, and not have a terminal appear. I never even tried making a normal "Application" launcher to the script, since I couldn't run the script double-clicking it, but found the terminal worked. Anyway, first I tried making a normal launcher to **~/Scripts/./PanelSwitcher.sh** but no-go. Tried without the extra [COLOR="#4b0082"]./[/COLOR] but no-go either, until I changed the **~** to **/home/myusername**.

OK, while we're here, can one of you terminal gurus tell me what is up with that, as I thought I could replace **/home/ozzman/** with **~/**. And how do I make a launcher to run 2 commands, as in [COLOR="Indigo"]**cd ~/panelswitcher-read-only/source && python panelswitcher.py**[/COLOR] - as that works in an open terminal, but not as a launcher (I've tried both kinds, with use of quotation marks and everything, to no avail). This would just save me making a script which I would then have to point to, just for 2 commands.

But at least I figured out a normal launcher to a normal path (without an extra ./ to invoke the script) does what I want. But I'd appreciate any answers to those 2 questions above. Cheers.

---

### Post by bingoUV on 2008-08-17
From reading your post, it is very difficult to know what you have figured out already, and what you are still asking. Short questions, separated in different points will get you more answers.

One thing I could understand. To make more than one application start from a launcher, you need to start a shell. This is because the command you give is directly executed without being passed to a shell.
e.g
```

xterm && xterm

```

This calls the executable xterm with 2 arguments: && and xterm. i.e. argument no. 1 is "&&" and argument no. 2 is "xterm".

You need to start 2 xterms, do this
```

bash -c "xterm && xterm"

```

---

### Post by spupy on 2008-08-17
> **OzzyFrank said:**
> OK, while we're here, can one of you terminal gurus tell me what is up with that, as I thought I could replace **/home/ozzman/** with **~/**. And how do I make a launcher to run 2 commands, as in [COLOR="Indigo"]**cd ~/panelswitcher-read-only/source && python panelswitcher.py**[/COLOR] - as that works in an open terminal, but not as a launcher (I've tried both kinds, with use of quotation marks and everything, to no avail). This would just save me making a script which I would then have to point to, just for 2 commands.

```
python ~/panelswitcher-read-only/source/panelswitcher.py
```

I hope I understand you correctly?

---

### Post by OzzyFrank on 2008-08-17
Hi guys. OK, **bingoUV**: sorry, I actually tried to lay it out as clearly as possible (you may notice I go to way more trouble to highlight things etc than most others out there). Also, you may note I was typing that while still trying things, so is like a running commentary (the reason being to save posting 8 different times, as I could delete things not even worth mentioning, etc). Now I have to admit I am the one confused by your instructions... is **bash -c "xterm && xterm"** to go into the launcher? Or are you saying I need to run this command in a terminal _before_ I can even consider running a launcher that executes 2 commands? (If so, that would sort of defeat the purpose, unless you can explain otherwise). Please clarify.

**spupy**: Thanks, had sort of thought of that, but hadn't gotten around to trying it. I am ignorant of things like **python**, so wasn't even sure if it was a program or just a programming language! Or whether it was more like a .dll (in Windows terms) than an .exe as such. However, seeing that **python** was being called upon before the script, it had crossed my mind to try that (then forgot all about it). So thanks, that makes perfect sense, to call python and just point to the script, rather than first changing to the folder and running python then the script into it.

---

### Post by DeathOnJuice on 2008-08-17
To run a program in the background, thus letting the terminal close, put a & at the end of it.

So, python ~/blah/script.py & should do the trick.

---

### Post by OzzyFrank on 2008-08-17
**DeathOnJuice**: Thanks, will try that when back in Ubuntu. Seems like a very handy little tidbit of info! I assume it works with anything, not just python scripts. Cheers.

Oh, so what was the verdict of my question re replacing **/home/ozzman/** with **~/**?. Does this only work in the terminal, and not in launchers?

---

### Post by mc4man on 2008-08-17
I'd just make the launcher comm. something like this
 
./scripts/amarok2
replacing amarok2 with your script name

---

### Post by OzzyFrank on 2008-08-17
Gotta love Linux - so many ways of doing the one thing! And seriously, I'm not being sarcastic here or vitriolic in the slightest!

Now to wait for more info on **[COLOR="Indigo"]bash -c "xterm && xterm"[/COLOR]** as it seems it could be a good thing to know.

---

### Post by bingoUV on 2008-08-18
put this in launcher's command field: bash -c "xterm && xterm"

And yes, ~ works in a shell. If you want to make ~ work like your home directory, again start a shell from the launcher's command. Like 
bash -c "~/scripts/yourScript"


PS: just try things out when in confusion. This is a small thing, won't damage your desktop seriously.

---

