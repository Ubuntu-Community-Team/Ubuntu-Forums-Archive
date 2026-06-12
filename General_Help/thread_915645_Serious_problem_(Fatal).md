---
title: "Serious problem (Fatal)"
date: 2008-09-10
forum: General Help
---

### Post by taamir on 2008-09-10
Hi i used ubuntu for 1-2 month without any problems but in the past two weeks It started getting stuck in the middle of work.
So that i have to use the RESET buttun on the computer..
Whan It loads back up it sometimes dosent even recognize the hard drive that Linux is installed on, sometimes couzing problems for windows as well...

PLEASE PLAESE HELP :confused::(

---

### Post by devosion on 2008-09-10
Yikes. It sounds like the hard drive itself could be suffering from the hard reboot. Can you mark when exactly you receive the hard freeze? I myself am experiencing a similar problem but have not yet been able to discover the reason for the hard freeze. Check your dmesg logs at /var/logs and try to recount the last actions that were performed before the freeze.

---

### Post by taamir on 2008-09-10
I am writing this while surffing from windows, however it happens on diffrent cases such surffing the web,listening to music watching movies... Nothig complex like games etc.

-edit-
is there a system check tool of some kind?

---

### Post by devosion on 2008-09-10
If Ubuntu is running fine besides the hard crash a system check tool wouldn't provide much assistance. The problem you are experiencing isnt as isolated as you think, earlier today I was browsing a thread that was several pages long with people recounting the same issue we are having. I havent yet had a chance to look over the entire thread but a common motif seems to be problems with wireless card configurations and drivers. Are you using a wireless card? Beyond this im not quite sure what it could be, but if you viewed your logs and posted the end of some of the logs in the path I provided there might be something there that could provide some insight to your own particular issue.

---

### Post by taamir on 2008-09-10
I'm not using wireless card..
allso I sent my computer to a lab were I bought the hard drive that I use for Ubuntu ( f: ) (some of it as NTSC - windows) they said everything is fine and gave my back the computer.
It worked fine and then again it got freeze twice in ubuntu and one in windows when I wrote to the hard drive f: .
any way I think I'll use the windows system backup and uninstall ubuntu than I'll see what goes.
too bad I kunda liked it....

---

### Post by balaknair on 2008-09-10
Hi taamir.
How old is your PC? Because this reminds me of what I experienced before my old PC(running Win2000) died taking 30GB of my data with it(autospy findings pointed to faulty motherboard and RAM modules reacting to power supply fluctuations that caused the frequent crashes, which made me hit the reset button often, which killed my ageing hard drive). So you might want to get a check up for your PC(and back up your data).


Hitting the reset button can corrupt partition tables so that they cannot be mounted, and if done frequently it can even trash your hard drive completely(been there, done that). 

Remember the ctrl-alt-del combo from windows, there's something similar in Ubuntu if you do get stuck(usually it's the GUI- XWindows- that gets stuck) you can just restart the graphic interface with ctrl-alt-backspace. This restarts the GUI without trashing your hard drive.

---

### Post by taamir on 2008-09-10
Wow it sounds like my problem Bad RAM and motherboard...
my computer really started to go slower....
now I need to prove it to the guys that "fixed" my computer they tolled me they checked it with their tools, I think Its a F*****g LIE. they are just lazy and dont want to fix my New, still under Warrenty hard-disk.

-edit-
Sorry for the language.. any one knoe ?

---

