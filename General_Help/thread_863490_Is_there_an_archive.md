---
title: "Is there an archive?"
date: 2008-07-18
forum: General Help
---

### Post by sugarplumfairy on 2008-07-18
I'm just curious, but when you're computer keeps these system logs, does it just keep them for one day? Do they get automatically deleted? How can you access the archive where i can look at what i was doing last week?

---

### Post by hal8000 on 2008-07-18
There are many messages and logs on every unix system. However its not "spyware" as such.

If you use the unix terminal to lauch commands and programs then
.bash_history can be read to see what commands you typed, the history can be set to store 500 lines or so you can can trawl through this file to see what you typed.

The system log keeps track of system commands and messages keeps track of what the kernel is doing. Often these logs are useful and should be kept to refer back to if something went wrong. A program called log rotate compresses the logs and archives them. Most of the logs are kept in /var/log/ directory.

Thats a simplified explantation to help you.

---

### Post by sugarplumfairy on 2008-07-18
so if you're trying to cover your trail you have to delete the .bash_history files AND the files in the /var/log? Yes, sounds dodgy, but it's not really, just said i was somewhere else when i wasn't...

---

