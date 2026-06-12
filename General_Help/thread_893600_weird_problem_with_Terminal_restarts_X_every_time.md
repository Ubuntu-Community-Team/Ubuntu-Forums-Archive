---
title: "weird problem with Terminal: restarts X every time"
date: 2008-08-18
forum: General Help
---

### Post by Dan_Dranath999 on 2008-08-18
Just installed Hardy a week ago. I have a weird problem whenever i use the terminal: If i use the right or left arrow keys, and there's nowhere to go (like the end of a command, or the beginning of the command-line if there's nothing written on it yet) it makes the error noise... and then **[COLOR="DarkRed"]X JUST RESTARTS... just like when ctrl+alt+backspace are pressed.[/COLOR]**

¿It's a bug? I didn't find anything like that in the Hardy known issues thread.

---

### Post by Dan_Dranath999 on 2008-08-19
bump!

---

### Post by colobix on 2008-08-19
I dont know if this will work but heres a suggestion.
Go to add/remove, remove the terminal and install it again.
See if it helps, if not you can try to install another termrminal.

---

### Post by Dan_Dranath999 on 2008-08-19
it's not just the terminal. It happens with firefox find-feature as well:

see [http://ubuntuforums.org/showthread.php?t=813214](http://ubuntuforums.org/showthread.php?t=813214)

it seems the "error" sound has something to do with it. (i changed alsa to pulse, still no luck)

---

### Post by Dan_Dranath999 on 2008-08-23
Something weird: I have been using (downloaded and compiled) the linuxwacom driver for my wacom Bamboo, with Feisty and Gutsy, no significant problems. 

Today, my tablet started to behave strangely, and i tried to compile the driver again (have to do it every time the kernel updates, anyway) but i noted that i didn't have this problem in terminal, so i opened Firefox and tried to replicate the bug in the find-feature. It was fixed.

But my tablet was messed up.

So i compiled the driver again, and:
1.- My tablet is OK now.
2.- The bugs are BACK.

---

