---
title: "[SOLVED] customizing my setup"
date: 2008-09-23
forum: General Help
---

### Post by lanr01 on 2008-09-23
I am slowly getting things setup and customized to my liking in gnome. I want to have mozilla's thunderbird load upon logging into my session. I have added a few things to session preferences for startup programs, but I can't find what file actually calls thunderbird up to load. Can anyone tell me what file it is that loads thunderbird?

sorry for what is probably a dumb question for most here..

Rick

---

### Post by russlar on 2008-09-23
Open up the menu editor, and navigate to the Thunderbird launcher. Right click Thunderbird's entry, and click Properties. That will have the command. If it only has "thunderbird %u", open a terminal and run which thunderbird. This will give you the absolute path.

---

### Post by drs305 on 2008-09-23
The default command in the main menu/internet section is "thunderbird %u".

---

### Post by nickgaydos on 2008-09-23
thunderbird %u
By the way, no question is dumb.

---

### Post by rsambuca on 2008-09-23
Can someone explain what the "%u" part does?

---

### Post by russlar on 2008-09-23
> **rsambuca said:**
> Can someone explain what the "%u" part does?

I'm guessing it's a variable, keyed to which user launches it.

---

### Post by lanr01 on 2008-09-23
what is the command line to open the menu editor? I show that it is installed, but it doesnt show under applications under other where it said it is installed..


Thanks,
Rick

---

### Post by drs305 on 2008-09-23
alacarte

---

