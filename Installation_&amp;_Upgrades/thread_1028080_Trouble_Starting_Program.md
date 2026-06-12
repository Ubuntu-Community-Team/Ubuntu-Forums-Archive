---
title: "Trouble Starting Program"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by hoopcrazytr on 2009-01-02
Hey I probably have this in the wrong category but, I just recently downloaded PlaneShift (an MMORPG) and installed it on my desktop. (running kubuntu) Its all installed and it has the desktop shortcuts all set up but when I click them, their little icon does its bouncy business next to my mouse and at the bottom taskbar it shows it loading. It keeps bouncing and loading for like 1 minute then just completely stops and is no longer on the taskbar or next to my mouse. How do I get this program running? Please help..:(

---

### Post by melojo on 2009-01-02
open a terminal and type

```
planeshift
```

providing that is the script that starts the game

and it should give an indication why it won't run

---

### Post by hoopcrazytr on 2009-01-02
I tried that in the terminal and this is what I got

michael@michael-desktop:~$ planeshift
bash: planeshift: command not found

---

### Post by melojo on 2009-01-02
can you right on the icon and then properties and then type and change it to open in terminal.

---

### Post by hoopcrazytr on 2009-01-02
i right clicked on it and set it to run in terminal, when I did that and clicked back on the program...the black terminal screen came on for like 5 seconds then went off. No text appeared in the terminal and nothing happened.

---

### Post by melojo on 2009-01-02
here is a link
[http://www.planeshift.it/guide/en/installation-running.html](http://www.planeshift.it/guide/en/installation-running.html)

linux is the same for unix

looks like psclient is the script

to execute a script put     ./       in front of it

that is a period and foreword slash put it in front of psclient

---

