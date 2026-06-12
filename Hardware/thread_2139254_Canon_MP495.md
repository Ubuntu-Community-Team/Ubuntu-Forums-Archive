---
title: "Canon MP495"
date: 2013-04-26
forum: Hardware
---

### Post by Metalman4life on 2013-04-26
[SIZE=3][FONT=georgia]My Canon MP495 was set up via USB, was recognised in Ubuntu and printed successfully. Today,
under printer options in System Settings, the printer is not detected; a message reads, "Printing service not available. Start the service on this computer or connect to another server", followed by a CUPS error. If I go to print a document only the 'generic printer' is available. 

[SIZE=3]T[/SIZE]houghts? 

(Ubuntu 12.10, 64bit)
[/FONT][/SIZE]

---

### Post by pdc on 2013-04-26
when I google 

I guess you don't tell us which version of ubuntu; or if it is 32bit or 64bit .....can you help us there..............

> [COLOR="#EE82EE"]Printing service not available. Start the service on this computer or connect to another server[/COLOR]

I get this 

[http://ubuntuforums.org/showthread.php?t=1778698](http://ubuntuforums.org/showthread.php?t=1778698)

in post #3 Matthew goes to some lengths to describe what he did to fix the problem;

I wonder if this would help you?

_____________________________________

neil in post #4 suggested 2 commands helped him:

> sudo apt-get purge cups

and 

> sudo apt-get install cups --install-suggests

.........as to why all this is happening on your computer ................goodness knows ........... can you advise of any unusual activity?

---

### Post by Metalman4life on 2013-04-27
Thanks buddy, the commands worked perfectly. It certainly seemed quite  weird because afaif I had not changed anything significant. No unusual  activity that I'm aware of. I wonder what the causal agent was. . .

---

### Post by pdc on 2013-04-27
glad that all is working now; alarming to be hit by such things "out of the blue" but good all is now working

---

